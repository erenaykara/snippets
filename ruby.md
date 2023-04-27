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

Documenting a method
```ruby
  # This shared example allows testing the pagination feature of a graphQL query
  #
  # @param [Symbol] resource - Name of the graphQL resource
  # @param [Lambda] pre_check - You can define a check that will be called before pagination expectations
  # @param [String] order_column (default: "id") - Testing pagination without explicit order leads to random failures.
  #                                                By default we order by "id", but sometimes it is not possible,
  #                                                because few graphQL queries does not allow ordering by "id".
  #                                                Then you can use custom value by providing this argument.
  #                                                Look at the example 2
  # @param [String] order_klass -(default: nil) - To set ordering in graphQL, we need to include
  #                                               in the query the ordering class.
  #                                               In the most cases we can compute it from the resource argument.
  #                                               But in some cases it is not possible. Look at the example 3
  #
  # @example 1
  #   # The most basic example
  #   it_behaves_like "paginated query", resource: :addresses do
  #     let(:records) { addresses }
  #   end
  #
  # @example 2
  #   # Usage of order_column argument
  #   it_behaves_like "paginated query", resource: :innoProviders, order_column: "gesnr" do
  #     let(:records) { inno_providers }
  #   end
  #
  # @example 3
  #   # Usage of order_klass argument
  #   it_behaves_like "paginated query", resource: :zipcodes, order_klass: "XGeoZipcodesOrderParam!" do
  #     let(:records) { zipcodes }
  #   end
```

