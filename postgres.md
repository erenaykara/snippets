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

# + its size
\l+
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

przebudowuje index (samo przebudowanie może nic nie dać dla query plannera, bo statystyki się nie zmienią. VACUUM ANALYZE może być potrzebny)
```
REINDEX table prices;
```

usuwa bloata, aktualizuje stataystyki
```
VACUUM ANALYZE prices;
```

aktualizacja statystk
```
ANALYZE prices;
```

kiedy był vacum i analize?
```sql
SELECT relname, 
       last_vacuum, 
       last_autovacuum, 
       last_analyze, 
       last_autoanalyze 
FROM   pg_stat_all_tables 
WHERE  schemaname = 'public' 
and relname = 'prices'
ORDER  BY last_vacuum DESC;
```

rozmiar tabel i indeksów
```sql
SELECT
	*,
	Pg_size_pretty(total_bytes) AS total,
	Pg_size_pretty(index_bytes) AS INDEX, Pg_size_pretty(toast_bytes) AS toast,
		Pg_size_pretty(table_bytes) AS TABLE
	FROM (
		SELECT
			*,
			total_bytes - index_bytes - Coalesce(toast_bytes, 0) AS table_bytes
		FROM (
			SELECT
				c.oid,
				nspname AS table_schema,
				relname AS TABLE_NAME,
				c.reltuples AS row_estimate,
				Pg_total_relation_size(c.oid) AS total_bytes,
				Pg_indexes_size(c.oid) AS index_bytes,
				Pg_total_relation_size(reltoastrelid) AS toast_bytes
			FROM
				pg_class c
			LEFT JOIN pg_namespace n ON n.oid = c.relnamespace
		WHERE
			relkind = 'r') a
	WHERE
		table_schema = 'public'
	ORDER BY
		total_bytes DESC) a; 
```
