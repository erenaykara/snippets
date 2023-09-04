Bulk rename files:
```
git ls-files | rename -s 'billing_document' 'document'
-p to handle also directory rename.
```

Select second column:
```
git diff --name-status 3-27-stable | awk '{print $2}'
```

Prepare custom scope pattern for rubymine of files changed in current branch:
```
git diff --name-status 3-27-stable | awk '{print "file:"$2}' | paste -sd "|" -  | sed 's/|/||/g'
```

Monitor process
```
top -pid 94091
```

List trace of process
```
sudo dtruss -s -p 94091
```

List puma ports in format for top tool.
```
pids=( $(ps aux | grep puma | grep -v Cellar | awk '{print $2}') ) ; echo "${pids[@]/#/-pid }"
```

Direct output - [source](https://askubuntu.com/questions/420981/how-do-i-save-terminal-output-to-a-file)
```
          || visible in terminal ||   visible in file   || existing
  Syntax  ||  StdOut  |  StdErr  ||  StdOut  |  StdErr  ||   file   
==========++==========+==========++==========+==========++===========
    >     ||    no    |   yes    ||   yes    |    no    || overwrite
    >>    ||    no    |   yes    ||   yes    |    no    ||  append
          ||          |          ||          |          ||
   2>     ||   yes    |    no    ||    no    |   yes    || overwrite
   2>>    ||   yes    |    no    ||    no    |   yes    ||  append
          ||          |          ||          |          ||
   &>     ||    no    |    no    ||   yes    |   yes    || overwrite
   &>>    ||    no    |    no    ||   yes    |   yes    ||  append
          ||          |          ||          |          ||
 | tee    ||   yes    |   yes    ||   yes    |    no    || overwrite
 | tee -a ||   yes    |   yes    ||   yes    |    no    ||  append
          ||          |          ||          |          ||
 n.e. (*) ||   yes    |   yes    ||    no    |   yes    || overwrite
 n.e. (*) ||   yes    |   yes    ||    no    |   yes    ||  append
          ||          |          ||          |          ||
|& tee    ||   yes    |   yes    ||   yes    |   yes    || overwrite
|& tee -a ||   yes    |   yes    ||   yes    |   yes    ||  append
```

Curl command that writes response to file and allows multiple run (don't wait for response)
```
curl 'http://dev-alpha.convertersapp.com:3000/admin/eibs.json?context=grader' -X POST -H 'Accept: */*' -H 'Content-Type: application/json' -H 'X-CSRF-Token: V2Phw9ATe1qbd3hdKBkE/sYW9nS5DTg+Q1XJCz7a87XSo1Y4crNCIOiP6ex3aQICqGnaAPfiG3KLrea6LIJq/w==' -H 'Cookie: _alpha_app_web_session=aWNWMjU5TlhIeFEr' -H 'Sec-Fetch-Mode: cors' --data-raw '{\"eib_form\":{\"name\":\"test2\",\"company_name\":\"test12\",\"email\":\"test12@test.test\",\"username\":\"#{prefix}\",\"prefix\":\"#{prefix}\",\"client\":1846,\"permissions\":{\"packing_list_management\":false,\"converter_assays_visibility\":false,\"see_metal_prices_tab\":false,\"see_general_archived_cc\":false}}}' >> results 2>1 &
```


Change user on aws
```
sudo -i -u deploy
```

Find source location of alias "gb"
```
sudo grep -r "alias gb" /home/mariusz
```

trace the route an IP packet would follow to some internet host
```
traceroute
cd /usr/local/Cellar/mtr/0.95/sbin
sudo ./mtr rollbar.com -c 1800 -w > ~/mtr.txt
```

Check DNS
```
nslookup grg.convertersapp.com
```

List proceses that uses port:
```
lsof -i :3000
```

Disk space on all partitions
```
df -h
```

Sort files by size in directory:
```
du -sh db/seeds/* | sort -h
```

Run rspec on all tests from this branch
```
git diff --name-only develop | grep _spec | xargs bundle exec rspec
```

List lines as single line space separated
```
git diff --name-only develop | grep _spec | paste -sd' ' -
```
