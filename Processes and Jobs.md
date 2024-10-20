# Processes and Jobs

## Listing Processes
In this challenge, /challenge/run has been renamed to some random file (it's still within the /challenge directory so it's like /challenge/some_name).
`ls` can't be used to display everything in the /challenge directory, but since the program is running, it will show up in currently running processes. 
So the `ps` command can be used.
The commands: 
```
hacker@processes~listing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 15:23 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 15:23 ?        00:00:00 /run/dojo/bin/sleep 6h
root          68       1  0 15:23 ?        00:00:00 /challenge/13337-run-149
root          72      68  0 15:23 ?        00:00:00 sleep 6h
hacker        73       0  0 15:23 pts/0    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker        90      73  0 15:24 pts/0    00:00:00 ps -ef
hacker@processes~listing-processes:~$ /challenge/13337-run-149
Yahaha, you found me! Here is your flag:
pwn.college{wwl4b5hODlR8uAxplBvePtJVr2H.dhzM4QDL4ATO0czW}
```
`ps -ef` displays every process' full format output. One of these is: `root          68       1  0 15:23 ?        00:00:00 /challenge/13337-run-149`, which is the only process under the/challenge directory.  
`/challenge/13337-run-149` can directly be run and gives the flag.  

The above can also be done suing `ps -aux`.

flag: `pwn.college{wwl4b5hODlR8uAxplBvePtJVr2H.dhzM4QDL4ATO0czW}`

## Killing Processes
The `kill` command followed by the process id is used to terminate a process.  
In this challenge, `/challenge/dont_run` must be terminated before `/challenge/run` can be executed to give the flag.  
Use `ps -aux` ( or `ps -ef`)to see all processes.  
```
hacker@processes~killing-processes:~$ ps -aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0   1056   640 ?        Ss   15:46   0:00 /sbin/docker-init -- /nix/var/nix/pro
root           7  0.0  0.0   5052  2560 ?        S    15:46   0:00 /run/dojo/bin/sleep 6h
root          71  0.0  0.0   4732  3200 ?        S    15:46   0:00 su -c /challenge/.launcher hacker
hacker        73  0.0  0.0   4976  3200 ?        Ss   15:46   0:00 /challenge/dont_run
hacker        74  0.0  0.0   5052  2560 ?        S    15:46   0:00 sleep 6h
hacker        75  0.0  0.0   5240  3840 pts/0    Ss   15:46   0:00 /run/dojo/bin/ssh-entrypoint
hacker        97  0.0  0.0   7868  3200 pts/0    R+   15:47   0:00 ps -aux
```
The id for /challenge/dont_run is: 73.  
The next commands are: 
```
kill 73
/challenge/run
```
Which gives:
```
Great job! Here is your payment:
pwn.college{A-fDBXaN3LhPYs_-s1hYzdIVuA_.dJDN4QDL4ATO0czW}
```

>[!NOTE]
>If ps -ef is run after this, it can be seen that /challenge/dont_run is not one of the running processes:
```
hacker@processes~killing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 15:46 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/b
root           7       1  0 15:46 ?        00:00:00 /run/dojo/bin/sleep 6h
hacker        74       1  0 15:46 ?        00:00:00 sleep 6h
hacker        75       0  0 15:46 pts/0    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker       103      75  0 15:57 pts/0    00:00:00 ps -ef
```


flag: `pwn.college{A-fDBXaN3LhPYs_-s1hYzdIVuA_.dJDN4QDL4ATO0czW}`

## Interrupting Processes
In this challenge, you won't get the flag till `/challenge/run` is interrupted.  
First, run `/challenge/run` and then interrupt it using the Ctrl+C command.  
```
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{0fGnwC4ga4z2O6h_fYFYKpudZln.dNDN4QDL4ATO0czW}
```
flag: `pwn.college{0fGnwC4ga4z2O6h_fYFYKpudZln.dNDN4QDL4ATO0czW}`  

## Suspending Processes

First run `/challenge/run`. The followng message appears:
```
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          82      65  0 03:56 pts/0    00:00:00 bash /challenge/run
root          84      82  0 03:56 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can
background me with Ctrl-Z or, if you're not ready to do that for whatever
reason, just hit Enter and I'll exit!
```
Enter Ctrl+Z: `^Z`  
Then enter `/challenge/run` again. This will give the flag.  

flag: `pwn.college{k5ChZvLS6gjgLe-oPPyWIy3hg38.dVDN4QDL4ATO0czW}`

## Resuming Processes
The `fg` command is sued to resume a suspended proceess. In this challenge, /challenge/run has to be resumed to get the flag. The commands are:
```
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{cH5D2Yv6QTcnsc9H6JtJnuam0IJ.dZDN4QDL4ATO0czW}
```

`flag: pwn.college{cH5D2Yv6QTcnsc9H6JtJnuam0IJ.dZDN4QDL4ATO0czW}`
