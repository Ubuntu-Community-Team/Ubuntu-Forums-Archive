---
title: "Password on shutdown"
date: 2009-06-29
forum: x86 64-bit Users
---

### Post by nucleuskore on 2009-06-29
Hi everybody,
I am having a peculiar problem with my Ubuntu 9.04. When I click shutdown

[shut1.png](http://www.zshare.net/image/62010887419835c5/)

I get a dialog box asking for my password saying there's someone else logged in

[shut2.png](http://www.zshare.net/image/62010889e30b0044/)

If I click cancel, open a shell and type **users**, I see two users logged in
neville neville

Should it have just read
neville

or is it showing my user group too as neville so hence the name appearing twice

I have installed with defaults and haven't touched Users and Groups. I haven't fiddled with any system policies.

This password on shutdown is getting quite annoying. Any suggestions

---

### Post by ajgreeny on 2009-06-29
The two usernames you see is normal for some reason which I can't remember at the moment.  I think it is to do with the non-x session if I remember correctly.  Why you need a password I can't imagine but go to System >Admninstration >Login Window and have a look on the first tab for the "Edit Commands".  The halt command on my machine shows as 
/sbin/shutdown -h now "Shut Down via gdm."
exactly that including the quote marks etc.  If yours is different, try that (after backing up yours first just in case) to see if it makes things work as expected.

---

### Post by nucleuskore on 2009-06-29
[[IMG]http://img510.imageshack.us/img510/3540/screenshotzfuplh.th.png[/IMG]](http://img510.imageshack.us/i/screenshotzfuplh.png/)

It's exactly that!

---

### Post by nucleuskore on 2009-06-29
When I click on more details and then the link

[[IMG]http://img294.imageshack.us/img294/1751/shut3.th.png[/IMG]](http://img294.imageshack.us/i/shut3.png/)

this is what I get

[[IMG]http://img294.imageshack.us/img294/9485/shut4.th.png[/IMG]](http://img294.imageshack.us/i/shut4.png/)

Any ideas?

---

### Post by ajgreeny on 2009-06-29
Do you actually have more than one user on your system, not actually logged in as far as you know, but who potentially could do so?  It sounds from your first post as if you don't, but I'm baffled at the moment as to where to go on this.

---

### Post by nucleuskore on 2009-06-29
As you can see, NO

[[IMG]http://img38.imageshack.us/img38/7448/screenshothnl.th.png[/IMG]](http://img38.imageshack.us/i/screenshothnl.png/)

but I have a hunch, let me see if I'm right

---

### Post by nucleuskore on 2009-06-29
I installed all the software I have on my PC on Virtualbox but am not able to recreate the problem. SO I installed Virtualbox itself, just installed, on to the Virtual Ubuntu to see if there was any problem with the permissions from there but no. I'm at a loss too. I hope someone gives me a solution :)
My terminal output for **who**

neville  tty7         2009-06-30 06:46 (:0)
neville  pts/0        2009-06-30 07:05 (:0.0)

---

### Post by nucleuskore on 2009-06-29
I googled around with a little different terms, this is what I got
[http://linuxoutlaws.com/forums/viewtopic.php?f=9&t=1567](http://linuxoutlaws.com/forums/viewtopic.php?f=9&t=1567)
[https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/368594](https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/368594)

wonder if it is some bug. I can easily circumvent this problem by changing the value of the multiple user thing in policykit, but that's not the point. Why does the thing happen with defaults? I was scared I have a rootkit or something.

---

### Post by nucleuskore on 2009-06-29
I searched launchpad and it looks like someone has a similar problem

See here
[https://bugs.launchpad.net/hundredpapercuts/+bug/389115](https://bugs.launchpad.net/hundredpapercuts/+bug/389115)

I wonder who is this user nobody who does not allow me to shutdown

[img]http://s269.photobucket.com/albums/jj44/visio159/Unismilies/38large.png[/img]

---

### Post by nucleuskore on 2009-06-30
Dear ajgreeny and everybody else
I finally solved my problem. Since "nobody" was not allowing me to shutdown, I ran

**ps -U nobody**

and go the following output

  PID TTY          TIME CMD
 2570 ?        00:00:00 su
 2691 ?        00:00:00 sh
 2692 ?        00:00:00 monopd

PID 2692 is the monopd server for hosting Monopoly games. I uninstalled monopd.

Problem solved, case closed.

---

