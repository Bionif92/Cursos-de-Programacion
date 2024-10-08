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
git switch third-branch // other way to switch branches

git switch -c four-branch // create and switch to a new branch
````

### Deleting-Working Directory Files

If you delete the file normally, you will have the existing one in your commit

````bash
git ls-files // see the files in the commit

git rm working-with-branches.txt // delete the file from the commit
````

### Undoing Unstaged Changes

If you make a change in a file and you want to undo it:

````bash
git checkout the-file.txt // undo the file to the commit

git checkout . // undo all the files to the commit

git restore // the same thing instead of checkout

git clean -dn // see which untracked files will be deleted

git clean -df // delete the untracked files
````

### Undoing Staged Changes

After you use git add to the staged part, if you dont wont to commit, you can do this:
````bash
git reset initial-commit.txt // not so used
git chechout initial-commit.txt // after this to step it will restore the file

git restore -- staged initial-commit.txt 
git chechout initial-commit.txt // same as the two step named before
````

### Deleting Stages with Git Reset

Git Reset helps you reset the head of our branch, basically undo commits

````bash
git reset --soft HEAD~1// Remove one commit, but the stage is on, and the file too because we select soft reset

git reset HEAD~1// Remove one commit, the stage but not the file

git reset --hard HEAD~1 // Remove everything
````

### Deleting Branches

````bash
git branch -D fourth-branch // delete branch
````

### Commiting Detached Head Changes

Commit to the master branch

````bash
git chechout commit-id// detached head

git add .
git commit -m "message"// make changes 

git switch master // need to generate a new branch with the id they gave you

git branch "detached-branch" id-given
````
If you want to put this branch information into master:
````bash
git switch master

git merge detached-branch
````
Can also create a new branch with the changes of the detached and then merge to master

### Understanding .gitignore

Some of the files you dont want to work with git:

Make a .gitignore file:
```js
the-file.txt //file you want to ignore

Other way
*.log // all log files are ignored
!test.log // this one has not to be ignored

Other way
web-app/* // the foulder with all the things inside are ignored
```
Need to add .gitignore to the track files

## Diving Deeper into Git

### Understanding the Stash

You make progress, you want to go back to the previous commit, but you dont want to make a new commit of the changes

Stash - internal memory, you can save uncommited unstaged changes

```js
git stash // go back to the previous commit

git stash apply // bring back your changes, the latest ones

git stash list // see all the stash apllied as a list

git stash apply 0 // go to the latest, if 1 go to the previous and so on

git stash push - m "message" // push a stach with a message

git stash pop 0 // add the stash to the commit, then you need to add and commit into a new commit

git stash drop 1 // delete the stash

git stash clear // clear all stash
```

### Bringing Lost Data Back

If you make a hard reset, how to bring back the lost data:
```js
git reflog // storage of 30 days, search de commit you lost and have the id

git reset --hard id // head change to the commit we deleted before

Also for branches

git reflog 
git checkout id // create detached head
git switch -c feature // new feature branch
```

### Merge Types

 - Fast Forward
 - Non Fast Forward (Recursive, Octopus, Ours, Subtree)

### Fast Forward Mege

Condition: no additional commit in master (after feature branch was created)
Merge moves HEAD forward but does not create a new commit

```js
Create the branch feature, and the crate the foulder feature with the changes

git switch master
git merge feature // head moved to master to the last commit on feature

git merge --squash feature // head is not updated, all the new features are added to the stage, then you have to commit this changes
```

### The Recursive Merge

Additional commits in both master and feature branch after feature branch was created
```js
git merge --no-ff feature // both branches are merged and create the commit by themselves

To bring back to the latest commit of mater, only have to reset the merge
git reset --hard HEAD~1
```

### Appling Git Rebase

Rebasing -- modify the branch adding the changes of master to it

The rebase does not move commits, it creates new commits. **It is a problem if you work with a proyect with more people**

```cmp
//first in feature branch
git rebase master // rebase feature with new ids

git switch master
git merge feature
```

When consider using:

 - New commits in master branch while working on feature branch
 - If features relies on additional changes on master
 - Feature is finish - implementation into master without merge commit

### Handling Merge Conflicts

If you want to merge master with feature, and in one file, the content is different in the same line

In the file, you will see:

 - Accept current change
 - Accept incoming change
 - Accept both changes
 - Compare changes (highlight the differences)

```cmp
git status // you can see the problem and the solutions, same with git log --merge
// you can fix problem and commit or:
git merge --abort
git diff // you can see also the problems you have
```

### Cherry Pick

Cherry Picking - Add a specific commit to a branch (HEAD), copies commit with new id+

In the example, something in master is wrong, we made a new branch, make new features and correct the mistake, and we only want to modify this change in master

```cmp
// from feature switch to master
git cherry-pick id-commit // change mistake in master with a new id
```

### Working with Tags

Tag - to put a tag into the commit to find it quickly

Git supports two types of tags: lightweight and annotated. A lightweight tag is very much like a branch that doesn't change — **it's just a pointer to a specific commit**. Annotated tags, however, are stored as full objects in the Git database.

```cmp
git tag // list of tags in the proyect

git tag 1.0 id-commit // lightweight tag

git show 1.0 // show you the commit

git checkout 1.0 // we refer to that commit

git tag -d 1.0 // delete the tag

git tag -a 2.0  -m "This is the latest version"//annotated
```

### Useful Resources & Links

More on merge conflicts =>  [https://git-scm.com/book/en/v2/Git-Tools-Advanced-Merging#_advanced_merging](https://git-scm.com/book/en/v2/Git-Tools-Advanced-Merging#_advanced_merging)

Additional merge strategies =>  [https://git-scm.com/docs/merge-strategies](https://git-scm.com/docs/merge-strategies)

## Understanding GitHub


### What is Github?

Github -  Remote repository

### Creating Remote Repository

Create a Repository on GitHub

### Connect Local with Remote Repository

We will use the second option: **push an existing repository from the command line**

````
// VSC terminal
git init
git add .
git commit 
git remote add origin (url) //url given in the repository
git branch -M main // rename master to main, if you want you can keep master
git push origin main // or master
````
Appear a Pop Up to sign to GitHub, need token

### Create Token

Github/Menu/Settings/Developers Settings/Personal Access Tokens/Generate New Token

Need to give access to the sepecif things we need:

 - Repo
 - workflow
 - write packages
 - delete packages
 - gits
 - users
 - delete repo
 - write discussions

### Pushing a second commit

````
// VSC terminal
git add .
git commit 
git push origin master
git branch -a // can see local and remote tracking branch
````

In Github, in history you can see the commits

### Remote Tracking Branch

Copy of remote branch in local, to push and pull first modify this

Example: create another branch

````
// VSC terminal
git branch -a // can see local and remote tracking branch
git branch -r // can see only remote
git push origin feature 
````

Can create branch in Github, and files, to bring them to VSC:

````
// VSC terminal
git ls -remote // can see al branches on remote

git fetch origin // bring things from remote
git pull origin// combination of fetch and merge, need to be al branches existing on local
git checkout remotes/origin/feature-remote // make a detached head with all changes of remote, and generate new branch with switch
````

### Creating local tracking branches

Create local tracking branch to feature-remote
````
// VSC terminal
git branch --track feature-remote origin/feature-remote // create local tracking branch

//if you made a change in local, the remote tracking branch is not changed
git push

git pull //need to be on the branch you want to overwrite

git branch -vv // can see the conection to remote tracking branches

git remote // can see the servers, in this case origin

git show remote origin // information
````
**Keep the same names for local and remote tracking branches**

### Cloning a Remote Repository

On GitHub, Code button, Clone option, copy url

````
// VSC terminal
Dont use git init
git clone copied-url .

cd github-basic // change to the file you cloned
//Need to create a local tracking branck to work localy
git branch --track origin/feature remote/origin/feature
````

If you want to add a branch to the cloned:

````
// VSC terminal
git checkout -b feature-local
git push origin feature-local // create a remote branch called feature-local
````

To have a local tracking branch, you made a copy of remote branch, then delete it, and then generet a local tracking branch from the branch you just uploaded

````
// VSC terminal
git --branch feature-local origin/feature-local
````

### Understanding the upstream

````
// VSC terminal
git push -u origin feature-upstream
````

**More easy, create the local tracking branch when you push the local branch into remote**

### Deleting Remote Branches & Public Commits

Need to fetch to refresh the data from remote

````
// VSC terminal
git branch -D feature // delete local branch
git branch --delete --remotes origin/feature // delete remote tracking branch
git push origin --delete feature // delete remote branch
````

**If you delete remote branch, the remote tracking branch will be deleted too**

**If you want to delete a commit, delete it normally and then push, this will bring problems if you work with others**

````
// VSC terminal
git push --force origin master
````

## Git Hub Collaboration & Contribution

### GitHub Usercases

4 Types:

 - Cloud Storage
 - Portfolio Page
 - Collaboration
 - Contribution

### GitHub Account Types

Three types:

 - Personal User Account
 - Organization Account (shared account to collaborate)
 - Enterprise Account (central managment of multiple accounts)

### Changing repository from public to private

To change Personal Account into Organzation:
Settings/Organizations

Into the Repository, Settings/Scroll down to Danger Zone
Change Visibility

### Pushing Commits to a Public Repository

Can you push information to a public repository?
No, need the token

### GitHub Security

To give the infomation to work on our proyects, need the collaboration access

### Adding Collaborator to a Private Account

Repository/Settings/Manager Acess

Invite Collaborators

Then you can create your personal token

### Collaboration in Private Repositories

Nothing change if you are a collaborator in a private repositories

### Level of Access

In a private repository, repository owners can only write access to collaborators

### Limiting Interaction in Repository

Profile/Settings/Moderation Settings/Interaction Limits

Can limit interaction for public repositories

You have the moderation setting for each public repositories too

### Organizations

Add other account into the organization, member role access

For Big Proyects

Profile/Settings/Organizations - Need a Team Plan

Only one Organization

In the Repository/Settings/Manage Access -- you can add members on base roll and change member privileges

**You can add outside collaborators - Repo/Setting/Manage Access - Invite teams or people**

If you can only read the repository you cant overwrite

Adding member to an organization - Organization/People

### Teams

Organization/Teams

Flexible Repository Access

Allows you to give certain access to each repository intead of entering every member to change the managment of the repository

### Fork & Pull Request

Contribution - give value but not know the other person

Generate Remote Copy Repository from the original user and use this to clone it - fork
The contributor ask original user if want to see the modified repo - pull request 

### Forking a Repository

Repo/Fork (right top corner)/select the destination of the copy

### Pull Request 

How to merge the copy?

The collaborator has to inform the user to see the overwritten copy
Repo/pull request/new pull request

When it deliver to the user:
Open / Close pull request or merge the pull request

### Openning & Closing Issues

Repo/Issues - New Issues 

### GitHub Proyects

Repo/Proyects - Template: Kanban

Is to follow your proyect with cards

You can add issues to the proyect, inside the issue when is created

### Readme File

Repo/ Add Readme File

### Useful Resources & Links

More about Permission Levels for User Account Repositories => [https://docs.github.com/en/github/setting-up-and-managing-your-github-user-account/managing-user-account-settings/permission-levels-for-a-user-account-repository](https://docs.github.com/en/github/setting-up-and-managing-your-github-user-account/managing-user-account-settings/permission-levels-for-a-user-account-repository)

VueJS GitHub Page => [https://github.com/vuejs/vue](https://github.com/vuejs/vue)

## Real Proyect

Can delete node modules and intall them again with npm install
You can put it in .gitignore

Control + C to exit the server

Need to give access to push the new branch - add him as collaborator - Repository/Settings/Manage Access/Invite Collaborator -  Now he can create a token

How to merge two branches - git pull/git merge feat/cart-logic (his own branch on merged on main)
Also want to merge Manuel branch:
````bash
git checkout feat/cart // create auto a local tracking branch

git checkout main
git merge feat/cart 
````
Need to fix the code because of the conflicts

**Fork is created by the collaborator profile**, then clone the file and work locally, then push it again to github, then create the pull request, clic on compare across forks, and select the proyect

When you merge the pull you are making a commit, on description put the detaill of merge










<!--stackedit_data:
eyJoaXN0b3J5IjpbLTU4OTQ3NjUzMywxMzE4MjA4ODE5LDE5ND
MyMDUyMjEsLTE1NjIzNDU2NjgsLTEwNjk0NDA2OSwtMTIyNjc5
NDM2OSwtMTY2MjQ3NjMwNCwyNjI1NzYwOTIsLTEwMDc3NjQ3MS
wtMTc0NjY1NDIzMCwzNDc1ODIyOCwyMDY3NDg1NDgxLC0xMzEz
MjExMTA3LDE1Nzg2NDI1NTUsMjExNTAzMjYyOSwtMTY5MzIyMz
Q2Niw5NTMwNDIyMTIsLTE2MjgwMTA1OTAsMzQ2MTAyNjg2LC0z
NTc2MDI5ODVdfQ==
-->