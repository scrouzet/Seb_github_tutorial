% Github very practical and simple (thus totally incomplete) tutorial
% Sébastien Crouzet - Oszillab, Berlin
% January 15, 2014

<!---
<img src='images/github-logo.png?raw=true' alt='GitHub Logo' height='100'>

pandoc github_tutorial.md -o github_tutorial.html
pandoc -t dzslides -s github_tutorial.md -o github_tutorial_slides.html
--->

# What is Github?

It started as a developer's collaborative platform. 

It is now the largest online storage space of collaborative works that exists in the world.

Github is just a special kind of social website. They are a company with the aim of making money. But they do it through a good business model rather than ads or selling your private data. 

Learning how Github works is like learning to use Facebook (more or less).

What is more tricky is to learn Git.

# What is Git?

Git is version control software, which means it manages changes to a project without overwriting any part of that project.

It was created by Linus Torvalds (the same guy who programmed the linux kernel)

<img src='images/linus_torvalds.jpg?raw=true' alt='Linus Torvalds' height='100'>

#Why using something like Git? 

**Problem**: Say you and a coworker are both updating pages on the same website. You make your changes, save them, and upload them back to the website. So far, so good. The problem comes when you both work on the same page at the same time. One of you is about to have your work overwritten and erased.

**Solution**: With a version control application, you can both upload your revisions to the same page. Git will save two copies. Later, they can be merged easily if there is no conflict. You can even revert to an earlier version at any time, because Git keeps a 'snapshot' of every change ever made.

# The git terminology

**Repository**: An online directory where your projects lives. Sometimes GitHub users shorten this to 'repo.' It can be local to a folder on your computer, or it can be a storage space on GitHub or another online host.

**Commit**: This is the command that gives Git its power. When you commit, you are taking a 'snapshot' of your repository at that point in time, giving you a checkpoint to which you can reevaluate or restore your project to any previous state.


# Git-Specific Commands

There are a LOT of Git commands. But to use the basics of Git, you'll only need to know a few terms.

	git init
Initializes a new Git repository. Until you run this command inside a directory, it's just a regular folder. Only after you input this does it accept further Git commands.

	git config
Short for 'configure,' this is most useful when you're setting up Git for the first time.

-----------------------------

	git help
Forgot a command? Type this into the command line to bring up the 21 most common git commands. You can also be more specific and type 'git help init' or another term to figure out how to use and configure a specific git command.

	git status
Check the status of your repository. See which files are inside it, which changes are not committed yet, and which branch of the repository you're currently working on.

-----------------------------

	git add one_file_I_changed.m
This brings new files or files you made changes to to Git's attention. Only after being added, they'll be included in Git's 'snapshots' of the repository.

	git commit -m "Blabla bla blabla"
Git's most important command. After you make any change, input this to take a 'snapshot' of the repository. The associated message is a short description of the changes you made. It is very important to make it as meaningful as possible.

-----------------------------

	git push
When working on your local computer, and want to make your commits visible online on GitHub: you 'push' the changes up to GitHub with this command.

	git pull
When working on your local computer, and want to grab the most up-to-date version of the repository to work with: you 'pull' the changes down from GitHub with this command.

# Daily workflow with git

Simple version (what I do):

<img src='images/git-basicwf1.png?raw=true' alt='Daily workflow' height='120'>

-----------------------------

More elaborate version (what real programmers do):

<img src='images/git_daily_workflow_small.png?raw=true' alt='Daily workflow' height='400'>


# A very concrete example
Let's say you are one of the developer of EEGLAB (and let's say EEGlab would be hosted on github). Today you want to finally fix this stupid bug that deletes the reference channel at import with the function made for Biosemi. You'd do:

	cd ~/thePathToEEGlab/eeglab/ 
	git pull

-----------------------------

Now you have the up-to-date version of eeglab. 

You then fix the bug in the function you wanted to modify. You run the code and do the necessary tests to check that what you did works well, etc. 

It works. So now it's time to make this official and allow everybody to take advantage of this modification.

	git add this_function.m
	git commit -m 'Blablabla'
	git push

-----------------------------

Hands-on: create and update a Github repository

-----------------------------

# Setting Up GitHub And Git For The First Time

Before being able to do that, you'll first need to sign up for an account on GitHub.com. It's as simple as signing up for any other social network.

You also need to install and setup git:
https://help.github.com/articles/set-up-git

If you are working on Windows or Mac, you can just download the official Github client and it will offer to install the command line tool. I like the official clients, but here I'll only do the tutorial with the command line, which allows to really understand the order of actions. Once you've understood that, using the GUI client will be very straightforward. 


# Creating Your Online Repository
Now it's time to create a place for your project to live: a repository or 'repo' for short, a digital directory or storage space where you can access your project, its files, and all the versions of its files that Git saves.

Go back to GitHub.com and click the tiny book icon next to your username. Or, go to the new repository page if all the icons look the same. Give your repository a short, memorable name. Make it public.

Once you've clicked the green 'Create Repository' button, you're all set: you now have an online space for your project to live in.

<<<<<<< Local Changes
## Creating Your Local Repository
The space for your project to live online is now set, but that’s not where you’ll be working on it. Your work is going to be done on a local directory on your computer. So we need to actually link that repository we just made as a local directory.
=======
# Creating Your Local Repository
The space for your project to live online is now set, but that's not where you'll be working on it. Your work is going to be done on a local directory on your computer. So we need to actually mirror that repository we just made as a local directory.
>>>>>>> External Changes

First, create this directory at the appropriate location on your computer:

	mkdir ~/src/Seb_GitHub_tutorial

It's better to use the same name as for the Github repository. Next, go inside your directorty:

	cd ~/src/Seb_GitHub_tutorial
	touch README.md
	git init
	git add README.md
	git commit -m "first commit"
	git remote add origin https://github.com/scrouzet/github_temporary_tutorial.git
	git push -u origin master

-----------------------------

Now we're finally using a Git command. For your next line, type:

	git init

This tells the computer to recognize this directory as a local Git repository. If you open up the folder, it won't look any different, because this new Git directory is a hidden file inside the dedicated repository. However, your computer now realizes this directory is Git-ready, and you can start inputting Git commands.

Now you've got both an online and a local repo for your project to live inside. You need to connect them.


# Connect Your Local Repository To Your GitHub Repository

Assume that we have a GitHub repo called 'MyProject' located at https://github.com/username/myproject.git.

	git remote add origin https://github.com/username/myproject.git


# Making changes to the repository

Now let's add the first part of your project by making your first commit to GitHub. Type:

	touch Readme.md

We can see the new Readme file. But Git does not really care yet about it, as you can see by typing:

	git status

Readme.md is listed as an 'untracked' file, which means Git is ignoring it for now. 

-----------------------------

To make Git notice that the file is there, type:

	git add Readme.md

The first file is added. Now it's time to take a 'snapshot' of the project so far, or 'commit' it:

	git commit -m '1st upload of Readme.md'

Now that we've done some work locally, it's time to 'push' the first commit up to GitHub.


	git push

Log into GitHub again. You'll notice the changes we just made are registered in the repository.


# Useful resources
- http://gitref.org/
- http://rogerdudler.github.io/git-guide/

# If you want to become a power user, then

**Branch**: How do multiple people work on a project at the same time without Git getting them confused? Usually, they 'branch off' of the main project with their own versions full of changes they themselves have made. After they're done, it's time to 'merge' that branch back with the 'master,' the main directory of the project.

**Fork**: Another level of branching specific to Github.

**Pull request**: You've done modifications on the main repository and you think they should be merged to the main project, then you do a pull request of your specific commit.
