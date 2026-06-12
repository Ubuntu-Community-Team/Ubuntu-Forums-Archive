---
title: "[SOLVED] SERIOUS - Is this a bug? - Authorization Failed"
date: 2008-09-08
forum: x86 64-bit Users
---

### Post by tigerplug on 2008-09-08
Hi all, 

I'm running Ubuntu x64 on a Dell Inspiron 1520 and have had no problems up until now.

Basically (and I quote this from a ticket I found via google):

> When the gnome login shows up before I get a chance to enter my username or password an error pops up stating 'authorization failed'. Clicking ok just makes the same error occur again. All I can do is ctrl+alt+backspace and ctrl+alt+del to reboot.

This is exactly what is happening to me.
However, the ticket that I found was closed (unresolved).

You can view the ticket here: 
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/203755](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/203755)


If anyone can help me I would really appreciate it!
I'm really under pressure to try get my machine working again as there is some pretty urgent work I need to get done for a few clients.


Thanks in advance!


Tigerplug

---

### Post by tigerplug on 2008-09-08
Anyone experience the same?

Even if I could get a quick fix for now it'd be great?

---

### Post by Thelasko on 2008-09-08
The reason the bug report was closed, was because it's not a bug.  It's likely the user did something that caused the issue.  Think back, what did you do right before this happened?  Did you install any software?  Install a new theme?

The only person who knows the solution to that bug report is the person who posted it.  Judging by the post, it appears he just reinstalled Ubuntu.
> It was too unusable for me to narrow down any particular issue. 

You can also try posting on the bug report page.  Inform people you are having the same issue.  Maybe it will be reopened.

---

### Post by tigerplug on 2008-09-09
Thanks for the reply - I finally got it sorted!

It took me a while to figure out what I had done and try retrace my steps (as I hadn't rebooted in a few days).

The problem was with the NM-APPLET - I changed some setting hoping that it (the NM-APPLET) wouldn't ask me for a password everytime I started Ubuntu.

I had to mount my HD using a live CD and then change the file back - the main issue for me was finding out which file it was. I got it in the end!






Tigerplug

---

### Post by Thelasko on 2008-09-09
Glad you were able to get your issue resolved.  Thanks for posting your solution so others can benefit from it.  Please go to thread tools and mark this thread [solved].

Thanks

---

### Post by bigdani on 2009-06-22
Hi everyone, 

I'm quite beginer in ubuntu 9.04 and I have almost the same problem but with a little difference, after install some "Education" aplications from "add and remove programas" in the ubuntu menu then ask me to reboot my system and when it was starting a Edubuntu screen appears with a small windows in the middle of the screen with the only option of "user name" but before I can do something an error pop up saying "Authorization failed"

PD: I don't have edubuntu I have Ubuntu 9.04 the last one
PD: what's NM-APPLET??

I hope heard from you soon
thanks

---

