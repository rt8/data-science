# AWS Lambda 

## Lambda Design Pattern
This design pattern achieves builds REST webservice with these attributes:
- highly available
- Asynchronous
- scalable
- event driven 

 
1. Route 53
2. API Gaetway (using https)
3. Lambda (async front door to enqueue and writes message to SNS)
4. Simple Notification Service (triggers another Lambda to do processing)
5. Lambda (retrieves message from SNS to do processing)
6. output to RDS, Email, another REST web service ...

## Lambda handler 
Code pattern for writing Lambda handlers
```python
import boto3
import json
def lambda_handler(event, context):
 try:
  ... a block of code
  return json.dumps({"result":"success", "message":"task completed"})
 except Exception e:
  return json.dumps({"result": "fail", "message":"ERROR: %s" % str(e)})
```

## Update function code (Boto3)
Use Python Boto library to update lambda function code
```python
import boto3
import zipfile
import sys

FUNC_NAME = sys.argv[1]
ZIPFILE_PATH = sys.argv[2]

print FUNC_NAME 
print ZIPFILE_PATH

client = boto3.client('lambda')
with open(ZIPFILE_PATH, 'rb') as fp:
    try:
        zipdata = fp.read() 
        print len(zipdata)
        r = client.update_function_code(
            FunctionName = FUNC_NAME,
            ZipFile=zipdata,
            )
    except Exception as e:
        print "error"
        print e
print "upload complete"
```


## Simple Notification Service (SNS)
Publish JSON data to SNS message.  This will pass the JSON data to another Lambda function that will be triggered by SNS subscription.
```python
import boto3
import json
def lambda_handler(event, context):
  client = boto3.client('sns')
  snsData = {}
  snsData['default'] = "default message"
  snsData['item'] = value
  message = {'default': json.dumps(snsData)}
  r = client.publish(
    TargetArn = '<enter sns arn>',
    Message = json.dumps(message),
    MessageStructure='json'
  )
  print message
  # {u'default': u'{"default": "default message", "item": "value"}'}
```

This will enable a Lambda that was triggered by SNS subscription to retrieve JSON data contained in the SNS message. 
```python
import boto3
import json
def lambda_handler(event, context):
    jdata = json.loads(event['Records'][0]['Sns']['Message'])
    v = jdata['item']
    print v
    # "value"
```

## Simple Queue Service (SQS)

Writte Message to SQS.
Add name from AWS Gateway (REST Web Service) http request body to SQS
```python
import boto3
def lambda_handler(event, context):
    name = event['name']
    sqs = boto3.resource('sqs')
    queue = sqs.get_queue_by_name(QueueName='ENTER_YOUR_SQS_NAME')
    messagebody = '{"name": %s }' % name
    response = queue.send_message(MessageBody=messagebody)
    m = "[success] %s added to processing queue" % resId
    returnMessage = json.dumps({"result":"success", "message":m})
    # log to AWS CloudWatch
    logger.info(returnMessage)
    return returnMessage
```

 
Retrieve message from SQS.
```python
import json
def lambda_handler(event, context):
    sqs = boto3.resource('sqs')
    queue = sqs.get_queue_by_name(QueueName='ENTER_YOUR_SQS_NAME')
    # Get messages from SQS
    messageList = queue.receive_messages(MaxNumberOfMessages=10)
    messageCount = len(messageList)
    
    if messageCount == 0:
        return {"messsage" :"no messages in sqs"}
    else:
        message = "recevied %d messages in sqs" % len(messageList)
        
        for m in messageList:
            # Write message to AWS CloudWatch
            logger.info(m.body)
            # Delete message when done
            m.delete()
```
