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

