---
title: "New User setting up printing, also general KDEPrint question"
date: 2006-05-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by CanadianUser on 2006-05-25
First of all, this is my first post as I am (once again) new to Linux.  I had originally been into Linux back in the kernel 1.2 days, then got back into it again after kernel 2.0 came out, and got out of it a couple of years ago just after 2.4 came out.  As it has been a while, I am highly rusty on configuring Linux.

Having said that disclaimer, here is my problem.  My printer, Samsung ML-2010 (usb connection printer), works perfect under Windoze, and is recognized as apparently set up just fine under Linux in KDEPrint and even says that the printer is online and accepting print jobs.  :confused: However, even though the printer really is turned on, plugged in, and everything else basic, when I try a test page, absolutely nothing happens.  The print jobs list show that the job is 'processing' and then nothing after that, it never prints.   I don't know for sure, but cups seems to me to be running just fine, but I am too rusty at this, so I could be wrong.  

Also, what is the default CUPS login and password anyway.  When trying the web/html based interface, nothing is accepted.  Documentation seems to indicate system root login and password.  Tried this and failed, tried user name and password, and a number of other various attempts such as 'admin' and password, root and no password, ](*,) (you get the idea).

Any suggestions would be appreciated.  Thanks and ttfn.

Michael

---

### Post by warp99 on 2006-05-26
[QUOTE=CanadianUser]First of all, this is my first post as I am (once again) new to Linux.  I had originally been into Linux back in the kernel 1.2 days, then got back into it again after kernel 2.0 came out, and got out of it a couple of years ago just after 2.4 came out.  As it has been a while, I am highly rusty on configuring Linux.

Having said that disclaimer, here is my problem.  My printer, Samsung ML-2010 (usb connection printer), works perfect under Windoze, and is recognized as apparently set up just fine under Linux in KDEPrint and even says that the printer is online and accepting print jobs.  :confused: However, even though the printer really is turned on, plugged in, and everything else basic, when I try a test page, absolutely nothing happens.  The print jobs list show that the job is 'processing' and then nothing after that, it never prints.   I don't know for sure, but cups seems to me to be running just fine, but I am too rusty at this, so I could be wrong.  

Also, what is the default CUPS login and password anyway.  When trying the web/html based interface, nothing is accepted.  Documentation seems to indicate system root login and password.  Tried this and failed, tried user name and password, and a number of other various attempts such as 'admin' and password, root and no password, ](*,) (you get the idea).

Any suggestions would be appreciated.  Thanks and ttfn.

Michael[/QUOTE]

Seems to be a problem with that driver/printer and amd64. Looks like you need the ia-32 libs since the driver is only 32-bit. Here's a tutorial on this problem with a debian install:

[http://base0.net/archives/32-Getting-a-Samsung-ML-2010-to-work-in-Debian-Linux-amd64x86_64.html]("http://base0.net/archives/32-Getting-a-Samsung-ML-2010-to-work-in-Debian-Linux-amd64x86_64.html")

Also with CUPS on KDE you can't HTML into the web based app due to how root access is handled by ubuntu. You can access the printer configuration through the system menu to obtain the same result. Remember that during the install kubuntu gives default admin to the printer otherwise you couldn't install the drivers. 8)

---

### Post by CanadianUser on 2006-05-26
Thanks for the response.  I never thought about the whole 32bit libraries idea myself so thanks for bringing it to my attention.

---

