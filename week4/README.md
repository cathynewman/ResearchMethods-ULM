# Week 4: Introduction to Python

## Readings
From now on, I'll be posting some suggested readings that will give you some helpful background information and examples. These are optional.

For this week, take a look at:
- [Think Python, ch. 1: the way of the program](http://www.greenteapress.com/thinkpython2/html/thinkpython2002.html)
- [Think Python, ch. 2: variables, expressions, statements](http://www.greenteapress.com/thinkpython2/html/thinkpython2003.html)

A useful general resource for the next few weeks: [Style guide for Python code](https://www.python.org/dev/peps/pep-0008/)

## Struggling? Frustrated? Some good resources
- [How to think like a programmer: lessons in problem-solving](https://medium.freecodecamp.org/how-to-think-like-a-programmer-lessons-in-problem-solving-d1d8bf1de7d2)
- [Think like a programmer](https://zapier.com/blog/think-like-a-programmer/)
- [10 skills necessary for coding](https://www.computersciencezone.org/10-skills-necessary-coding/)

## Create a Python REPL

Let's create a new REPL, this time for Python. Click the _Add_ button, choose **Python**, and name your new REPL something easy, like **mypython**.

Open your new Python REPL! Share it with me (**newmanlab**)

# What is Python?
- Interpreted, high-level language
- Very popular among computational biologists
- Perhaps the most "human readable" programming language...

Without knowing any Python, look at this code below and see if you can figure out what it will do, then run it to see if you're right.

```
num_list = [1, 2, 3, 4]
new_list = []

for entry in num_list:
    new_list.append(entry*2)

print(new_list)
```

Were you able to guess correctly? Python is written in such a way that it mimics human speech and writing.

***Ask for help when you need it.***

***I'm not joking.***

***This class is a little different than others in that we don't have many "throwaway moments" when you learn a fact, use it on a test, then maybe never use it again.***

***If you don't get it now, it might be a problem later, so we'll work on it. Now.***

# Variables in Python

The concept of a **variable** in Python is the same as in bash. The syntax is a bit different, though.

## Operators

The following binary operators can be used with most data types. For ease of reading, always surround binary operators with a single space on each side.
- **Assignment:** `=` - assigns a variable name to some data
- Comparisons: `==`, `!=`
- Comparisons specific to numbers: `<`, `>`, `<=`, `>=`
- Math: `+`, `-`, `/`, `*`

Printing the value of a variable to the screen is actually easier than in bash. In Python, the `$` is not needed!

```
# Define variable x
x = 10

# Print value to screen
# Best way
print(x)

# This also works
x

# What if you wanted to print a literal x though?
print("x")
```

**Note:** Python is much less picky than bash is about spacing _within_ a line. These produce identical results:
- `x=(2+3)`
- `x = (2 + 3)` - this format is much cleaner and more readable.

## Variable Names

- `b` - single lowercase letter
- `B` - single uppercase letter
- `lowercase`
- `lower_case_with_underscores`
- `CapitalizedWords` - also known as CapWords or CamelCase (bumpy look of letters)
- `mixedCase` - differs from CapitalizedWords by initial lowercase character!
- `UPPERCASE` - not often used for variable names
- `UPPER_CASE_WITH_UNDERSCORES` - not often used for variable names
- `Capitalized_Words_With_Underscores` - ugly!

Names to AVOID:
- Never use `l` (lowercase L), `O` (uppercase letter o), or `I` (uppercase i) as a single-character variable name.
- In some fonts, these characters are indistinguishable from the numerals 1 and 0. (And the l and I may also be indistinguishable.)

Rules:
- Legal characters: **letters, numbers, underscores** (no spaces!!!)
- The first character can't be a number.

# Basic Python Data Types

We'll go through the basics of each of these data types in this lecture, and then in later lectures we'll expand on some of them.

## Numbers

Python can handle both integers and floating point (decimal) numbers.
- Integers: `myInt = 10`
- Floating point numbers (decimals): `myFloat = 3.21312`
	- Floats are stored differently in the computer's memory than integers are, and saving whole numbers as integers can mean programs take less memory to run.

Define myInt and myFloat as above. Now calculate `myInt / myFloat`. What type of number is the result?

```
# Show variable type
type(myInt / myFloat)
```

Now try `float(myInt)` and `int(myFloat)`. What are the results? Look back at the values of `myInt` and `myFloat` by typing `print()` with the variable names. Have they changed?
- Note: `int` can convert floating-point values to integers, but it doesn’t round off; it chops off the fraction part.

    ```
    int(3.9999)
    ```

## Strings - `myStr = "This is a string."`
Strings can be of any length, but are always defined with quotation marks.

In Python, single-quoted strings `' '` and double-quoted strings `" "` are the same. Pick one and stick to it consistently. But when the string itself contains single or double quote characters, use the other one to avoid backslashes in the string. It improves readability.

```
myStr = 'Say "Hey" to your neighbor.'
```

Strings can be concatenated together with the `+` operator.

```
myStr = "biology"

# No quotes around variable name
# Quotes around literal text
newString = myStr + " is super interesting"

print(newString)
```

## Methods
Methods are functions (sort of like actions or verbs) that belong to a variable.

Methods are accessed and used by appending them to the name of a variable, separated by a period `.` Methods end with an empty set of parentheses `()`. **Do not** put a space before `(` or between `(` & `)`.

For instance, let's say we define a string - `myStr = "biOLogy   "` (with a zero instead of "o," and with 3 spaces after the "y")

Here are some useful methods that can be used with that string:
- `myStr.upper()` - Converts all characters in the string to uppercase
- `myStr.lower()` - Converts all characters in the string to lowercase
- `myStr.strip()` - Removes whitespace from the beginning or ending of the string

Methods can also be chained! - `myStr.strip().lower()`

**Find & replace:** the first argument is the text to find, and the second argument is the text to use when replacing.
- `myStr.replace("y","ical")`

**Counting:** count the number of **L** s in the string and return the number. (Does capitalization matter?)
- `myStr.count("L")`

Try that command with the letter "o"... How could you modify the command to count all **o** s in this string?

## User Input
Python has a special function, `input("Message: ")`, to accept input from a user. This function reads the user input and returns it. But be sure to store it in a variable so you can use it later!

**Note:** Put a space between the `:` and the end `"` to make the output look cleaner, so the user input doesn't appear immediately after the `:` (you can try it with and without the space to see the difference).

```
userStr = input("Input a string: ")
```

You can use the string **methods** we discussed above to standardize user input - such as changing character case, etc.

```
# Here, you don't specify whether words should be capitalized.
userStr = input("Type any 3 words: ")

# Suppose you need the user input to be all lowercase.
# To ensure the subsequent code works, take user input and convert to lowercase.
# Here, we're only printing it to screen, but you get the idea.

print(userStr.lower())
```

# Python Scripts
A **script** is just a file containing a series of commands. Scripts are formatted as text files. But the things in this file are special.

Running a script in Python produces the same result as sequentially typing in and running each command separately in Terminal. Scripts save time by allowing Terminal to non-interactively run a series of commands - in other words, Terminal will run the next command immediately without you being right there at your computer to type in the command.

To write a script, you'll need to think through the steps involved in whatever task you need to complete and then write a command for each step.

**!!! This ability to break a big problem into individual steps is the most important skill in programming.**

## Comments in Python
Now that we will be writing more complicated code, **comments are essential**. Just as in bash, comments in Python are indicated by a `#` at the beginning of a line.

REPL has a shortcut keystroke to toggle lines between being commented and uncommented. Highlight the block of lines you want to comment/uncomment, then:
- Mac: &#8984; (`cmd`) + `/`
- Windows: `ctrl` + `/`

`# This is an example of a comment`

## Code Blocks
Over the next couple of weeks, we'll get to Python coding that requires close attention to indentation to separate "blocks" of code. Python is extremely picky about this. But even in cases where Python doesn't care about blocking, you should use vertical white space to make your code as clean and readable as possible.

Which of the following two sets of code looks better to you?

```
# Define a string
myStr = "biology"
# Add some strings together and print
newString = myStr + " is super interesting"
print(newString)
```

```
# Define a string
myStr = "biology"

# Add some strings together and print
newString = myStr + " is super interesting"
print(newString)
```

You'll also notice in the example above that I included comments for commands that don't really need to be commented. The decision to include a comment or not is often subjective. Typically, comments are necessary for code that isn't particularly straightforward, or as a brief descriptor at the beginning of a code block. In other words, you're never going to see a comment for something as simple as "Define a string."

But when you're just starting out and learning, it's a good rule of thumb to comment most of your commands or code blocks, even if you don't think it's really necessary.

# Errors

This is a great time to talk about how crucial it is to learn to pay attention to the text of error messages and use them to figure out exactly the problem in your code. **I am here to help, but you cannot come to me with every single error you encounter and expect me to troubleshoot it for you. Learning to troubleshoot your code is critical.**

***Once you know why you get certain types of errors, they become much easier to fix!***

## The `traceback`

Errors in Python have a very specific form, called a `traceback`. Let's examine one:

```
# This code has an intentional error.

myStr = "biology"
newString = mystr + " is super awesome"
print(newString)
```

This particular traceback has 1 level. You can determine the number of levels by looking for the number of "File" lines. Here, the traceback shows code from the most recent call, with a reference to the **2nd line** in the code.

So what error did the program actually encounter? In the last line of the traceback, Python helpfully tells us:
- The category or type of error (in this case, it is an `NameError`), and
- A more detailed error message (in this case, it says `name 'mystr' is not defined`). Can you find the mistake now?

If you encounter an error and don’t know what it means, it is still important to read the traceback closely. That way, if you fix the error but encounter a new one, you can tell that the error changed. Additionally, sometimes just knowing _where_ the error occurred is enough to fix it, even if you don’t entirely understand the message.

If you do encounter an error you don’t recognize, try looking at the official Python documentation on errors. But note that you may not always be able to find the error there, as it is possible to create custom error messages. (In those cases, hopefully the custom error message is informative enough to help you figure out what went wrong!)

**REPL HELPFUL TIP:** REPL actually marks code errors on the script itself! If you type in the above example exactly as written (including the name error), you'll see that REPL has a red underline on line 2. Hover your mouse over that line of text to see the error message.

## Variable Name Errors

A `NameError` occurs when you try to use a variable that does not exist. Try this: `print(a)`

Variable name errors come with some of the most informative error messages, which are usually of this form: `name <VARIABLE_NAME> is not defined`

There are a few very common reasons why you might have an undefined variable:
- You meant to use a string but forgot to put quotes around it.

    ```
    print(hello)
    ```

- You forgot to create the variable before using it.

    ```
    string1 = "biology"
    string3 = string1 + string2
    print(string3)
    ```

- You made a typo when you were writing your code. (Shown above in initial example.)
  - Remember that variables are case-sensitive!
  - The variable `myStr` is different from `mystr`.

## Syntax Errors

A **syntax error** means something is wrong with the "grammar" of your code and Python couldn't figure out how to read it. This is similar to forgetting punctuation in writing your spoken language. Most likely, you've messed up the punctuation somewhere, such as forgetting to close all your `( )` or `" "`

People can typically figure out what is meant by text with no punctuation, but people are much smarter than computers! If Python doesn't know how to read the program, it will just give up and inform you with an error.

```
# Do you see the error?

myStr = "biology
print(myStr)
```

Here, Python tells us that there is a `SyntaxError` on the first line, and even puts a little arrow in the place where there is an issue - end of the line. In this case, Python was reading in the string and ran into an unexpected end of line (EOL). Python expects the string to be completed (closed) before EOL. The problem here is that the variable definition is missing a closing `"` at the end, so Python thinks the string isn't finished. Correct the error and run the code again.
