# Shell Variables

## Printing Variables 
The value stored in the variable `FLAG` has to be printed to get the flag.   
`echo` prints what the user passes as the argument so it cannot directly print the value of a variable.   
`$` is prepended to the variable name to print the value.  
The command is: `echo $FLAG`  

flag: `pwn.college{0ouh0bdgmmOnsYxuKbQv6OC68fK.ddTN1QDL4ATO0czW}`

## Setting Variables  
In this challenge, the value `COLLEGE` must be assigned to the variable `PWN` to get the flag.  
This is done with `=`.  
>[!NOTE]
>There must be NO spaces before or after the =.

The command is: `PWN=COLLEGE`

flag: `pwn.college{swWvPphayISppgGLmKS4-aGNVrO.dlTN1QDL4ATO0czW}`

## Multi Word Variables
`" "` are used to encase variables with multiple words.   
You cannot directly set a variable with spaces in between the words because when the shell sees a space, it **ends** the variable assignment and interprets the next entry as a command that it tries to execute.  
The command is: `PWN="COLLEGE YEAH"
flag: `pwn.college{ojaAqta8WeCaV-Wh8W2kiMHlJTq.dBjN1QDL4ATO0czW}`


## Exporting Variables
Variables declared in a shell process are **local** to that shell process, i.e., other commands won't inherit them.  
For example, if a new shell is invoked within the shell, the new 'child' shell won't inherit the variables set in the previous shell.  

In this challenge, the variable named PWN (with the value COLLEGE) must be exported so a different command: `/challenge/run` can access it.   
The variable named COLLEGE (with the value PWN) must not be accessible to `/challenge/run` so it shouldn't be exported.  
The commands are: 
```
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ sh
sh-5.2$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{AVD98Ap5k2Jwg9b1FquCL7EGjCa.dJjN1QDL4ATO0czW}
```
>[!NOTE]
>I've used sh to invoke another shell in the process but this isn't necessary. Since the variable declaration is local to that particular shell process, /challenge/run will not inherit COLLEGE and directly invoking /challenge/run after declaring COLLEGE will give the flag.
>
>However, the new shell can be used to demonstrate that COLLEGE isn't inherited:

Using echo after using sh gives: 
```
hacker@variables~exporting-variables:~$ sh
sh-5.2$ echo $COLLEGE

sh-5.2$ echo $PWN
COLLEGE
```


flag: `pwn.college{AVD98Ap5k2Jwg9b1FquCL7EGjCa.dJjN1QDL4ATO0czW}`


