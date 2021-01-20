```ruby
it "renders the headers" do
  aggregate_failures do
    expect(mail.subject).to eq("Price list from Test")
    expect(mail.bcc).to eq(["abc@company.com"])
    expect(mail.from).to eq(["company@email.com"])
  end
end
```
