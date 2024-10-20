# Pondering PATH

## The PATH Variable  
First, empty the PATH variable so that `rm` can't delete the flag when /challenge/run is executed.  
Command: `PATH=""`  
Now enter: `/challenge/run`  
This gives: 
```
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
```

flag: `pwn.college{QHtL_bFC44SQUa6YgnEkoO_Dok0.dZzNwUDL4ATO0czW}` 

## Setting PATH
In this challenge, /challenge/run must be entered with its bare name, but exists in the `/challenge/more_commands` directory.   
PATH can be set to this directory through: `PATH=/challenge/more_commands`  
Now `/challenge/run` can be entered, It gives:  
```
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{czGfd-etDl_mt_UkjFwtupJ8RUm.dVzNyUDL4ATO0czW}
```


flag: `pwn.college{czGfd-etDl_mt_UkjFwtupJ8RUm.dVzNyUDL4ATO0czW}`

## Adding Commands
First, I made a directory named `mydir` to store the `win` file in.  
Then I `cd` to `mydir`.  
Once in the directory, I use `nano win.sh` to create and write to the win file (which is what/challenge/run will automatically invoke).  
In the file, I enter `cat /flag` and save it.  
To make it directly executable, I enter `chmod +x win`.  
Now, I have to append win's directory to PATH without overwriting its previous contents to preserve cat.  
To do this, I'll echo PATH using `$PATH`  
This gives: `/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin`  
`cat` is stored here.  
So I'll now set the PATH variable to: `PATH="/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/home/hacker/mydir"`.  
This essentially adds mydir to the PATH variable while preserving its previous directories.  
Now I can run `/challenge/run`.  
This invokes win and ives the flag.

flag: `pwn.college{w7plEBg22_HX5UjwT7gRF54Hevz.dZzNyUDL4ATO0czW}`

## Hijacking Commands  
This challenge, like the first one of this module, will have /challenge/run invoke `rm` which will delete the flag.  
To prevent this, `rm` can be overwritten.  
Like the previous challenge, I `cd` to `mydir` and write to rm there, using `nano rm`  
In the `rm file`, I give the commands:  
```
read ANS < /flag; echo $ANS
```
Now, I can overwrite PATH with the path of `rm`.  
`PATH=/home/hacker/mydir`  
Now `/challenge/run` can be run and will give the message:
```
Trying to remove /flag...
pwn.college{oOkqczARJcDLQPiSZUstvsQ5WDY.ddzNyUDL4ATO0czW}
```

Another way to do this challenge would've been to preserve `cat` in the PATH variable contents like I did in the last challenge. 
First I enter the follwing in the `rm` file:  
`cat /flag`  
Now, I echo the contents of PATH. 
Then, I change PATH to:  
` PATH="/home/hacker/mydir:/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"`   
>[!WARNING]
>/home/hacker/mydir must come before the original directories of PATH.
>This makes it so the rm file in mydir is checked first by rm and when it is executed, the cat /flag command runs.
>If /home/hacker/mydir were after the original dirctories of PATH, rm would delete the flag. To demonstrate:
```
PATH=/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/home/hacker/mydir
hacker@path~hijacking-commands:~/mydir$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /usr/bin/rm. Executing!
Uh oh, looks like I successfully removed the flag! That means you did not
properly set PATH to keep me from finding 'rm'. Since the flag is gone, you
will need to re-launch the challenge from the module page! Better luck next
time.
```
Thus, mydir is added first.  

Now, challenge/run can be run.
This gives:  
```
hacker@path~hijacking-commands:~/mydir$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /home/hacker/mydir/rm. Executing!
pwn.college{oOkqczARJcDLQPiSZUstvsQ5WDY.ddzNyUDL4ATO0czW}
```

flag: `pwn.college{oOkqczARJcDLQPiSZUstvsQ5WDY.ddzNyUDL4ATO0czW}`
