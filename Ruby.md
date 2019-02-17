* `#` - Comments
* You can get the class of anything (including numbers, strings, and methods) with `.class`

## Arithmetic

* `+`/`-`/`/`/`*`/`%`
* `**` - Exponentiation
* Syntatic sugar for calling a method: `1.+(1) # 2`

## Special Values

* `nil`
* `false`
* `true`

## Expressions

* `==` / `!=` - Comparison
    * `nil` and `false` are the only falsey values
* `<=`, `>=`, `<`, `>`
* Comparison operator: `<=>`
    * `1` if first argument is greater, `-1` if less, `0` if equal
* `&&`, `||`, `and`, `or`
    * `and` & `or` have lower precedence, and are for chaining
* `a, b, c = [1, 2, 3]` - Destructuring
* `*[a, b, c] # a, b, c ` - Splat

## Strings

* `"This is a string #{interpolation}"` - Only with double-quotes
    * You can concat strings with `+`
* You can repeat strings with `*`
* `<<` - Append operator

## Output

* `puts` - Print with newline
* `print` - Print without newline

## Variables

* `x = 1`
* Assignment returns the value assigned (you can chain assignments)
* `snake_case` by convention
* `status = :pending` - Symbols. Immutable, descriptive. Like enums
    * Strings can be converted into symbols and vice-versa
    * `status.to_s`, `"pending".to_sym`
* `$global` - Global variable
* `@instance` - Instance variable
* `@@class` - Class variable 
* `Constant` - Constant

## Arrays

* `array = [0, "dog", false]`
* `array[0]`, `array.first`, `array[-1]`, `array.last`
* `array.reverse`
    * `array.reverse!` reverses in place
* `array << 6`, `array.push(6)`
* `array.include?(1)`

## Hashes

* `hash = { 'color' => 'green' }`
* `hash['color']`
* `hash.keys`
* Check for existence: `hash.key?(:status)`, `hash.value?(3)`
* Empty value returns `nil`
* You can use symbols in hashes and drop the `:`: `hash = { color: green }`

## Collections

Hashes and Arrays have `.each`, `.map`, `.count`, .etc

## Conditionals

```ruby
if true
    'something true'
elsif false
    'something false'
else
    'something else'
end
```

```ruby
grade = '82'

case grade
when '100'
    puts 'Good job!'
when '80..99'
    puts 'Ok'
else
    puts 'Huh?'
end
```

## Loops

```ruby
(1..5).each do |counter|
    puts "iteration: #{counter}"
end
```

```ruby
some_array.each do |counter|
    puts "iteration: #{counter}"
end
```

Less common:

```ruby
for counter in 1..5
    puts "iteration: #{counter}"
end
```

* `each_with_index`
* `map`, `reduce`

## Blocks

* Like lambdas. Can be stored as objects, called, etc.
* `{ |counter| puts "iteration #{counter}" }`

## Exceptions

```ruby
begin
    raise NoMemoryError, 'You ran out of memory.'
rescue NoMemoryError => exception_message
    puts 'NoMemoryError!', exception_message
else
    puts 'No exceptions!'
ensure
    puts 'This always runs'
end
```

## Methods

* Implicitly return the last statement
* Parentheses optional

```ruby
def double(number)
    number * 2
end

double(2)
double 2
double double 2

def sum(first, second)
    first + second
end

sum(1, 2)
sum 1, 2
sum(sum(1, 2), 3)
sum sum(1, 2), 3
```

* Methods take an optional, implicity block parameter that you can yield:

```ruby
def surround
    print '{'
    yield
    print '}'
end

surround { puts 'this is in braces' }
```

* Blocks can be passed into methods as a 'proc' like this:

```ruby
def guests(&block)
    block.call(4)
end

guests { |n| "You have #{n} guests."}
```

* You can coalesce arguments into an array with the `*` splat operator:

```ruby
def guests (*array)
    array.each block
end
```

* Methods that return booleans end with `?`
* Methods that mutate end with `!`

## Classes

```ruby
class Human < Animal
    @@species = 'H. sapiens' # Class variable

    def species
        @@species # return class variable
    end

    def initialize(name, age = 0) # Constructor
        @name = name # Instance variable
        @age = age
    end

    # Manual accessor
    def name=(name) # Setter
        @name = name
    end
    def name # Getter
        @name
    end

    # Automatic accessor
    attr_accessor :name
    attr_reader :name
    attr_writer :name

    # Static method
    def self.say(message)
        puts message
    end

end

kyle = Human.new('Kyle')
Human.say('Hi')
```

## Modules

```ruby
module ModuleExample
    def example
        'some string'
    end
end

class IncludedClass
    include ModuleExample
end

Person.new.example # some string

class ExtendedClass
    extend ModuleExample
end

Person.example # some string
```
