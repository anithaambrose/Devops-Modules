# Git Commands 

## Git conguration setup 

git config --list
git config --global user.name "xxx"
git config --globa user.email "xxx@xx.com"

## Add github to terminal connection
git remote add origin http://github.com/username/repo.git

## Verify Connection
git remote -v

## Initializing Git  - working directory 

git init

## Staging Area

git add .

## Local Repository 

git commit -m "commit-defn"

## Push Code to remote repository

git push
git push -u origin main/master 

## Status of files - untracked 

git status

## Logs of local repository 

git log 
git log --oneline 
git log --oneline --graph --all 



