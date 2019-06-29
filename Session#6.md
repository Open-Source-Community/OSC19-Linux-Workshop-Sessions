# Session#6
[![](https://raw.githubusercontent.com/Open-Source-Community/oscgeeks.orgImages/master/Minified%20Images/navbar/logo-osc.png)](https://oscgeeks.org)

# Git Version Control
A Free Open Source DVCS ”distributed version control system ” 

# How it Works!

- ## Snapshots, Not Differences
    - Compares SHA1 sum of modified files.
    - Saves the new file as a Whole "easier to retrive lost data"
    - Each Snapshot contains references to the files "to save space uses ref. only"

- ## Stores new versions of files only

    ![N|Solid](./Images/Session%206/saves_new_ver_only.png)

- ## Each snapshot contains each file

    ![N|Solid](./Images/Session%206/snapshots.png)

- ## Everything is local “distributed”
    - Each Computer has all the history of the project
    - Makes it faster and easeir to contribute 
    - Safer beacuase the data are not onlt on one repo

- ## Git has Integrity
    - Everything in Git is CHECKSUMMED "fast ,reliable"
    - Uses SHA-1 hash "a 40 hexadecimal char string"
    - Easy to recognize corrupted files.

- ## Git Generally Only Adds Data "Everything is almost reversible"



# Files’ Three States
- Modified
- Staged
- Committed

# Installtion
```sh
$ sudo apt update
$ sudo apt intsall git
```

# First Time Configurations 
```sh
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
git config --global core.editor nano
git config --global merge.tool meld 
```

# Git Help
git has a really good command manual for each command
```sh
$ git help <command>
$ man git <command>
$ git <command> -h #summarized
```
# Important Terms
- Repository
- Index “Staging area”
- working tree “Project tree”
- Commit
- Branch
- Tag
- Master
- Head

# Git Basics

## Create a new repository

```sh
    $ git init # Intialize an empty/new repository
    $ git clone <URL># to Clone/Copy exsiting repository
``` 

`<URL>`: can be git, shh, http, https, file , etc 

## Doing changes in the repository

- ### Remove files or directories

    ```sh
    git rm <file name| wild card>
    ```

- ### Move or rename files or directories 

    ```sh
    git mv <file directory | file name | wild card> <new directory | new file name>
    ```

## Recording Changes to the Repository 

![N|Solid](./Images/Session%206/pasted%20image%200.png)

- ### Checking status of your files

    ```sh
    $ git status`
    $ git status -s # Summarized
    ```

    - `??`    “ untracked ”
    - A     “ staged ”
    - M     “ Modified staged “ 
    - `M`    “ Modified untracked “

    Example: 

    ```sh
    $ git status
    $ echo 'I' > README #creates a new file
    $ git status
    ```

- ### Staging Modified Files

    Stage your files after adding not before
    
    ``` sh
    $ git add <files|WildCards> 
    ```
    
    Example:

    ```sh
    $ git add README
    $ git status
    $ echo “USE” >> README
    $ git status
    $ git add README
    $ git status
    ```

- ### Ignoring Files

    A file listing patterns to match them with files in your repositories.

    File name “.gitignore”

    - .gitignore [`common templates`](https://github.com/github/gitignore)

    - See `man gitignore` for more information

- ### Viewing staged and unstaged

    ``` sh
    $ git status
    $ git diff #diffreneces between commited  and modified/untracked
    $ git diff --staged #diffreneces between commited and modified/tracked/staged
    ```

    Example 1

    ``` sh
    $ git commit -am “cleaning the stage”
    $ echo “Git” >> README
    $ echo  “Git” > Cont.md
    $ git add README Cont.md
    $ git diff # 
    $ echo “OSC” > Cont.md
    $ git status
    $ git diff
    ```

    Example 2

    ``` sh
    $ git commit -am “cleaning the stage”
    $ echo “1” > file
    $ git add file && git commit -m “new file”
    $ echo “2” > file
    $ git add file
    $ echo “3” >file
    $ git diff
    $ git diff --staged
    ```

- ### Committing Changes

    ```sh
    git commit
    git commit -m "short Message"
    git commit -am “Your Message” #Stage all untracked files and commit all files in staged area
    ```

    Example 

    ``` sh
    $ git commit -am “cleaning the stage”
    $ echo “1” > newfile
    $ git commit -am “new file”
    $ git status
    $ git add newfile && git commit -m “new file”
    # Change “newfile” and try using commit -am “changed new file”
    ```

- ### Commit History

    ```sh
    $ git log
    $ git log -p
    $ Git log -<number>
    $ git log --since <date>
    $ git log --until <date>
    ```

    `<data>`or `<number>` EX : “ 2008-01-15” or  EX : "2 years 1 day 3 minutes ago" 
        
## Undoing Things

### Undo add (Unstaging a Staged File)

```sh
git reset <files>
```

### Amend

```sh
git commit --amend
```

Used to change your latest log message and to make modifications to the most recent commit

### Undo Commit

``` sh
    $ git revert<commit>
    $ git checkout<file|commit>
    $ git reset
    $ git reset --soft<commit>
    $ git reset --hard<commit>
```
    - <commit>:
        - SHA1
        - Head^,Head@{number}

## Remote Repositories

- #### Clone a Repository

        -git clone<URL>
        -https://github.com/
        -git://github.com/koke/grit.git
        -git@github.com:mojombo/grit.git
        -/srv/git/project.git
        -file:///srv/git/project.git

- ### Showing Your Remotes

    ```sh
        $ git remote
        $ git remote -v
    ```

- ### Add Remotes

    ```sh
        $ git remote add <Name> <URL>
    ```

- ### Fetching and Pulling Repositories 

    ```sh
        $ git fetch <remote>
        $ git pull <remote> <branch>
    ```

- ### Pushing into Repositories

    ```sh
        $ git push <remote> <branch>
    ```

## Branching

- ### List branches

```sh
     $ git branch
     $ git branch -a
```

- ### Create new branch

    - #### git branch testing
    ![N|Solid](./Images/Session%206/Branching.png)
        
    - #### switching Branch 
                - “git checkout testing”
    ![N|Solid](./Images/Session%206/Switching.png)
        
    - #### Commiting in a New Branch
    ![N|Solid](./Images/Session%206/Commiting.png)
        
    - #### Return to master Branch   
    ![N|Solid](./Images/Session%206/Return.png)
    
    - #### Commiting again Branch
    ![N|Solid](./Images/Session%206/Commiting_agin.png)

- ### Switch branches

```sh
     $ git Checkout <branch name>
```

- ### Delete Branches

```sh
     $ git branch -d <branches>
```

- ### Merging Branching
    
    - Fast-forward
    - Recursive “Three Way merge”
    - git mergetool
    - meld

- ### Combine Commits and Modify History of a Branch
    
    -  git rebase

## Remote Branches
     
![N|Solid](./Images/Session%206/Remote_br.png)
![N|Solid](./Images/Session%206/Remote_br2.png)
![N|Solid](./Images/Session%206/Remote_br3.png)

## Local Git Repositories 

    - git daemon
    - base-path=<path> 
    - export-all 
    - reuseaddr 
    - informative-errors 
    - verbose
    - enable=receive-pack
    - You can use aliases

## git aliases

    - git  config --global alias.<name> ‘commands’
    - git config --global alias.serve '!git daemon --base-path=. --export-all --areuseaddr --informative-errors --verbose' 
    - git hub or git serve

# Resources

- [`Pro GIt`](https://github.com/github/gitignore)
- [`git daemon`](https://railsware.com/blog/2013/09/19/taming-the-git-daemon-to-quickly-share-git-repository/)
- [`rest vs checkout vs revert`](https://www.atlassian.com/git/tutorials/resetting-checking-out-and-reverting)



