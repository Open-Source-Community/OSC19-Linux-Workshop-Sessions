# The Manual Pages, Links, &Managing Directories and Files #
[![](https://raw.githubusercontent.com/Open-Source-Community/oscgeeks.orgImages/master/Minified%20Images/navbar/logo-osc.png)](https://oscgeeks.org)

----
### Summary ###
    1. Man Pages
        1.1. What are Man pages?
        1.2. Searching for a Command
    2. Managing Directories and Files
        2.1. File Extensions
        2.2. Creating Directories
        2.3. Creating Files
        2.4. Renaming and Moving Files
        2.5. Copying Files
        2.6. Deleting Files and Directories
    3. Links
        3.1. What are Links?
        3.2. Soft “Symbolic” Links
        3.3. Hard Links
        3.4. Deleting Links

-------------
## Man Pages ##
### What are Man Pages ? ###
It stands for manual pages.

They’re a set of pages that explain what every command on the system
does, what options are available, what arguments it can take, and shows
you how to use them.

**To open a man page type:**`` man [COMMAND NAME]``
>>*Example:*`` man man``
This will show you the manual of the “man” command.
You can use the arrow keys to navigate the pages and you can hit **q** to quit
or **h** for help.

If you want to search for a specific word you can press slash (/) then type in
the keyword and then press enter.

>*Example:*`` /sections`` will make you search for “sections”.
**Result:**
This indeed does bring up the first occurrence of the word “sections”.

*Note: You can also use
``info`` and ``--help`` to get
information about a
command.

### Searching for a Command ###

If you need to do a specific task but don’t know which command can do it:
* you can use  ``apropos ``or ``man -k ``to search for that command by the
keyword of the command.
>>example :``man -k "rename"``

* You can use`` whatis ``or`` man -f ``to quickly see what a command does
>>example:``whatis mv``
example:``man -f ls``
-----------------
## Managing Directories and Files ##
### File Extensions ###
A file extension is the ending of a file’s name that helps the operating
system and the user know the kind of file it is and what program should run
to open this file.
By default Linux has 3 types of files:
1. Regular File (-):
• **Readable file**(.txt, .cpp)
• **Binary file**(.exe)
• **Image file** (.png, .jpg)
• **Archive or “Compressed” file** (.zip, .rar, .doc, .pdf)
2. **Directory (d)**: A folder containing other files or folders
3. Special
• **Block File (b)**: Hardware files (Like some files under /dev/)
• **Soft “Symbolic” Link File (l)**: File pointing to another file (shortcut)
### Creating Directories ###
you can use ``mkdir`` to make new directories.
>>Example:
``mkdir linux``
``mkdir "mydir is here "``
If you want to create more than one directory at a time you
can do the following:
``mkdir one two three``

**Note: We use double quotes
``“ ”`` if the name of the
directory has more than one word.
This is to avoid making the
shell interpret the 2 words as
2 separate arguments
### Creating Files ###
You can use ``touch`` to create a file, like`` mkdir`` you can pass as many
arguments to it and it’ll create the files for you.
>>Example:
You want to create 2 files:``touch file1 file2``
### Copying Files ###
To copy files you can use:`` cp``
>>Example:
To copy a file, the following syntax can be used:``cp <original file> <copy file>``
## Renaming and Moving Files ##
To rename a file use: ``mv``
>>Example:
Create a file that is called file1 and rename it to textfile.
``touch file1``
``mv file1 textfile``
To move “cut” a file use`` mv``
>>Example:
Moving **“textfile”** from **~/one)** to **~/two**.
``mv textfile ../two/textfile``
--------------
## links ##
### What are Links? ###
A link in Linux is a file that points to another file/directory. Creating links is
similar to creating shortcuts.A file can have multiple links linked to it. But a
link can only be linked to (pointed to) one file.
There are two types of links:
  1. Soft or Symbolic links.
  2. Hard links.

_These links behave differently when the source of the link (what is being
linked to) is moved or removed._
**→ Symbolic links are not updated, and become “hanging links”.**
**→ Hard links always refer to the source, even if moved or removed.**
>>For example: We have a file A.txt. If we
create a soft link and a hard link both
pointing to it and then delete A.txt, the
result is visible in the opposite figure.
We can simply say that a soft link is just a
file that points to another (shortcut), while a
hard link is a copy of a file that is always
synchronised with it.

***Note: You can think of
links like pointers in
programming
languages, if you’re
familiar with them.

### Soft “Symbolic” Links ###
● _A soft link is similar to the file shortcut feature which is used in
Windows operating systems._
● _Soft links can be linked across different filesystems, although if the
original file is deleted or moved, the soft link will not work correctly
and is referred to as a “hanging link”._
● _Soft links contain the path for original file but not the content._
● _A soft link can link to a directory._
>>Example:
Make a link using the`` ln ``command.
The option ``-s`` makes the link a soft link and not a hard one.
``ln -s Filename Linkname`` :**Make a soft link**

### Hard Links ###

● _A hard link is similar to creating a copy that is always synced with the
original file._
●_ Hard links can’t be made across different file systems. But, if the
original file is deleted or moved, the hard link will still work._
●_ A hard link can’t link to a directory._

>>Example:
Make a hard link using the ``ln`` command.
``ln Filename Linkname``
It is exactly like a synced copy of
the file.

### Deleting Links ###
To delete a link you can use ``unlink `` or`` rm``
>>Example:
``unlink linkname``

And since a link is a file after all, you can also delete it with ``rm``.
>>Example:
``rm linkname``
