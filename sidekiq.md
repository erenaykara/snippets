#### Jak wyczyścić wszystkie joby, żeby kolejna była wolna?
1. redis musi być uruchomiony. 
```
rails console
Sidekiq.redis { |conn| conn.flushdb }
```
