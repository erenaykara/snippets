Start console
```
psql postgres
```

Create role and databases
```
CREATE ROLE promocje WITH SUPERUSER LOGIN;
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
