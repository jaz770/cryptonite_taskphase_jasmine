# Comprehending Commands
This module teaches linux commands.

## cat: not the pet, but the command!
The `cat` command reads out files. It can take multiple arugemts and will concatenate the corresponding files in that order.  
The flag is stored in the `flag` file in the home directory.(which is where the shell starts).   
  

To display the contents of the file, the cat command needs to be used. 
Enter `cat flag` to display the flag.  
flag: `pwn.college{MpXIdSTksHxQQCDRAuxS0k4lBHe.dFzN1QDL4ATO0czW}`


## catting absolute paths
The `cat` command can also take absolute paths as arguments and read the corresponding files.  
The absolute path to the flag file here is `/flag`.  
Thus, enter `cat /flag` to get the flag.  
flag: `pwn.college{g9-1Mo20ZAtFLdvTO2Xnd2gWayW.dlTM5QDL4ATO0czW}`

## more catting practice
In this challenge, the `cd` command is unusable. So the absolute path to the flag file must be given as an argument to cat.  
The absolute path: `/usr/lib/bash/flag.`.  
Thus, the command is: `cat /usr/lib/bash/flag.` 

flag: `pwn.college{Iv5TqEc8fMT90aU3kiX3F-AkZLU.dBjM5QDL4ATO0czW}`

## grepping for a needle in a haystack
`cat` cannot output files that are too large. The`grep` command is useful in these cases, since it lets you look for specific content in the file.    

  
The flag is in the `/challenge/data.txt` file, which contains a hundred thousand lines of data.   
Outputting all its content with cat, even if possile would not let you easily find the flag.  

Use the command `grep pwn.college /challenge/data.txt`. This looks for occurences of pwn.college in the file, txt.   
Since the flag always starts with pwn.college, this will accurately output the flag. 
  
flag: `pwn.college{0teGwx3tGnwDiAhuxl_RBtJqWAe.ddTM4QDL4ATO0czW}`

## listing files
Using the `ls` command to list the files in the `/challenge` directory shows that `run` has been renamed to `8075-renamed-run-2147`.  
The commands to acces the flag are:   
```
ls /challenge 
cd challenge  
./8075-renamed-run-2147
```

Note: The above could also be done with the absolute path `/challenge/8075-renamed-run-2147`  

flag: `pwn.college{cr_HPjlVSJqP0KIUTKO6B7YBNfJ.dhjM4QDL4ATO0czW}`
