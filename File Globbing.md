# File Globbing
Teaches globbing.

## Matching with *
Since the `cd` command can only be 4 characters at most, use `cd /ch*`.  
This will bring you to the challenge directory.  
Now enter `./run` to get the flag.  
I've used `cd/ch*` to be as specific as psossible without exceeding the character limit.  
you can also use `cd /c*` to change to the directory. In fact, in this challenge it will automatically bring you to the challenge directory.  

flag: `pwn.college{URE_a0m2Zx-5JN-boBdi-3Uer05.dFjM4QDL4ATO0czW}`

## Matching with ?
The problem states: 
change your directory to /challenge, but use the ? character instead of c and l in the argument to cd!  
Thus, the command is:
```
cd /?ha??enge
./run
```
Which givies the flag.  

flag: `pwn.college{4sitykY6WKRdcpgHnx0XJMJZ2i7.dJjM4QDL4ATO0czW}`. 

## Matching With []
First, `use cd /challenge/files` 
Since [] treats the entered characters, each as wildcards and the [] forms the total set, we can use this to get the flag.  
The command: ` /challenge/run file_[absh]`  
Which gives the flag.

flag: `pwn.college{ESl4LGwmgLhAuBxPiB_M5TWo3DN.dNjM4QDL4ATO0czW}`

## Matching Paths With [] 
The flag is located in the /challenge/files directory this time, in either file_a, file_b, file_h, or file_s.  
The command: ` /challenge/run /challenge/files/file_[absh]`.  

flag: `pwn.college{gjUSno8xrLJXo_ax_v6jb5v-dDw.dRjM4QDL4ATO0czW}`

## Mixing Globs
First, use `cd /challenge/files`.  
Now, /challenge/run needs challenging, educational and pwning as arguments. In 6 characters or less. So c,e,p, can be put in [] and the rest can be wildcards. So our command is: 
`/challenge/run [cep]*`  
Which gives the flag.
flag: `pwn.college{8fN72MLRwl5OwKbMTGBnv_B5rG8.dVjM4QDL4ATO0czW}`

## Exclusionary Globbing
Since every file that doesn't start with p,w or n needs to be in the argument, let's exclude those.
So the command is:  
`/challenge/run [!pwn]*`  
This excludes p,w,n and treats the other characters as wildcards that _can_ be included.
flag: `pwn.college{0CZLWxqD-f6k701uzfR_xuNpeDd.dZjM4QDL4ATO0czW}`



