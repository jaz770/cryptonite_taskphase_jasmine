# Pondering Paths
Teaches the basics of Linux filepaths.  
A path is the specific location or route through which a file or directory can be accessed within a file system.  
For a system, each level in the hierarchy is a directory.

## the root
Invoking the pwn program through its path gives you the flag.  
After you ssh into the the challenge screen on your terminal, enter `/pwn` to get the flag.

flag: `pwn.college{cxGLDAdRudlKoiATrAVmHLQJLlM.dhzN5QDL4ATO0czW}`

## program and absolute paths
In this challenge, you have to enter the absolute path of the challenge program, 'run' to get the flag.  
An absolute path makes no assumptions about your current location in relation to the location of the file or directory it's describing. It mentions every step through the file system from the root required to reach the program.  
Once in the challenge instance, enter the absolute path `/challenge/run` to get the flag.

flag: `pwn.college{4ZtLxD46BEVg2HqrNPzZ9PHnGOE.dVDN1QDL4ATO0czW}`

## position thyself
You can navigate between different directories using the `cd` command.
You need to run `/challenge/run` but can only run it from thr `/sys` directory.
Use the command `cd /sys` to change directories.  
Now you're in the correct directory, and can enter `/challenge/run` to get the flag.

flag: `pwn.college{glG6uvQV0fQcfako3pdfBy4jyJ2.dZDN1QDL4ATO0czW}`

## position elsewhere
The cd command is used to change directories.  
You have to execute `/challenge/run` to get the flag but it is not in your current working directory.  
Change directory to `/tmp` using `cd /tmp` and then enter `challenge/run` again to get the flag.

flag: `pwn.college{gJjPqqd3emiMWvlhfnqH34lJ36m.ddDN1QDL4ATO0czW}`


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


## explicit relative paths, from /
Again, you have to execute `challenge/run` to get the flag. But unlike last time, it must be donw with `.`  

`.` refers to the current working directory , i.e., if you're currently in some directory `first/second/third`, `.` will let you specify this directory without mentioning its full path.
In this challenge, the current wroking directory is `/`(root.) 
To get the flag `'challenge/run` must be entered after root.  
The command `./challenge/run` implicitly refers to the current directory (root) and `challenge/run` after that.
This gives the flag.

flag: `pwn.college{UP5R24g9K5L0rDNo7mEB1U8S1Sn.dBTN1QDL4ATO0czW}`

## implicit relative paths
The challenge demonstrates the importance of `.` in relative path referencing.  
The challenge needs to be run from the `/challenge` directory. The `run` file is located in this directory. So, theoretically, you can just enter `run` to get the flag.  
But this will not actully work due to a safety measure linux has: it explicitly avoids looking in the current directory when you provide a 'naked' path, to avoid accidentally executing programs that have the same name in your directory.  
To run execute the challenge, you can explicitly use a relative path to launch `run`. This is done using `.` to reference the current working directory.
  
(Note: `.` implicitly referes to your current directory. But you have to _explicitly_, yourself use this _implicit_ path to specify that you are looking for files in the current directory.)  
  
Use the relative path, `./run` to get the flag.

flag: `pwn.college{wLszza5NgPKJS_LubZwNFxL1yon.dFTN1QDL4ATO0czW}`

## home sweet home
In this challenge, `/challenge/run` will write a copy of the flag to any file specified as an argument on the commandline.  
It must be an absolute path in the home directory, and before expansion, the argument must be 3 characters or less.  
Since the file is in the home directory, `~` can be used to specify it.  
Thus, the command will look similar to this: `/challenge/run ~/f`  

flag: `pwn.college{ooBnwCpzwCs3eFIiqDlCmvQi9FL.dNzM4QDL4ATO0czW}`

