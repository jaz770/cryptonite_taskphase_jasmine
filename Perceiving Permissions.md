# Percievingg Permissions

## Changing File Ownership
This challenge introduces `chown`, which is used to change the owner of a file.   
Use the `/chown` command to change the owner of the the file- `/flag` to hacker so its contents can be catted.  
The commands: 
```
chown hacker /flag
cat /flag
```
flag: `pwn.college{cu3a2csdZds3n7Mk2YRdLP7HzsO.dFTM2QDL4ATO0czW}`

## Groups and Files
The /flag file is accessible to the group that owns it. So, the group that owns /flag must be changed to hacker.  
This can be done with the `chgrp` command:  `chgrp hacker /flag`  
THen `cat /flag` can be used.  


flag: `pwn.college{MXOj-_AIeQf6jhLpvbsgfbBXVuQ.dFzNyUDL4ATO0czW}`

## Fun with Group Names
In this challenge, the group name is randomized.  `id` can be used to see which groups `hacker` (the user we are), is a part of.  
The output is: `uid=1000(hacker) gid=1000(grp32296) groups=1000(grp32296)`  
So the chgrp command will look like: `chgrp grp32296 /flag`.  
Then `cat /flag` can be used as usual.  


flag: `pwn.college{EZVQyk7KReQw9iG3_nTpBuv1BKc.dJzNyUDL4ATO0czW}`

## Changing Permissions 
In this challenge, only root can read /flag. So, permissions have to be changed so other users can also read it. Since `r` is used for granting permission to read a file, the command is:  
`chmod o+r /flag`.  
After this, `cat /flag` can be used.  

flag: `pwn.college{8hojwBdVHDD-LQDslFc0KcX6Is6.dNzNyUDL4ATO0czW}`


## Executable Files
