#### Jak wyczyścić wszystkie joby, żeby kolejna była wolna?
1. redis musi być uruchomiony. 
2.
```
rails console
Sidekiq.redis { |conn| conn.flushdb }
```
3. Restart redis/sidekiq
