Bulk rename files:
```
git ls-files | rename -s 'billing_document' 'document'
```

Select second column
```
git diff --name-status 3-27-stable | awk '{print $2}'
```
