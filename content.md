# Ruby Gym: Character Types

Write a program that:
  - Takes a `String`
  - Counts the total number of letters in the given `String`
  - Counts the total number of spaces in the given `String`
  - Counts the total numbers of digits in the given `String`
  - and prints the information out

Example output for `string = "here 12 plus 25"`:

```
"Number of letters in the string is: 8"

"Number of spaces in the string is: 3"

"Number of digits in the string is: 4"
```

Make your program match this target output using the randomly `sample`d `string`s provided. Then get the tests to pass.

Hint: It may be helpful to use the advanced `gsub` techniques with the `Regexp` class; see [the Ruby reference](https://learn.firstdraft.com/lessons/33-the-one-ruby-reference#advanced-gsub-techniques-with-regexp-class).


```ruby
strings = [
  "here 12 plus 25",
  "puzzle number 04 ",
  " "
]
string = strings.sample
pp string
# write your program below
```
{: .repl #character_types title="Character Types" readonly_lines="[1,2,3,4,5,6,7,8]"}


```ruby
describe "Character Types" do
  it "finds 8 letters, 3 spaces, and 4 digits when the string is 'here 12 plus 25'" do
    path = "/tmp/code.rb"
    allow_any_instance_of(Array).to receive(:sample).and_return("here 12 plus 25")
    output = capture_stdout { require_relative(path) }
    expect(output).to match(/Number of letters in the string is: 8.?\n.?Number of spaces in the string is: 3.?\n.?Number of digits in the string is: 4/i), "Expected output to be 'Number of letters in the string is: 8\\nNumber of spaces in the string is: 3\\nNumber of digits in the string is: 4', but was '#{output}'."
  end

  def capture_stdout
    old_stdout = $stdout
    $stdout = StringIO.new
    yield
    $stdout.string
  ensure
    $stdout = old_stdout
  end
end
```
{: .repl-test #character_types_test_1 for="character_types" title="Character Types finds 8 letters, 3 spaces, and 4 digits when the string is 'here 12 plus 25'" points="1"}


```ruby
describe "Character Types" do
  it "finds 4 letters, 5 spaces, and 7 digits when the string is 'game 1 12 58 09 '" do
    path = "/tmp/code.rb"
    allow_any_instance_of(Array).to receive(:sample).and_return("game 1 12 58 09 ")
    output = capture_stdout { require_relative(path) }
    expect(output).to match(/Number of letters in the string is: 4.?\n.?Number of spaces in the string is: 5.?\n.?Number of digits in the string is: 7/i), "Expected output to be 'Number of letters in the string is: 4\\nNumber of spaces in the string is: 5\\nNumber of digits in the string is: 7', but was '#{output}'."
  end

  def capture_stdout
    old_stdout = $stdout
    $stdout = StringIO.new
    yield
    $stdout.string
  ensure
    $stdout = old_stdout
  end
end
```
{: .repl-test #character_types_test_2 for="character_types" title="Character Types finds 4 letters, 5 spaces, and 7 digits when the string is 'game 1 12 58 09 '" points="1"}


```ruby
describe "Character Types" do
  it "finds 0 letters, 0 spaces, and 0 digits when the string is ''" do
    path = "/tmp/code.rb"
    allow_any_instance_of(Array).to receive(:sample).and_return("")
    output = capture_stdout { require_relative(path) }
    expect(output).to match(/Number of letters in the string is: 0.?\n.?Number of spaces in the string is: 0.?\n.?Number of digits in the string is: 0/i), "Expected output to be 'Number of letters in the string is: 0\\nNumber of spaces in the string is: 0\\nNumber of digits in the string is: 0', but was '#{output}'."
  end

  def capture_stdout
    old_stdout = $stdout
    $stdout = StringIO.new
    yield
    $stdout.string
  ensure
    $stdout = old_stdout
  end
end
```
{: .repl-test #character_types_test_3 for="character_types" title="Character Types finds 0 letters, 0 spaces, and 0 digits when the string is ''" points="1"}
