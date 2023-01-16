Login to mysql shell:
```
mysql -u root -p

# or without pasword when mysql installed with brew
mysql -u root
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

Triggers
```mysql
CREATE DEFINER=`root`@`localhost` TRIGGER `contracts_before_update` BEFORE UPDATE ON `contracts` FOR EACH ROW this_trigger:BEGIN
	SET NEW.product_name 	= 'CYK';
END;
DROP TRIGGER contracts_before_update;
SHOW CREATE TRIGGER contracts_before_update;
```
