# Week 5: Functions

## Testing your code
A note: You can and should always test run your code in REPL before submitting an assignment!

## Readings
For this week, take a look at:
- [Think Python, ch. 3: functions](http://www.greenteapress.com/thinkpython2/html/thinkpython2004.html)
- [Think Python, ch. 6: fruitful functions](http://www.greenteapress.com/thinkpython2/html/thinkpython2007.html)

# What is a function?
**Functions** are the verbs of a programming language. We can think of functions like organs in our body - they are sets of code that work together to accomplish some task. Functions take some **variables** as input (**arguments**) and either do something with them or return a new variable.

You can recognize that you are calling a function by the presence of `( )`. (You've seen this before, with **methods**. Methods are special types of functions that belong to a variable.) They _always_ have parentheses, even if they don't need any arguments to be passed to them: for example, `myFunction()`

Functions are always written like this:

```
# Example with 1 argument
myFunction(variable1)

#Example with 2 arguments
myFunction(variable1, variable2)

# The number and type of arguments needed is specific to each function.
```

# Simple examples

You're already familiar with a basic function! Perhaps the simplest function to use is `print()`. `print()` can take an arbitrary number of variables as arguments and will print them to the screen, separated by a space:

```
x = "Today is"
y = "Wednesday"

# Same result with or without space after comma
print(x, y)

# But try this. How is the result different?
print(x + y)
```

Here are a few other useful functions and what they do:
- `len(string)` - Takes one _string_ argument and returns its length (number of characters)

    ```
    y = "Wednesday"
    print(len(y))
    ```

- `abs(number)` - Takes one argument (_integer_ or _float_) and returns its absolute value

    ```
    z = -45.2347
    print(abs(z))
    ```

- `round(float)` - Takes one _float_ argument and rounds it to the nearest integer

    ```
    w = 33.7943
    print(round(w))
    ```

- `type(variable)` - Takes one variable as an argument and returns its type

    ```
    w = 33.7943
    print(type(w))
    ```

Functions have help available with the `help()` function: `help(round)`

## Nesting functions

Just like we can string together multiple methods, we can **nest** functions one inside another.

Suppose we have a variable that's a negative floating point number, and we want to take the absolute value and round it to the nearest integer.

(In this example, it doesn't matter which function you do first since the math result is the same whether you round and then take the absolute value or take the absolute value and then round. But in many cases, the order of functions will matter.)

A good way to build a function is stepwise from the inside-out:
1. Take the absolute value of z: `abs(z)`
2. Round the result of step 1: `round(abs(z))`
3. Print the result of step 2: `print(round(abs(z)))`

```
# Putting it all together

z = -45.2347
print(round(abs(z)))
```

# Making your own functions

So far, we've used built-in functions. But Python also allows us to make our own new functions. We often do this for two main reasons:
- **Organization:** Code that's in functions is easier to read. Imagine opening a book with no paragraphs. How hard to read would that be?
- **Reusability:** If we perform the same analysis frequently, functions can be packaged to make them easier to reuse.

To make a new function, use a **function definition** `def` to specify the name of a new function and the sequence of statements that run when the function is called.

**Remember:** you have to create a function before you can run it (the function definition has to run before the function gets called). After you've defined the new function, you can then run the function just like any other function: `functionname()`

```
# Define new function named print_lyrics
def print_lyrics():
    print("I'm a lumberjack and I'm okay.")
    print("I sleep all night and I work all day.")

# Run the function print_lyrics
print_lyrics()
```

## Structure of a function definition

The first line of the function definition is the **header**; the rest is the **body**.
- Header begins with `def` and ends with a colon `:`
- Body must be indented.
- ***If either of the above is incorrect, your code will not work.***

![python indentation](images/python_code_blocks.png)

In our example, `print_lyrics` is the name of this new function.
- The rules for function names are the same as for variable names.
- **Avoid** having a variable and a function with the same name!

## Function versatility

Recall: Functions can contain **arguments** (variables) as input.

```
# Define a new function that takes two numerical arguments and multiplies them
def do_multiplication(x, y):
    product = x * y
    print(product)

# Run function with specified arguments
do_multiplication(8, 5)
```

Remember: If the argument is a **string**, it must be inside `" "` when you call the function.

Here's an example that takes a string argument. This is a modification of the script you wrote for last week's assignment: counting the number of each nucleotide in a DNA sequence.

**Note:** You can use vertical whitespace within a function definition to make it easier to read. As long as the entire body of the function definition is indented properly, the code will work.

```
# Define new function to count nucleotides and print
def count_nucleotides(dnaseq):

  # Count each nucleotide and assign count to new variable
  num_a = dnaseq.lower().count("a")
  num_c = dnaseq.lower().count("c")
  num_g = dnaseq.lower().count("g")
  num_t = dnaseq.lower().count("t")

  # Total number of nucleotides
  sum = num_a + num_c + num_g + num_t

  # Print results to screen
  print("DNA sequence:", dnaseq)
  print("A:", num_a)
  print("C:", num_c)
  print("G:", num_g)
  print("T:", num_t)
  print("Total nucleotides:", sum)

# Run function with specified DNA sequence
count_nucleotides("AACTTTTGGGGAGAG")

```
