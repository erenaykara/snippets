Budowanie obrazu
```
docker build -f docker/tests/Dockerfile -t name:tag .
```

Stworzenie kontenera na podstawie obrazu
```
docker run -itd --name="debug-failing-test" "compsa/panel-producenta-tests:ruby-2.6.5"
```

Skopiowanie plików do kontenera:
```
docker cp . 2032-panel-producenta-tests--debug-failing-test:/usr/src/app
```

Zalogować się do kontenera
```
docker exec -it 2032-panel-producenta-tests--debug-failing-test bash -l
```

Uruchomić ponownie zatrzymany kontener
```
docker start 2032-panel-producenta-tests--debug-failing-test
```

Uruchomić kontener w taki sposób, aby kontener widział moją lokalną bazę danych oraz żebym mógł otworzyć aplikację odpaloną w kontenerze przeglądarkę.
```
docker run -itd -p 3005:3000 --name="price_tag_debug2" pp:2368-with-gsubed-host-in-database-yml
# 3005 to port pod jakim będę uruchamiał apkę u siebie lokalnie, a 3000 to port na jakim uruchomię w kontenerze serwer.

docker exec -it price_tag_debug2  bash -l
vim config/database.yml
# Zamień localhost na host.docker.internal
bundle exec rails server
```


Postgres for a rails app in docker:
```
docker pull postgres:9.6.10
docker volume create pgdata
docker run -itd \
  -v pgdata:/var/lib/postgresql/data \
  -e POSTGRES_PASSWORD=abc123! \
  -e POSTGRES_USER=alpha \
  -e POSTGRES_DB=alpha_dev \
  -p 5433:5432 \
  --name="postgres-for-alpha" "postgres:9.6.10"

psql postgresql://postgres:password@localhost:5433/postgres
CREATE ROLE alpha WITH SUPERUSER LOGIN PASSWORD 'abc123!';

# use 5433 as db host in database.yml
rake db:create


heroku pg:backups:capture
heroku pg:backups:download b2538
docker exec postgres-for-alpha pg_restore \
  --verbose --clean --no-acl --no-owner \
  -h postgres --dbname=postgresql://alpha:abc123!@127.0.0.1:5433/alpha_dev latest.dump
```
