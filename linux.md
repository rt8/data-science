#Linux

##Curl

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

## httpie (alternative to Curl)
To install
```sh
$ sudo apt-get install httpie
```
To redirect REST Web service to a text file.   
For example, you want to retrieve a json object from API
```sh
$ http -all \
POST https://api.address.com/resource \ 
header1:value \
header2:value \
body_field=value \
--print=b > filename.txt
```

To pretty print json object from REST Web service
```sh
$ http -all \
POST https://api.address.com/resource \ 
header1:value \
header2:value \
body_field=value \
--print=b  | python -m json.tool | pygmentize -l javascript 
```


##Cron (Automation Scheduler)
Cron entry to run every 10 minutes and use flock to ensure only one instance is executed.  Also append logs to output file 
```{r, engine='bash', count_lines}
# run every 10 minutes
*/10 * * * * flock - n /tmp/lockfile.lock /usr/bin/python script.py >> /var/log/project/logfile.log 2>&1
```
Cron commands
```bash
crontab -e          # launch text editor to edit crontab
crontab -l          # show existing cron schedule
crontab -r          # delete contents of crontab
crontab <filename>  # Push file contents into crontab.  This will overwrite everything in crontab
# comments          # add comments to crontab
```

## Logrotate
Rotate log files periodically before they get too big.

Add logrotate configurations to `/etc/logrotate.conf`

Below example will compress logs every month and keep 12 months of logs.  Use `size` or `maxsize` option if you want to rotate logs when it reaches certain file size.
```sh
/var/log/projectName/*.log {
	monthly
	size 100M
	rotate 12
	compress
	delaycompress
	missingok
	notifempty
	create 644 root root
}
```

## Grep (Search)
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

##sFTP
Using sftp in the command line.  
```sh
$ sftp username@hostname      # connect to sftp server
> ls                          # list files in directory
> get <remoteFileName>        # download file to local machine
> cd <remoteDirectoryName>    # change directory
```
