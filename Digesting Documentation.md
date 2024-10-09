# Digesting Documentation

## Learning From Documentation
You have to run `challenge/challenge` to get the flag. But just entering the command won't work since it needs an argument passed to it.  
The documentation in the descroption says that the argument `--giveflag` should be used with `challenge/challenge`.  
Enter ` /challenge/challenge --giveflag`.  
This will give the flag.  

flag: `pwn.college{Abj-u96wZ6Ram6RjYiZ0gRIdmjU.dRjM5QDL4ATO0czW}`

## Learning Complex Usage
`challenge/challenge` uses the `--printfile` argument to print to the terminal.   
So, to get the flag, enter: `/challenge/challenge --printfile /flag`  

flag: `pwn.college{86g3cnJPiTgwzIEtIops9v03hVn.dVjM5QDL4ATO0czW}`

## Reading Manuals
First, use the `man` command to read the manual of `challenge`.  
The manual says that the argument `--zefxkv NUM` to `challenge/challenge` prints the flag if the NUM value is 085.  
The manual:  
```
CHALLENGE(1)                              Challenge Commands                             CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --zefxkv NUM
              print the flag if NUM is 085

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                                    May 2024                                  CHALLENGE(1)
```
Enter ` /challenge/challenge --zefxkv 085` to get the flag.  

flag: `pwn.college{ENzKefQx0kQJv8Anpr5pNB3MxE1.dRTM4QDL4ATO0czW}`

## Searching Manuals
Use `man challenge` to read the manual.   
Search for flag using `/flag`. Use the `n` command to keep viewing the next command till the right one comes up.  
A message saying :`--dxwp This argument will give you the flag` is seen.  
Use `q` to return to the home directoey prompt.  
Enter: `/challenge/challenge --dxwp` to get the flag.  

flag: `pwn.college{YGzLn2uVDp1Ji8SwfMjc_seJJ5a.dVTM4QDL4ATO0czW}`


## Searching for Manuals
Use `man man` to read the manual for man.  
Keep entereing to read the commands that man contains. `The man -k printf` program is one of the commands. It says:  
```
man -k printf
           Search the short descriptions and manual page names for the keyword printf as regular  ex‐
           pression.  Print out any matches.  Equivalent to apropos printf.
```
This can be used to find manual page named for flag.  
Enter `man -k flag`.  
There's a command `azjuvwtdls (1)       - print the flag!`.  
Use `man azjuvwtdls`.  
It shows:   
```
--azjuvw NUM
              print the flag if NUM is 533
```
Use `/challenge/challenge --azjuvw 533` to get the flag.  

flag: `pwn.college{AaIzjK5TLSuYY3vwtdlsKzPU3QO.dZTM4QDL4ATO0czW}`

## Helpful Programs
Use `/challenge/challenge --help`.   
```
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
```
Enter: `/challenge/challenge -p`.  
`The secret value is: 335` is the output.  
Enter: `/challenge/challenge -g 335`.  
This gives the flag.  

flag: `pwn.college{E3QmdbyfKfkykmZ3h59e7IrNAir.ddjM4QDL4ATO0czW}`

## Help for Builtins
Enter `help challenge` to read the guide.  
```
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "A2UFiaNL".
```
The `--secret VALUE` command has to be used.  
Enter: `challenge --secret A2UFiaNL`.   
This gives the flag.


flag: `pwn.college{A2UFiaNLLeKo-4DbHcaSTMSK5Rf.dRTM5QDL4ATO0czW}`

