```ruby
aggregate_failures "testing response" do
  expect(response.status).to eq(200)
  expect(response.headers).to include("Content-Type" => "application/json")
  expect(response.body).to eq('{"message":"Success"}')
end
```
