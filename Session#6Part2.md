# Undoing Things

# Unstaging a Staged File

## Reset  
- git reset <files>

## Amend
- git commit --amnend
         - Used for 
         - to change your latest log message
            - to make modifications to the most recent commit
            - Use git rebase to combine commits and modify history of a branch.

## Undo Commit
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

## Showing Your Remotes
``` sh
    $ git remote
    $ git remote -v
 ```
## Add Remotes
 ``` sh
    $ git remote add <Name> <URL>
 ```

## Fetching and Pulling Repositories 
``` sh
    $ git fetch <remote>
    $ git pull <remote> <branch>
 ```
## Pushing into Repositories
``` sh
$ git push <remote> <branch>
 ```
## Branching
- #### List branches
        ``` sh
     $ git branch
     $ git branch -a
        ```
- #### Create new branch
        ``` sh
        $ git branch <new name>
        ```
- #### Switch branches
        ``` sh
        $ git Checkout <branch name>
        ```
- #### Delete Branches
        ``` sh
        $ git branch -d <branches>
        ```

## Creating a New Branch 

- ##### git branch testing
![N|Solid](./Branching.png)
    
- #### switching Branch 
            - “git checkout testing”
![N|Solid](./Switching.png)
    
- #### Commiting in a New Branch
![N|Solid](./Commiting.png)
    
- #### Return to master Branch   
![N|Solid](./Return.png)
 
- #### Commiting again Branch
 ![N|Solid](./Commiting_agin.png)

## Merging Branching
- Fast-forward
- Recursive “Three Way merge”
- git mergetool
     - meld

## Remote Branches
     
![N|Solid](./Remote_br.png)
          ![N|Solid](./Remote_br2.png)
                ![N|Solid](./Remote_br3.png)

## Local Git Repositories 
- #### $ git daemon
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

## Resources

- [`Pro GIt`](https://github.com/github/gitignore)
    
    - [`git daemon`](https://railsware.com/blog/2013/09/19/taming-the-git-daemon-to-quickly-share-git-repository/)
    
    - [`rest vs checkout vs revert`](https://www.atlassian.com/git/tutorials/resetting-checking-out-and-reverting)


# Thank You

