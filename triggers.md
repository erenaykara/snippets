Debug locally
```
rails g model TriggerDebug trigger:string statement:string value:string --no-test-framework
rake db:migrate

INSERT INTO trigger_debugs (`trigger`, statement, value) VALUES ('', 'column_name_string', column_name_string);

puts "TriggerDebug.count: #{TriggerDebug.count}"
puts "TriggerDebug rows:"
TriggerDebug.all.each { |record| puts record.attributes.slice('trigger', 'statement', 'value') }
```
