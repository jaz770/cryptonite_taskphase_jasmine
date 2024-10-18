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
>I've used sh to invoke another shell in the process, but this isn't necessary. Since the variable declaration is local to that particular shell process, /challenge/run will not inherit COLLEGE and directly invoking /challenge/run after declaring COLLEGE will give the flag.
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

## Printing Exported Variables
The `env` command is used to print out **all** exported ariables set in the shell. 
The variable name and its content are printed.  
In this challenge, the FLAG variable is one of the variables exported to the current shell.  
Enter `env` to print all the exported variables. This gives:  
```
 env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
DOJO_AUTH_TOKEN=2a549887d4b4aeaa1b9c67a410b4d71bd966464df59fd938c7c617912663ba06
HOME=/home/hacker
LANG=C.UTF-8
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=00:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.7z=01;31:*.ace=01;31:*.alz=01;31:*.apk=01;31:*.arc=01;31:*.arj=01;31:*.bz=01;31:*.bz2=01;31:*.cab=01;31:*.cpio=01;31:*.crate=01;31:*.deb=01;31:*.drpm=01;31:*.dwm=01;31:*.dz=01;31:*.ear=01;31:*.egg=01;31:*.esd=01;31:*.gz=01;31:*.jar=01;31:*.lha=01;31:*.lrz=01;31:*.lz=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.lzo=01;31:*.pyz=01;31:*.rar=01;31:*.rpm=01;31:*.rz=01;31:*.sar=01;31:*.swm=01;31:*.t7z=01;31:*.tar=01;31:*.taz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tgz=01;31:*.tlz=01;31:*.txz=01;31:*.tz=01;31:*.tzo=01;31:*.tzst=01;31:*.udeb=01;31:*.war=01;31:*.whl=01;31:*.wim=01;31:*.xz=01;31:*.z=01;31:*.zip=01;31:*.zoo=01;31:*.zst=01;31:*.avif=01;35:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.webp=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:*~=00;90:*#=00;90:*.bak=00;90:*.crdownload=00;90:*.dpkg-dist=00;90:*.dpkg-new=00;90:*.dpkg-old=00;90:*.dpkg-tmp=00;90:*.old=00;90:*.orig=00;90:*.part=00;90:*.rej=00;90:*.rpmnew=00;90:*.rpmorig=00;90:*.rpmsave=00;90:*.swp=00;90:*.tmp=00;90:*.ucf-dist=00;90:*.ucf-new=00;90:*.ucf-old=00;90:
FLAG=pwn.college{00LJ_qCv5WYBAhokNsaj7E39sUL.dhTN1QDL4ATO0czW}
LESSCLOSE=/usr/bin/lesspipe %s %s
TERM=xterm
LESSOPEN=| /usr/bin/lesspipe %s
SHLVL=1
LC_CTYPE=C.UTF-8
PATH=/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
_=/run/workspace/bin/env
```
A variable named `FLAG` has the flag as its value:  
`FLAG=pwn.college{00LJ_qCv5WYBAhokNsaj7E39sUL.dhTN1QDL4ATO0czW}`

flag: `pwn.college{00LJ_qCv5WYBAhokNsaj7E39sUL.dhTN1QDL4ATO0czW}`

## Storing Command Output
The output of /challenge/run has to be stored in a variable named PWN.  
The value stored in PWN is the flag.  
The command is:  `PWN=$(/challenge/run)`  
In this, the output of challenge run (obtained through $) is assigned to PWN (using =).  
After this `echo $PWN` is used, which gives the value in PWN, which is the flag.  


flag: `pwn.college{QJpn5kCMpAqfGaR12rsUzorGFZd.dVzN0UDL4ATO0czW}`

## Reading Input
In this challenge, PWN has to be assigned the value COLLEGE, but using the `read` command. This lets the user enter input.  
The commands are:
```
read -p "Enter value of PWN:"  PWN
Enter value of PWN:COLLEGE
```
The `-p` argument to `read` lets you specify a prompt that will appear when expecting input. In the above commands, `Enter the value of PWN` appears as the input from the user is expected.  
This helps clearly demarcate input and output.

The above commands give the output: 
```
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{wgmzc-mdO2hnZkRKerRVlG7YDHp.dhzN1QDL4ATO0czW}
```
flag: `pwn.college{wgmzc-mdO2hnZkRKerRVlG7YDHp.dhzN1QDL4ATO0czW}`

## Reading Files
In this challenge, `/challenge/read_me` has to be read into the PWN variable.  
The output of `/challenge/read_me` can be redirected to standard input using `<`.   
The `read` command takes the output of `challenge/read_me` as the input to be assigned to PWN.  
The command:  `read PWN < /challenge/read_me`  
>[!NOTE]
> `<` redirects the contents of the arguement to standard input (stdin).
>Since the `read` command reads from standard input, it can read the value redirected to standard input at assign it to the respective variable.


flag: `pwn.college{QZk4yOf6jxvBcrDmJAf9q668xT_.dBjM4QDL4ATO0czW}`
