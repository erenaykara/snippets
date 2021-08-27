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

Import dump from heroku
```
pg_restore latest.dump --dbname=alpha_production --role alpha --no-owner --clean --if-exists
```

Run sql command from unix
```
psql postgres -c "DROP DATABASE alpha_prd_9_jun_copy;"
```

Find slowest query:
```sql
SELECT * FROM pg_stat_statements ORDER BY max_exec_time DESC LIMIT 1;
```
