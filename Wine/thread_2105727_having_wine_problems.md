---
title: "having wine problems"
date: 2013-01-16
forum: Wine
---

### Post by Questionable Choices on 2013-01-16
Okay so I just installed ubuntu on my windows 7 laptop using wibu
and I updated everything via the software updater, though when I try and install wine I get the following error 
Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
Details
The following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not going to be installed

I would much appreciate any help
I love everything about the look and feel of linux
I just got to get the jist of things
I have been using windows since 98 and I don't know technical terms, I am the type that once I do something I just remember and can pretty much do it from then on out, the problem with linux though is I am a noob at it and I feel like I am back in 98 when I didnt know jack squat about windows lol

---

### Post by Questionable Choices on 2013-01-16
I have ubuntu 12.10 on a windows 7 laptop that was installed with wibu
i have a 
AMD A6-4400M APU with Radeon(tm) HD Graphics × 2 
3.3 Gib of memory 
and 64 bit os
so I updated my software
I went to terminal and tryed installing it this way and this is what it said

mdkinc@ubuntu:~$ sudo apt-get install wine
[sudo] password for mdkinc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
mdkinc@ubuntu:~$ install openjdk-6-jre
install: missing destination file operand after `openjdk-6-jre'
Try `install --help' for more information.
mdkinc@ubuntu:~$ 


would appreciate any help!!

---

### Post by offgridguy on 2013-01-16
I never had any success installing wine either.  So i quit trying.  However in your case i
would suggest starting a new thread in the Wine-sub forum,  you will probably get more
replies. :D

---

### Post by lisati on 2013-01-16
*Thread moved to **Wine**.*
(and merged with new thread)

---

### Post by Mark Phelps on 2013-01-19
I don't get it ...

Wubi is used to allow you to install Ubuntu from INSIDE Windows -- so you don't have to create a new partition.

Wine is designed to allow you to run SOME, repeat SOME, Windows apps in Ubuntu -- when you don't have Windows.

You already HAVE Windows -- so why are you messing around with Wine?

---

### Post by kjh_ngisd on 2013-01-19
@ [Questionable Choices]("http://ubuntuforums.org/member.php?u=1777493")
I'm not sure this is an answer per se, but it looks like you're using wine 1.4.x and I think you'd want to upgrade to wine 1.5 . It's possible you've got some package dependencies that are off because you're on 1.4. I'm running 1.5.19 and it's clean for me. 

@ Mr. Phelps
2 reasons:
1. because you can . Sometimes that's enough. 
2. If you're in the middle of doing something on Linux and you want to run a quick Win program, you don't want to have to reboot. 

-kevin

---

### Post by Mark Phelps on 2013-01-21
> **kjh_ngisd said:**
> @ Mr. Phelps
2 reasons:
1. because you can . Sometimes that's enough. 
2. If you're in the middle of doing something on Linux and you want to run a quick Win program, you don't want to have to reboot. 
-kevin

OK ... but ... You have to REINSTALL everything in Wine that you might want to use from Windows.  You can't just point to it in Windows from Wine.  If you have much stuff installed, that is a LOT of work just to prevent rebooting for 5 minutes.

Also, the question was posed to the OP, and while I certainly respect YOUR opinion, I really wanted to hear back from them. Why? Because maybe they were trying to install Wine to solve a problem -- that could be installed WITHOUT the hassle of installing Wine and getting it working.  OR, maybe they were installing Wine to run a Windows app, for which there was already a Linux solution -- and they simply didn't know that.

So, while your opinions were interesting, they said nothing about why the OP was doing this.

---

### Post by offgridguy on 2013-01-22
> **mark phelps said:**
> ok ... But ... You have to reinstall everything in wine that you might want to use from windows.  You can't just point to it in windows from wine.  If you have much stuff installed, that is a lot of work just to prevent rebooting for 5 minutes.

Also, the question was posed to the op, and while i certainly respect your opinion, i really wanted to hear back from them. Why? Because maybe they were trying to install wine to solve a problem -- that could be installed without the hassle of installing wine and getting it working.  Or, maybe they were installing wine to run a windows app, for which there was already a linux solution -- and they simply didn't know that.

So, while your opinions were interesting, they said nothing about why the op was doing this.
+1

---

