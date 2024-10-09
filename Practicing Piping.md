# Practicing Piping
Teaches input and output redirection.  

## Redirecting Output
You have to write the word PWN to the filename COLLEGE.  
The command: `echo PWN > COLLEGE`.  

flag: `pwn.college{gts9rpUMF25KcVcR8nnshb3JdTZ.dRjN1QDL4ATO0czW}`

## Redirecting More Output
You have to write the output of `/challenge/run` in file `myflag`.  
The comand: `/challenge/run > myflag`  
Now `cat` can be used to output the contennt og myflag.  

flag: `pwn.college{YyC-OxQcomN3NCiEOFFv8FSpuMZ.dVjN1QDL4ATO0czW}`

## Appending Output
The output of /challenge/run has to be appended to the file /home/hacker/the-flag.  
Use the command: ` /challenge/run >> /home/hacker/the-flag`  
Now you can use `cat ./the-flag` to output the contents of the file.  
This will give you the flag.  

flag: `pwn.college{ACG21MomY_YqVAgpfmcpLbhyybL.ddDM5QDL4ATO0czW}`

## Redirecting Errors 
You have to redirect the output of /challenge/run to /myflag and the errors of /myflag to instructions.  
You can use `2` to redirect the /myflag errors to instructions.  
The command is: `/challenge/run > myflag 2> instructions`  
Now, use `cat myflag`, which reads out the flag.  

flag: ` pwn.college{0eBD95YCOv2CNzDmLZWb9n-l6eB.ddjN1QDL4ATO0czW}`

## Redirecting Input
First, redirect `COLLEGE` to `PWN`.  
Now, redirect `PWN` to `/challenge/run` as the input.  
```
echo COLLEGE>PWN
/challenge/run<PWN
```

flag: `pwn.college{cHY1JnAoPAm-nRr4a77bwB3LGgB.dBzN1QDL4ATO0czW}`

## Grepping Stored Results
First, use `/challenge/run > /tmp/data.txt` to redirect output to `/tmp/data.txt`.  
Now, you can grep for files with pwn.college since the flag always starts with that.  
The command:  `grep pwn.college /tmp/data.txt`  
flag: `pwn.college{wWwi493jRpR4JnIVZ-u7_7-J6yC.dhTM4QDL4ATO0czW}` 


## Grepping Live Output
Instead of storing the result of `/challenge/run` to a file, and then grepping for the flag, you can use `|` to connect (pipe) the output of the command on the left to the input of the command on the right.  
Thus, the command is: `/challenge/run | grep pwn.college`  
Which gives the flag.  
flag: `pwn.college{Aq0GKkGgMKE8lpRHvkMzjuDGcuS.dlTM4QDL4ATO0czW}`  

## Grepping Errors
You havr to `grep` to find errors in this challenge. The structure of the commands will remain the same. Redirect the error to a file, pipe the output of this file to the input of the command to the right of `|`.  
The command: `/challenge/run 2>& 1 | grep pwn.college`

flag: `pwn.college{gTUlDtd1zg6L3Y72QrNnCkgGWcW.dVDM5QDL4ATO0czW}`

## Duplicating Piped Data with Tee
The `tee` command reads standard input, then writes the output of a program to standard output and simultaneously copies it into the specified file.  
Since `/challenge/pwn` cannot be directly piped to `challenge/college`, write `/pwn` to some arbitrary file using tee. 
`/challenge/pwn | tee something | /challenge/college`  
This gives the output:  
```
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
output of 'pwn' and figure out what the code needs to be.
```
So the output isn't being piped into `/challenge/college` because the input doesn't contain the correct secret code.  But you can `cat` the content of `something` to see what `pwn` contains.  
`cat something` gives:  
```
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "UrasQSM7"
```
So the command is: `/challenge/pwn --secret UrasQSM7 | /challenge/college`
Which gives the flag.

flag: `pwn.college{UrasQSM7fplbg8XYp42t6hEaAoV.dFjM5QDL4ATO0czW}`

## Writing to Multiple Programs
The output of `/challenge/hack` has to be written to `/challenge/the` and `/challenge/planet`.  
To let tee pipe to two commands, `/challenge/the` can be substituted with `>(/challenge/the)` which functions like a temporary file that that has `/challenge/the`'s input.  
So you can pipe to two commands. The command is: 
`/challenge/hack | tee >(/challenge/the) | /challenge/planet`  
Which gives the flag.  

flag: `pwn.college{IQOJG8S9b2psur58jowk9CZiNLO.dBDO0UDL4ATO0czW}`  

## Split-piping stderr and stdout  
It initially seemed to me that you could first pipe hack's output to `/challenge/planet` using `/challenge/hack | /challenge/planet` and then use `2>&1` to redirect to stder.   
However, running `/challenge/hack | /challenge/planet` gives:   
`You must redirect my standard error into '/challenge/the'!`   
So stderr must be redirected first. But doing this redirection first seperately brings up the issue of mixing stdout and stderr- as mentioned in the challenge description.   

So to prevent this, I can redirect the error (using 2>) to a file. Specifically, the temporary file for `/challenge/the`, which is `>(/challenge/the)`.   

In this case, stderr never interacts with stdout so there's no mixing.  
Now, this is like the previous problem where you have to pipe to two commands. So the final command will look like:   
`/challenge/hack 2> >(/challenge/the) | /challenge/planet`  

Which gives the flag.  
flag: `pwn.college{MS4oPGXXeynEvW0mgBVJ9Ombbsq.dFDNwYDL4ATO0czW}`  



