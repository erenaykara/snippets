#### Wymuszenie pełnych zapytań SQL, żeby można je było sobie kopiować do tableplus
```
# config/database.yml
prepared_statements: false
```

List all rake tasks with source path
```
rake -W
```


Enable sql logs in rails console or runner
```
ActiveRecord::Base.logger = Logger.new($stdout)
ActiveRecord::Base.logger = Logger.new("#{Rails.root}/log/activerecord.log")
```

Refer url helper in rails console
```
app.delete_all_merchants_promo_path
```

Make hash accepting keys as string or symbols:
```
result.with_indifferent_access
```
https://api.rubyonrails.org/v4.2/classes/ActiveSupport/HashWithIndifferentAccess.html

Create only development db
```
SKIP_TEST_DATABASE=true rake db:create
```

Cast user input into boolean. https://api.rubyonrails.org/classes/ActiveModel/Type/Boolean.html
```
cast_hidden = ActiveModel::Type::Boolean.new.cast(hidden)
```
