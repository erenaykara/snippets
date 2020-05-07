#### Ustawienie domyślnej schema path (przydatne w tableplus)
```
SET search_path TO mplatform;
```
#### Pobranie tabeli z internetu i wgranie jej lokalnie potem
```
pg_dump -h 00.00.00.44 -p 5432 -U user -d dbName -t schema.tableName > file.sql
psql dbName < file.sql
```
