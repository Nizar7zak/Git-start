# Git-start

### What is Git? and why it is so popular?
Git is the most popular version control system in the world, a version control system records the changes made to our code over time in a special database call Repository.

We can look at our project history and see who has made what changes when and why, and if we screw something up we can easily revert our project back to an earlier state.

Without VCS we'll have to constantly store copies of entire project in various folders, like this

> v1.0.0

> v1.0.1

> v1.0.2

> v1.0.3  and so on..

This is very slow and does not scale at all especially if multiple people have to work on the same project.
you would have to constantly toss around the latest code via email or some other mechanisms, and then manually merge the changes.

**with a VCS we can track our project history and work togther.**
### VCS fall into two categories:-

1. Centralized :-
   All team members connect to a central server to get the latest copy of the code, and to share thier changes with others. subversion and microsoft team foundation server are examples of centralized version control system.
   the problem with centralized architecture is the single point of failure, if the server goes offline we cannot collaborate or save snapshots of our project. so we have to wait until the server comes back online.

2. Distributed :-
   In distributed system we don't have these problems, every team member has a copy of the project with its history on thier machine, so we can save snapshots of our project locally on our machine, if the central server is offline we can synchronize our work directly with others. Git and Mercurial are examples of distributed VCS, out off all Git is the most popular VCS in the world.

### WHY Git?

1. Free.
2. Open Source.
3. Super Fast.
4. Scalable.
5. cheap Branching/Merging

So Git is almost everywhere, more than 90% of software projects in the world use Git, that's why almost every job description for software developer metnions Git.

### USING Git:-

1. The command line.
2. Code editors & IDEs
3. Graphical User Interfaces (GitKraken)

> we can use in the command line, so we open a terminal or command prompt window to execute Git commands, this is the fateset, now if you don't like the command line, well! you're in luck because most modern code editors & IDEs have built-in support for basic Git features.

### Command line or GUI?
YOU SHOULD USE THE RIGHT TOOL FOR THE JOB.

#### Why Command Line?

1. GUI tools have limitations.
2. GUI tools are not always available.

### INSTALLING Git :-
* Check any version I have 
> git --version

* Installing Git
> on windows after install git you must install git BASH to emulate linux cmd

### Configuring Git:-

1. name
2. email
3. default editor
4. line ending

We can sepcify these configuration at three diffrent levels:-

1. **SYSTEM:-** setting here apply yo all users of the current computer (All users)
2. **GLOBAL:-** all repositories of the Current user
3. **LOCAL:-** The Current repository

In the terminal window we type:-
```
git config --global user.name "type your name here"
git config --global user.email yourEmail
git config --global core.editor "code --wait"
```
* With wait flag we tell the terminal window to wait until we close the new vs code instance.

> git config --global -e
* This will open our default editor to edit all the global settings.

Next we're going to configure how git should handle end of lines, this is a very important setting that a lot of peoples miss.

> On windows end of lines are marked with two special characters:-
1. Carrigae Return (\r)
2. Line Feed (\n)

> On macOS/Linux system end of lines are indicated with line feed (\n)

That means if we don't handle end of lines properly we're going to run into some weird issues down the road, to prevent this, we have to configure a property called (core.autocrlf) which is short for carriage return line feed.

> git config --global core.autocrlf true/input
> 
if you are on windows you shuold set it to true, if you are on Linux you shuold set it to input.

### Visual Diff tool 
> git config --global diff.tool vscode
>
> git config --global difftool.vscode.cmd "code --wait --diff $LOCAL $REMOTE"

* In terminal we can use (git difftool) command to see diff.

### Get Help!
let's say you want to learn more about the config command, you can simply google (git config) and see full documentation about it, and you can see the same content by type( git config --help) on terminal.
press space to go to the next page and q to exit page.

to get a short summary of this command just type in terminal
> git config -h

### Git WORKFLOW
#### What we do on a daily basis when using git?
Imagine we have a project directory and git repo which is actually a hidden sub dicectory in our project directory, every day as part of working on various tasks, we modify one or more files, when our project reaches a state we want to record, we commit those changes into our repo.

Creating a commit is like taking a snapshot of our project, in Git we have a special area or special intermidate step, that does not exist in most other version control systems, it's called the Staging Area, it's essentially what we're proposing for the next commit or the next snapshot, so when we're done making changes, we add the modified files to the staging area, review our changes and if everything is good then we'll make a commit. the proposed snapshot will get permanently stored in our repo.
 
### Staging area:- 
> Allows us to review our work before recording a snapshot, if some of the changes should not be recorded as part of the next snapshot, we can unstage them and commit them as part of another snapshot, that's the basic git workflow now.

### COMMIT :-
Each commit contains a unique identifier that gets generated by Git, it's like a revision number. each commit also contains information about what was changes, by who, when, as well as complete snapshot of our project at the time it was created, so we can quickly restore the project to an earlier snapshot without having to compute the changes.

### SAVE ALL CONTENT --> WASTE A LOT OF SPACE?!
No, because Git is very efficient in data storage, it compresses file contents and does not store duplicate content, do you want to know how? at this time we should just know each commits conatins a complete snapshot of our project.

* git ls-files => show files in staging area 
* git rm --cached -r fileName => delete files recursive 

### Just to Know Git Object contains:-
1. Commits
2. Blobs (files)
3. Trees (Directories)
4. Tags


## CHEAT SHEAT

### Creating Snapshots

#### Initializing a repository
> git init

#### Remove .git
> rm -rf .git

#### Staging files-_
> git add file1.js # Stages a single file
> 
> git add file1.js file2.js # Stages multiple files
> 
> git add _.js # Stages with a pattern
> 
> git add . # Stages the current directory and all its content


#### Viewing the status
> git status # Full status
> 
> git status -s # Short status
> 

#### Committing the staged files
> git commit -m “Message” # Commits with a one-line message
> 
> git commit # Opens the default editor to type a long message


#### Skipping the staging area
> git commit -am “Message”
> 

#### Removing files
> git rm file1.js # Removes from working directory and staging area
> 
> git rm --cached file1.js # Removes from staging area only
> 

#### Renaming or moving files
> git mv file1.js file1.txt
> 

#### Viewing the staged/unstaged changes
> git diff # Shows unstaged changes
> 
> git diff --staged # Shows staged changes
> 
> git diff --cached # Same as the above
> 

#### Viewing the history
> git log # Full history
> 
> git log --oneline # Summary
> 
> git log --reverse # Lists the commits from the oldest to the newest

#### Viewing a commit

> git show 921a2ff # Shows the given commit
> 
> git show HEAD # Shows the last commit
> 
> git show HEAD~2 # Two steps before the last commit
> 
> git show HEAD:file.js # Shows the version of file.js stored in the last commit
> 
> git ls-tree HEAD~1 # Shows all changes files in this commit
> 

#### Unstaging files (undoing git add)
> git restore --staged file.js # Copies the last version of file.js from repo to index
> 

#### Discarding local changes
> git restore file.js # Copies file.js from index to working directory
> 
> git restore file1.js file2.js # Restores multiple files in working directory
> 
> git restore . # Discards all local changes (except untracked files)
> 
> git clean -fd # Removes all untracked files
> 

#### Restoring an earlier version of a file
> git restore --source=HEAD~2 file.js
> 

### Browsing History

#### Viewing the history
> git log --stat # Shows the list of modified files
> 
> git log --patch # Shows the actual changes (patches)
> 

#### Filtering the history
> git log -3 # Shows the last 3 entries
> 
> git log --author=“Nizar”
> 
> git log --before=“2020-08-17”
> 
> git log --after=“one week ago”
> 
> git log --grep=“GUI” # Commits with “GUI” in their message
> 
> git log -S“GUI” # Commits with “GUI” in their patches
> 
> git log hash1..hash2 # Range of commits
> 
> git log file.txt # Commits that touched file.txt
> 

#### Formatting the log output 
> git log --pretty=format:”%an committed %H”
> 

#### Creating an alias
> git config --global alias.lg “log --oneline"
> 

#### Viewing a commit
> git show HEAD~2
> 
> git show HEAD~2:file1.txt # Shows the version of file stored in this commit


#### Comparing commits
> git diff HEAD~2 HEAD # Shows the changes between two commits
> 
> git diff HEAD~2 HEAD file.txt # Changes to file.txt only
> 

#### Checking out a commit
> git checkout dad47ed # Checks out the given commit
> 
> git checkout master # Checks out the master branch
> 

#### Finding a bad commit
> git bisect start
> 
> git bisect bad # Marks the current commit as a bad commit
> 
> git bisect good ca49180 # Marks the given commit as a good commit
> 
> git bisect reset # Terminates the bisect session
> 

#### Finding contributors
> git shortlog
> 

#### Viewing the history of a file
> git log file.txt # Shows the commits that touched file.txt
> 
> git log --stat file.txt # Shows statistics (the number of changes) for file.txt
> 
> git log --patch file.txt # Shows the patches (changes) applied to file.txt
> 

#### Finding the author of lines 
> git blame file.txt # Shows the author of each line in file.txt
> 

#### Tagging
> git tag v1.0 # Tags the last commit as v1.0
> 
> git tag v1.0 5e7a828 # Tags an earlier commit
> 
> git tag # Lists all the tags
> 
> git tag -d v1.0 # Deletes the given tag
> 

### Branching & Merging 

#### Managing branches 
> git branch bugfix # Creates a new branch called bugfix
> 
> git checkout bugfix # Switches to the bugfix branch
> 
> git switch bugfix # Same as the above
> 
> git switch -C bugfix # Creates and switches
> 
> git branch -d bugfix # Deletes the bugfix branch


#### Comparing branches
> git log master..bugfix # Lists the commits in the bugfix branch not in master
> 
> git diff master..bugfix # Shows the summary of changes
> 

#### Stashing 
> git stash push -m “New tax rules” # Creates a new stash
> 
> git stash list # Lists all the stashes
> 
> git stash show stash@{1} # Shows the given stash
> 
> git stash show 1 # shortcut for stash@{1}
> 
> git stash apply 1 # Applies the given stash to the working dir
> 
> git stash drop 1 # Deletes the given stash
> 
> git stash clear # Deletes all the stashes
> 

#### Merging 
> git merge bugfix # Merges the bugfix branch into the current branch
> 
> git merge --no-ff bugfix # Creates a merge commit even if FF is possible
> 
> git merge --squash bugfix # Performs a squash merge
> 
> git merge --abort # Aborts the merge
> 

#### Viewing the merged branches 
> git branch --merged # Shows the merged branches
> 
> git branch --no-merged # Shows the unmerged branches

#### Rebasing 
> git rebase master # Changes the base of the current branch

#### Cherry picking
> git cherry-pick dad47ed # Applies the given commit on the current branch

### Collaboration

#### Cloning a repository
> git clone url

#### Syncing with remotes
> git fetch origin master # Fetches master from origin
> 
> git fetch origin # Fetches all objects from origin
> 
> git fetch # Shortcut for “git fetch origin”
> 
> git pull # Fetch + merge
> 
> git push origin master # Pushes master to origin
> 
> git push # Shortcut for “git push origin master”


#### Sharing tags
> git push origin v1.0 # Pushes tag v1.0 to origin
> 
> git push origin —delete v1.0

#### Sharing branches
> git branch -r # Shows remote tracking branches
> 
> git branch -vv # Shows local & remote tracking branches
> 
> git push -u origin bugfix # Pushes bugfix to origin
> 
> git push -d origin bugfix # Removes bugfix from origin


#### Managing remotes 
> git remote # Shows remote repos
> 
> git remote add upstream url # Adds a new remote called upstream
> 
> git remote rm upstream # Remotes upstream


### Rewriting History

#### Undoing commits
> git reset --soft HEAD^ # Removes the last commit, keeps changed staged
> 
> git reset --mixed HEAD^ # Unstages the changes as well
> 
> git reset --hard HEAD^ # Discards local changes
> 

#### Reverting commits
> git revert 72856ea # Reverts the given commit
> 
> git revert HEAD~3.. # Reverts the last three commits
> 
> git revert --no-commit HEAD~3..

#### Recovering lost commits
> git reflog # Shows the history of HEAD
> 
> git reflog show bugfix # Shows the history of bugfix pointer

#### Amending the last commit 
> git commit --amend
> 
> Interactive rebasing
> 
> git rebase -i HEAD~5
