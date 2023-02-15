# Lab 1

**Due Tuesday, Aug. 25, at 11:59 PM (Central)**

Filesystem structure for today’s lab activity:
- lab1/
	- aboutme.txt
	- temp.txt
	- biology/
		- biologyfact.txt

**Instructions:** Complete the following steps in REPL by typing commands directly into the command line in the terminal window:
1. Change directory to ~/mybash.
2. Using mkdir and touch, recreate the filesystem structure shown above.
	- Be careful! Pay close attention to the hierarchy to make sure you are creating each file and folder in the correct location. If you accidentally mess up and create a file/folder in the wrong place, just use a command to move it. That’s why we learned all those commands.
	- There are multiple ways you can accomplish this step. You could create all files/folders from your current working directory, being careful to use relative paths so they’re created in the correct locations. Or you could change directory into the location where you want to create each new folder/file (create lab1, go to lab1, create biology). Doesn’t matter; outcome is the same.
3. Click on aboutme.txt to open the file in REPL’s text editor. Type in some information about yourself, such as an interesting fact about yourself. (The files automatically save.)
4. Click on biologyfact.txt to open it. Type in a cool biology fact, anything at all.
5. Using cd and an absolute path, change directory to the biology folder.
6. Now, using cd and a relative path, change directory back to the lab1 folder.
7. List the contents (in long list form) of the lab1 folder and send the output to a new file (in current folder) named lab1contents.txt
8. Now, carefully delete the file temp.txt (use a command in terminal, not the menu in the filesystem window).
9. Using history and sending the output to a file (in lab1) named commands.txt, show the history of commands you ran for steps 1-8 (including any mistakes and corrections, that’s fine).
	- I know REPL can be weird with history, so if it doesn’t bring up your full history, don’t worry. If it’s partial, just include what’s there.

**Downloading & submitting your completed work:**
- Click the 3 dots to the right of the Add Folder button to show the Files menu. Click Download as zip.
- Keep the default filename (should be mybash.zip), and make sure you know where on your computer you’re downloading the file to.
- You don’t need to unzip the file. Keep it as is.
- Upload that same zip file to Moodle for the Lab 1 assignment.
- You’re done!
