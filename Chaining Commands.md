# Chaining Commands 

## Chaining with Semicolons
In this challenge, /challenge/pwn and /challenge/college have to be chained.
The command is: `/challenge/pwn; /challenge/college`  

flag:`pwn.college{QTw7Xpcr_m-NihAaHOWzIpiX_pY.dVTN4QDL4ATO0czW}`

## Your First Shell Script  
In this challenge, `/challenge/pwn` and `/challenge/college` must chained and executed through a file.  
To be able to write to the file, use the `nano` during file creation. This will transfer you to nano, which is a file editor.  
The command: `nano x.sh`  
Now enter the commands you want to execute: `/challenge/pwn; /challenge/college`  
Now save the file as x.sh and return to the shell.  
Now enter: `bash x.sh`. This gives the flag. 

flag: `pwn.college{cj1-wCYD1qvFYTjcvJg8lmqleRU.dFzN4QDL4ATO0czW}`

## Redirecting Script Output 
In this challenge, /challenge/pwn and /challenge/college must be executed as a single command.  
This can be done with piping the output of x.sh( which contains the previous two commands) into /challenge/solve.  
The command: `bash x.sh | /challenge/solve`  
This gives the flag.  
>[!NOTE]
>/challenge/pwn; /challenge/college is already written to x.sh from the previous challenge.

flag: `pwn.college{Y7ctkatC5SNKzbNtYwg982kSpV2.dhTM5QDL4ATO0czW}`

## Executable Shell Scripts  
In this challenge, /challenge/solve has to be executed from a script, **without** using bash.  
Create a file, say `a.sh` using `nano a.sh`.  
Enter /challenge/solve in the file and save it.  
Now, change file permission to make a.sh executable usinh `chmod +x a.sh`  
The file can now be executed with the absolute or relative path: 

`./a.sh`  
This gives the flag.
flag: `pwn.college{4mK3VvUBAdf7WB81mJKfQeZHrld.dRzNyUDL4ATO0czW}`
