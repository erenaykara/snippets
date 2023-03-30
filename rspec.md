```ruby
it "renders the headers" do
  aggregate_failures do
    expect(mail.subject).to eq("Price list from Test")
    expect(mail.bcc).to eq(["abc@company.com"])
    expect(mail.from).to eq(["company@email.com"])
  end
end
```


What is '+' and what is '-' in the test failure output?
```ruby
  it "????" do
    body = { test: 1 }.to_json
    response = OpenStruct.new(body: body)

    expect(response).to have_json_response(
      test: 2
    )
  end

expected that {:test=>1} to have json response {:test=>2}
Diff:
@@ -1 +1 @@
-:test => 2,
+:test => 1,
```

```ruby
it "is ??" do
  a = Product.new(id: 1)
  expect(a).to have_attributes(id: 2)
end

Failure/Error: expect(a).to have_attributes(id: 2)
   Diff:
   @@ -1 +1 @@
   -:id => 2,
   +:id => 1,
```

```ruby
it "??" do
  left = [1, 2]
  expect(left).to match_array([1, 3])
end

expected collection contained:  [1, 3]
actual collection contained:    [1, 2]
the missing elements were:      [3]
the extra elements were:        [2]       
```
