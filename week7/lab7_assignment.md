# Lab: Week 7

For this lab, you will be starting an analysis of 7 new DNA sequences. Submit your script as **lastname_lab7.py**

**Spoiler Alert:** The last page (p. 4 of PDF) shows the expected output for this assignment.

**Scenario:** You are still working on Ganymede, but you're finished with geology. You signed up for this mission to be a biologist. Ganymede has a surprisingly large number of species that are able to survive in its harsh environment, and you are now studying the wildlife of this moon. Over the past few months, you have been building a database of DNA sequences. You have found several groups of closely related individuals, and you have named each group as a new species. Now, you have collected a short DNA sequence from 7 additional animals. We don't yet have enough knowledge about the animals to be able to identify them on sight, but you can search the database to see if these new sequences match any known sequences.

**DNA Sequence GC Content:** The GC content of a DNA sequence is simply the proportion of nucleotides that are G or C. In some species, GC content has been associated with genome size or chromosome structure. GC content is also often used in analyses of molecular evolution (especially, examining nucleotide composition heterogeneity among species or higher groups) and sometimes in phylogenetic analyses (relationships among species).

# Instructions

The following is not a step-by-step; it's a list of things that your script needs to do. See the backbone for the step-by-step. **Read all the way through pages 1-2 here before starting.** Write a Python script that iterates through each DNA sequence in the list of unknown sequences and for each sequence:
- Calculates the GC content
- Prints the DNA sequence
- Prints "medium" and the GC content if the GC content is > 0.4, or prints "low" and the GC content if the GC content is < 0.4, or prints an error message like "Something went wrong with GC content" if the result is anything else.
	- Print in one line – example output for GC of 0.55: medium 0.55
	- The math: GC content = (G count + C count) / sequence length
		- Remember your basic math: parentheses are important for correct order of operations.
		- Look back at previous tutorials if you don't remember how to count the number of a certain letter in a string or find the total length of a string.
- Tests if the sequence is present in any of the lists of known sequences, and if so, prints the name of the matching animal. If the sequence is not in any of the known lists, print something like "New unknown species!"
	- Example: if the sequence is present in the list named <code>dog</code>, output should print "Dog" or "dog" (case doesn't matter because you're telling Python to print the literal string, not calling a variable name inside <code>print()</code>)
- Print a blank line with <code>print("")</code>
	- This is just to make the output easier to read.
	- No space between the quotation marks, or it will print that space. You just want to print an empty line with nothing on it.

# Backbone Script

Here is a script backbone that you can use as a guide (you can copy or modify… this is just a guide). Also use the example we went through in the tutorial as a guide.

**Commenting:** Remember that from here on out, you will need to get in the habit of including copious comments in your scripts. If in doubt, comment it, even if it might be unnecessary. If your script is just bare-bones with very little commenting, I'll start counting off. The below is just a backbone to get you started.

```
# Unknown sequence list


# Known sequences


# Define function to calculate GC content of a sequence
    
    # Remember to return the value to use it later


# Iterate through unknown sequence list

      # Print the sequence

      # Print GC content info:
      # If GC content function result > 0.4, print "medium" and GC content
      # If GC content function result < 0.4, print "low" and GC content
      # Print error message if GC content function result is anything else

      # Search each known list, print animal name if sequence is in list

      # Print blank line
```

# DNA Sequences

Copy/paste these into your script.

**The new unknown sequences:**

["TAATAATCACCACCCTCCTCACTCTAGTCCTATT", "TACGGATCCTATCTCTACAAAGAAACATGGAACA", "AAAGAAACATGGAATATCGGAGTTATTTTACTAT", "ACCCGAGACGTACAATACGGATGACTCATCCGTA", "TAAAATGAAGAGTCTTTGTAGTATAATCATTACC", "ATGACCAACATTCGAAAATCATACCCCCTTACCA", "GAATCCAACATTCGAAGCTCATACCCCATTACCA"]

**Database of known sequences (6 lists, each list name is a species):**

nenreep = ["TGAACTAATGGCCCACACAATACGAAAAACACAT", "CTCATTTATTGACTTACCAACCCCCTCAAACATC", "TGTTTAATTACACAAATCTTAACAGGACTATTTC", "TTTCATCCGTAGCACACATCTGCCGAGACGTAAA", "AGCTTCATTTTTTTTCATTTGTATTTTTCTTCAT", "AAAGAAACATGGAATATCGGAGTTATTTTACTAT", "TTCCGTGAGGACAAATATCATTTTGGGGGGCAAC", "AGGGGATACTTTAGTTCAGTGAATTTGAGGCGGG", "GCCTTCCACTTTTTATTCCCATTTTTAATTGCTG", "CAGGATCTAATAACCCAACAGGAATAACCTCAAA"]

rooflac = ["GGCTCACTTCTGGGCGTTTGCCTAATTGCTCAGA", "CAGACACCTCTCTTGCATTTTCATCCATCGCTCA", "CAACCTTCATGCTAACGGCGCATCCTTCTTTTTT", "TACGGATCCTATCTCTACAAAGAAACATGGAACA", "CTTTTGTAGGTTATGTTCTCCCATGAGGTCAAAT", "ATCAGCCGCCCCATACATCGGCACAAACCTAGTT", "ACCTTGACCCGCTTTTTTACTTTTCACTTCATTC", "TCCTCTTCCTCCATCAAACAGGCTCGTCTAATCC", "TCACCCCTACTTTTCTTACAAAGATCTGTTTGGC", "ACCTTTGCCCCTAACATTCTAGGAGACCCCGACA", "ACATCAAACCAGAGTGGTACTTTCTGTTTGCTTA"]

ynemard = ["ATGACCATAAACCACCGAAAAACCCACCCACTAA", "GCCCCTCCAACATCTCTGCCTGATGAAACTTTGG", "TACTGGAATTTTCCTAGCTATACACTACTCCCCA", "ACCCGAGACGTACAATACGGATGACTCATCCGTA", "GCATCTACCTTCACATCGGACGAGGACTCTATTA", "AATTATCCTACTACTCCTAACAATAGCCACTGCA", "TTTTGAGGTGCCACCGTTATTACTAACCTCCTCT", "GAATCTGAGGTGGATTCTCAGTAGACAACGCAAC", "ATTTACAATCATAGGTCTAACAATAGTACACCTA", "GGATTAAACTCAAACACTGACAAAATCCCATTCC", "TTCTAATACTAACCCTCCTACTAACCCTAACACT", "CACACCAGCCAACCCCCTATCTACCCCACCACAT", "ATTCTACGATCTATCCCAAACAAACTAGGTGGCG"]

myywox = ["ATGACAATCACACGAAAATCCCACCCAATTCTAA", "CCTCCAATATCTCTGCATGGTGAAACTTCGGCTC", "AGGCCTATTCCTAGCCATGCACTACACCGCAGAC", "CGAGATGTCCAATACGGCTGACTAATCCGAAACC", "TCTACCTCCACATCGGACGGGGCCTATACTACGG", "AGTCCTACTATTACTAGTAATAGCCACCGCCTTC", "TGAGGCGCCACAGTAATCACCAACCTATTATCCG", "TCTGAGGGGGATTCTCGGTAGACAACGCTACCCT", "CACCATCATCGCCCTAGCAATATTGCACCTACTT", "CTTAACTCCAACCCAGATAAAATCCCGTTCCACC", "TAATAATCACCACCCTCCTCACTCTAGTCCTATT"]

zeylour = ["ATGACCAACATTCGAAAATCATACCCCCTTACCA", "CATCTAACATCTCAGCATGATGAAACTTCGGCTC", "CGGCCTCTTTTTGGCCATACACTACACATCAGAC", "CGCGACGTTAATTATGGCTGAATCATCCGATATT", "TGTACATACATGTAGGACGGGGAATATACTACGG", "CATACTATTATTTACAGTCATAGCCACAGCTTTT", "TGAGGAGCAACCGTAATCACTAACCTCCTGTCAG", "TCTGAGGGGGCTTCTCAGTAGACAAAGCCACCCT", "CATTATCTCAGCCTTAGCAGCAGTACACCTCTTA", "ATTACATCCGATTCAGACAAAATCCCATTCCACC", "TACTAGTTTTAACACTCATACTACTCGTCCTATT", "CCCAGCCAACCCTTTAAATACCCCTCCCCATATT", "CTCCGATCCATCCCCAACAAACTAGGAGGAGTCC"]

bebrod = ["GCTTCAATCTTATATTTCACCATCTTATTGATCC", "TAAAATGAAGAGTCTTTGTAGTATAATCATTACC", "TCCCTAAGACTCAAGGAAGAAGCTCTTGCTCCAC", "TCCCTGACACCCCTACATTCATATATTGAATCAC", "TTCTTCCCTCCCCTATGTACGTCGTGCATTAGTG", "TATCCTTACATAGGACATATTAACTCAATCTCAT", "CACTTAGTCCAATAAGGGCTTAATCACCATGCCT", "TCTCGCTCCGGGCCCATACTAACGTGGGGGTTAC"]

# Example Step

Take the first sequence in the unknown list as an example. Here is the process your script should run on that item:
1. Prints the seq: <code>TAATAATCACCACCCTCCTCACTCTAGTCCTATT</code>
2. Runs function to calculate GC content: length=34, #G=1, #C=13; (1+13)/34 = 0.4117647058823529
3. Prints GC content info: <code>medium 0.4117647058823529</code>
4. Tests if the sequence is present in any of the known lists, and if yes, prints animal name. It is present in list myywox, so prints: <code>Myywox</code>
5. Prints blank line

# Expected Output – Check Your Work!

Here is what your full output should be. Use this to check your work. The only reason your output would differ is if you search the known lists in a different order, which is fine. It's also fine to not capitalize the name of the animal in the output text. But otherwise, _within__ each block of text in the output, everything should look the same between your output and the below.

```
TAATAATCACCACCCTCCTCACTCTAGTCCTATT
medium 0.4117647058823529
Myywox

TACGGATCCTATCTCTACAAAGAAACATGGAACA
low 0.38235294117647056
Rooflac

AAAGAAACATGGAATATCGGAGTTATTTTACTAT
low 0.2647058823529412
Nenreep

ACCCGAGACGTACAATACGGATGACTCATCCGTA
medium 0.5
Ynemard

TAAAATGAAGAGTCTTTGTAGTATAATCATTACC
low 0.2647058823529412
Bebrod

ATGACCAACATTCGAAAATCATACCCCCTTACCA
medium 0.4117647058823529
Zeylour

GAATCCAACATTCGAAGCTCATACCCCATTACCA
medium 0.4411764705882353
New unknown species!
```
