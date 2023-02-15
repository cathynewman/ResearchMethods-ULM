# Lab: Week 6

For this lab, you will be modifying the script you wrote last week to convert trefnos to blorvimas. (Also make any changes to your trefnos_to_blorvimas function itself that I noted on the feedback to your week 5 assignment.) Submit your script as **lastname_lab6.py**

Modify and add to your script to loop through a list of numbers (mass in trefnos), run <code>trefnos_to_blorvimas</code> on each number to convert it to blorvimas, and append the result to a new list. **This time don’t round the result!** The final result of your script should be a list of the numbers in blorvimas. As a reminder, there are 56.281 blorvimas in 1 trefno.

**Input** list of masses in trefnos:
[22.5, 68.2, 34.8, 87.4, 63.5, 56.4, 37.6, 41.3, 21.3, 40.2]

When you run your script, this should be your **output**:
[1266.3225, 3838.3642, 1958.5788, 4918.9594, 3573.8435, 3174.2484, 2116.1656, 2324.4053, 1198.7853, 2262.4962]

The output list should not be in your script; it’s what should get printed to the screen when you run your script on the input list above. **Note:** some results may look strange (4918.959400000001 instead of 4918.9594) because floating point numbers can’t be converted exactly to binary in Python. This is ok. Your script still works as expected and you don’t need to change anything.

# Backbone Script

Here is a script backbone that you can use as a guide (you can copy or modify… this is just a guide). I used 4 spaces here for indentation just to make it look clearer in this document, but 2 is fine (default in repl); consistency is what matters.

```
# Define function to convert a number in trefnos to blorvimas
    
    # Remember to return the value to use it later


# Define input list


# Create empty output list


# Loop through input list with for loop
    
    # Run trefnos_to_blorvimas to convert each number and append result to output list


# Print output list
```
