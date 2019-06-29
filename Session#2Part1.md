# Session#2 Part 1
[![](https://raw.githubusercontent.com/Open-Source-Community/oscgeeks.orgImages/master/Minified%20Images/navbar/logo-osc.png)](https://oscgeeks.org)

# The Command Line & The Linux Filesystem Hierarchy


# The Shell
## What is the shell ?

Remembering this diagram from last session, the shell is the first layer that a user can use to interact with the
operating system.

![](./Images/Session%202/layers.jpg)


It looks something like this:

![](./Images/Session%202/Linux_shell.jpg)

This is the standard __“TTY”__ shell that you can use, it is the default one you’ll find on Linux distributions that don’t have a GUI.

## Ways to connect to a shell
You can access the __TTY__ shell by pressing CTRL + ALT + any of the function keys ranging from 2 to 7.

_**Example:** CTRL + ALT + F3_

__Note : If you are using laptop you may have to press the 'fn' key alongside the combination to make it work.__

__Note : By default, most Linux distributions use TTY7 (F7) or TTY2 (F2).__

It doesn’t really seem like the nicest or most intuitive way to use your system, and what makes it even worse is that you have to exit the GUI every time you need to type a command.

That’s why we have the _glorious_ terminal! 

# The Terminal Emulator
## What is a terminal emulator?
The terminal emulator is a great way to connect to a shell without having to close your GUI. It is an amazing way to execute commands. _i.e Type commands in a window that is inside your GUI._

And it looks something like this:

![](./Images/Session%202/terminal_emulator.png) ![](./Images/Session%202/terminal_emulator_2.png)


## Ways to open a terminal
The terminal can be opened using any of the following methods (and many more):
* CTRL + ALT + T (Works on Ubuntu and Linux Mint)
* SUPER + T (Works on some distributions like elemetaryOS)
* ALT + F2 then typing in “gnome-terminal” or “konsole” (The name of the terminal emulator that your distribution uses)
* Right click on the desktop and click on “Open a terminal”
* Opening the terminal from the GUI by searching for it in the menu. Search for (Terminal, Console, Konsole, etc..)

_**Note:** The Windows key is called “Super” or “Meta” in Linux._

# The Command Line
## The Command Line Prompt
When you open the terminal you’ll see something like this:

![](./Images/Session%202/command_line_prompt.jpg) 
![](./Images/Session%202/command_line_prompt-2.jpg)

It is prompting you to enter a command, let’s break it down:

```osc/root``` : The username of the current logged in user.

```@```: Defines that you are connected to the machine that has the name after it

```mint```: The name of the computer running (Name of the host)

```~```: The working directory, the directoy that the terminal is working in right now.

```$```: States that you are logged in as a regular user.

```#```: States that you are logged in as the system administrator (root).

So we can basically summarise it to the following:

```USERNAME@HOSTNAME:WORKING_DIRECTORY($/#)```

## The Command Line Syntax
When ordering the computer to do something, **i.e giving it a command**, you have to take care of the syntax.

Just like programming languages, the Linux shell has specific syntax that you have to use. Just so that it could be understood by the shell.

The syntax goes as follows:
![](./Images/Session%202/command_line_syntax.jpg)

**The Command:** Intuitively, this is the command that you give to the system, i.e.
delete, move, copy, list, etc..

**The Option:** Modifies the action of the command.

**Example:** List “ALL” files, delete “recursively”, show the first “40” lines of a file, delete the file “by force”

**The Arguments:** What you’re going to apply the command to. i.e. Delete (command) a certain file (argument). We can say in short that the options modify the command’s effect on the argument.

#### Let’s take the ls command as an example:
```ls``` – lists the content of a directory(folder).

Running the command ls does the following:
![](./Images/Session%202/ls_command.jpg)

But that format isn’t really good if you want a detailed view, so we add the ```-l``` option which makes it list the content but in a “long” form:

![](./Images/Session%202/ls-l_command.jpg)

Much better! Everything is clealer and organised in a list.

How about we take a look at the hidden files too?

The ```-a``` option lists “all files”, this command can be shortened down to ```ls -la``` or ```ls -al```

**Note: Hidden files and directories in Linux start their name with a dot”.”.**
![](./Images/Session%202/ls-l-a.jpg)

# Filesystems
## What is a filesystem?
A filesystem is the way that the files are stored on a storage device (i.e. Hard Drive, USB Flash Drive, etc..).

Each operating system uses a certain filesystem:
![](./Images/Session%202/filesystem.png)

**Note: Linux supports NTFS and FAT32, but Windows doesn’t support EXT4 or XFS, that’s why you can’t see the Linux partitions on Windows.**

## Windows Directory Structure
A directory structure is the way an operating system's files are arranged displayed to the user.
![](./Images/Session%202/windows_directory_structure.png)

Windows, like every operating system, has a specific directory structure for its **NTFS** file system. Each disk is assigned a letter, and you browse your files based on that. 

**Note: C:\ and D:\ could be 2 seperate physical hard drives.**


Linux also has a directory structure, called **“Filesystem Hierarchy Standard”** or **“The Linux Filesystem Hierarchy”**.


# Linux Filesystem Hierarchy
### The root ‘/’ directory
The ‘/’ directory or the “root” directory is where everything begins on Linux.

No matter what you want to access, where it is, it will somehow connect to the
root directory.

#### Here’s a demonstration of the Linux Filesystem Hierarchy:

![](./Images/Session%202/linux_filesystem.png)

From the previous, we can see that: “Everything in Linux is a file”. 
Even devices and processes, everything is a file under the ‘/’ directory somehow.

**Note: C:\ and D:\ here are not accessed as C:\ or D:\\, but instead as directories under ‘/’.**

**Let’s test it out!**
![](./Images/Session%202/ls_root.jpg)
If we list the content of the root directory using the ```ls``` command, we will find the directories in the previous diagram.

Now we know what a filesystem, directory, and file are. Let’s talk about how we can access them.

## Navigating through the filesystem

You opened a terminal, now what?
The first thing you want to do is to know where the terminal is working:

![](./Images/Session%202/pwd.jpg)

```pwd```: Print Working Directory, tells you the directory your terminal is working in.

![](./Images/Session%202/ls.jpg)

Now that you know where you are in the system, you should see the content of
the directory using the ```ls``` command.

What if we wanted to enter the Pictures directory?

![](./Images/Session%202/cd.jpg)

```cd```: Change Directory, changes the working directory to the specified argument.

Now the working directory is Pictures, notice how the text before **$** also changed to **~/Pictures** which is the same as **/home/osc/Pictures**, which is the working directory.

What if I wanted to go back to the home directory?
There are 4 ways:
* ```cd ~```: This basically means cd /home/osc since ~ means the home directory of the current user.
* ```cd /home/osc```: Tells the shell to change the working directory to /home/osc.
* ```cd```: Running the cd command without an argument takes you to the home directory by default.
* ```cd ..```: .. refers to the parent directory, continue reading:

### The ```.``` and ```..``` Links
Each directory has 2 hidden files (links) in it, ```.``` and ```..```.

The ```.``` link refers to the directory itself.

The ```..``` link refers to the directory before it (parent directory).

Example: If the working directory is /home/osc/Pictures/, then:

```‘.’ = /home/osc/Pictures/``` and ```‘..’ = /home/osc/``` which is the directory before it.

To verify:

![](./Images/Session%202/verify_'.'_and_'..'.jpg)

This can be a little confusing at first, so practice with yourself and maybe try drawing it on a piece of paper to visualise how things really work.

### Relative and absolute paths

Let’s simplify this by taking a guy called “Jack” as an example, Jack goes to FCIS ASU every day, this is the path he takes daily:
![](./Images/Session%202/relative_and_absolute_path.png)

Jack’s route to college daily is **Home->Bus Stop->Abbassia->FCIS ASU.**

If he met someone at Abbassia and asked him: “Where are you going?”, Jack’s response will be **“FCIS ASU”** only, because that’s the next step.
If someone asked Jack “What’s your full route to college?”, Jack’s response would be **“ Home->Bus Stop->Abbassia->FCIS ASU”.**

**Note that his route from Abbassia is shorter because it is relative to Abbassia.**

The same thing applies in Linux for directories and files.

**Absolute Path:** The total path leading to the directory.

**Relative Path:** The path relative to the working directory.

**Example:**
In the diagram, let the working directory be /home/User1

![](./Images/Session%202/example_absolute_and_relative_path.png)

The relative path for “Videos” would be: Videos

The absolute path would be: /home/User1/Videos

##### Test yourself(Solution at the end):
In the same diagram, let the working directory be /home/User1 and the user you’re logged in as called User1.

* Which directory does ‘.’ refer to?
* Which directory does ‘..’ refer to?
* What would be the working directory if you run ```cd ..```?
* What would be the working directory if you run ```cd .```?
* What would be the working directory if you run ```cd``` Videos?
* What would happen if you run ```cd ../User2/```?
* What would happen if you run ```cd```?
* What would happen if you run ```cd User2```?
* What would happen if you run ```cd /home/User2```?

#
#
#
#
#
##### Solution:
* The directory itself (User1).
* The parent directory (the directory before it: home).
* The working directory would be home.
* The shell will change the directory to the current working directory so nothing will change.
* The shell will change the working directory to /home/User1/Videos.
* The shell will change the working directory to /home/User2 (This is the relative path)
* The shell will change the working directory to /home/User1 as you are logged in as User1, so nothing will change because the working directory is already /home/User1
* Error, there isn’t a directory called “User2” under the directory “User1”.
* The shell will change the working directory to /home/User2 (This is the absolute path)
