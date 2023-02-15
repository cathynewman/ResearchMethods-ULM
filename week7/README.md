# Week 7: Iteration and Conditionals

## Midterm Exam
- [ ] Next week (open Weds morning, close the following Tues night).
	- No lecture, quiz, or assignment next week. Only the exam.
- [ ] I am writing up a document that has a lot more info about the exam, format, what to expect, etc. I will post it on Moodle tomorrow.
- [ ] Read the document first, then ask me any questions.

## Reading
For this week, you may wish to take a look at:
- [Think Python, ch. 5: Conditionals and Recursion](http://www.greenteapress.com/thinkpython2/html/thinkpython2006.html)
- [Think Python, ch. 7: Iteration](http://www.greenteapress.com/thinkpython2/html/thinkpython2008.html)

# Flow Control

One very important programming concept is **flow control:** controlling the order in which Python statements are executed. We've already explored one method of flow control: the **`for` loop**.

The other primary method of flow control is the use of **conditionals:** doing different things depending on current conditions.

# Booleans - `True` or `False`

Conditional statements test whether or not a given condition is true. So in order to work with conditionals, we first need to talk about another type of variable: the **boolean**. Booleans can take the values `True` or `False` only.

We can return booleans using certain operators in **logical statements** (a statement that returns `True` or `False`). Logical statements return a boolean variable indicating the result of the comparison.
- `<` - is less than
- `>` - is greater than

    ```
    # Set x equal to 10
    x = 10

    # Test statements
    x < 20
    # out: True
    x > 20
    # out: False
    ```

- `!=` - is _not_ equal to
- `==` - is equal to

    ```
    # Set x equal to 10
    # ONE equal sign is still for variable assignment!
    x = 10

    # Test if x is equal to 15
    x == 15
    # out: False

    # Using one = here would reassign x
    # which is not what you want to do
    x = 15
    # Now x is 15, not 10
    ```

- `in` - given item is in given list

    ```
    mylist = ["cat", "dog", "bird", "frog"]

    "dog" in mylist
    "buffalo" in mylist
    ```

- `.startswith()` - string starts with given string argument

    ```
    seq = "AACTGGGAGATC"

    seq.startswith("C")
    ```

Those are just a few of the possible operators in Python. If you want a better idea of what all you can do, see [this website here](https://www.w3schools.com/python/python_operators.asp). Of particular interest to us in this tutorial are the comparison operators (>), logical operators (and, or), and membership operators (in, not in).

# `if` statements

The **`if` statement** does two things:
1. Tests if a certain condition is true.
2. If true: does a thing.

The general form is:

```
if <CONDITION>:
    <DO_THIS>
```

Two things to note, just like with `for` loops:
- The first line of the `if` statement ends with a colon `:`
- The code block inside the `if` statement must be indented.

```
expression_level = 150

if expression_level > 100:
  print("Gene is highly expressed")
```

Most of the time, we want to use an `if` statement to test a property of some variable whose value we don't know at the time we're writing the program. The example above is obviously not very useful since the value of the expression_level variable is set there in the script and isn't going to change!

Here's a slightly more interesting example – We'll define a list of gene accession names and print out just the ones that start with "a". To do this, we need to iterate through the list using a `for` loop:

```
accs_list = ["ab56", "bh84", "hv76", "ay93", "ap97", "bd72"]

for accession in accs_list:
  if accession.startswith("a"):
    print(accession)
```

`if` statements can be used on their own (without an `else`), but no code will be executed when the condition is false, so this often isn't very useful.

# `if...else` statements

To include code blocks that should be executed _when the condition is false_, we use an `if...else` statement. These have the general form:

```
if <CONDITION>:
    <DO_THING_WHEN_TRUE>
else:
    <DO_THING_WHEN_FALSE>
```

**Important Notes:**
- The `else` part of the block is at the same indentation level as `if`.
- Both the `if` line and `else` must end with colon `:`

**Formatting Note:** Although your code would still work if you put a blank line between the `if` and `else` blocks, this is bad practice. ***Always keep the entire `if...else` block together with no blank lines*** because it executes as a single block of code. Going forward, I will start counting off points for bad style when it's something we've talked about like this.

```
# Set x equal to 10
x = 10

# Test a condition and do things depending on condition
if x > 15:
  print("x is greater than 15")
else:
  print("x is not greater than 15")
```

## Nesting a series of conditions with `elif`

Sometimes we want to test a **series of conditions** to decide what to do.
- If Condition A is True, do Thing A.
- If Condition A is False, test Condition B.
	- If Condition B is True, do Thing B.
	- If Condition B is False, test Condition C.
		- If Condition C is True...

In these cases, we can follow the logic of the thought process above and use a **nested set** of `if...else` statements:

```
x = 10

if x > 15:
  print("x is greater than 15")
else:
  if x < 15:
    print("x is less than 15")
  else:
    print("x equals 15")
```

***Correct indentation is critical.*** You must pay extremely close attention to the code blocks when writing nested conditional statements. Below is an image of the same code but with color-coded conditional blocks:

![if-else indentation](images/if-else_indentation.png)

**Another note:** Now that we're working with multiple levels of indentation, this is a reminder that you must always use the same number of spaces for each level of indentation. For example, REPL's default is 2 spaces, so you use an additional 2 spaces for each additional level:
- Initial: 0 spaces
- First indentation level: 2 spaces
- Second indentation level: 4 spaces

Now, although nested `if...else` statements are very useful, they can get cumbersome rather quickly if we're stepping through more than just a couple of conditionals. For example:

```
nuc = "A"

if nuc == "A":
  print("Nucleotide is an A")
else:
  if nuc == "C":
    print("Nucleotide is a C")
  else:
    if nuc == "G":
      print("Nucleotide is a G")
    else:
      if nuc == "T":
        print("Nucleotide is a T")
```

As you can see, the above block of code is pretty clunky, even though we're only stepping through four conditionals. Thankfully, Python offers a much more concise way to write this!

Instead of using 2 lines for `else` and the subsequent `if`, we compact those lines into a single `elif` (literally, squishing together the words "else" and "if"). This also removes the messiness of multiple levels of indentation.

```
nuc = "A"

if nuc == "A":
  print("Nucleotide is an A")
elif nuc == "C":
  print("Nucleotide is a C")
elif nuc == "G":
  print("Nucleotide is a G")
elif nuc == "T":
  print("Nucleotide is a T")
```

### Closing out `elif` statements

As the above code is currently written, nothing would happen if the variable `nuc` has a value _other than_ `A`, `C`, `G`, or `T`.

This can be a big problem when accepting input from a user or file that might provide a nonsensical value. The user needs to know that something is wrong and what they need to do to correct the problem. If your script simply ends without doing anything, that's incredibly unhelpful.

So to capture these cases when the input is invalid, it's always best to close with a simple `else` that returns some sort of **custom error message**:

```
nuc = "H"

if nuc == "A":
  print("Nucleotide is an A")
elif nuc == "C":
  print("Nucleotide is a C")
elif nuc == "G":
  print("Nucleotide is a G")
elif nuc == "T":
  print("Nucleotide is a T")
# Message for invalid input
else:
  print("This is not a valid nucleotide")
```


# Exercise

Now, let's take a list of strings (in this example, a list of vertebrates) and do some things with each item:
1. Print the string text
2. Find the length of the string and print text depending on string length
3. Search several other lists ("database") for the string and print text depending on result
4. Print a blank line after each iteration

Here is the backbone to get us started. Copy/paste into REPL:

```
# Input list
verts_to_classify = ["cat", "bird", "salamander"]

# Database of lists
amphibians = ["frog", "toad", "salamander", "caecilian"]
mammals = ["dog", "bear", "fox", "koala", "cat", "monkey", "human"]
reptiles = ["lizard", "snake", "turtle", "croc", "bird", "dinosaur"]

# Define function to find length of string


# Iterate through input list

  # Print animal name

  # Print length of animal name in characters--
  # <If length < 9, print "Short word:", length>
  # <If length > 9, print "Long word:", length>
  # <Anything else: error message>

  # Search database and classify animal--
  # <amphibians: animal name, "is an amphibian">
  # <mammals: animal name, "is a mammal">
  # <reptiles: animal name, "is a reptile">
  # <Anything else: message>

  # Print blank line
```
