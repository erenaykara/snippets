Bulk rename files:
```
git ls-files | rename -s 'billing_document' 'document'
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
