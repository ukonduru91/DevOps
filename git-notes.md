Git Learnings:
==============

Git is version control software.

Commands and concepts:

```bash git init```  

#Initializes a Git repository in the current working directory.  
#It creates a hidden .git directory which is essential for Git to track versions/commits and function correctly.  
#This directory contains folders and files like: hooks, info, objects, refs, config, description, HEAD.  
#If you run Git commands in a directory where the .git folder is not present, the commands will not work.

```bash git clone <remote repository url>```

#Similar to git init, this command clones the remote repo to local system including .git folder and full commit history.  
#It automatically adds the remote repository with the alias origin.  
#This is the preferred method when working with an existing remote repository.

```bash git status``` 

#Shows on which branch you are currently on, untracked files,  
#also tracked files if they are modified but not added to staging area, etc.

```bash git add <filename> or .``` 

#Adds files from working directory to staging area.  
#The period (.) represents all files (wildcard).

```bash git commit -m <commit message>```

#Commits the files from staging area to local repository.  
#Always specify a relevant commit message.

```bash git push -u origin <remote repo url>```

#Pushes the changes to remote repository.  
#Here you may have a doubt where is remote repo url to push the changes,  
#if you initialized using git init you have to add remote repo as  
#<git remote add origin "url">,  
#if you performed <git clone> it automatically sets alias origin by default to remote url.  
#if you set up-stream using -u origin, from next time you can simply run git push  
#as your branch will refer to main -> origin/main automatically.  
#if you add a different remote repo you can give it any name of your choice.

```bash git remote -v``` 

#To check all the remote repositories added to your local repo.

```bash git remote add origin <url>```

#To add a remote repository url with alias origin.

```bash git restore <filename> or . ```

#To discard changes from files in your working directory  
#(reverts them to the last committed/staged state).  
#Warning: This permanently deletes unstaged changes!

```bash git restore --staged <filename> or .```

#To unstage files from staging area back to working directory  
#(changes are kept in working directory).