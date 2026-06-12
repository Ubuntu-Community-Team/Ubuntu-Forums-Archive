---
title: "users &amp; group"
date: 2009-05-09
forum: x86 64-bit Users
---

### Post by jayanramesh on 2009-05-09
Dear buddies,
 I have accidently disabled all rights (permission}& everything so now I am unable to open update manager and synaptic package manager to do things.Please lent me a hand to regain my privileges.When I open update manager I 've got like this
>  Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '62914597' '-o' 'Synaptic::closeZvt=true' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmpimaaXc' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.
> "Failed to run /usr/sbin/synaptic as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator"-- if I  try to open synaptic manager
HELP will be very much appreciated

PS:Single user

---

### Post by _Purple_ on 2009-05-09
Are you running update manager? How did you change the permission?
Can you type this command in terminal and post the output?
```
groups
```

---

### Post by jayanramesh on 2009-05-09
Dear_Purple_,
Here is the output> "jayanr@jayanr-me:~$ groups
root jayanr
jayanr@jayanr-me:~$ 
And if I type " sudo bash" in terminal I've got the output like this
> ayanr@jayanr-me:~$ sudo bash
[sudo] password for jayanr: 
jayanr is not in the sudoers file.  This incident will be reported.
jayanr@jayanr-me:~$ 


I have changed my privilege through -System > Administration > users & groups.

---

### Post by pixel :-) on 2009-05-09
The simplest way i can think of that should work

i don't remember the names  and details very well

Reboot, at grub choose, the second option(maintenece, emergency something like that in the title), it will fall, in a blue screan, it will give you options, chose the start a chell option (more or less). Its going to be with root rights. give the command

startx

You'll get login at gnome as root. Fix your rights with the gui tool and leave. At the chell promt just type 

exit 

boot will continiou as normal, or you'll return to the blue screen and there tell it to continiou normal boot

---

### Post by jayanramesh on 2009-05-09
Dear pixel :-),
Thanks a lot . ok,I will try and let you know that.

---

### Post by jayanramesh on 2009-05-10
Dear pixel :-),
Came up the GUI but everything froze without detecting mouse and keyboard so could you be kind enough to show me the  other sort of remedy to solve this problem.The COMMAND "startx' really come to X-START as if all went to the wall.
your stuff and your helping hand is highly esteemed.

Thank you

---

### Post by sisco311 on 2009-05-10
In the root shell, add your user to the admin group, log out and choose to resume a normal boot:
```
adduser username admin
```
replace username with your login name 

press Ctrl+D to log out. 

[http://www.psychocats.net/ubuntu/fixsudo]("http://www.psychocats.net/ubuntu/fixsudo")

---

### Post by jayanramesh on 2009-05-10
Dear sisco311,
Cute and cool -a friend in need is a friend indeed.THANK you very very much.I got back.......

jnR

---

