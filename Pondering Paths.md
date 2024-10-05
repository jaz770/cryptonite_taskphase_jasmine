# Pondering Paths
Teaches the basics of Linux filepaths.  
A path is the specific location or route through which a file or directory can be accessed within a file system.  
For a system, each level in the hierarchy is a directory.

## The Root
Invoking the pwn program through its path gives you the flag.  
After you ssh into the the challenge screen on your terminal, enter `/pwn` to get the flag.

## Program and Absolute Paths
In this challenge, you have to enter the absolute path of the challenge program, 'run' to get the flag.  
An absolute path makes no assumptions about your current location in relation to the location of the file or directory it's describing. It mentions every step through the file system from the root required to reach the program.  
Once in the challeneg instance, enter the absolute path `/challenge/run` to get the flag.
