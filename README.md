# FastestCSV

Fastest CSV class for MRI Ruby and JRuby. Faster than faster_csv and fasterer-csv. 

Uses native C code to parse CSV lines in MRI Ruby and Java in JRuby.

Supports standard CSV according to RFC4180. Not the so-called "csv" from Excel.

The interface is a subset of the CSV interface in Ruby 1.9.3. The options parameter is not supported.

Originally developed to parse large CSV log files from PowerMTA.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'fastest-csv'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install fastest-csv

## Usage

Parse single line

```ruby
FastestCSV.parse_line("one,two,three")
 => ["one", "two", "three"]

"one,two,three".parse_csv
 => ["one", "two", "three"]
 ```

Parse file without header

```ruby
FastestCSV.foreach("path/to/file.csv") do |row|
  # ...
end
```

Parse file with header

```ruby
FastestCSV.open("path/to/file.csv") do |csv|
  fields = csv.shift
  while values = csv.shift
    # ...
  end
end
```

Parse file in array of arrays

```ruby
rows = FastestCSV.read("path/to/file.csv")
```

Parse string in array of arrays

```ruby
rows = FastestCSV.parse(csv_data)
```

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Added some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
