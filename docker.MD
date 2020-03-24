#### Stworzenie kontenera na podstawie obrazu
```
docker run -itd --name="debug-failing-test" "compsa/panel-producenta-tests:ruby-2.6.5"
```

#### Skopiowanie plików do kontenera:
```
docker cp . 2032-panel-producenta-tests--debug-failing-test:/usr/src/app
```

#### Zalogować się do kontenera
```
docker exec -it 2032-panel-producenta-tests--debug-failing-test bash -l
```
