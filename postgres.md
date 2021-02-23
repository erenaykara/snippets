Start console
```
psql postgres

# or in asdf
 psql -d default
```

Create role and databases
```
CREATE ROLE promocje WITH SUPERUSER LOGIN;
CREATE ROLE alpha WITH SUPERUSER LOGIN PASSWORD 'abc123!';
CREATE DATABASE promocje WITH OWNER=promocje;
CREATE DATABASE promocje_test WITH OWNER=promocje;
DROP DATABASE alpharecycling;
```

List databases
```
\l
```


List roles
```
\du
```

Copy database locally
```
CREATE DATABASE production_copy WITH TEMPLATE production;
```
