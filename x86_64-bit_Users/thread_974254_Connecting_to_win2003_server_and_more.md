---
title: "Connecting to win2003 server and more"
date: 2008-11-07
forum: x86 64-bit Users
---

### Post by jhbumby on 2008-11-07
Hello everyone.  Finally I get to get back into the Ubuntu scene.  I just installed Ubuntu 8.10 64 bit on my office computer.  Everything is going great.  Everything so far has been fantastic.  However, I need help connecting into the server, sort of.  Here is what I have so far...

I can connect to the internet no problem through the server, thusly my ability to type this message.  However, the server doesn't see me.  And although I see the server, I can not connect to any of the shares - in fact, I don't even see the icons.  I need to connect to another computer's printer and share files.  I have been trying to hook up Samba, but i am not even sure if I need this.  I have also tried configuring and connecting a VPN, but have screwed that whole thing up (not really, just was unable to do it).  At this point, I am so bass ackwards, on everything, I don't know which way is up.  I am trying this thing out on this computer with the hopes to connect others soon. 

I would love for someone who has done this before with success to give me a clue, a push in the right direction, or perhaps specific instruction as to how to do this.  Perhaps there is a program to install on windows server and this one that just does it???  (If not, there should be..., just for dummies like me!)  Anyway, thanks a bunch.  I tried searching the threads for this, but nothing worked that I have tried so far.  Perhaps others have run into this problem??  Thanks again - John

---

### Post by cariboo on 2008-11-07
Can you post the output of:

```
smbclient -L <servername> -U%
```

Where <servername> is the name of the Win2003 server.

This should show you all the shares and printers available on the server.

BTW this is more a networking problem then 64bit, this problem could happen in either 32bit or 64bit.

Jim

---

