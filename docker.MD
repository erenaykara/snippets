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
docker exec -it price_tag_debug2  bash -l
vim config/database.yml
# Zamień localhost na host.docker.internal
bundle exec rails server
```
