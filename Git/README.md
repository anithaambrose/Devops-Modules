# Source Code Management?

SCM manages code, tracks the project changes, keeps account of who is working   the period and the commits the individual or the team makes on a code, makes it easy to roll back to the early versions of code.

# What is GIT?
  •	Git is a DevOps tool used for source code management.
  
  •	It is a free and open-source distributed version control system.
  
  •	used to tracking changes in the source code, enabling multiple developers to work together on non-linear development.
  
  •	has code history, backup and is accessible from anywhere by anyone if shared access is given.
  
## VCS: Version Control system is of 2 types:

  1.	Centralized Version Control System (CVCS) - contains 1 repository - i.e globally remote, all users pushes code to it and commits 
    1.	dis_adv: if the central server goes down no user can access or commit their changes to code.
    2.	need to be connected always with the  Central repo over the internet to access/work/commit our work.
    	
  2.	Distributed Version Control system (DVCS) - 
    1.	each developer has a complete copy of the project's history on their local machine
    2.	enables offline work, faster operations, and easier collaboration

## Repository: fundamental version control object.
Its like a Folder where codes and files are stored.

## Why version control?

  Collaborating → versioning→ Rolling back →Understanding.
  
  GitHub is a web-based platform that uses Git for hosting and collaborating on code.
  
  Git tracks changes to files, enabling collaboration and allowing users to revert to previous versions. 
  
  GitHub provides a place to store Git repositories online, along with tools for project management and code review. 
  
## Git Terminologies:

  ### Repository:
    fundamental version control object. Its like a Folder where codes and files are stored.
 
  ### Server:
    It stores all repository(local repo is also a server but it is private server). It contains metadata also.
  
  ### Commit:
    ➢ It means sending code file from staging area to local repository.
    ➢ It stores changes in local repository you will get an commit-ID.
    ➢ It’s a 40 alpha-numeric characters.
    ➢ It uses SHA-1 checksum concept.
    ➢ Even if you change one dot(.) commit-ID will get changed.
    
  ### SHA-1 Checksum Concept:-
  
    ➢ It is used to know the status of code is changed or not in between sending & receiving.

## Git WorkFlow:

  creating a working directory → adding to staging area →commit changes to local repository→push to .github/remote repo.
  
    1.	working directory is where you can see files physically and modify the changes 
    2.	staging  is where you can see the changes - checkpoints 
    3.	local repo(.git) is where committing the changes to local 
    4.	the push code to remote repository (github)
    
Git workflow with Github:
Stages - 	Description
  1	      Launch linux machine 
  2	      Install git
  3	      Make a directory
  4	      Run git init(above directory converts into .git repository(local repo)
  5	      .git will divide into 3 region:
          ->workspace/working directory
          ->staging area
          ->local repo
  6 	    Coding is done into workspace
  7 	    Add coding file in staging area
  8 	    Now commit code file from staging area to local repo branch
  9 	    Push coding file to central repo(github)
  10 	    Pulling code to other machine from github, you can see data in local repo/staging area/working directory.

Concept & Commands:

# REMOTE REPOSITORY

A repository, often referred to as a "repo," is a central location where Git stores all the files, history, and metadata of a project.

## git Remote Repository

A remote repository is a copy of the repository stored on a server or hosting platform (github).

It allows for collaboration and synchronization among multiple developers.

To check the configuration of the remote server, run the git remote command.

```
git remote

Verbose output
git remote -v

Add Remote Server
git remote add github-url
Ex: git remote add https://github.com/demo/demo.git

Remove Connection
git remote rm

Rename Remote Server
git remote rename

Change Remote
git remote set-url

Fetch Remote Server
git remote fetch
```

# CONFIGURATION

## git config

Get and set configuration variables that control all facts of how Git looks and operates.

```
git config
Set Name: 
 git config --global user.name "User name"

Set Email:
git config --global user.email "example@gmail.com"

Set Editor:
git config --global core.editor Vim

Show Configuration:
git config --list
```

# PROJECT CREATION

## git init 

Command-line utility that Initializes the git repository by creating a new blank (.git) a local repository which tracks all the changes made to the files that are.

`
git init
`
## git Clone 
Command-line utility which is used to make a local copy of a remote repository. It accesses the repository through a remote URL.

```
git clone
Ex: git clone RepoURL

git clone https://github.com/demo/demo.git
```

# BASIC WORKFLOW

## git status 

Command-line utility that displays the untracked files from the repository. These files can be added to our repository.

`
git status
`
## git add 

Command-line utility that is used to add file contents to the Index (Staging Area).
```
git add filename 

git add . or git add *

```
## git Commit

Command-line utility that is used to record/commit the changes in the repository.
```
git commit

git commit -m “msg”
```
## git rm
Command-line utility that is used to remove a file from a Git repository.
`
git rm test.txt 
git rm -r test.txt
`

# BRANCHING

  Branch = Folder
    •	master branch = main branch 
    •	new branch will make a copy of the main branch , for us to work, so we dont alter the original version of the files pushed to the github.
 
  Branch Types:
    1.	Main/Master - Production ready code
    2.	Develop - active development 
    3.	Feature - New Feature related codes
    4.	Release - Pre-release Feature , testing happens here before moving to production
    5.	Hotfix - emergency fixes
  
  Note:
    •	Master always have the deployable code.
    •	Feature branch is created to make the code changes so we don't alter the original/application code.

## git branch

Command-line utility that allows you to create, list, rename and delete branches.

```
create branch 
git branch branchName
Ex: git branch Demo

List Branch
git branch or git branch --list

Delete Branch
git branch -d branchName
Ex: git branch -d Demo

Rename Branch
git branch -m branchName
Ex: git branch -m Demo1

Delete Remote Branch
git push origin --delete branchName 
Ex: git push origin --delete Demo
```

## git checkout

Command-line utility that lets  switching to a different branches

It allows developers to work on a specific branch and access its code and history.
```
git checkout branch Name
Ex: git checkout Demo

Create and switch Branch
git checkout -b  branchName
Ex: git checkout -b Demo

Discord changes
git checkout --test.txt
```
### git merge

Command-line utility that helps merge/combines the changes from one branch into another. 

It integrates the commits of a source branch into a target branch, incorporating all the changes seamlessly.
```
git merge branch Name

git merge source branch  target branch
Ex: git merge Demo1 Demo

```

## git rebase

Rebasing is a process to re apply commits on top of another base commit.
```
git rebase
Ex: git rebase Demo

Continue to apply changes
git rebase --continue

Skip changes and apply 
git rebase --skip

```

### Merge VS Rebase
  1.	Merge doesn't have a linear commit history 
  2.	Rebase rewrites the commit history in a linear fashion

  Branch merge:
    •	You can’t merge branches of different repositories.
    •	We use pulling mechanism to merge branches.
    •	To merge branches (git merge <branchname>). Then run git log –oneline.

## git Cherry-pick

Cherry-picking in git is a Command-line utility that lets us apply a specific commit from one branch into another branch.
simply used to add a commit from one branch to another branch.

`
git cherry-pick commit-ID
Ex: git cherry-pick 1dsfe345
`

## git Stash

Command-line utility thats helps temprarily saves files without committing so that we can Switch branches and later come back to those files.
Preventing them from aborting. this applies only for modified file untracked files and not new files that are untracked.

```
Save Stash
git stash save “Msg”

List Stash
git  stash list

Apply Stash
git stash apply stash ID
Ex: git stash apply 1dsfe345

Show Changes
git stash show or git stash show -p
```

# DATA STREAM

## git Push

The push term refers to upload local repository content to a remote repository. 

Pushing is an act of transfer commits from your local repository to a remote repository. 

Pushing is capable of overwriting changes; caution should be taken when pushing.

```
Push Data
git push origin master

Delete Remote Branch
git push origin --delete

to remove branch locally & remotely.
EX: git push origin --delete hotfix/myapp
```

## git pull 

When working collaboratively, a developer can request changes from their branch to be merged into another branch through a pull request. 

This process allows for review and discussion before the merge takes place.

```
git pull
or
git pull origin master

```
# REVERSING

## git revert

Command-line utility thats is used to undo an existing commit where the state of the file moves backward , but the version controls commit history moves forward.

 git revert is simply applied to revert a commit operation.

```
git revert <commit-ID>
```
## git reset

The git reset command is used to undo the changes in the local repository. 

The git reset command is used to reset the commits made based on their count specified.

```
git reset

git reset - - hard or --soft or - - mixed 

```

Reset Types:
1.	Soft reset - undo commits keep the changes in stage area
2.	mixed reset -  undo commits , keeps the changes in working directly
3.	hard reset - completely deletes the commit and all the changes permanently. - Dangerous

SOFT Reset:
Remove last 2 commits:  >>undoes commit , but pushes those files to staged area as modified files
`
git reset --soft HEAD~2
`

MIXED Reset: default
Removing the last 1 commit : >> undoes 1 commit & but pushes those files to working directory as  untracked files
`
git reset --mixed HEAD~1
`
HARD Reset:
Removes last 1 commit permanently i.e., noting here goes to working or staging area
`
git reset --hard HEAD~1
`

## LOGGING 

## git log
Git log is a utility tool to review and read a history of everything that happens to a repository.

```
git log
git log --oneline
git log --oneline --graph --all -> for non linear structure.

Diff
It compares the different versions of data sources.

`
git diff 
`
git diff branch1 branch2 or git diff commit1 commit2
```

## git reflog:
  Shows the actions performed in git local repo that includes 
  •	branch switch 
  •	commit history
  Read the history from bottom to top order.
`
git reflog
`
## .gitignore  

Files mentioned in .gitignore is ignored by git & doesn't track or push them to github.

## Github SSH

Secure Shell (SSH) Protocol facilitates the communication among systems in an unsecured network by providing a secure channel over it. 

It safeguards the connection to remote servers enabling user authentication.

Using SSH, you can connect to your GitHub account eliminating the need of giving username and password each time you push changes to the remote repository. 

The integration process involves setting up SSH Keys within both the local and remote systems.

```
ssh-keygen -t ed25519 -C "anithaambrose11@gmail.com"

Path to add key  - github webpage → settings →ssh & GpG Keys → new ssh→ give name, paste the public key and click add sshkey
 
```



