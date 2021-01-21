heredoc [source](https://www.rubyguides.com/2018/11/ruby-heredoc/)
```ruby
    it "adds links to files" do
      text = "PDF files: [links]"
      output_html = html_output_for(text, files: files)
      expected_output = <<~EXPECTED_OUTPUT.chomp
      <p>PDF files: <ul>
          <li><a href=\"https://abc.com/file.pdf\">converter</a></li>
          <li><a href=\"https://abc.com/file.pdf\">scrap_metal</a></li>
      </ul>
      </p>
      EXPECTED_OUTPUT
      expect(output_html).to eq(expected_output)
    end
```
