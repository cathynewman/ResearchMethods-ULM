# Lab: Week 9

For this lab, you will be modifying your script from Lab 7. Submit your script as **lastname_lab9.py**. You DO NOT need to submit your output file, only the script. **Input (seq) files are on Moodle.**

**Scenario:** You are still working to identify species on Ganymede. Now you need to sort this last set of unknown sequences into species. All output from this script will write to a single output file, which we will create in CSV format (comma separated values), with the extension *.csv. That just means each data item in a line is separated by a comma.

# Instructions

Take your script from Lab 7 (after making all changes that I noted in your feedback), and modify it to meet the following criteria. I've highlighted in yellow (on the PDF) some of the changes from lab 7 that would otherwise be too easy to accidentally overlook. Please pay close attention.
- Reads in the unknown sequences from file **unknown_seqs.txt** and stores the seqs in a list.
- Reads in the known sequences from their files. The easiest way to do this is to create one list (e.g., <code>known_seqs</code>) where each list item is a _list__ of the seqs from 1 species. In other words, the list known_seqs will contain 5 lists of seqs. To create this:
	- Loop through each known filename (yes, the full filename can be a string) and do:
		- Open file (save as a var)
		- Create a <code>templist[]</code>
		- Loop through each line in file and append stripped line to <code>templist</code>
		- Append final <code>templist</code> to <code>known_seqs</code>
		- Close file
- Opens an output file (don't need to create it first; opening it will create it) and writes header to file:
	- Name it something like <code>ganymede_species_results.csv</code>
	- Header: write to file one line (one string, _including EOL character at end_) that specifies each "column" in the file: DNA sequence, GC category (low, med), GC content (value), species.
		- No spaces. Suggested string: <code>"sequence,gc_category,gc_content,species\n"</code>
- Function that calculates the GC content (same as last time, no modification).
- Writes the DNA sequence to file (modify line that printed seq to screen) with comma at end.
- Writes to file "medium," (includes comma) and the GC content (+comma) if GC content is > 0.37, or writes to file "low," (includes comma) and the GC content (+comma) if GC content is <=0.37, or prints to screen (_not write to file_, so this stays the same as last time) an error message like <code>"Something went wrong with GC content"</code> if the result is anything else.
- Tests if the sequence is present in any of the sub-lists of known sequences, and if so, writes to file the name of the matching animal, followed by EOL character (\n). If the sequence is not in any of the known lists, write to file something like <code>"New_species"</code> (note this time no spaces or punctuation)
	- Note: This time we aren't including zeylour, so delete that species from this if/elif/else block.
	- The known seqs for each species are stored in lists, which themselves are items of the list <code>known_seqs</code>. So you will be searching the first item in <code>known_seqs</code> (recall how to point to a specific list item with its index), etc.
		- BE SURE you pay attention to the order of the items in <code>known_seqs</code> and keep the same order in this block, or else you'll end up writing the wrong species name to file.
- DO NOT write or print a blank line at the end. Delete that from your script.
