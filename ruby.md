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


#### Ruby's `$LOAD_PATH` - [source](https://stackoverflow.com/a/6671633/847670)
```ruby
# file_caller.rb
class FileCaller
  def call
    puts "hej. I am File"
  end
end

# main.rb
require "file_caller"
FileCaller.new.call
```

```
❯ ruby main.rb
Traceback (most recent call last):
	2: from main.rb:1:in `<main>'
	1: from ..kernel_require.rb:92:in `require'
...kernel_require.rb:92:in `require': cannot load such file -- file_caller (LoadError)
```

```
❯ ruby -I "."  main.rb
hej. I am File
```

#### Memory benchmark
```ruby
gem 'get_process_mem'

@memory_benchmarks = []
def log_memory(text)
  mem = GetProcessMem.new.mb
  @memory_benchmarks.push(mem)
  puts ("after #{text} PMEM: #{mem}")
end
```

#### Parse stdout provided by piping: `cat log.log | ruby_script`
```ruby
#!/usr/bin/env ruby

ARGF.each_line do |line|
```


#### Run ruby against each line from pipe.
```
cat filename | ruby script.rb
```

```ruby
# script.rb
STDIN.each_line.to_a
  .map { |line| matches = line.match(/job_id=([a-z0-9]+)/); matches[1] }
  .uniq
  .each { |job_id| line = info_start_lines.find(job_id); puts line.worker_klass }
```

#### Heredocs
```
angelica = <<-TEXT
I’m a girl in a world in which
My only job is to marry rich
My father has no sons so I’m the one
Who has to social climb for one
TEXT

sql = <<-SQL.squish
          SELECT
            REFERENCED_TABLE_NAME
          FROM
            information_schema.referential_constraints
          WHERE
            CONSTRAINT_SCHEMA = '#{ActiveRecord::Base.connection.current_database}'
            AND TABLE_NAME = '#{entity.table.name}'
            AND REFERENCED_TABLE_NAME = '#{primary_name}'
            and unique_constraint_name = 'PRIMARY'
        SQL
```

Debug when source_location not possible
```
TracePoint
```

Run shell command and fail on non-zero status
```ruby
stdout, stderr, status = Open3.capture3("bundle exec rails db -p < #{path}")
raise StandardError, stderr.join(" ") if status != 0
```

class methods trick
```ruby
class << self
  def most_popular
  end

  def the_king
  end
end
```

