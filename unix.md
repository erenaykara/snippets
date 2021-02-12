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
