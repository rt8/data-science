#Linux

#Curl

Test REST API by post method.  
Also shows verbose http communications, sends data, and uses http authentication headers.
Also consider using httpie
```bash
$ curl -v POST \
https://api.address.com/resource \
-d "{\"field1\":\"value1\", \"field2\":\"value2\"}" \
-H "Content-Type: application/json" \
-H "auth: token_value"
```

#Cron


# Grep
Find pattern in all files in this directory tree (recursively).
```bash
$ grep -RI "<pattern" .
```
