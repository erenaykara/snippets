Debug locally
```
rails g model TriggerDebug trigger:string statement:string value:string
rake db:migrate

INSERT INTO trigger_debugs (trigger_name, statement, value) VALUES ("products_before_insert.sql:48", "NEW.id", NEW.id);

TriggerDebug.all
```
