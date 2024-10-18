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

flag: `pwn.college{wwl4b5hODlR8uAxplBvePtJVr2H.dhzM4QDL4ATO0czW}`
