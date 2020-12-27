## BASH

- Bourne Again SHell, or “bash” for short is one of the most widely used shells, and its syntax is similar to what you will see in many other shells.
 
 Your prompt might look like the following:
 
 ```
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
