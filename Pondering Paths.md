# Pondering Paths
Teaches the basics of Linux filepaths.  
A path is the specific location or route through which a file or directory can be accessed within a file system.  
For a system, each level in the hierarchy is a directory.

## the root
Invoking the pwn program through its path gives you the flag.  
After you ssh into the the challenge screen on your terminal, enter `/pwn` to get the flag.

## program and absolute paths
In this challenge, you have to enter the absolute path of the challenge program, 'run' to get the flag.  
An absolute path makes no assumptions about your current location in relation to the location of the file or directory it's describing. It mentions every step through the file system from the root required to reach the program.  
Once in the challenge instance, enter the absolute path `/challenge/run` to get the flag.

## position elsewhere
The cd command is used to change directories.  
You have to execute `/challenge/run` to get the flag but it is not in your current working directory.  
Change directory to `/tmp` using `cd /tmp` and then enter `challenge/run` again to get the flag.

## position yet elsewhere
This is like the previous challenge. You have to be in the `/etc/apt/sources.list.d` directory.
Use the command `cd /etc/apt/sources.list.d`  
You're now in the correct directory and can enter the command, `/challenge/run` to get the flag. 

flag: `pwn.college{gcedq0necvUpbEQB3Hm1n4CppfC.dhDN1QDL4ATO0czW}`

## implicit relative paths, from /
Up until now, all flags were retirived through absolute paths, starting from /(root).  
In this challenge, a relative path is to be entered to get the flag.  First access the root directory through `/`.  
The relative path to the file is now `challenge/run`.  (`/` does not have to be entered before challenge now, since we're suing a relative path.)  
This will get the flag.

flag: `pwn.college{o6FjVkZ4TYio8VMPQOx87GeQVFC.dlDN1QDL4ATO0czW}`
