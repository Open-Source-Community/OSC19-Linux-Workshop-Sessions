# Session#3 Part 2
[![](https://raw.githubusercontent.com/Open-Source-Community/oscgeeks.orgImages/master/Minified%20Images/navbar/logo-osc.png)](https://oscgeeks.org)


# Users, Package Managers, & Intro to Processes
 
## Users and Groups
 
### Users
 
A user is anyone who has access to the system, it could be a user account for a real user (i.e a human) or a system user assosciated with a service or a program.
The root user is considered the admin of the system and has access to everything.
You can know any user’s ID and the groups that they’re in by using the command 
```
id <username>
```
for example

![Image of id username](./Images/Session%203/username.png)

A userID is a positive integer assigned to the user to identify it.
Root will have the userID 0.
After that will be system users that are assosciated with services or
programs, numbered from 1 up to 999, real user accounts start from the UID 1000.

- UID 0 - Root user
- UID 1 - 999 - System and Program users
- UID >= 1000 - Real users

The users of the system are stored in the /etc/passwd file.

![Pic of etc/passwd](./Images/Session%203/etc.PNG)

Looking at the content of the
file here, we can see that the
root user is the first with UID 0.
We have system users ranging
from 1 to 120.

Example: lightdm has a UID of
108, it is a display manager, a system application.

The final 2 lines have the 2 real
users on the system. Example: Hassan, UID 1000 (First real user created).

#### Adding and deleting users

To create a user, simply enter the command
```
sudo useradd -m <username>
```

**Breaking it down**

```sudo```: Needed because you need administrator privilage to create a new a user.

```useradd```: The command used to add users.

```-m```: An option used to make a home directory for the new user by default.

If we create a user named temp and check the content of the etc/passwd file
again:

![Picture of etc/passwd](./Images/Session%203/etc%202.PNG)


To delete a user, simply enter the command
```
sudo userdel <username>
```

#### Setting password for users

To set or change a password for a user, we use the command
```
sudo passwd <username>
```

It’ll then prompt you to enter the password.

#### Switching Users

To switch user, we use the command
```
su username
```
Then you’ll be prompted to enter the password

![image of switch user](./Images/Session%203/su%201.PNG)

To return to original user enter the command
```
exit
```

![image of su 2](./Images/Session%203/su%202.PNG)

### Groups

Groups are basically a collection of users, it helps organize user access on the system.

For example: If you’re working for a company, you don’t want the HR to edit the code and at the same time you don’t want the developers to read the HR files.

You’ll put all the HR personnel in a group and give that group access to HR files and deny access to anyone who isn’t in the HR group.

#### Adding and Deleting Groups

To create a new group, use the command
```
sudo groupadd <groupname>
```
To delete a group, use the command
```
sudo groupdel <groupname>
```

#### User Modification

Every user has 1 primary group and supplementary groups, to modify any user we
use the command 
```
usermod
```
To change the primary group we’ll add the option 

```-g new_primary_group```

To change the supplementary groups we’ll add the option

```-G new_supplementary_groups```


However this will overwrite the current supplementary groups a user has.

If we want to append the stated groups, we’ll add the a option to append

```-aG new_supplementary_groups```

**Example**
```
usermod -g prim_group -aG sup_groups user
```
_________________________________

## Package managers

### Packages and Repositories

A package in linux is considered to be a collection of files, it can be an application, a program or even documentation. Packages in Linux are stored in repositories where the package manager can easily find, download, and install them.

**Repositories** can be considered something like an app store, that has many packages on it, and you choose to install and upgrade packages from it.

### Package Manager

The package manager is responsible for downloading, installing, searching, removing, and upgrading packages.

It consists of high and low level parts.

The **high level** package manager, called *apt* or *apt-get* in Debian-based distributions, it is responsible for searching the repositories and finding the packages, it is also responsible for resolving dependancies.

A **dependancy** is a package required for another package to work.

For example: The program GIMP requires a toolkit called GTK+ to work, so the package manager automatically installs GTK+ when installing GIMP.

The **low level manager**, called *dpkg* in Debian-based distributions, is the one responsible for the actual **installation** and **compilation** of the packages.

### Installing and Removing Packages

To install a package, we use the command
```
sudo apt install packages_names
```
![image of package installation](./Images/Session%203/install%20package.PNG)

In this example, vim-runtime is considered a dependancy, as vim needs it to work, the package manager notified us that it’ll be installed alongside vim.

To remove a package, we use the command
```
sudo apt remove package_name
```

### Searching for Packages

To search for packages, enter the command
```
sudo apt search <keyword>
```

## ![Image of package search](./Images/Session%203/search.PNG)

### Updating and Upgrading

As mentioned before, packages are downloaded from repositories, which can be considered a storage for packages. However after a while the packages get updated and maybe new packages are added, the local repository data on your system may get outdated so you need to update the local data.

The command ```apt update``` will update the links inside the repository data file so that when you download or update something from the repository you’ll get the lastest version.

As for the command ```apt upgrade``` it upgrades all the packages on your system to their latest versions available in the repositories.

______

## Processes

### What are Processes

A process is any program that is currently running on the system, you’ll have foreground processes and background processes.

Background processses aren’t seen by the user, this will include things such as update managers, network managers, etc...

Foreground processes are programs that are currently being used by the user, such as Google Chromium, Firefox, GIMP, Codeblocks, etc..

### PS and Top Commands

The ```ps``` command is responsible for telling you all the processing currently running on the terminal

![Image of PS](./Images/Session%203/PS.PNG)

- PID is short for Process ID.
- ```ps aux``` will show you ALL of the processes running on the system.

The ```top``` command will tell you all the current processes running in the system, and update them if any processes are killed or changed.

![Image of top](./Images/Session%203/top.PNG)

If you look at the figure above, you’ll see a command with the PID 1 called systemd, this is the initialisation service responsible for the whole system after booting.

### Signals

A signal is basically a command sent by the system to a process, the signal we’ll discuss today is called _sigkill_ which is responsible for **ending a process**.

It is similar to **End Task** in Windows.

To send a sigkill, we can use the command
```
kill <PID>
```
Or we can use the command
```
killall <process_name>
```
![Image of kill](./Images/Session%203/kill.PNG)

Note: ‘#’means the start of a comment in the Linux shell.











