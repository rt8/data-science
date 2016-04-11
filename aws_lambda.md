# AWS Lambda 

Publish to SNS
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

Fetch from SNS
```python
import boto
import json
def lambda_handler(event, context):
    jdata = json.loads(event['Records'][0]['Sns']['Message'])
    v = jdata['item']
    print v
    # "value"
```
