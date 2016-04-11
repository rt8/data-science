# AWS Lambda 

Publish message to SNS.  This will pass json data to another lambda function that is triggered by SNS subscription.
```python
import boto
import json
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

Fetch message from SNS
```python
import boto
import json
def lambda_handler(event, context):
    jdata = json.loads(event['Records'][0]['Sns']['Message'])
    v = jdata['item']
    print v
    # "value"
```
