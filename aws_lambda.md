# AWS Lambda 

Publish to SNS
```
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
```

Fetch from SNS
```
import boto
import json
def lambda_handler(event, context):
    jdata = json.loads(event['Records'][0]['Sns']['Message'])
    print jdata['item']
```
