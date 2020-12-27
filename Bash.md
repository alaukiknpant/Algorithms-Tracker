## BASH

- Bourne Again SHell, or “bash” for short is one of the most widely used shells, and its syntax is similar to what you will see in many other shells.
 
 Your prompt might look like the following:
 
 ```shell
 missing:~$ 
 ```
 
This means that

1. You are on the machine missing
2. Your “current working directory”, or where you currently are, is ~ (short for “home”).
3. The $ tells you that you are not the root user 
4. You execute a command on the prompt

#### $PATH

- If the shell is asked to execute a command that doesn’t match one of its programming keywords, it consults an environment variable called $PATH
- $PATH - lists which directories the shell should search for programs when it is given a command

- We can find out which file is executed for a given program name using the which program

```shell
missing:~$ which echo
/bin/echo
```

- A path on the shell is a delimited list of directories; separated by / on Linux and macOS and \ on Windows
- On Linux and macOS, the path / is the “root” of the file system, under which all directories and files lie
- A path that starts with / is called an absolute path. Any other path is a relative path.
- . refers to the current directory, and .. to its parent directory

#### Permissions

```shell
missing:~$ ls -l /home
drwxr-xr-x 1 missing  users  4096 Jun 15  2019 missing
```
Lets break this down:
1. **d**rwxr-xr-x
 - First, the d at the beginning of the line tells us that missing is a directory. 

2. d __rwx__ __r-x__ __r-x__
- These indicate what permissions the owner of the file (missing) - rwx, the owning group (users) - rx, and everyone else (rx) have on the relevant item.


#### Connecting programs
- In the shell, programs have two primary “streams” associated with them: their input stream and their output stream
- Normally, a program’s input and output are both your terminal. That is, your keyboard as input and your screen as output. However, we can also rewire those streams!
- The simplest form of redirection is < file and > file. These let you rewire the input and output streams of a program to a file respectively:

```shell
missing:~$ echo hello > hello.txt
missing:~$ cat hello.txt
hello
missing:~$ cat < hello.txt
hello
missing:~$ cat < hello.txt > hello2.txt
missing:~$ cat hello2.txt
hello
```


#### Shebang 
- a shebang is the character sequence consisting of the characters number sign and exclamation mark (#!) at the beginning of a script.
- When a text file with a shebang is used as if it is an executable in a Unix-like operating system, the program loader mechanism parses the rest of the file's initial line as an interpreter directive. 
- The form of a shebang interpreter directive is as follows:
```
#!interpreter [optional-arg]
```
Some typical shebang lines:

#!/bin/sh – Execute the file using the Bourne shell, or a compatible shell, assumed to be in the /bin directory
#!/bin/bash – Execute the file using the Bash shell
#!/usr/bin/env python3 – Execute with a Python interpreter, using the program search path to find it

#### Difference between sh and bash

sh (or the Shell Command Language) is a programming language described by the POSIX standard. Bash is an extension of sh.

#### Answers to Questions

A. Create a new directory called missing under /tmp.

```shell
mkdir /tmp/missing
```

B. Create a new directory called missing under /tmp.

```shell
man touch
```

C. Use touch to create a new file called semester in missing.

```shell
cd /tmp/missing | touch semester
```

D. Write the following into that file, one line at a time:

```
#!/bin/sh
curl --head --silent https://missing.csail.mit.edu
```

```shell
echo '#!/bin/sh' > semester 
echo 'curl --head --silent https://missing.csail.mit.edu' >> semester
```

E. Try to execute the file, i.e. type the path to the script (./semester) into your shell and press enter. Understand why it doesn’t work by consulting the output of ls (hint: look at the permission bits of the file).

There is no execute right to the user (x).

F. Use chmod to make it possible to run the command ./semester rather than having to type sh semester. How does your shell know that the file is supposed to be interpreted using sh? See this page on the shebang line for more information.

```chmod +x semester```

Shell knows that the file is supposed to be interpreted using sh because the interpreter defined after the shebang (#!) is sh in /bin/sh.

G. Use | and > to write the “last modified” date output by semester into a file called last-modified.txt in your home directory.

```ls -l semester | cut -c33-46 > last-modified.txt```
