# Introduction to Variables

## Learning Goals

- Define a variable
- Identify properties of variables
- Define pass-by-value as it relates to variables

## Introduction

Earlier, we learned about the different data types we can use to represent
information. We could, for instance, write the number "10," and Ruby will
recognize it as an Integer:

```ruby
10
# => 10
10.class
# => Integer
```

We know that the Integer class has a variety of built in methods we can use on
the number, just as all data type classes do:

```ruby
10.even?
# => true
```

This is cool, but limited in functionality. We cannot reuse the value, `10`,
that we've written. We can't access it later.

Variables solve this problem. With variables, we can store data like numbers in
_barewords_, allowing us to access them later. In this lesson, we're going to
introduce variables and some examples of how they are used. Use IRB in the
terminal or Learn's IDE to follow along.

## Define a Variable

Variables are barewords that we define by assigning a value. Most often, values
are data types. We assign variables by writing their name followed by an equals
sign and the value we want to assign:

```ruby
first_number = 7
# => 7

second_number = 14
# => 14

name = "Tzvi"
# => "Tzvi"
```

By assigning variables, we can access this data later by writing the variable
name instead of the value itself:

```ruby
second_number
# => 14
```

Variables represent their values in our code. For instance, two variables
assigned to numbers can be added together, just like the numbers themselves:

```ruby
first_number = 7
second_number = 14

sum = first_number + second_number

puts sum
```

The code above will print '21'.

Variables are a tool for storing and using data in our programs. We tell our
computer to set aside some space to hold that information so we can retrieve it
later. A variable is the location where the information resides, when we need it
we know just where to look.

Another example using a string:

```ruby
president = "Barack Obama"
puts "In 2016, the US president was " + president
```

The above code will print `In 2016, the US president was Barack Obama`.

`first_number`, `second_number`, `name`, `sum`, and `president` are all
**variables**. Much like in math, variables are words or characters that hold
values. In algebra, however, variables are only placeholders for numbers. In
Ruby, a variable can point to almost any type of value including numbers,
strings, arrays, and hashes.

## Identify Properties of Variables

### A Variable Has a Name

```ruby
i
result
user1
brkfstCereal
all_words_in_the_dictionary
CountryOfOrigin
FIRST_NAME
age
longest_word
```

These would all be valid variable names in Ruby. They would not all be good
variable names. There is strong convention among Rubyists to use what is known
as _snake case_:

```ruby
this_is_an_example_of_snake_case = 100
```

In snake case, words are separated by underscores. This is opposed to _camel
case_, where upcased characters indicate word breaks:

```ruby
thisIsAnExampleOfCamelCase = false
```

Variable names should start with a lowercase letter. A variable that begins with
an uppercase letter is known as a [**constant**][constant] and has different
characteristics.

There are also some rules that mark invalid variable names:

```ruby
# Invalid Names
1st_place
end
second place
third!place
```

A Ruby variable cannot start with a number, be a Ruby reserved word, or have
punctuation or space characters.

Besides these restrictions, we are free to name variables whatever we would
like. It is often helpful, especially when working in a collaborative setting,
to make sure your variable names are descriptive and indicative of what they are
storing.

### A Variable has a Value That Can Be Changed

A variable's name is like a label on a container. Its value is what is stored
inside that container. The name points to the value. Above, `president`
holds onto the value "Barack Obama" and `first_number` has the value of the
number 7.

We can reassign the value of variables as needed:

```ruby
first_number = 7
second_number = 14



first_number = 10
sum = first_number + second_number
# => 24
```

Notice that the final equation, `first_number + second_number`, didn't change.
With variables, we are able to assign and change the value without having to
change the name.

### A Variable has a Type That Can Be Changed As Well

A variable's type is the type of the value it holds. Ruby is what is known as a
_dynamically typed_ language. That means the value of a variable can change its
type and does not need to be explicitly and permanently defined. There is
nothing stopping you from changing the value of `sum`, which now is the number
24, to the string "whatever I want".

```ruby
sum
# => 24
sum.class
# => Integer

sum = "whatever I want"
# => "whatever I want"
sum.class
# => String
```

Ruby is also a _strongly typed_ language. This means a variable will never be
automatically _coerced_ to another type without you explicitly changing the
type.

- Adding two numbers will return a number: `2 + 2` returns `4`
- Adding two strings will return a string: `"2" + "2"` returns `"22"`
- Adding a number and a string **will raise an error**: `2 + "2"` raises a `TypeError`.

When you are building larger programs it is important to have in mind the type
of the value that a variable refers to.

### Variables Allow Us To Write Abstractly

Variable names can remain the same while their _values_ change. This enables a
powerful programming tool: abstraction.

When we write:

```ruby
first_number = 7
second_number = 14

sum = first_number + second_number
```

..we are defining a calculation without having to be explicit in what the values
are. We've _abstracted_ the process away from the concrete data. If all we were
doing was adding 7 and 14, we could accomplish that in a single line. But here,
we've created a reusable _adding machine_. This example may seem trivial, but
we can create much more complicated processes, all without having to know the
exact data we're working with.

## Bonus: Define Pass-by-Value as It Relates to Variables

We have seen that the variable itself, the location where information is stored,
is distinct from the value stored at that location. The variable `first_number`
can change value as needed without changing its name. Let's try something out to
demonstrate this.

First, we will declare a new variable with an original value, then do something
to change that value, and finally we'll take a peek at our variable again. Open
up IRB to follow along:

```ruby
sound = "squeak"

# We can peek at the value of sound by typing its name
sound
# => "squeak"

sound.upcase
# => "SQUEAK"
```

Ok, the moment of suspense has arrived! Now if we type `sound` again what do you
think its value will be?

...

...

```ruby
sound
# => "squeak"
```

Hmmm... `sound` is still pointing to the original _lowercased_ value. The
`sound` variable remains unchanged here. When `sound.upcase` was called, `sound`
provided its value to the `upcase` method to do its thing. In fact, it must
have made a _copy of that value_ that `upcase` could operate on while still
holding onto the original unaltered value. If this process did not happen the
value 'squeak' wouldn't exist for us to look up and we'd only be able to see
'SQUEAK'.

This is what we mean by pass-by-value. A variable makes a copy of the value it
holds and passes the copy over to something else that alters or changes it. The
alternative process is known as pass-by-reference. Here, changes to a variable
would alter what is stored in the actual location it refers to. After the
process was complete the variable would be holding a new and different value.

The practical result of pass-by-value is that we can perform operations on or
involving a variable without altering its value. We typically have to use
an equals sign to reassign variables (there are some data type methods that can
still alter a variable if needed).

## Conclusion

Variables play a critical role in programming. They allow us to store data at a
particular location and retrieve it later. Variables can be reassigned as
needed, and can even change their data type in Ruby. There are some conventions
we try to follow to make our code easier to understand, such as using
`snake_case` as opposed to `camelCase`. Variables allow us to write complex
processes without having to deal with the concrete data directly.

## Resources

- [Intro to Variables Video][video]
- [Wikibooks: Ruby Programming/Syntax/Variables and Constants][wikibook]

[constant]: https://ruby-doc.org/core-2.5.0/File/Constants.html
[wikibook]: http://en.wikibooks.org/wiki/Ruby_Programming/Syntax/Variables_and_Constants
[video]: http://learn-co-videos.s3.amazonaws.com/ruby/about-variables-ruby.mp4

<p class='util--hide'>View <a href='https://learn.co/lessons/variable-readme'>About Variable Assignment</a> on Learn.co and start learning to code for free.</p>
