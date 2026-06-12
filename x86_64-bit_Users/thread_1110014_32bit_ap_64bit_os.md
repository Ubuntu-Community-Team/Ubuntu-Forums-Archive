---
title: "32bit ap 64bit os"
date: 2009-03-29
forum: x86 64-bit Users
---

### Post by Leetbumble on 2009-03-29
So I've been looking all over the interwebs and for some reason (bill gates is trying to stop me) I can not find any clue about installing 32bit applications (and what I need to do to make them run) while on a 64bit system.

Any input is welcome... including telling me I'm an idiot and posting the links I missed.

~Thank you~

---

### Post by 3Miro on 2009-03-29
I heard you have to jump through some hoops to make 32-bit win apps run on 64-bit windows, now about Linux and what Bill doesn't want you to know:

To run a 32-bit Linux app under 64-bit Linux you have to simply run it. There are some dependencies, however, if you install something from the repos everything is naturally taken care of (you just end up with /lib32 folder with some stuff in it). I am running 32-bit skype on two 64-bit machines without any trouble.

To run 32-bit windows app under Linux, you have to install wine via either the regular repository or by adding the winehq one and then go through the same process of setting up a program under wine as you would anyway (it varies from an app to an app). I am running a number of 32-bit windows games under my 64-bit Linux and everything is quite happy.

Under 64-bit Virtual Box you can also run 32-bit windows or Linux virtual machines and it also works fine.

---

### Post by jespdj on 2009-03-30
What 32-bit software do you have that you need to run on 64-bit Ubuntu? Are you sure that there is no 64-bit version of that software available?

You can forcibly install 32-bit packages (for the i386 architecture) with dpkg:
```
sudo dpkg -i --force-architecture package.deb
```
But you will need to make sure that you have all the dependencies installed (32-bit versions of libraries etc. that the program might need). The [getlibs](http://ubuntuforums.org/showthread.php?t=474790) script can help you to automatically find and install those dependencies.

---

### Post by gorucan on 2009-03-30
just use 8.10 and you will be able to use any 32-bit app normally like you would on 32-bit os.

---

### Post by Slim Odds on 2009-03-30
> **gorucan said:**
> just use 8.10 and you will be able to use any 32-bit app normally like you would on 32-bit os.

If only it were that simple.....

---

### Post by philinux on 2009-03-30
Apt post on first page of forum. GETLIBS

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

