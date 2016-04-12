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
Find pattern (ignore case) in file and redirect results to another file
```bash
$ grep -I "<pattern>" <fileName> > results.txt
```
Find pattern in all files in current directory tree (recursively).
```bash
$ grep -RI "<pattern>" .
```
To show surrounding lines use -A (lines after), -B (lines before), -C (surrounding lines)
``` bash
# show 2 lines before and after pattern found
$ grep -C 2 -RI "<pattern>" .
```
