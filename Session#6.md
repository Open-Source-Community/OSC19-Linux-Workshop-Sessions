# Session#6
# Git Version Control
A Free Open Source DVCS ”distributed version control system ” 

# How it Works!

- #### Snapshots, Not Differences
  - Compares SHA1 sum of modified files.
  - Saves the new file as a Whole "easier to retrive lost data"
  - Each Snapshot contains references to the files "to save space uses ref. only"
- #### Stores new versions of files only
  ![N|Solid](./Artwork/Session%206/saves_new_ver_only.png)
- #### Each snapshot contains each file
  ![N|Solid](./Artwork/Session%206/snapshots.png)
- #### Everything is local “distributed”
    - Each Computer has all the history of the project
    - Makes it faster and easeir to contribute 
    - Safer beacuase the data are not onlt on one repo
- #### Git has Integrity
    - Everything in Git is CHECKSUMMED "fast ,reliable"
    - Uses SHA-1 hash "a 40 hexadecimal char string"
    - Easy to recognize corrupted files.
- #### Git Generally Only Adds Data "Everything is almost reversible"



## Files’ Three States
- Modified
- Staged
- Committed

## Installtion
```sh
$ sudo apt update
$ sudo apt intsall git
```

## First Time Configurations 
```sh
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
git config --global core.editor nano
git config --global merge.tool meld 
```

## Git Help
git has a really good command manual for each command
```sh
$ git help <command>
$ man git <command>
$ git <command> -h #summarized
```
## Important Terms
- Repository
- Index “Staging area”
- working tree “Project tree”
- Commit
- Branch
- Tag
- Master
- Head
# Git Basics
- #### Git Repository
```sh
$ git init # Intialize a Embty/new repository
$ git clone <URL># to Clone/Copy exsiting repository
```
 `<URL>`: can be git, shh, http, https, file , etc 
- ## Recording Changes to the Repository 
    ![N|Solid](./Artwork/Session%206/pasted%20image%200.png)
    - #### Checking status of your files
        ```sh
        $ git status`
        $ git status -s # Summarized
        ```
        - `??`    “ untraked ”
        - A     “ staged ”
        - M     “ Modified staged “ 
        - `M`    “ Modified untracked “
        Example: 
        ```sh
        $ git status
        $ echo 'I' > README #creates a new file
        $ git status
        ```
    - #### Staging Modified Files
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
    - #### Ignoring Files
        A file listing patterns to match them with files in your repositories.
        File name “.gitignore”
        - .gitignore [`common templates`](https://github.com/github/gitignore)
        - See `man gitignore` for more information
- ## Viewing staged and unstaged
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
    - #### Committing Changes
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
    - #### Remove
        ```sh
        git rm <file name| wild card>
        ```
    - #### Move
        ```sh
        git mv <file name| wild card>
        ```
    - ### Commit History
        ```sh
        $git log
        $ git log -p
        $ Git log -<number>
        $ git log --since <date>
        $git log --until <date>
        ```
        `<data>`or `<number>` EX : “ 2008-01-15” or  EX : "2 years 1 day 3 minutes ago" 

