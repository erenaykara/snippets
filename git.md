```
git rebase --onto <newparent> <oldparent>
```

revert merga pull requesta z merge commitem
```
git revert -m 1 <commit_sha>
```

git push specific commit to specific remote branch
```
git push upstream 159aef45:master --force
```

Filter git log by author and filename changed
```
git log --author "Mariusz" -- '*serializer*'
```

Log evolution of a method
```
git log -L :status_reason_inclusion:app/models/client.rb
```

Ignore RuboCop Changes in git blame
```
vim .git-blame-ignore-revs
# put commit hash of refactoring commmits
```
