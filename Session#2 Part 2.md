# Session#2 Part 2
![](https://github.com/MahmoudElmanayly/OSC19-Linux-Workshop-Sessions/blob/master/Artwork/Session%202/logo-osc.png)

# Manual Pages, Links and Managing Directories and Files

## Man Pages
### what ate Man Pages ?

It stands for manual pages.

They're a set of pages that explain what every command on the system does, what options are available, what arguments it can take, and shows you how to use them.

To open a man page type:  ***man [command name]***

**Example** :  ***man man***
This will show you the manual page of the "man" command.
You can use the arrow kwys to navigate the pages and you can hit ***g*** to quit of ***h*** for help.

![](https://github.com/MahmoudElmanayly/OSC19-Linux-Workshop-Sessions/blob/master/Artwork/Session%202/man%20page.png)
If you want to search for a specific word you can press ***slash(/)*** then type in the ***<keyword>*** 

**Example :** */section* will search for "sections".

![](https://github.com/MahmoudElmanayly/OSC19-Linux-Workshop-Sessions/blob/master/Artwork/Session%202/search%20in%20man%20page.png)

This indeed does bring up the first occurrence of the word ***"sections"***.
You can learn more about sections from this image.

![](https://github.com/MahmoudElmanayly/OSC19-Linux-Workshop-Sessions/blob/master/Artwork/Session%202/searched%20words.png)

> You can also use ***info*** and ***--help*** to get information about a command.

**Example** : ***info ls***	   ***ls -help***

### Searching for a Command
If you need to do a specific task but don't know which command can do it:
> You can use ***apropos*** or ***man -k*** to search for that command by the keyword of the command.

**Example :**
You want to rename a file but don't know what command does that:

![](https://github.com/MahmoudElmanayly/OSC19-Linux-Workshop-Sessions/blob/master/Artwork/Session%202/apropos.png)

As you can see, all of these are commands that can rename files.
Which one youc choose is up to you. You can use man pages to know more about these commands and select the suitable one for your case.

> You can use ***whatis*** or ***man -f*** to quickly see what a command does.

**Example :**

![](https://github.com/MahmoudElmanayly/OSC19-Linux-Workshop-Sessions/blob/master/Artwork/Session%202/whatis.png)

## Managing Directories and Files
### File Extensions
A file extension is the ending of a file's name that helps the operating system and the user know the kind of file it is and what program should run to open this file.

By default Linux has 3 types of files:
1. Regular file(-):
     - Readable file (.txt, .cpp)
     - Binary file (.exe)
     - Image file (.png, .jpg)
     - Archive or Compressed file (.zip, .rar)
2. Directory(d): A folder containing files or folders
3. Speical:
     - Block File(b): Hardware files (Like some files under /dev/)
     - Soft "Symbolic" link file(l): File pointing to anthor file (shortcut)

### Creating Directories
You now know how to use man. Can you search for a command that makes a directory ?

**Solution:** ***man -k "make dir"*** and the command is: ***mkdir***

**Example:**

![](https://github.com/MahmoudElmanayly/OSC19-Linux-Workshop-Sessions/blob/master/Artwork/Session%202/make%20dir.png)
![](https://github.com/MahmoudElmanayly/OSC19-Linux-Workshop-Sessions/blob/master/Artwork/Session%202/make%20dir%202%20words.png)

> **Note**:We use double quotes " " if the name of the directory has more than on word. This is to avoid making the shell interpret the 2 words as 2 separate arguments.*
If you want to create more than one directory at a time you can do the following:

![](https://github.com/MahmoudElmanayly/OSC19-Linux-Workshop-Sessions/blob/master/Artwork/Session%202/make%20dirssss.png)

Let's check:

![](https://github.com/MahmoudElmanayly/OSC19-Linux-Workshop-Sessions/blob/master/Artwork/Session%202/ls%20-l.png)

### Creating Files
You can use ***touch*** to create a file.

**Example:**

You want to create 2 files:

![](https://github.com/MahmoudElmanayly/OSC19-Linux-Workshop-Sessions/blob/master/Artwork/Session%202/create%202%20files.png)

### Copying Files
To copy files you can use ***cp***.

**Example:**

Copy "Hello.txt" to "Copy.txt"

![](https://github.com/MahmoudElmanayly/OSC19-Linux-Workshop-Sessions/blob/master/Artwork/Session%202/copy.png)

### Renaming and Moving Files
To rename a file use ***mv***

**Example:**

Create a file that is called file1 and rename it to textfile.

![](https://github.com/MahmoudElmanayly/OSC19-Linux-Workshop-Sessions/blob/master/Artwork/Session%202/remane%20file.png)

To move "cut" a file use ***mv*** too.

**Example:**

Moving "textfile" from ~/one to ~/two

![](https://github.com/MahmoudElmanayly/OSC19-Linux-Workshop-Sessions/blob/master/Artwork/Session%202/move%20file.png)

### Deleting Files and Directories
You can delete a file or a directory using the ***rm*** command.
> try to figure it out from the man pages on your own scroll down :
> Find how to do the following:
> - Delete a file.
> - Delete an empty directory.
> - Delete a non empty directory.
> - Delete a file but ask for confirm before.
> - Delete by fore and don't prompt the user.

**Solution:**

*rm filename*

*rm -r directory_name* OR "rmdir directory_name"

*rm -r directory_name*

*rm -i filename*

*rm -f filename*

## Links

### What are links?
A link in linux is a file that points to another file/directory. Creating links is similar to creating shortcuts. A file can have multiple links. But a link can only be linked to (pointed to) one file.

#### There are two types of links:
	1. Soft or Symbolic links.
	2. Hard links.

These links behave differently when the source of the link ismoved or removed.
Symbolic links are not updated, and become "hanging links".
Hard links always refer to the source(inode), even if moved or removed.

**For example:** 

We have a file A.txt if we create a soft link and a hard link both pointing to it and then delete A.txt, the result is visible in the opposite figure.

We can simply say that a soft link is just a file that points to another, while a hard link is a xopy of a file that is always sychronised with it.

![](https://github.com/MahmoudElmanayly/OSC19-Linux-Workshop-Sessions/blob/master/Artwork/Session%202/remove.png)

### Soft "Symbolic" Links
A soft link is similar to the file shortcut which is used in windows OS.
Soft links can be linked across different filesystems, although if the original file is deleted or moved, the soft link will not work correctly and is referred to as a "hanginf link".

**Example:**

Make a link using the ***ln*** commmand.
The option *-s* makes the link a soft link and not a hard one.

![](https://github.com/MahmoudElmanayly/OSC19-Linux-Workshop-Sessions/blob/master/Artwork/Session%202/soft%20link.png)

You can see that indeed, S_Link is pointing to File.txt

### Hard Links
A hard link is similar to creating a copy that is always synced with the original file.
Hard links can't be made across different file systems. But, if the original file is deleted or moved, the hard link will still work.
A hard link can't link to a directory.

**Example:**

Make a hard link using the ***ln*** command.

![](https://github.com/MahmoudElmanayly/OSC19-Linux-Workshop-Sessions/blob/master/Artwork/Session%202/hard%20link.png)

In this example you can see that H_Link is treated as a normal file, it is just linked to File.txt. After editing File.txt, H_Link was edited too.
It is exactly like a synced copy of the file.


### Deleting Links

To delete a link you can use ***unlink*** or ***rm***

**Example:**

![](https://github.com/MahmoudElmanayly/OSC19-Linux-Workshop-Sessions/blob/master/Artwork/Session%202/unlink.png)

And since a link is a file after all, you can also delete it with **rm**.

**Example:**

![](https://github.com/MahmoudElmanayly/OSC19-Linux-Workshop-Sessions/blob/master/Artwork/Session%202/remove%20link.png)
