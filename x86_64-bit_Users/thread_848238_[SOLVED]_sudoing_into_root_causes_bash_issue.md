---
title: "[SOLVED] sudoing into root causes bash issue"
date: 2008-07-03
forum: x86 64-bit Users
---

### Post by wbrown on 2008-07-03
Greetings:  

I am having issues with my shell in my 64bit hardy release.  I currently cannot scp files from a remote server to my hardy box because of missing files in the bash shell.  I also get this strange behavior when trying to sudo into the root user: 

bill@myHost:/home/bill$ sudo su
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found

Does anyone know what the issue is here? 
here is my /etc/profile file:

# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "`/usr/bin/id -u`" -eq 0 ]; then
  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11"
else
  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/gam
es"
fi

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
        . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

export PATH


umask 022


Is this issue related to it being a 64 bit version of ubnutu?  I am not sure how to troubleshoot this more. 

Thanks for looking.
Bill.

---

### Post by Cappy on 2008-07-03
No .. it's not a 64-bit specific problem.

Post your $PATH using
```
echo $PATH
```

You're missing critical files so you're probably missing ubuntu-minimal
```
sudo apt-get install ubuntu-minimal ubuntu-desktop
```
If you're not running a graphical desktop don't install ubuntu-desktop. If you're running Kubuntu install kubuntu-desktop instead. If you're running Xubuntu install xubuntu-desktop instead.

By the way, root's logon file is at /root/.bashrc but you have bigger problems that are causing most of those errors.

---

### Post by cariboo on 2008-07-03
You don't need sudo to switch users (su). To switch users just type:

```
su <user>
```

It will ask for the password of the user that you are switching to.

Jim

---

### Post by Artemis3 on 2008-07-05
Try sudo -i

Also sftp and filezilla can help you copy files.

---

### Post by wbrown on 2008-07-22
Greetings Cappy:

the "echo $PATH" was the tip I needed.  When I did that as root, I had the following for my path:

"$JAVA_HOME/bin:$PATH"

I needed to remove the following 2 lines from /etc/environment.  
...
PATH="$PATH:$MAVEN_HOME/bin"
PATH="$JAVA_HOME/bin:$PATH"
...

Apparently, you cannot use $VAR in the value for the variable because it is not interpreted yet and every declaration of a variable (PATH in my case) overwrites any previous value.  

Thanks.
Bill.

---

