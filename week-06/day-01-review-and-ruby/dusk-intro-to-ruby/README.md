# Welcome To Ruby
## Control Flow and Methods


| After this module, you can phone your friends and tell them you can: |
|:--- |
| Identify control flow patterns and functions in Ruby |
| Apply control flow to create command line applications |
| Apply methods in ruby to solve problems |


### Parts of A Language

* `Primitives`
* `Combinations`
* `Abstractions`


### Ruby vs. JS Primitives

Let's recall some of our JS Data Types


#### Javascript

* `null`, `undefined`
* Strings
* Booleans
* Number
  * `.toString`
* Arrays
  `indexOf`,`splice`, `slice`
* Objects
  * `["some_key"]`, `.some_key`
* operators
  * `==`, `===`, `>`, `>=`, ..
  * `!`, `||`, `&&`
  * `+`, `-`, `/`, `*`
* Console methods
    * `console.log`
    * `prompt`

#### Ruby 

* `nil`
* Integers
    * Fixnum
    * Bignum
     * `to_s`
* Floats
* Strings
  * `.to_i` and `.to_f` `*INTEGER`
* Symbols 
* Booleans
* Arrays / Ranges
  * `[x..y]`, `[x...y]`, `index`
* Hashes
  * `{ :key => value }`
  * `{ key: value }` which is the same as `{:key =>value }`
  * `[some_key]` and `[some_key]=` 
  * `key`,`.keys`, `.each`
* operators
  * `||=`, `*=`, `/=`
  * `==`, `.equal?`, 
  * `!`, `not`, `||`, `&&`
  * `**`, `+`, `-`, `/`, `*`
* General Delimited Input
    * `%w`, `%r` 
* Console Methods
    * `puts`, `p`
    * `gets` and `gets.chomp` 

### Control flow


#### Javascript ([Some Control Flow Structures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Statements))

* Conditionals 
    * `if`, `else if`, `else`, `switch`, ...
* Loops
    * `do-while`, `while`,  ... 
* iterators,
    * `for-in`
* Exceptions
    * `try`, `catch`

#### Ruby ([Some Control Flow Structures](http://en.wikibooks.org/wiki/Ruby_Programming/Syntax/Control_Structures))

* Conditionals 
    * `if`, `elsif`, `else`, `unless`, `case when else` ...
* Loops
    * `until`, `while`, `times` ... 
* iterators,
    * `.each`, `for ... in`
* Exceptions
    *  `begin`, `rescue`, `ensure` 


### Some Abstractions

#### Javascript

* Function
    * Anonymous: `function (param1, [..param2, [...]]){...}`, 
    * Named: `function Name(param1, [..param2, [...]]){...}`
    * Uses lexical scope
    * Used as values
    * require explicit return
    * all `params` are optional

#### Ruby   

 * Function
    * uses `def` 
    * Do not capture scope
    * Not used as values
    * optional parameters must be specified
    * implicitly returns last evaluation
    
* block
    * used with `.each`, `.map`, et cetera
    
    ```ruby
    some_method do [param1, [param2, [...]] 
        # some code
    end
    
    ```
    * captures scope

[Further Reading on Blocks](http://mixandgo.com/blog/mastering-ruby-blocks-in-less-than-5-minutes)

#Intro to Ruby

#### Define a method

```ruby
# announce you are creating a method with 'def'
def say_hello
  # all logic and action within belongs to the method
  puts "Hello"
# end your method defniition with 'end'
end

# call the method 'say_hello'
say_hello
```

#### Define a method with a parameter

```ruby
def say(something)
  puts something
end

say('hello')

say 'hello'
```

If you don't have code that needs to use method result immediately, Ruby allows to specify parameters omitting parentheses:

```ruby
# calling method, not using parentheses
results = method_name parameter1

# You need to use parentheses if you want to work with the result immediately.
# e.g., if a method returns an array and we want to reverse element order:
results = method_name(parameter1).reverse
```

#### Define a method that operates on two parameters
```ruby
def add_numbers(first, second)
  puts first + second
end

add_numbers(1,2)
add_numbers 1, 2
```

#### Printing and returning are different
```ruby
def add_numbers_quietly(first, second)
  first + second
end

add_numbers_quietly(1,2)
add_numbers_quietly 1, 2
```

#### Methods in Ruby always return the value of the last evaluated expression
```ruby
def implicitly_return_5
  if true
    5
  end
end

implicitly_return_5
```

* What was the value of the if statement?
* `status_of_world = if 1 == 2 then "messed up" else "a-o-k" end`
* `result = 1 == 2 ? "wuh oh" : "phew"`


#### Parameters can have default values

```ruby
def say(something = "Hello")
  puts something
end

say # prints "Hello"
say "Goodbye" # prints "Goodbye"
```
#### Recursion: methods can call themselves

```ruby
def recurse(depth)
  if depth > 0
    puts "Spiraling down..."
    recurse(depth - 1)
    puts "Spiraling up..."
  else
    puts "Bottom of the rabbit hole"
  end
end

recurse(5)
recurse 5
```

## The biggest difference from javascript

#### Functions have locally scoped variables
The following code wont work. Why?

```ruby
foo = 1

def do_stuff
  foo += 1
  bar = 1
  puts foo
  puts bar
end

do_stuff

puts foo
puts bar
```

The problem is the ruby is locally scoped. Meaning that a function only has access to its variables and the variables it defined inside of itself.

```ruby
foo = 1

def do_stuff
  foo = 1
  foo += 1
  bar = 1
  puts foo
  puts bar
end

do_stuff

puts foo
puts bar

def do_stuff2(x)
  foo = x
  foo += 1
  bar = 1
  puts foo
  puts bar
end

puts do_stuff2(foo)
```

[Ruby Method Calls In Depth](https://en.wikibooks.org/wiki/Ruby_Programming/Syntax/Method_Calls)

## Exercises

You may create a separate file for each of the exercises to avoid cluttering a file.

### Looping And Other Exercises

Use a loop to do  the following:

1.) Write a method called `p_times` that takes a `statement` and a `num` puts the `statement` some `num` of times to the console.

2.) Write a method called `letter_count` to count letter occurence in a string, returned as a `Hash`.

3.) Write a method called `mock_me` that `gets` some input from the terminal and puts it until the input is the word `quit` or `q`. (Be sure to remove trailing `\n`.)

4.) Write a method called `print_contacts` that takes a `hash` of `name` and `phone-number` key-value pairs and puts the `name` with the contact info.

5.) Write a method called `get_contact` that

* takes a `contacts` hash,
* prints the contacts,
* prompts the terminal for a **new** `name` and a `phone` number, 
* and then adds the `name` and `phone` as a key value pair respectively if `name` is not already a contact. 
* The `get_contact` method should `return` the `contacts` hash.

### List exercises

#### Using `Array#inject`
[API on Array#inject](http://apidock.com/ruby/Enumerable/inject)

Write a method for each exercise below that uses `Array#inject`:

1.) Write a method called `get_sum` to find the `sum` of the values in an array.

2.) Write a method called `get_max` to find the `max` of the values in an array.

3.) Write a method called `get_min` to find the `min` of the values in an array.

4.) Write a method called `reverse_str` to reverse a string.

**Challenge**: *write a method called `partial_sums` that pushes the partial sum of an array to a new list*

```
partial_sums([])
#=> [0]
partial_sums([5])
#=> [0, 5]
partial_sums([5,6,7])
#=> [0, 5, 11, 18]
```

#### Using `Array#map`
[API on Array#map] (http://ruby-doc.org/core-2.2.0/Array.html#method-i-map)

Write a method for each exercise below that uses `Array#map`:

1.)  Write a method called `multiply_by` that takes a number and returns an array of numbers multiplied by that number.

2.)  Write a method called `reverse_each` that takes an array of words and returns an array of reversed words.

3.)  Write method called `get_responses` that takes an array of questions (strings) and returns an array of responses input from the console for each question. (Hint: you will need to use `gets.chomp` and `puts` )

### Method Problems

* Write a method to compute the `factorial` of a number.
* Write a method to check if a number is a `palindrome`.
* Write a method to `reverse` a word in-place, do not use iterators, use only a while loop and indices.
* Write a method to `merge` to two sorted Arrays.

### Further Reading

* [Tutorialspoint Ruby Quick Guide](http://www.tutorialspoint.com/ruby/ruby_quick_guide.htm)
* [Ruby Hash in Detail] (http://ruby-doc.org/core-2.2.0/Hash.html)
* [RubyMonk Library](https://rubymonk.com/learning/books/1-ruby-primer)
* [Online IRB Environment] (http://joshnuss.github.io/mruby-web-irb/)
