Login to mysql shell:
```
mysql -u root -p
```

List dbs
```
SHOW DATABASES;
```

```
CREATE DATABASE menagerie;
```

Drop db:
```
DROP database mvp_test;
```

Copy db:
```
mysqldump -u root --password=test mvp_dev | mysql -u root -p mvp_test;
```
