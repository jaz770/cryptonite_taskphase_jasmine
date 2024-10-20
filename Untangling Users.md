# Untangling Users

## Becoming root with su
First, use `su` to switch to the root user.  
This will prompt the user for a password, which in this cause is `hack-the-planet`.  
Entering it will give: `root@users~becoming-root-with-su:/home/hacker#`  
Now enter: `cat /flag`  
This gives the flag.
flag: `pwn.college{4N5bdFPcgNSy1Fo4o1jpU8Usa8t.dVTN0UDL4ATO0czW}`

## Other Users with su  
`su` can also be used to switch to a particular user instead of root. For this, that username must be passed as an argument to `su`.  
Here, we have to switch to `zardus`.  
Enter `su zardus`  
This will give a password prompt. Enter `dont-hack-me`.  
Now you can run `/challenge/run`, which gives the flag.  
flag: `pwn.college{Y45E1tmD2dIqiGmlzEoidgF7ufT.dZTN0UDL4ATO0czW}`

## Cracking Passwords
First enter `john /challenge/shadow-leak`  
This will create the directory `john` and run `/challenge/shadow-leak` from there.  
```
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04887g/s 284.6p/s 284.6c/s 284.6C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
```
The password is: `aardvark`.  
Now enter `su zardus`. When asked for the password, enter `aardvark`.  
Now you can run `/challenge/run` as zardus, which gives the flag.  

flag: `pwn.college{4TQSs58pP-NTBK5oqI5Q-lvmoUB.ddTN0UDL4ATO0czW}`

## Using sudo
