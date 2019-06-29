# Session#5 Part 1
[![](https://raw.githubusercontent.com/Open-Source-Community/oscgeeks.orgImages/master/Minified%20Images/navbar/logo-osc.png)](https://oscgeeks.org)


# Shell "Bash"Scripting in GNU/Linux
### What's a shell?
The simplest and most direct way for the user to use their machine.

BASH = Bourne Again SHell
![BASH](https://camo.githubusercontent.com/7c9b27101ba491969d016f2f2427c3e066f7bd0b/68747470733a2f2f63646e2e7261776769742e636f6d2f6f64622f6f6666696369616c2d626173682d6c6f676f2f6d61737465722f6173736574732f4c6f676f732f4964656e746974792f504e472f424153485f6c6f676f2d7472616e73706172656e742d62672d636f6c6f722e706e67)

# What is a shell script and why use one?
#### - Running a series of shell commands to:
* **Process Files**
  * Reading Files.
  * Checking if files exist
  * Checking if files have changed.
* **Automate Tasks**
  * Automating the backing up of data
  * Automating package installations
  * Automating package installations
* **Using Linux Commands inside a program**
   * Use Linux commands inside programs
   * Use Linux commands inside programs

### Command Line Format
Options modify the commands behaviour on the arguments.
##### EXAMPLES:
`[COMMAND]` | `[OPTIONS]` | `[ARGUMENTS]`
---------- | ----------- | ------------
`ls` | `-ld, -la, -lA` | file or directory
`rm` | `-r, -f, -ir` | file or directory
binwalk | `-B` | file
You can find what a command's options are and what it does by running:
**1. man command**
**2. info command**
**3. command --help**

# *CAUTION!*
-Never run a Linux command unless you know what it does.
-Take care if a command has a -f command as an option, it could mean by force.
-Never run any of the following commands unless you know what you're doing:
`rm -rf /` or `rm -rf /*` -> Deletes everything on your system, including Windows and Linux files.
`:(){:|:&};:` (aka Fork Bomb) -> Keeps executing a function that calls itself until the system crashes.
`command > /dev/sda` -> Data loss on the specified block.
`mkfs.ext3 /dev/sda` -> Formats the specified block to ext3, don't do so unless intended.


# Basic Useful Utilities
* **`cat`** Reads the content of a file. __*Example*__:`cat file.txt`
* **`grep`** Searches for a string or pattern inside a file. __*Example:*__ `grep "flag" file.txt`
* **`head/tail`** Display the first/last 10 lines of a file. __*Example:*__ `head file.txt / tail file.txt`
* **`tr`** Replaces occurrences of a character with another. __*Example:*__ `cat file.txt | tr 'a' 'b'`

### IO redirection
* **`|`** Pipes the output of one command to the input of another. __*Example:*__  `cat file.txt | grep 'a'`
* **`>`** Redirects the output of a command to a file. __*Example:*__ `grep "error" log.txt > err.txt`
* **`>>`** Apprends the output of a command to a file. __*Example:*__ `grep "error" log2.txt >> err.txt`

# **Bash Scripting**
**_1. Input and Output_**
Input, output, and passing arguments to shell scripts.
**_2. Variables_**
Using variables such as integers and strings to store data.
**_3. Arithmetic_**
Mathematical operations.
**_4. Conditionals_**
Flow Control.
**_5. Loops_**
Repeating the executions of commands.
**_6. Functions_**
Organising your script by dividing it into blocks.

# **How to begin writing a shell script?**
1. Create the file. `touch scriptname.sh`
2. Give execute permissions. `chmod +x scriptname.sh`
3. Run the script. `./scriptname.sh`
4. Pass args if needed. `./scriptname arg1 arg2`

* Scripts are a series of commands running after each other.
* The shell reads the script line by line and executes the commands immediately.
  * Don't put 2 commands in the same line, if you do so then make sure to put a semicolon between them. Example: `read x; echo $x`
* You can start running any text editor and creating a text file (any extension works but lets make it .sh to make things clean).
* Usually, when files are made they dont have execution permissions. Give your file the permission by running the following command: `chmod +x SCRIPTNAME.sh`
* After youve written the script, you can run it by running: `./SCRIPTNAME.sh`
* To pass arguments to the script: `./SCRIPTNAME.sh argument1 argument2`

# **Input and Output in Bash**
### Input
* Input is referred to as STDIN.
* You can pass arguments to a bash script as input.
* To prompt input to the user, you use the command: `read` which is roughly equivalent to `scanf()` in C or `input()` in Python.
### Output
* Output is referred to as STDOUT.
* To print output to the user, you use the command: `echo` which is roughly equivalent to `printf()` in C or `print()` in Python.

# **Variables in Bash**
* Variables in bash hold values, which could be a number, a character, or a string of characters.
* Variables names are case-sensitive and cant start with a number, but can start with an underscore.
* To assign a value to a variable:
  * `varname=text with spaces`
  * `varname=text with spaces without any processing`
  * `varname=textwithoutspaces`
  * `varname=20`
* BASH does NOT support floating point integers natively.
* You can also use \ as an escape character to prevent certain characters from being processed by the shell such as the space character:
  * `x=text with spaces` -> value of x = text
  * `x=text\ with\ spaces` -> value of x = text with spaces
* `varname` -> refers to the variable.
* `$varname` -> refers to the value of the variable.

# **The Difference between   and  **
* " " -> Interprets whats inside it, including any expressions, variables, etc..
* ' ' -> Interprets whats inside it literally, without calculating or expanding expressions.
**EXAMPLE**
x=2                 
`echo "$x"`  output->  **2**
`echo $x ` output-> **2**
`echo x`  output -> **x**
`echo 'x'` output-> **x**
`echo '$x'` output-> **$x**
# **Using Passed Arguments**
* You can pass arguments to the script by running: `./SCRIPTNAME.sh argument1 argument2`
**To use these arguments as variables, you can access their values by using $X where is the order of the argument.**
_EXAMPLE:_ `./script1.sh 452 SHELL_SCRIPTING`
# **Environment Variables**
* Global system variables accessible by all the processes running under the operating system.
* Environment variables are useful to store system-wide values such as the directories to search for the executable programs (PATH).

**Variables include:**
* `BASH_VERSION` Bash version.
* `HOST_NAME` Host name.
* `HOME` Home directory.
* `PATH` Executable locations.
* `TERM` Default terminal.
* `SHELL` Default shell.
* `EDITOR` Default text editor.

**`printenv` will show you all of the environment variables on your system.**
**`echo $VAR_NAME` prints the value of the specified variable**
# **Arithmetic in Bash**
* **You can do 6 basic arithmetic operators in Bash:**
  * `a + b` addition (a plus b)
  * `a - b` subtracting (a minus b)
  * `a * b` multiplication (a times b)
  * `a / b` integer division (a divided by b)
  * `a % b` modulo (the integer remainder of a divided by b)
  * `a ** b` exponentiation (a to the power of b)
* **Arithmetics can be done using the expression: $((expression))**
  * Example: `a=$((5 - 3 + $b))`
  * Which means: variable `a` is equal `=` to the value of `$()` the expression `(5 - 3 + $b)`









