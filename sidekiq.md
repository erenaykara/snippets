#### Jak wyczyścić wszystkie joby, żeby kolejna była wolna?
1. redis musi być uruchomiony. 
2.
```
rails console
```
3.
```
Sidekiq.redis { |conn| conn.flushdb }
```
3. Restart redis/sidekiq

#### Log outside of sidekiq worker class
```ruby
logger = Sidekiq.logger
logger.info "Value"
```
