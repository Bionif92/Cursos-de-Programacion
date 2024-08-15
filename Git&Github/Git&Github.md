# Git & Github Course

## Getting Started

Git: version managment tool

Github: brings git capabilities to the cloud

### Git 

Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

You only have one file, but you can bring back previous states of the same work

 - Version Control System+
 - Manage Code History
 - Track Changes
 - Local tool

### Github

 - Largest Development Platform
 - Cloud Hosting & Collaboration Provider
 - Git Repository Hosting

## Windows Command Prompt

Command Prompt (cmd)

````cmd
cd .. // move a folder backwards

dir // see content

D: // change to disc D

cd Users // move to Users folder from relative path

cd Desktop\git-basics // move to that folder

cd C:\Users\Franco // move from absolute path

cd / // go to the root directory

cls // clear command prompt
````
You use absolute path for development

### Creating-Deleting Files & Foulders

````cmd
mkdir command-prompt // you create a foulder where you are

echo our first file > test.txt // content name-of-file file-type

type text.txt // show you our first file

del text.txt // delete the file

rmdir command-prompt // delete the foulder
````

### Copying and moving files

````cmd
copy test2.txt other // copy the file into the other foulder

move test2.txt other // move the file into the other foulder

move other main // move main foulder into main foulder
````

### Useful links

Windows Command Prompt overview =>  [https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/windows-commands](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/windows-commands)

The "new" Windows Powershell (not used in the course) =>  [https://docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-7](https://docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-7)

## Version Managment with Git

Commit -> Snapshot

Master Branch -> All commits

Git = Tracking changes, not storing files again and again

You can make a duplicate of the running work, make the changes you want with commits, and when it is finish, modify the exisiting one

### Installing Git

 1. Download Git from the page and install
 2. See the version installed with this:
````bash
git --version
````

### Initializing first Repository & Creating first Commit

Use command prompt on terminar VSC

````bash
git status // see status of repositories

git init // to initialize git in the foulder, create git foulder for repositories

git add initial-commit.txt // can add more files next to the one listed

git add . // track all the files
````

With this you put the files in the staging area

````bash
git commit -m "added first .txt file" // commit the change, with that message

git config --global user.email "email"

git config --global user.name "name"// need this to configure first to let you run commit
````

### Diving in Commits with log

````bash
git log // see the commits, most important the id 

git checkout id // you will be back to that step

git checkout master // you get back all things
````
This is explained in the next lecture

### Understanding and creating Branches

````bash
git branch // see all the branches, master is the default

git branch name-new-branch // create new branch

git checkout name-new-branch // switch branches

git chechout -b name-new-branch // shortcut for the previous two steps
````
If we create a branch based on another branch then all commits will be taken into this new branch

### Mergin Branches

Need to be in the branch you want the changes

````bash
git merge third-branch // add the new things from third-branch to master
````

### Understanding Head

For default, it is the latest commit on a branch

### Detached Head

Working with a commit you choose, outside any branch

````bash
git checkout id // you are in the detached head

git branch // you see the branches and the detached head
````

### Branches & Git Switch

````bash

````
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc2MjA1NjYyMSwxOTA5MjY5MDUzLC0xNT
I3NTc4MjYyLDQ1ODMzNjE0LDY2MDQzNTU5OSwtMjEzNTQ5MDkz
LDEzNTkxNjAxNjAsLTE3NTU2Mjg0NjAsLTE4NjIwMTM2OTIsNz
U0MDgzNjcyLDU2MjQ5MDU4NywtNDI4MjM3NTQ5LDU4OTcwNTg3
NCw0MDg2ODIxMTgsLTE4OTU4MTE3MDYsLTc3NTQ5NzA4MCwxMD
cwMTg5NjM3LC0xOTA0NDI0NDU1LDk4NzgxMTUyNSw0MTgzMzY0
OTVdfQ==
-->