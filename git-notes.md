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


```bash git fetch```

#Updates local copy of remote branches e.g., origin/main or origin/feature_branch , but does not affect local branches or working directory, you can check those as ```bash git log origin/main --oneline```

```bash git merge origin/main```

#Changes that are updated to reference remote branch gets merged into the current branch you are on.

```bash git pull origin main```

#Command executes both fetch and merge in the backend and merges the changes from remote repo to local repo

```bash git diff main origin/main```

#Shows the result by comparing the latest commits from each branch

Merge Conflicts

Merge conflicts occur when Git cannot automatically reconcile changes between two branches.
This usually happens when:

- The same line(s) in a file were changed differently in both branches
- A file was deleted in one branch but modified (or still exists) in the other

Resolving Merge Conflicts (e.g. when merging branch-b into main)

1. Update your local main branch
``` bash git checkout main ```
``` bash git pull origin main ```

2. Switch to your feature branch
``` bash git checkout branch-b ```

3. Merge main into your branch (this will show conflicts)
``` bash git merge main ```

Git will pause and list conflicting files.
Open each conflicting file in your editor — Git marks conflicts like this:

Manually edit to keep the desired version(s), remove the markers, then:

``` bash git add . ```
``` bash git commit -m "Resolve merge conflicts with main" ```
``` bash git push origin branch-b ```

Now the conflicts are resolved and you can complete the PR merge on GitHub/GitLab/etc.

Git Rebase

Important Safety Rule
Never rebase commits that have already been pushed and shared with others (especially not main or any shared branch).
Rebasing rewrites history and can cause serious problems for teammates.

Use rebase only on your private/personal feature branches that no one else has based work on.

Why prefer rebase over merge?

Regular git merge usually creates an extra merge commit — even when there are no actual code conflicts.
This can make the history look cluttered with many merge commits.

git rebase takes all your commits and reapplies them cleanly on top of the target branch → results in a nice, linear history without extra merge commits.

How to rebase your branch onto main

#Make sure main is up to date
``` bash git fetch origin ```
``` bash git checkout main ```
``` bash git pull origin main ```

#Switch to your branch and rebase
``` bash git checkout branch-b ```
``` bash git rebase main ```

If conflicts appear:
Git pauses after each conflicting commit. Resolve them the same way as during a merge, then continue:

``` bash git add <resolved-file> ```
``` bash git rebase --continue ```

After successful rebase (all conflicts resolved):

#History was rewritten → we need to force-push
#Use --force-with-lease (safer than plain --force)
``` bash git push origin branch-b --force-with-lease ```



