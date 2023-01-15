# Ruby Style Guide

Much of this was taken from [RuboCop's guide](https://web.archive.org/web/20160410033955/https://github.com/styleguide/ruby) and [Airbnb's guide](https://web.archive.org/web/20160410033955/https://github.com/styleguide/ruby).

## Source Code Layout
### Tabs or Spaces?
Use only spaces for indentation. No hard tabs.

### Identation
Use two spaces per indentation level (aka soft tabs).

 ```ruby
# bad - four spaces
def some_method
  do_something
end

# good
def some_method
  do_something
end
```
### Maximum Line Length
Limit lines to 80 characters.

Keep each line of code to a readable length. Unless you have a reason to, keep lines to fewer than 100 characters.

### Terminate Files with a Newline
End each file with a newline.

### Spaces and Braces
No spaces after ```(```, ```[``` or before ```]```, ```)```. Use spaces around ```{``` and before ```}```.
 
```ruby
# bad
some( arg ).other
[ 1, 2, 3 ].each{|e| puts e}

# good
some(arg).other
[1, 2, 3].each { |e| puts e }
```

### Indent ```when``` to ```case```
```ruby
# bad
case
  when song.name == 'Misty'
    puts 'Not again!'
  when song.duration > 120
    puts 'Too long!'
  when Time.now.hour > 21
    puts "It's too late"
  else
    song.play
end

# good
case
when song.name == 'Misty'
  puts 'Not again!'
when song.duration > 120
  puts 'Too long!'
when Time.now.hour > 21
  puts "It's too late"
else
  song.play
end
```

### Empty Lines between Methods
```ruby
# bad
def some_method
  data = initialize(options)
  data.manipulate!
  data.result
end
def some_other_method
  result
end

# good
def some_method
  data = initialize(options)

  data.manipulate!

  data.result
end

def some_other_method
  result
end
```

### Empty Lines around Attribute Accessor
Use empty lines around attribute accessor.
```ruby
# bad
class Foo
  attr_reader :foo
  def foo
    # do something...
  end
end

# good
class Foo
  attr_reader :foo

  def foo
    # do something...
  end
end
```

## Naming Conventions
### English for Identifiers
Name identifiers in English.
```ruby
# bad - identifier is a spanish word
salario = 1_000

# good
salary = 1_000
```

### Snake Case for Symbols, Methods and Variables
Use ```snake_case``` for symbols, methods and variables.
```ruby
# bad
:'some symbol'
:SomeSymbol
:someSymbol

someVar = 5

def someMethod
  # some code
end

def SomeMethod
  # some code
end

# good
:some_symbol

some_var = 5

def some_method
  # some code
end
```

### CapitalCase for Classes and Modules
Use ```CapitalCase``` for classes and modules.
```ruby
# bad
class Someclass
  # some code
end

class Some_Class
  # some code
end

class SomeXml
  # some code
end

class XmlSomething
  # some code
end

# good
class SomeClass
  # some code
end

class SomeXML
  # some code
end

class XMLSomething
  # some code
end
```

### Snake Case for Files
Use ```snake_case``` for naming files, e.g. ```hello_world.rb```.

### Screaming Snake Case for Constants
Use ```SCREAMING_SNAKE_CASE``` for other constants (those that don’t refer to classes and modules).
```ruby
# bad
SomeConst = 5

# good
SOME_CONST = 5
```

### Predicate Methods Suffix
The names of predicate methods (methods that return a boolean value) should end in a question mark (i.e. Array#empty?). Methods that don’t return a boolean, shouldn’t end in a question mark.
```ruby
# bad
def even(value)
end

# good
def even?(value)
end
```

### Predicate Methods Prefix
Avoid prefixing predicate methods with the auxiliary verbs such as is, does, or can. These words are redundant and inconsistent with the style of boolean methods in the Ruby core library, such as empty? and include?.
```ruby
# bad
class Person
  def is_tall?
    true
  end

  def can_play_basketball?
    false
  end

  def does_like_candy?
    true
  end
end

# good
class Person
  def tall? 
    true
  end

  def basketball_player?
    false
  end

  def likes_candy?
    true
  end
end
```