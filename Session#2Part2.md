# Session#2 Part2 
[![](https://raw.githubusercontent.com/Open-Source-Community/oscgeeks.orgImages/master/Minified%20Images/navbar/logo-osc.png)](https://oscgeeks.org)
# The Manual Pages, Links,  and Managing Directories and Files

## Man Pages 
### What are Man Pages ? ###
It stands for manual pages.

They’re a set of pages that explain what every command on the system does, what options are available, what arguments it can take, and shows you how to use them.

**To open a man page type:**`` man [COMMAND NAME]``

**Example**: ``man man``

This will show you the manual of the “man” command.
You can use the arrow keys to navigate the pages and you can hit **q** to quit or **h** for help.

![](./Images/Session%202/man%20page.png)

If you want to search for a specific word you can press slash (/) then type inthe keyword and then press enter.

**Example**: ``/sections`` will make you search for “sections”.

![](./Images/Session%202/search%20in%20man%20page.png)

This indeed does bring up the first occurrence of the word ***"sections"***.

![](./Images/Session%202/searched%20words.png)

* Note: You can also use ``info`` and ``--help`` to get information about a command.

**Example**: ```info ls```  and ```ls --help```

### Searching for a Command ###

If you need to do a specific task but don’t know which command can do it:

* You can use ``apropos`` or ``man -k`` to search for that command by the keyword of the command.

**Example**: ``man -k "rename"``

![](./Images/Session%202/apropos.png)

As you can see, all of these are commands that can rename something.
Which one youc choose is up to you. You can use man pages to know more about these commands and select the suitable one for your case.

* You can use ``whatis`` or ``man -f`` to quickly see what a command does

**Example:** ``whatis mv``

![](./Images/Session%202/whatis.png)

-----------------
## Managing Directories and Files
### File Extensions
A file extension is the ending of a file’s name that helps the operating system and the user know the kind of file it is and what program should run to open this file.

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
______
______
______
**Solution:** ```man -k "make dir"``` and the command is: ```mkdir```

**Example:**

![](./Images/Session%202/make%20dir.png)
![](./Images/Session%202/make%20dir%202%20words.png)

**Note: We use double quotes ``“ ”`` if the name of the directory has more than one word.

This is to avoid making the shell interpret the 2 words as 2 separate arguments.

If you want to create more than one directory at a time you can do the following:

![](./Images/Session%202/make%20dirssss.png)

Let's check:

![](./Images/Session%202/ls%20-l.png)



### Creating Files ###
You can use ``touch`` to create a file, like`` mkdir`` you can pass as many arguments to it and it’ll create the files for you.

**Example:**

You want to create 2 files:``touch file1 file2``

### Copying Files ###
To copy files you can use:``cp``

**Example:**

To copy a file, the following syntax can be used:``cp <source file> <destination file>``

![](./Images/Session%202/copy.png)

## Renaming and Moving Files ##
To rename a file use: ``mv``
**Example:**

Create a file that is called file1 and rename it to textfile.

![](./Images/Session%202/remane%20file.png)

To move “cut” a file use`` mv``

**Example:**
Moving "textfile" from ~/one to ~/two

![](./Images/Session%202/move%20file.png)

### Deleting Files and Directories
You can delete a file or a directory using the ```rm``` command.

- Try to figure it out from the man pages on your own scroll down
- Find how to do the following:
    - Delete a file.
    - Delete an empty directory.
    - Delete a non empty directory.
    - Delete a file but ask for confirm before.
    - Delete by force and don't prompt the user.
_____
_____
_____
_____
**Solution:**

- ```rm filename```

- ```rm -d directory_name``` OR ```rmdir directory_name```

- ```rm -r directory_name```

- ```rm -i filename```

- ```rm -f filename```


## Links ##
### What are Links? ###
A link in Linux is a file that points to another file/directory. Creating links is similar to creating shortcuts. A file can have multiple links linked to it. But a link can only be linked to (pointed to) one file.

There are two types of links:
  1. Soft or Symbolic links.
  2. Hard links.

_These links behave differently when the source of the link (what is being
linked to) is moved or removed._

**→ Symbolic links are not updated, and become “hanging links”.**

**→ Hard links always refer to the source(inode), even if moved or removed.**

**For example:** 

We have a file A.txt if we create a soft link and a hard link both pointing to it and then delete A.txt, the result is visible in the opposite figure.

We can simply say that a soft link is just a file that points to another, while a hard link is a copy of a file that is always sychronised with it.

![](./Images/Session%202/remove.png)

***Note: You can think of links like pointers in programming languages, if you’re familiar with them.

### Soft “Symbolic” Links ###
- _A soft link is similar to the file shortcut feature which is used in Windows operating systems._
- _Soft links can be linked across different filesystems, although if the original file is deleted or moved, the soft link will not work correctly and is referred to as a “hanging link”._
- _Soft links contain the path for original file but not the content._
- _A soft link can link to a directory._

**Example:**
Make a link using the`` ln ``command.

The option ``-s`` makes the link a soft link and not a hard one.

![](./Images/Session%202/soft%20link.png)

You can see that indeed, S_Link is pointing to File.txt

### Hard Links ###

- _A hard link is similar to creating a copy that is always synced with the original file._
- _Hard links can’t be made across different file systems. But, if the original file is deleted or moved, the hard link will still work._
- _A hard link can’t link to a directory._

**Example:**

Make a hard link using the ``ln`` command.

![](./Images/Session%202/hard%20link.png)

In this example you can see that H_Link is treated as a normal file, it is just linked to File.txt. After editing File.txt, H_Link was edited too.

It is exactly like a synced copy of the file.

### Deleting Links ###
To delete a link you can use ``unlink`` or ``rm``

**Example:**

![](./Images/Session%202/unlink.png)

And since a link is a file after all, you can also delete it with ```rm```.

**Example:**

![](./Images/Session%202/remove%20link.png)
