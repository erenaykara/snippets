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
docker pull postgres:13.4-alpine
docker volume create pgdata

# -rm will remove container after stopping it.
docker run --rm \
   -v pgdata:/var/lib/postgresql/data \
  -e POSTGRES_USER=alpha \
  -e POSTGRES_DB=alpha_dev \
  -e POSTGRES_HOST_AUTH_METHOD=trust \
  --name "postgres-for-alpha" \
  -p 5433:5432 "postgres:13.4-alpine"

# use 5433 as db host in database.yml
rake db:create


heroku pg:backups:capture
heroku pg:backups:download b2538
docker exec postgres-for-alpha pg_restore \
  --verbose --clean --no-acl --no-owner \
  -h postgres --dbname=postgresql://alpha:abc123!@127.0.0.1:5433/alpha_dev latest.dump
```

Up only 1 service from many in docker compose
```
docker-compose -f .docker/local/docker-compose.yml --env-file .env.development.example up rabbitmq -d
```

Copy volume to create copy of mysql container
```
~/.bin/docker-convenience-scripts/docker_clone_volume.sh core-api-source-for-cloning core-api-copy

docker run --hostname=2694985803a4 --env=MYSQL_VERSION=5.7.40-1.el7 --env=MYSQL_SHELL_VERSION=8.0.31-1.el7 --env=MYSQL_ROOT_PASSWORD=test --env=TZ=Europe/Berlin --env=PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin --env=GOSU_VERSION=1.14 --env=MYSQL_MAJOR=5.7 --network=core-api-db_default -p 3306:3306 --restart=no --label='com.docker.compose.project=core-api-db' --label='com.docker.compose.service=mgis-mysql' --label='com.docker.compose.version=2.13.0' --runtime=runc --mount source=core-api-copy,destination=/var/lib/mysql --name=db-test -d mgis/mysql
```
