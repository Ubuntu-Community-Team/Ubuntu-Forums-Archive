---
title: "Ventrilo Server Install Help"
date: 2008-05-17
forum: x86 64-bit Users
---

### Post by wally501 on 2008-05-17
I attempted to install Linux i386 - 32bit (Version 3.0.2).  I followed the directions on the vent site, but when I attempt to run the command ventrilo_srv it will not start the server.  It is showing that it doesn't recognize the command.  I am currently using Ubuntu 8.04 (64bit).

Any ideas?

---

### Post by TuckLive on 2008-05-20
Are you in the directory containing ventrilo_srv and running the command:  ./ventrilo_srv?

---

### Post by wally501 on 2008-05-20
~/Desktop/Ventrilo/ventsrv$ ls
LICENSE  ventrilo_srv  ventrilo_srv.htm  ventrilo_srv.ini  ventrilo_status
~/Desktop/Ventrilo/ventsrv$ ./ventrilo_srv
bash: ./ventrilo_srv: No such file or directory

I have tried as a normal user and as root.
Still can't get it to start

---

### Post by wally501 on 2008-05-26
Anyone else have any ideas I  could try?  Thanks in  advance.

---

### Post by Treth on 2009-01-07
> **wally501 said:**
> ~/Desktop/Ventrilo/ventsrv$ ls
LICENSE  ventrilo_srv  ventrilo_srv.htm  ventrilo_srv.ini  ventrilo_status
~/Desktop/Ventrilo/ventsrv$ ./ventrilo_srv
bash: ./ventrilo_srv: No such file or directory

I have tried as a normal user and as root.
Still can't get it to start

This is the error thrown when your 64-bit architecture tries to run a 32-bit binary without the proper support libraries.  Do this and try again:

apt-get install ia32-libs

---

### Post by Harju on 2009-05-20
> **Treth said:**
> This is the error thrown when your 64-bit architecture tries to run a 32-bit binary without the proper support libraries.  Do this and try again:

apt-get install ia32-libs

Hey thanks alot for this tip, I've been searching and testing for hours to get this thing working. This is the first thing and main purpose of my Ubuntu machine so I'm very very new to Linux :)

---

### Post by ToBeHuman on 2009-08-18
```
christopher@turd-server:~/ventsrv$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
christopher@turd-server:~/ventsrv$ ls
LICENSE  ventrilo_srv  ventrilo_srv.htm  ventrilo_srv.ini  ventrilo_status
christopher@turd-server:~/ventsrv$ ventrilo_srv
-bash: ventrilo_srv: command not found
christopher@turd-server:~/ventsrv$
```


Okay, I've having the same problem as the OP. I've added the 32 bit support (I'm running Ubuntu 9.04 64). Does anyone have any suggestions?

THANKS.

---

### Post by ToBeHuman on 2009-08-18
Nevermind, it's working now.

---

