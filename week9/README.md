# Week 9: Files in Python

# File objects

To read or write from a file, we need to create a **file object** that can actually read the contents of or write to a file. Python has a built-in function to create a file object: `open("FILENAME", "MODE")`
- `FILENAME` argument = a string with the filename (or path to the file)
- `MODE` argument:
	- `r` - read from a file (default)
	- `w` - write to a file
	- `a` - append to a file

# Reading from files

To open up a new file object to read file contents, use syntax like this:

```
infile = open("filename", "r")
```

***!!! Important concept !!!*** Just to reiterate this once again, whenever we talk about filenames in programming, we mean the FULL filename, which includes the extension. A file named "data" is a different file from a file named "data.txt".

### Practice files

Create a text file in your repl using the **Add File** button in the Files pane on the left, and name the file `data.txt`. Make sure the filename includes the `.txt` extension. Add a few lines of text to your file. We will use this file throughout the tutorial.

## Reading in line-by-line

One of the most useful ways to read in a file is to read it in line-by-line recursively in a `for` loop.

```
infile = open("data.txt", "r")

for line in infile:
    print("Length of line is:", len(line))
```

Note that `line` is just a variable name we've chosen to hold each line as we iterate through the file. You can use any variable name you choose, just as with any other `for` loop.

Look at the output. Count the number of characters in each line of your infile. Is there a discrepancy? Why does there seem to be an extra invisible character in each line count???

### EOL: end-of-line character (`\n`)

Plain-text files have a special character to indicate the end of a line: a backslash followed by a lowercase n: `\n`. This is called an **end-of-line (EOL) character**.

***!!! Important !!!*** The EOL character (`\n`) is retained when the line is read in.

**Recall:** you can use the `.strip()` method to strip the whitespace (including EOL character) from the end of a string variable (a line, in this case). Compare the following to the previous example:

```
# Reset file current position to beginning
infile.seek(0)

# Line by line but strip trailing EOL
for line in infile:
    print("Length of line is:", len(line.strip())
```

### Reset file current position

Notice that the previous example includes the line `infile.seek(0)`. Try running the example again but without that line. What happens?

When Python is reading in a file line by line, when it reaches the end of the file, the line counter doesn't reset itself. The **file current position** remains at the end of the last line.

Force Python to move the _file current position_ back to the beginning of the file with the `.seek(0)` method invoked on the file object.

### More useful: read in line-by-line to list

Usually we aren't reading in a file and immediately doing something with each line (such as printing to screen). Instead, we often need to store the file text as a variable so we can use it later. Typically, we'll store each line as an item in a **list**.

Read in the file line-by-line and store it as a list, where each line is a list item, with line endings stripped. Nothing in the code below is new to you... We're simply taking what you've already learned about handling lists and applying it here to input from a file.

```
infile = open("data.txt", "r")

# Create empty list
species_list = []
# Read file and add lines as items to list
for line in infile:
  species_list.append(line.strip())
```

Print the list now to see what the above code did.

### Reading in multiple files

The most straightforward way to read in multiple files recursively is to add an extra step to the above: read in each file to a temporary list, which you append to the "final" list... So you ultimately end up with one big list, where each item is a "sub-list".

**File setup:** Create 3 new text files, each with 3 lines of text (one word each, let's keep it simple). For example:
- `birds.txt` - heron, cardinal, chickadee
- `mammals.txt` - cat, dog, moose
- `reptiles.txt` - turtle, snake, lizard

Here's the thought process we'll use:
1. Create empty list ("top list") to store all the file data.
2. Recursively read in each file...
3. Create a temp list to store lines from 1 file...
4. For a file, recursively read in each line and append STRIPPED line to temp list. After looping through each line, append temp list to "top list" as a new item...
5. Do step 4 for each file (that's what step 2 is).

Thus, the final "top list" is a _list of lists_. Let's do it with the files we just created:

```
# Create top list
list_of_animals = []

# Recursively read in each file
for i in ["birds.txt", "mammals.txt", "reptiles.txt"]:
    # Open file
    word_file = open(i, "r")
    # Create temp list
    templist = []
    # Recursively read in each line in file and add to templist
    for line in word_file:
        templist.append(line.strip())
    # Append templist to top list
    list_of_animals.append(templist)
    # Close file
    word_file.close()
```

Let's explore the result of the above code by looking at `list_of_animals`:

```
In: print(list_of_animals)
Out: [['heron','cardinal','chickadee'],['cat','dog','moose'],['turtle','snake','lizard']]

# How to access only the bird list??
# Print first item in list_of_animals
In: print(list_of_animals[0])
Out: ['heron','cardinal','chickadee']

# Same to access second or third item, use list indexes
```

# Writing to files

## Step 1: open file for writing

To create a file object to use for writing, we'll again use the `open()` function, but we'll specify `"w"` for the `MODE`

```
outfile = open("outfilename", "w")
```

Again, be sure to include the extension as part of the filename.

***!!! Important !!!*** You must _open_ the output file (as above) before you can write to it (below)!

## Step 2: write to file

To write to the file **line-by-line**, use the `.write()` method.

```
# Open output file
outfile = open("output.txt", "w")

# Write to output file
outfile.write("This is a new sentence.\n")

outfile.close()
```

**NOTE:** The `write()` method does NOT, by default, add a **newline character** (line break) to strings. To end a line, we have to explicitly include `\n` in the string to write. No spaces.

#### What can I write to a file?

The argument of `write()` ***must be a string, ALWAYS***.

If we want to put other values in a file (for example, numbers), we have to convert them to strings. The easiest way to do that is with `str()`:

```
x = 52
outfile.write(str(x))
outfile.close()
```

Python can also only write ***one string at a time***. If your `.write()` statement calls a variable to write and you want to add other things at the same time (such as EOL), add strings together using `+`. This creates a single combined string, whereas using a comma indicates referencing two separate strings.

```
x = 52

# To print to screen
# You can print >1 thing, use commas to separate
# And you can print numbers
print("The value of x is:", x)

# To write to file
# You can only print 1 thing, so add things together
# And it must be a string
# + doesn't auto generate spaces between the items
outfile.write("The value of x is: " + str(x))
outfile.close()
```

```
x = 52
outfile.write(str(x) + "\n")
outfile.close()
```

## Step 3: close file

When you finish writing everything you need to write to the file, you must **close the file** with `outfile.close()` before you actually see any changes appear in the file.

Closing the file saves all the changes you made while it was open.

# Write vs. Append

If your output file already exists with text before you run the script, opening that file with `"w"` will overwrite the preexisting text.

It WILL NOT overwrite _within a single run of the script_, even if the script includes loops.

For example, if your script has a `for` loop that writes something to the outfile each time, each iteration of the loop will append to the outfile. But if you later run the same script AGAIN (without changing the outfile name), then the outfile from the previous time you ran the script will be overwritten.

## Appending instead

If you open an outfile with `"a"`, you can run the script multiple times and each time the output will be appended to the end of the existing outfile without overwriting previous output.

```
# Open
outfile = open("output.txt", "w")
# Write
outfile.write("Today is Wednesday.\n")
# Close
outfile.close()

# Then run it again with different text
# Now look at the outfile. What does it contain?
```

Now, compare to:

```
# Open
outfile = open("output.txt", "a")
# Write
outfile.write("My last name is Newman.\n")
# Close
outfile.close()

# Now look at the outfile. What does it contain?
```
