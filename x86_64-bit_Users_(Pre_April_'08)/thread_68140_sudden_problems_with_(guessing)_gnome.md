---
title: "sudden problems with (guessing) gnome"
date: 2005-09-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by kb_ganesh on 2005-09-22
i am using Ubuntu 5.04 Hoary Hedgehog on a AMD 2800+ computer..had installed it around 2 weeks ago..everything was very fine till yesterday somethings happened all of a sudden..i was generally working on my non-root account named normal which i usually use..then clicked on show desktop..it shows up but on clicking the trash bin icon it says "permission denied"..i check up the permissions tab in its properties window..and normal did have rwx rights for it..so was puzzled a bit..and decided to restart X server using ctrl+alt+backspace as sound also was giving a few problems..

now, instead of showing me the login screen, i got some error(dint have the brains to note it down)..and the screen shifts to tty1 where it shows me the textual login..i try logging in using normal and it accepts my password but finally says "cannot execute /bin/bash: permission denied"..?!? i try logging in as another non-root user and same error..try logging in as root..and good, it worked. i give the startx command and gnome starts up fine, albeit as root user..btw, i had never been able to(nor wanted to) login as root in the main login screen..guess thats some default setting in ubuntu..dint care to change it..so, now i start the terminal and give su normal and it says "no shell"..i check up permissions for /bin/bash..and it is set to allow read and execute for other users..

so, i restart the system..(i had setup gnome to log me in as normal by default without showing the login screen)..and i see that samba server doesnt start up properly, says failed(one more thing failed too..but i couldnt catch hold of what it was as the text scrolled up too quickly). this had never happened before. so this made for interesting observation..now, the time comes for gdm to start..and what happens instead is that i can see the normal brown background of ubuntu but a dialog box that says "Cannot start the session due to some internal error" with an ok button..i click that..another box comes up
```

aaYour session lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.
     View details(~/.xsession-errors file)
/etc/gdm/PreSession/Default:Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default:running /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -X "/var/lib/gdm/"0.Xservers" -h "" -l ":0" "normal"
session_child_run:Could not exec /etc/gdm/Xsession /usr/bin/gnome-session"

```
with an ok button..i click it and the screen goes black for 3 seconds before a new dialog box comes up saying this..
```
Cannot start the greeter program:you will not be able to login. This display will be disabled. Try logging in by other means and editing the configuration file

```
clicking ok here takes me back to tty1..

where is the problem? i am sure i havent edited any configuration files and stuff..and i checked out the file permissions of /etc/gdm/Xsession and /usr/bin/gnome-session too..they all have read and execute permission for others..i even tried creating a new user "try" and using su try to change to that account..again get the "No shell" error..

has anyone had this kind of problem before? hope someone can tell me how to solve this..in the meanwhile, i guess i have to log in as root..i am thinking of installing E17 too..but i would like to know where the problem lies and how it can be solved..

thanks a lot!!

---

### Post by kb_ganesh on 2005-09-23
doesnt anyone have any idea on how this can be solved?!? i dont want to be living on a root account forever..

---

### Post by mlomker on 2005-09-23
[QUOTE=kb_ganesh]doesnt anyone have any idea on how this can be solved?!? i dont want to be living on a root account forever..[/QUOTE]

My only thought is that something is wrong with your environment variables.  Does the /etc/bash.bashrc file exist?  How about the /home/username/.bashrc file for your user?

Here's the output of **set** on my box as a reference:

```

root@mlomkernote:/etc # set
BASH=/bin/bash
BASH_ARGC=()
BASH_ARGV=()
BASH_LINENO=()
BASH_SOURCE=()
BASH_VERSINFO=([0]="3" [1]="00" [2]="16" [3]="1" [4]="release" [5]="x86_64-pc-linux-gnu")
BASH_VERSION='3.00.16(1)-release'
COLORTERM=
COLUMNS=80
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-KCi2MHd7O1
DESKTOP_SESSION=kde
DIRSTACK=()
DISPLAY=:0
DM_CONTROL=/var/run/xdmctl
EUID=0
GPG_AGENT_INFO=/tmp/gpg-T8ZKsU/S.gpg-agent:6522:1
GROUPS=()
GS_LIB=/home/mlomker/.fonts
GTK2_RC_FILES=/home/mlomker/.gtkrc-2.0
GTK_IM_MODULE=scim
GTK_RC_FILES=/etc/gtk/gtkrc:/home/mlomker/.gtkrc:/home/mlomker/.kde/share/config/gtkrc
HISTFILE=/root/.bash_history
HISTFILESIZE=500
HISTSIZE=500
HOME=/root
HOSTNAME=mlomkernote
HOSTTYPE=x86_64
IFS=$' \t\n'
KDE_FULL_SESSION=true
KDE_MULTIHEAD=false
KDE_NO_IPV6=true
KONSOLE_DCOP='DCOPRef(konsole-6854,konsole)'
KONSOLE_DCOP_SESSION='DCOPRef(konsole-6854,session-1)'
LANG=en_US.UTF-8
LANGUAGE=en
LIBGL_DRIVERS_PATH=/usr/X11R6/lib64/modules/dri/:/usr/X11R6/lib/modules/dri/
LINES=24
LOGNAME=mlomker
LS_COLORS='no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.ogg=01;35:*.mp3=01;35:*.wav=01;35:'
LS_OPTIONS=--color=auto
MACHTYPE=x86_64-pc-linux-gnu
MAILCHECK=60
OLDPWD=/lib/modules/fglrx/build_mod
OPTERR=1
OPTIND=1
OSTYPE=linux-gnu
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/bin/X11:/usr/local/sbin:/usr/local/bin
PIPESTATUS=([0]="0")
PPID=6863
PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w \$ '
PS2='> '
PS4='+ '
PWD=/etc
QT_IM_MODULE=scim
SESSION_MANAGER=local/mlomkernote:/tmp/.ICE-unix/6836
SHELL=/bin/bash
SHELLOPTS=braceexpand:emacs:hashall:histexpand:history:interactive-comments:monitor
SHLVL=3
SSH_AGENT_PID=6525
SSH_AUTH_SOCK=/tmp/ssh-jxiENc6472/agent.6472
TERM=xterm
UID=0
USER=root
WINDOWID=29360135
XCURSOR_THEME=default
XDM_MANAGED=/var/run/xdmctl/xdmctl-:0,maysd,mayfn,sched,rsvd,method=classic,auto
XIM_PROGRAM='scim -d'
XMODIFIERS=@im=SCIM
_=ld.so.conf
root@mlomkernote:/etc # 

```

Have you looked through the /var/log/xorg.0.log for errors in starting the X server?

I suppose you could **apt-get install --reinstall ubuntu-base** (do this from a command prompt with gnome not running).

---

### Post by kb_ganesh on 2005-09-23
thanks for the suggestion..i will try it out and get back as soon as possible.

---

### Post by kb_ganesh on 2005-09-23
i just verified that my "normal" account does have a .bashrc file..and /etc/bash.bashrc exists too..if need be, i will attach them..

this is what i get from set command

```

BASH=/bin/bash
BASH_ARGC=()
BASH_ARGV=()
BASH_LINENO=()
BASH_SOURCE=()
BASH_VERSINFO=([0]="3" [1]="00" [2]="16" [3]="1" [4]="release" [5]="x86_64-pc-linux-gnu")
BASH_VERSION='3.00.16(1)-release'
COLUMNS=80
CONSOLE=/dev/console
DIRSTACK=()
EUID=0
GROUPS=()
HISTFILE=/root/.bash_history
HISTFILESIZE=500
HISTSIZE=500
HOME=/root
HOSTNAME=njiggs
HOSTTYPE=x86_64
IFS=$' \t\n'
INIT_VERSION=sysvinit-2.86
LINES=25
LOGNAME=root
LS_COLORS='no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.ogg=01;35:*.mp3=01;35:*.wav=01;35:'
LS_OPTIONS=--color=auto
MACHTYPE=x86_64-pc-linux-gnu
MAILCHECK=60
OPTERR=1
OPTIND=1
OSTYPE=linux-gnu
PATH=/bin:/usr/bin:/sbin:/usr/sbin
PIPESTATUS=([0]="0")
PPID=5446
PREVLEVEL=N
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w \$ '
PS2='> '
PS4='+ '
PWD=/root
RUNLEVEL=S
SHELL=/bin/bash
SHELLOPTS=braceexpand:emacs:hashall:histexpand:history:interactive-comments:monitor
SHLVL=1
TERM=linux
UID=0
USER=root
_=clear

```

i tried reinstalling ubuntu-base too as suggested..booted into recovery mode and did the step from tty1..still no use..get the last error that says "the greetr cant be displayed....." and i cant login to other users as well..says /bin/bash permission denied..i have uploaded the X server log at [http://bah-raj.tripod.com/Xorg.0.log](http://bah-raj.tripod.com/Xorg.0.log) ..if you can, do have a look..i have a feeling that some file permission somewhere has been messed up but as far as i have checked, no essential file has been removed from read and execute permissions for all users..so, i am still left wondering whats gone wrong where...?!?

---

### Post by mlomker on 2005-09-23
>  from tty1..still no use..get the last error that says "the greetr cant be displayed....." 

I just found something on Google that says this is a GDM problem, not a gnome problem.  Try using **startx** from a prompt rather than going through GDM.

I couldn't read your xorg.0.log file--the formatting got lost and made it impossible.  You can post .txt files to messages on here.

---

### Post by kb_ganesh on 2005-09-23
thats what i have been doing till now..using startx from prompt..because when i boot up, i get this greeter error..and it takes me back to login at tty1..and there i am able to login only as root..when i try to login as any other user, it gives me the /bin/bash:permission denied message..after logging in as root, i use startx to come to gnome..

and i have tarred and attached the Xorg log file..hope this works.

---

### Post by mlomker on 2005-09-24
The xorg.log won't help me since X is working fine.  I misunderstood the situation, but now I get it.  

Let's give this a try (you can delete the old file/directory later if this works)

```

mv /usr/bin/gdmgreeter /usr/bin/gdmgreeter.old
mv /etc/gdm /etc/gdm.old
apt-get install --reinstall gdm bash

```

You could also install KDM (the login manager for KDE).  What I'm not certain of is whether or not the bash problem is causing the GDM problem.

---

### Post by kb_ganesh on 2005-09-24
ok..i got no idea how it worked but it did..and i am happy it did..after a bit of googling, i found that its some problem with some file permission somewhere but i couldnt find out where the problem lay..so, i thought of this solution..

```
chmod o+r --recursive /
chmod o+x --recursive /
```

and then i restarted gdm..and lo and behold, it worked like a charm..i guess i can call it solved though it leaves my computer a bit vulnerable..if anyone here can tell me if this gives rise to any security loopholes(which i am pretty sure it would)..and what are the files i need to rollback the permissions on..thanks again!!

---

### Post by mlomker on 2005-09-24
> and what are the files i need to rollback the permissions on..thanks again!!

Oh my goodness!  You've just made every file on your system executable by any user account.

I'd recommend backing up all of your valuable data and reinstalling your operating system.

---

### Post by fordfan753 on 2005-09-24
**OUCH!!** Not good!

---

### Post by kb_ganesh on 2005-09-24
i know its not good..but isnt there a better way out than reinstalling?!?

---

### Post by mlomker on 2005-09-24
[QUOTE=kb_ganesh]i know its not good..but isnt there a better way out than reinstalling?!?[/QUOTE]

There are too many files and they all need different permissions in order to be secure.  Your system will never be secure without reinstalling.

There are probably ways to save file permissions to a file and then copy them back, but it's too late now...you've already made the change.

---

