Git Learnings:
==============

Git is version control software:

Commands and concepts:

```bash git init```  

#Initializes git repo on the local system and in current working directory, it also create .git directory which is essential for git to track versions/commits and work correctly, it creates files and folders like hooks, info, objects, refs, config, description, HEAD. If we execute the git commands where .git directory is not present then git commands would not work.

```bash git clone <remote repository url>```

#Similar to git Initialize, this command clones the remote repo to local system including .git folder and commit history, and it add remote repository alias as origin, this is preferred if we are working in existing repository.

```bash git status``` 

#Status shows on which branch you are currently on and untracked files, also Tracked files if they are modified but not added to stagging area etc.

```bash git add <filename> or .``` 

#Adding all the files from local to stagging area, period(wild card) represents all the files.

```bash git commit -m <commit message>```

#To commit the files from Stagging area to Local repo, specify the releveant commit message.

```bash git push -u origin <remote repo url>```

#To push the changes to remote repo, here you may have a doubt where is remote repo url to push the changes, if you do initialized using git init you have to added remote repo as <git remote add origin "url" >, if you have performed <git clone> it automatically sets alias origin by default to remote url. if you set up-stream url as -u origin from next time you can simply run git push as your branch refer to main -> origin/main automatically. if you add a different remote repo you can give name of your choice

```bash git remote -v``` 

#To check all the remote repo's added to your session

```bash git remote add origin <url>```

#To add remote repo url with alias a origin.

```bash git restore <filename> or . ```

#To undo changes from the files that are in your local area

```bash git restore --staged <filename> or .```

#To unstage files from staging area, changes still remains in working area