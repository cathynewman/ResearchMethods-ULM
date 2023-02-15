# BIOL 5005/5006: Computational Biology

**Credit:** A lot of the materials for this course were modified from materials written by Dr. Jeremy Brown and Dr. April Wright.

## Where to find course materials

- **GitHub:** tutorials (like this document)
- **Moodle:** assignments, supplemental files (e.g., PowerPoint slides), quizzes, exams
  - I'll also post a link to each week's GitHub tutorial on Moodle.

## Rationale

This course will cover the basics of: **Programming**

Why do we want to do that? Necessity & portability.

- Most fields have some degree of computation, or computational thinking, baked into them.
- You might want to do the same types of analyses with multiple projects.
- You might want to help colleagues do the same analyses with their data.

The analysis of large data sets in biological research is becoming common, especially as new DNA sequencing technologies and data collection strategies have hugely increased the amount of data that can be collected by one researcher. Computational approaches are often needed to format and analyze these large data sets, but few biologists receive training in applying programming languages to these tasks.

This course will cover the basics of: **Data management in a computational framework**

Why do we want to do that?

* Convenience: The computer is much more effective at doing repetitive tasks than our brains are.
* Reproducibility: A computer stores records of what we have done more effectively than our brains do.
* Flexibility: When you read a paper and they're using the most cutting-edge tools, those tools are probably computational tools.

## Wow, that sounds like a lot

My goal is that when you all go on to further grad school, medicine, pharmacy, etc., you have more confidence in your ability to manage tasks that involve computation. That doesn't mean you'll never flounder! I still flounder at times. But you will have the skills to work through problems that arise. Importantly, even if you end up never coding again, the **critical thinking**, **mathematical thinking**, and **logical thinking** you learn in this course will help you in the future.

## Technology Requirements

This is a _computational_ biology course. **All students must have access to a computer with internet access.** Any OS is fine (Mac, Windows, Linux, Chromebook, etc.). Because this course is 100% online, you may use a laptop or a desktop computer.

**Internet browser:** Chrome, Safari, or Firefox (_not_ Edge or Internet Explorer... IE causes a lot of problems and breaks a lot of things).

**Suggestion:** It would be helpful (but NOT REQUIRED) to have a **second device** that's at least tablet sized to make it easier for you to simultaneously stream the Zoom tutorial video on your extra device and do the online coding activities on your computer. It's perfectly fine to do both at the same time on one computer, but a second device would allow you more screen space to work with.

**A note about tablets:** I have tested a few of the coding activities on my iPad, but not everything we will be doing. Since almost all of the coding in this course will be done through an online platform (not software you install on your computer), you could theoretically use a tablet instead of a computer. But tablet screens are so small that it would be very hard to to be successful in this course using a tablet as your primary machine. But in an emergency during the semester (for example, your computer breaks), you could use a tablet temporarily. (Theoretically, you could also use a phone, but that screen is even smaller.)

## What work will we be doing in this class?

This course is typically taught face-to-face, so we will have to work together to make the transition to virtual instruction successful. Here is what I envision for this course:

**Lecture:** I will hold a live virtual lecture on Zoom during the time that was originally scheduled for this course before it was moved online (Wednesdays at 4:00 PM). **Attendance is optional.** All Zoom lectures will be recorded and posted on the course Moodle site. During lecture, I'll introduce the day's concepts, and we will work through tutorials together. In other words, I will be walking through the steps with you on my computer as you work through the same steps on your own computer, and as a class we can work through any issues or problems that arise.

**Lab:** Lab will involve you working on independent exercises designed to guide you through the material for the week and help you apply the week's material to a new problem. I will be available to help with any problems or answer any questions and provide guidance. These assignments can be worked on in groups if you want, but each person turns in their own assignment. Assignments will be **due the following Tuesday at 11:59 PM Central Time.** (So, assignments do not have to be completed during the lab session itself.) In the past, when this was a regular face-to-face course, I made the scheduled lab time optional in the sense that once I finished the lecture material and guided tutorials, students were free to either stay and work on the assignment during lab time or leave and work on it during their own time throughout that week. This semester, I'm planning to keep the live Zoom session open for a certain amount of time after lecture so students can come and go as you wish and ask me questions. I may also see if I can set up "breakout rooms" where you can work privately in small groups.

**Project:** Each person will work on a project later on in the semester. The projects will be oriented to getting you to work with the concepts from class on a real data set. I'll provide more details later.

# Computer Setup

All of these instructions are on Moodle. I put them in a step-by-step here to hopefully streamline the course setup process.

### Primary languages: Bash, Python (3.x)

## 1) Create REPL account

All/most of our coding will be done using the online platform [repl.it](https://repl.it) in your favorite internet browser (Chrome, Safari, or Firefox).

#### To create a FREE repl account:
- Go to [repl.it](https://repl.it)
- Click the **sign up** button on the top-right.
- Create a username and password with your preferred email address. I recommend using your ULM email since this is for a class, but it doesn't really matter because your REPL account is not tied to Moodle in any way; it's just for your personal use during the semester.
- Click **sign up**
- Go to your email and click the link to verify your email address.
- Optional: REPL asks you to choose your skill level and interests.
- Languages: select **Python**, click **show 42 more**, and select **Bash** (about halfway down).
- Then you're done! You can click the **Home** tab in the left sidebar to go to your home screen.

## 2) Invite me to your REPL!

Sharing your REPL with me will allow me to see your REPL screen, highlight or make edits, and chat privately with you. This will be very useful for troubleshooting any problems you run into!
- Click the **Share** button on the top-right.
- On the _Invite_ tab, type my username: **newmanlab**
- Click the **Invite** button. That's it!
- Click anywhere outside the popup window to close it.

## 3) Set computer to show filename extensions

If you struggle with identifying file extensions (figuring out what type a file is), I suggest you set your computer to always show filename extensions (`.txt`, `.jpg`, `.sh`, `.pdf`, `.docx`, etc.).

**Windows**
- Control Panel > Appearance and Personalization > File Explorer Option (or Folder Options)
- Click the _View_ tab
- Under _Advanced Settings_, UNCHECK "Hide extensions for known file types"
- Click _Apply_ and _OK_

**Mac**
- In Finder, go to the _Finder_ menu > Preferences
- Click the _Advanced_ tab
- CHECK "Show all filename extensions"

## 4) Force browser to ask before downloading

Some web browsers by default might automatically save downloaded files to a certain location, such as your Downloads folder or Desktop. _We do not want this behavior_. To make sure you can always specify filenames and locations for downloading files, you need to set your browser to ***always ask before downloading***. You should be using Chrome, Safari, or Firefox. I will show instructions for each. DO NOT use Edge or Internet Explorer in this class. They cause all kinds of problems.

**Chrome**
- Open Chrome
- Look to the right of the address bar and click the 3 dots or horizontal bars to show menu > **Settings**
- Scroll down to the bottom and click **Advanced** to show more options.
- Under **Downloads**, make sure the toggle switch for "Ask where to save each file before downloading" is ***checked*** or set to ***ON*** (blue color).
- Close Settings tab.

**Safari**
- Open Safari
- Click **Safari** menu > **Preferences**
- In the **General** tab, set "File download location" to ***Ask for each download***
- Close Preferences window.

**Firefox**
- Open Firefox
- Look to the right of the address bar and click the 3 horizontal bars to show menu > **Preferences**
- In the **General** menu, scroll down to **Files and Applications**
- Make sure "Always ask where to save files" is ***checked***.
- Close Preferences tab.

## 5) Refresher: How to download files correctly

**PDF on Moodle:** ***How to download from REPL*** - The same instructions apply to downloading files from any website. I won't copy the info here, but make sure you understand these points about downloading files:
- Specify filename
- Check extension (_format_ or _save as type_) and add to filename only if necessary
- Choose download location

## 6) Refresher: How to unzip compressed archives

This info is also in the ***How to download from REPL*** document.

- **Mac:** Double-click ZIP file (macOS automatically unzips)
- **Windows:** Right-click ZIP file > _Extract All_

## 7) Organizing your class files

### Create a class folder

In an easily accessible place (like **Documents** or, temporarily, **Desktop**), create a new folder with a short and simple name, such as ***biol5005***

This is where you will save all files for this class.

### Organize

In your new **biol5005** directory, start creating subfolders to keep your files organized. I think the easiest structure will be the following set of subfolders:
- data
- scripts
- labs

Of course, you can change things around as you see fit. The most important thing is to learn to stay organized. Things will get out of control quickly when you work with lots of files if you don't take the time to keep it all organized in a structure that works for you.
