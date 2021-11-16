## GIT

### Configuration

```bash
# System Config
git config --system
# User level Config
git config --global
# project level
git config
```

### **Basic Configuration**

```bash
# user name
git config --global user.name "name"
# user email
git config --global user.email "email@mail.com"
# display config
git config --list
```

#### Additional Configuration

```bash
# text editor for editing
git config --global core.editor "nano"
# color out
git config --global color.ui true
# ignore file in every repo
git config --global core.excludefile filepath
```

### Commands

#### initialize

```bash
# initialize a git repo
git init
# add all files to stage
git add .
# other add options to add one file
git add file
```

#### Save changes

```bash
# save and commit the changes with message
git commit -m "message"
# add and commit [only for modified files]
git commit -a 
# show log messages
git log
# log option can by compinend
--until="2020-06-15" # until the date
--author="name" # made by name
--grep="regex" #search in message by regex
--oneline # get every commit in one line
-3 # only the last
--since="2020-06-15" # since this date to now
SHA1..SHA1 # from the first SHA to the second
SHA.. # from SHA to the end
SHA1..SHA2 file # the logs affected the file from the first SHA to the second
-p # get the diff along the log
--stat #  get stats about commits
--format=oneline # format the log with val (online, short, medium, full, fuller, email, raw)
--graph # graph the commit tree useful with branches
--all # from all branches
```

##### Message Best Practice

- short single line
- optionally blank line and then description
- be descriptive
- use labels at first [bug:, feature:, #152(issue no.)]

#### Track changes

```bash
# change between working directory , staging and repo
git status
# get the differance the new file in working and the old one in repo or stage
git diff file
# get the differance between all working directory and repo or stage
git diff
--staged # get the differance between stage and repo
SHA # get the differance between this commit and the working directory
SHA file # get the differance between this commit and the working directory
SHA1..SHA2 # get the differance between two commits
-b # ignore spaces changes
-w # ignore all spaces
--stat # get only stats of the change
--summary # get a summary  of the change
# add deleted file to stage
git rm file
# remove file from tracked files
git rm --cahched file
# rename file
git mv file1 file2
# move file
git mv file dir
```

#### Undo changes

```bash
# get the repo version of file
# -- indicate the current branch
git checkout -- file
# unstage file 
git reset HEAD file
# merge to the last commit or change the commit message
git commit --amend -m "message"
# get file from commit 
# -- indicate the current branch
git checkout HSA -- file
# change to the prev commit
# HSA of the commit to revert not the commit to revert to
git revert HSA 
# change the head
# after this command the log after is hidden from log it's better to take a copy of it
git reset --option  HSA
# reset options
--soft # don't change the working directory or stage
--mixed # don't change the working directory
--hard # completely change to the reo
```

#### **Ignore Files**

create a new file in the project .gitignore

##### add files to this file to ignore like:

- file.txt # will ignore this file
- *.jpg # will ignore all jpg
- videos/  # will ignore all file in this folder
- !videos/sample.mp4 # if the folder is ignore will exclude this file

##### what files to ignore

- compiled source code
- packages and compressed files
- logs and DB
- OS generated files
- check [gitignore](https://github.com/github/gitignore) repo for details

#### commit tree

```bash
# get the list of file at commit
git ls-tree tree-ish
# show the full info of the commit
git show tree-ish
```

##### tree-ish

is a reference for a commit

- SHA
- part of SHA >=  4
- HEAD
- branch reference
- parent of something (HEAD^ , HEAD~1)
- grandparent (HEAD^^ , HEAD~2) and so on ...

#### Branches

```bash
# get branches local
git branch
# branch options
-r # remote branches
-a # all branches
# create a new branch
git branch name
# switch to the new branch
git checkout name
# create and swithch
git checkout -b name
# rename branch
git branch -m name new_name
# delete a branch
git branch -d name
# merg branches (has to be called from the receiver branch)
git merge name
# merge option
--no-ff # don't make fast forward merge
--ff-only # only merge if it's a fast forward
--abort # abort in conflict
```

#### stash

```bash
# save files to stash
git stash save "message"
# view stash list
git stash list
# view stash changes
git stash show  -p stash@{0}
# git stash version and remove it from stash
git stash pop
# git stash version and don't remove it from stash
git stash apply
# delete stash items
git stash drop stash@{0}
#delete all
git stash clear
```

#### Remotes

```bash
# add a remote repo
git remote add name <repo URL>
# remove remote
git remote rm name
# push to remote repo
git push -u name branch
# clone a remote repo
git clone <repo URL>
# fech changes to local
git fetch 
# fetch and merge
git pull
```
