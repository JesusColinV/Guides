# Tutorial to use git
## _Colin Vilchis J.A_



Git is the most efficient tool to work as a programmer, it allows you to share your code to work collaboratively and maintain version control

## Requirments

- install git
- install git Bash
 
## Commands to navigate

It is important to move between the location of your files, this can be done from the command line

Command to recognize the location of your pointer
```sh
pwd
dir # native windows command
```
The change directory command allows you to change the location of the pointer
```sh
cd  /  # we move to the root, usually called disk C
cd     # we move to the root, usually called disk C
cd .. # It allows us to move to the parent folder of the pointer
cd .  # refers to the current folder
cd / {initial_letter}+tab # autocomplete de comand
```
The list the files that are in the folder where the pointer is
```sh
ls
ls -al # command to show hidden files listed
ls -a # command to show hidden files
```
Clean the console
```sh
ctrl + l
clear
```
Change disc 
```sh
cd /mnt/{disk-name} #linux
cd/{disk-name} #windows remember that windows does not distinguish uppercase letters from lowercase letters
```
Create a folder
```sh
mkdir {project-name}
```

Create a file
```sh
touch {file-name}.txt
```

## Commands to work
Recognize the content of a file

```sh
cat {file-name}.txt
```
<img src="assets/cat_command.PNG" alt="cat_c" width="1000"> </img>

Remember command history
```sh
history
!1 # repeat the first command, you can select the index you need
```

Delete a file
```sh
rm {file-name}.txt # be careful not to delete important files
```

Help to know a command
```sh
{any} --help
rm --help
```

## Good workflow practices
__Open visual studio code__ 
```sh
code
code {file-name}.txt
```

Creation of the work area within Ram memory 
```sh
git init
```
* At this moment the repository is created, identified in the folder .git locally

**Staging** is the area where files are functional, but you need to check and debug
Creation of the work area within Ram memory (clears at power off)

Add your file changes to staging
```sh
git add {file-name}.txt
git add . # to update all the files
```

Before add, the files are untraked, they can be identified by the git status command
```sh
git status
```

Remove memory from staging
```sh
git rm 
git rm --cached {file-name}.txt # delete from staging
```

It is a good practice to have branches of our work, by default the main branch is known as **master**

Add staging changes to the final save branch
```sh
git commit -m "{message to remember}"
git commit -am #files that have previously ever had add can be run in a single command the git add and git commit on new changes
git commit -a # go to vim, use **esc + i** to send the message
```
__*important*__
* You need to identify your user, by default use the windows environment variables, it is good practice to make sure you use the desired user, go to git configuration.
* When you don't add a command it change to vim editor, press **esc + shift + z + z** or **esc + w + q**

Read changes from a branch
```sh
git checkout
git checkout {id_commit_#} {file-name}.txt # changes in the same branch
git checkout {branch name} {file-name}.txt # pick up a different branch
```
* The second case returns to a past state, the file does not exist within the commit, only in staging, be careful because if you commit, you delete it
* The proper way to go back to the previous version is case 2 because it can be taken over by case 3 when you have a single branch. **You will follow a line shape that allows you to resume if you regret**

Creation of branches, to work by areas in the same file
```sh
git branch # read existing branches
git branch {branch-name}
```

Union between branches
```sh
git merge
```
Name of branches
* development #experimental
* hotfix
* main
* master

Recognize the history of a repository
```sh
git log # It recognizes the entire git command line, that is, the command used
git log {file-name}.txt
git log --stat # Changes after commit, in specific files
```

Recognize lines that change in a file
```sh
git show {file-name}.txt # important for error traceability
git diff {id_commit_1} {id_commit_2} # number 1 is the original, also allows you to identify staging differences and without tracking
```
* Problems can be solved with git add, you can use .gitignore to avoid files

Go back to a previous version of the repository
```sh
git reset {id_commit_#} --hard # clears staging
git reset {id_commit_#} --soft # remember staging
```
* The soft version allows adding what is stored in git add
* If you want to go back in time you can use hard, use git log to recognize that everything is deleted


## Git configuration

Identify all git settings
```sh
git config
```

Recognize your default configuration
```sh
git config --list
git config --list --show-origin # identifies where the settings are stored
```
* it is important to have a name and email

Update settings
```sh
git config --global user.name "{my-name}"
git config --global user.email "{my-email@gmail.com}"
```


##### How to join two branches that are not compatible?
* You should not checkout the master because you can lose your files, rather you should add the changes to your HEAD of your new branch.
* Once saved you can do checkout master to go to the HEAD of the last branch "master"
* In order to add the two changes, you must have updated the contents of each HEAD (add + commit)
* A merge for good practices always occurs from master, but if you do not have to recognize that it is done from the root where you want to continue (cheackout master + merge newbranch = master full) 
    * A conflict can occur if they share a line
    * A merge is a commit and needs a message
    * git log is updated with the content of the head of the last branch
    
Conflict resolution
* It is caused when both branches modify the same lines
* In your file, it's duplicated the line, remove the syntax and select the one you want or use the visual studio code function to graphically accept your change between the branches. Discuss with the author of the line about the best branch to save.


### Reminder
* HEAD is the head of the workflow, you must continue the flow from the head, to solve the head error you only have to checkout on HEAD
* The exception of this error is the creation of a new branch, which will have a new header
* The command flow for the changes is:
    * git status # acknowledge changes
    * git add and commit or git commit -am for old one
* Good practice for branch creation
    * Recognize your position with __git status__
    * __git show__ to recognize where the head is and know your last changes
    * __git branch newbranch__  + __git show__ recognizes that the head points to the master and the new branch
    * The last commit is stuck to two different branches , but continue working in master 
    * Use git checkout to define the branch you will work on __git checkout newbranch__
* The changes you make when you are on a branch only happen on it


# Tutorial to use github
## _Colin Vilchis J.A_

It is an online git server, it allows sharing and it is the visual interface of the repositories. Collaborative online tool.
* organization: It is the company you collaborate with.
* Project: it is a group of repositories that you can have.
* Gist: Code snippet that you can share.
* Licenses: there are open, restricted or semi-open code.

## Remote repository
The flow must be:
Working directory -> Staging -> Local repository -> Remote repository

Create a remote source of our files
```sh
git remote add origin {HTTP-address}
git remote # shows that the pointer is in origin
git remote -v # shows that the pointer is in origin verbally
```

Send from local repository to remote repository
```sh
git push {address} # It must be the HEAD of the master
```
Bring from remote repository to local repository
```sh
git clone {address}
```
Update your local repository, from a remote repository update
```sh
git fetch {address}
git pull # run the fetch and merge command in one
```
* Brings it to the local repository but does not copy it to the files, to update the files, you must load the latest version from the local repository to the current version using git merge

Steps to submit a file to your repository.
* Get the request address to send your file
    * Go to the download or clone function to see this address, it is recommended to use HTTPS.
    * Create your remote repository with **git remote add origin {HTTP-address}**
    * send your file to the remote rem using the command ** git push origin master ** 
* A typical error is that the remote repository contains code that we do not have locally.
    * The good practice is to first bring the remote contents to the local repository to later integrate and send it.
    * You can do this with the ** git pull origin master ** command to indicate that you bring the repository to our master branch.
        * A common warning is that there are no common commits, because we confirm that it does not exist in the repository. Make sure to talk about the same repository to continue.
    * The indicated command to skip the previous error is ** git pull origin master --allow-unrelated-histories **
    * Finally send your file to the remote rem using the command ** git push origin master ** 
        * The record is saved with the github user that matches the git config email 
