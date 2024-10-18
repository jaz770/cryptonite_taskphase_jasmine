# Comprehending Commands
This module teaches linux commands.

## cat: not the pet, but the command!
The `cat` command reads out files. It can take multiple arguments and will concatenate the corresponding files in that order.  
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

## touching files
the `touch` command creates a new file with the name of the argument given to it.  
Here, you have to create two files `/tmp/pwn` and `/tmp/college` before using `/challenge/run`.  
Thus, the code will be:   
```
touch /tmp/pwn
touch /tmp/college
/challenge/run
```

flag: `pwn.college{kvUEgWLLfFBuEXdvY9Xa2S7z4tC.dBzM4QDL4ATO0czW}`

## removing files
the `rm` command deletes the file given to it as the argument.  
Here, a delete_me file is created in the home directory.  
Use `rm delete_me` to remove it.  
Then enter `/challenge/check` which will check if the file has been deleted. If it has, you will get the flag.  

flag: `pwn.college{oHGlm698TA1l7Nq3O6ysHo6kqyU.dZTOwUDL4ATO0czW}`

## hidden files
The flag is in some file starting with a `.` in the root directory. 
First, change to the root directry, display the files, including those starting with a `.` and `cat` its contents out.  
The code:
```
cd /
ls -a
cat .flag-90526901540
```
(Note: The directory contains a file named  .flag-90526901540. That's the flag file)  

  
flag: `pwn.college{0mQm2L9KwoHFGZ1aLoitu4SkKNd.dBTN4QDL4ATO0czW}`

## An Epic Filesystem Quest
In the challenge, the previously learned commands are all used to find the flag.  

Start by changing to the root directory with, `cd /`  
Use `ls` to display the contents.   
There's a `NOTE` file. `cat ` its contents out.  
It says the next clue is in: ` /usr/lib/ruby/2.7.0/rdoc`  

Use `cs  /usr/lib/ruby/2.7.0/rdoc` to enter the directory. Use `ls` to displaay the file list again.  
There's a file named ALERT. `cat` its contents out. It says that the next clue is in `/usr/lib/python3/dist-packages/jedi/third_party/typeshed/stdlib/2and3/xml/sax`  

`cd` to `/usr/lib/python3/dist-packages/jedi/third_party/typeshed/stdlib/2and3/xml/sax`.  
Display the contents with `ls` 
There's a file named INFO that seems similoar to the previous clue files. `cat` its content.  
It says: 
```
Great sleuthing!
The next clue is in: /opt/linux/linux-5.4/include/config/rfkill

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
```

Since you can't use cd, give the absolute path to the `ls` command. 
` ls /opt/linux/linux-5.4/include/config/rfkill`  
There's a file named LEAD-TRAPPED. You can use the absolute path to this file with cat to display the conents without having to change directories now.   
use: `cat  /opt/linux/linux-5.4/include/config/rfkill/LEAD-TRAPPED`     
It says: 
```
The next clue is in: /usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/Gyre-Termes/Size6

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
```

Use `cd /usr/share/javascript/mathjax/jax/output/HTML-CSS/fonts/Gyre-Termes/Size6`.  
Use `ls` to display its files. There's two files, `BLUEPRINT` and `Regular`. BLUEPRINT is similar to the previous clue files so we'll `cat` it.   
`cat BLUEPRINT` gives:   
```
Tubular find!
The next clue is in: /opt/busybox/busybox-1.33.2/examples/var_service/ftpd

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
```


Use `cd /opt/busybox/busybox-1.33.2/examples/var_service/ftpd` to enter the directory.  
Use `ls`.  There's a `BRIEF` file. Using `cat BRIEF` gives:  
```
Lucky listing!
The next clue is in: /opt/linux/linux-5.4/drivers/net/ethernet/intel/e1000e

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
```

  
Do the same as earlier. Use `ls /opt/linux/linux-5.4/drivers/net/ethernet/intel/e1000e` to display the file list.  
There's a `SNIPPET TRAPPED` file. `cat` it using the absolute path: `cat /opt/linux/linux-5.4/drivers/net/ethernet/intel/e1000e/SNIPPET-TRAPPED`  
It says: 
```
Lucky listing!
The next clue is in: /opt/angr-management/_internal/jedi/third_party/typeshed/third_party/2and3/dateutil/tz
```
Use ` cd  /opt/angr-management/_internal/jedi/third_party/typeshed/third_party/2and3/dateutil/tz` and then use `ls.`  
There's a file named `TEASER`.  Do `cat TEASER`.   
It says: 
```
Congratulations, you found the clue!
The next clue is in: /usr/lib/python3/dist-packages/constantly-15.1.0.egg-info

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to '
```

Use `cd /usr/lib/python3/dist-packages/constantly-15.1.0.egg-info`  
Then use `ls -a`. Since the filename starts with a `.`, the regular `ls` command won't list it.  
The files are: `.  ..  .MEMO  PKG-INFO  dependency_links.txt  pbr.json  top_level.txt`  
Use `cat .MEMO`  
This gives:  
```
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{0jDfy-DqUwG2Z23QXOxWfDYabEb.dljM4QDL4ATO0czW}
```
Which contains the flag.  

  


flag: `pwn.college{0jDfy-DqUwG2Z23QXOxWfDYabEb.dljM4QDL4ATO0czW}`


## making directories
First, create a /tmp/pwn directory
Use `mkdir /tmp/pwn` to make the directory.  
Now, the college file has to be created in the `/tmp/pwn` directory.  
So `cd` to `/tmp/pwn`.   
Now use the command `touch college` to create the file.  
Enter `challenge/run` which will check if the college file exists. If it does, it will give the flag.  

  
flag: `pwn.college{gZ60JMC-MoRvPfdrp0hKmEAr2JY.dFzM4QDL4ATO0czW}`

## finding files
You have to use the `find` command to locate the flag. Since it's located in a file named `flag`, the command will be:  
`find / -name flag`  
THe output is like this: 
```
find: ‘/tmp/tmp.MiOQGWw5Zc’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
/usr/local/lib/python3.8/dist-packages/sympy/simplify/tests/flag
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
/usr/local/share/radare2/5.9.5/flag
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/root’: Permission denied
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
/opt/radare2/libr/flag
find: ‘/proc/tty/driver’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
```
The flag is not in any file that's inaccessible. So try using `cat` on the available paths.  

`cat /nix/store/pmvk2bk4p550w182rjfm529kfqddnvh3-python3.11-pwntools-4.12.0/lib/python3.11/site-packages/pwnlib/flag` shows:  
`cat: /nix/store/1yagn5s8sf7kcs2hkccgf8d0wxlrv5sz-radare2-5.9.0/share/radare2/5.9.0/flag: Is a directory`

Since only a few files are accessible, you can `cat` the contents of each till the flag is reached.

`cat  /usr/local/lib/python3.8/dist-packages/sympy/simplify/tests/flag` gives:  
`pwn.college{Mj4K43s4AIwBaAZN0UmHaK4MpwY.dJzM4QDL4ATO0czW}hacker@commands~finding-files:~$`  
Which is the flag.  

flag: `pwn.college{Mj4K43s4AIwBaAZN0UmHaK4MpwY.dJzM4QDL4ATO0czW}`

## linking files
`/challenge/catflag` gives the output `not-the-flag: no such file or directory`.  
So if `not-the-flag` is linked to the /flag file, it will have content that it can display and will not give the `no such file or directory` message.  
Link `not-the-flag to` `/flag`.  
```
ln -s /flag not-the-flag
```

`/challenge/catflag` will not give the flag since it can read flag's contents through `not-the-flag`.  

flag: `pwn.college{cLTZ0lE6OKu2XlB0T8iyRufx_ot.dlTM1UDL4ATO0czW}`


