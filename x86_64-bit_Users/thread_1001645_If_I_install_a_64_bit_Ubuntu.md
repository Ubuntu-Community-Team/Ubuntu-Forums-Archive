---
title: "If I install a 64 bit Ubuntu?"
date: 2008-12-04
forum: x86 64-bit Users
---

### Post by the lemming on 2008-12-04
If I install a 64 bit Ubuntu onto my computer can I only run 64 bit applications?

I'm still quite green behind the ears and I do have one or two applications which run on XP and Vista which do not run on Linux or even have a similar application to use.

So, if I try to run the applications in WINE will they work on my 64 bit Ubuntu?  The apps are 32bit

The application is called Memory Maps and it allows me to look at all my Ordnance Survey maps for Hill Walking

---

### Post by halovivek on 2008-12-04
It will support 32 bit also. i have windows vista ultimate 64 bit and ubuntu 64 bit in my system and it works fine. ):P

---

### Post by vgrisham on 2008-12-04
> **the lemming said:**
> If I install a 64 bit Ubuntu onto my computer can I only run 64 bit applications?

I'm still quite green behind the ears and I do have one or two applications which run on XP and Vista which do not run on Linux or even have a similar application to use.

So, if I try to run the applications in WINE will they work on my 64 bit Ubuntu?  The apps are 32bit

The application is called Memory Maps and it allows me to look at all my Ordnance Survey maps for Hill Walking

I've been using 64-bit Ubuntu for over two years, and I've had no difficulty getting the programs I need to work very well. The only program that I had to wrestle with was Amazon's music downloader. There is a terrific application called Getlibs that took care of the Amazon downloader and would take care of any other program that would need specific 32-bit support. Getlibs is a nice security blanket, though as I said, I've only needed it once.

As far as Internet based multimedia, everything works well in 64 bit Firefox now including Flash (for which Adobe just launched a 64-bit version exclusively for Linux) and Java apps.

As far as Wine goes, it installs programs into an artificial 32-bit Windows environment, so you're not going to need to hunt down 64-bit windows programs (and you wouldn't find many anyway). As time has passed, I've needed Wine less and less as I've found replacements for my Windows apps. 

You'll love 64-bit Ubuntu. Have fun.

---

### Post by dabl on 2008-12-04
You can run only applications _compiled for_ the 64-bit architecture, which is all 25,000+ in the Ubuntu repositories, including wine, plus any more that you care to compile from source on your platform.

"Compiled for" 64-bit Linux architecture is very different from "originally written for" 64-bit hardware.  There are relatively few of the latter variety, since we are early in the life cycle of 64-bit personal computers.

Wine will run your 32-bit windows apps, AFAIK. I don't use it, I use VMware Player (64-bit version), and run a 32-bit Win XP system in it, with its 32-bit apps.  No problem on my 64-bit Kubuntu system.  :)

---

### Post by talofo on 2008-12-07
> **halovivek said:**
> It will support 32 bit also. i have windows vista ultimate 64 bit and ubuntu 64 bit in my system and it works fine. ):P

:)) :)))

I'd like to have that, exactly that, on my Laptop.
Can you give me some advices (link, tutorials, resources). I'm totally newbie on all this.

Thanks a lot.

---

### Post by MedianMajik on 2008-12-07
> **talofo said:**
> :)) :)))

I'd like to have that, exactly that, on my Laptop.
Can you give me some advices (link, tutorials, resources). I'm totally newbie on all this.

Thanks a lot.

To start things off what are you currently using (some version of windows?) and what would you like to do?  Please post your computer specs as I do in my signature to speed up assistance.  

Sounds like you are interested in [dual booting]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm") both windows and [ubuntu]("http://www.ubuntu.com/getubuntu/downloadmirrors").  However, there are multiple ways to play with Ubuntu besides "taking the plunge."

If you just want to get your feet wet I recommend [Wubi]("https://wiki.ubuntu.com/WubiGuide").  It allows you to install Ubuntu inside Windows as though it were a mere program.  This method will take longer to install (up to hours), but can be deleted in seconds just like any standard Windows application.  Here is the [offical website]("http://wubi-installer.org/").

Another method you can try is running Ubuntu as a virtual machine if you'd prefer.  Your best bets are [VMware]("http://www.VMware.com") (free version) and[ Virtualbox]("http://www.virtualbox.org/") (open source).  In order to run a virtual machine you'll need memory to keep everything running smoothly.

Does any of these methods interest you?  Be aware that a quick keyword search through these forums or google (example: vista wubi ubuntu) will give you a wealth of information. ;)

---

### Post by talofo on 2008-12-07
> **MedianMajik said:**
> To start things off what are you currently using (some version of windows?) and what would you like to do?  Please post your computer specs as I do in my signature to speed up assistance.  

Sounds like you are interested in [dual booting]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm") both windows and [ubuntu]("http://www.ubuntu.com/getubuntu/downloadmirrors").  However, there are multiple ways to play with Ubuntu besides "taking the plunge."

If you just want to get your feet wet I recommend [Wubi]("https://wiki.ubuntu.com/WubiGuide").  It allows you to install Ubuntu inside Windows as though it were a mere program.  This method will take longer to install (up to hours), but can be deleted in seconds just like any standard Windows application.  Here is the [offical website]("http://wubi-installer.org/").

Another method you can try is running Ubuntu as a virtual machine if you'd prefer.  Your best bets are [VMware]("http://www.VMware.com") (free version) and[ Virtualbox]("http://www.virtualbox.org/") (open source).  In order to run a virtual machine you'll need memory to keep everything running smoothly.

Does any of these methods interest you?  Be aware that a quick keyword search through these forums or google (example: vista wubi ubuntu) will give you a wealth of information. ;)


Here we go:
HP8530p
Intel Core 2 Duo T9400 2.53ghz - 1066fsb
4GB DDR2 800mhz 
250GB 7200rpm Sata II
ATI Mobility Radeon HD 3650

I need to run Several Adobe Cs4 applications. ALL other things, I'd liked to use Ubuntu.

As far as I know: Wine doesn't support CS4.

I need to work on Ubuntu, do some programming, then, some image on adobies, then back to Ubunto do deal with some other things, and then, back to windows to test how users will see the site on IE FF Opera and others, on windows enviorments. So I belive dual boot, maybe is not the most confortable way of doing. 

Why 64bits? I'm looking for maxixum performance.

Thanks a lot fot your help. This laptop should arrive this week, I'm just asking some preliminary questions before.

If you think is convinient to ask right now, what is the best partition method regarding the use of VM ?


A long time ago, I've toutch Red Hat 3 or something, so No. I come from M$.


Thanks a lot,
MEM

---

### Post by MedianMajik on 2008-12-07
> HP8530p
Intel Core 2 Duo T9400 2.53ghz - 1066fsb
4GB DDR2 800mhz 
250GB 7200rpm Sata II
ATI Mobility Radeon HD 3650

> I need to run Several Adobe Cs4 applications. ALL other things, I'd liked to use Ubuntu.
  VM is the way to go if you need Ubuntu as a "test bed" for your programming.  Wine does not support it [yet]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318").  I feel your pain as I also use Adobe suite and can't settle for old versions.

> What is the best partition method regarding the use of VM?
  VM will help with the partitioning so it is quite easy to do.  You'll want to use ext3 format.  You get to select how much of your system resources the virtual drive has access to just like controlling a child's allowance, use of your car, etc.

Advantages of 64-bit?  It can recognize 4gb+ of memory and lots of disk space.  Adobe just released 64-bit flash for Linux so things are looking good for the future.  As already mentioned in this thread you can get 32-bit dependencies resolved quite easily.  It is what I use and I don't regret it (my main problems with switching to 64-bit Ubuntu *flash* are almost all resolved). 

Honestly, nothing is stopping you from running any combination of 32-bit and 64-bit Ubuntu.  You can always swap or remove one.

...Now I just wish I could update my Blackberry in Linux.  Time for me to install an XP virtual machine.

---

### Post by jespdj on 2008-12-08
> **dabl said:**
> You can run only applications _compiled for_ the 64-bit architecture, ...
No, that is wrong. 64-bit Ubuntu can also run 32-bit binaries. Software does not need to be recompiled for 64-bit. You just need to install the necessary 32-bit libraries.

However, almost all software for Ubuntu is available as a 64-bit native program.

---

### Post by talofo on 2008-12-11
> **MedianMajik said:**
> VM will help with the partitioning so it is quite easy to do.  You'll want to use ext3 format.  You get to select how much of your system resources the virtual drive has access to just like controlling a child's allowance, use of your car, etc.


Ok. VMWare will help. Ok. But what about before?

I receive the machine, I clean the OS that is inside by default.
Since this is a HP laptop, I will have a recovery partition (almost sure of it) should I remove it? Since, there will be no way for the HP to recover something that is absolutly changed right?


I will then start the Ubuntu Instalation - whould the instalation help me with the partition creation or should I done it before?


I've read on ubuntu manuals I belive, that it's a good idea to start creating one partitition for aplications another for music/videos/ /another for mydocuments.... 

Help! :s


Regards,
MEM

---

### Post by Sef on 2008-12-11
> I've read on ubuntu manuals I belive, that it's a good idea to start creating one partitition for aplications another for music/videos/ /another for mydocuments.... 


The basic set up is 3 partitions:

1) Root - where the applications and kernel reside.

2) Home - Where documents, photos, and music reside.

3) Swap

---

### Post by talofo on 2008-12-11
> **Sef said:**
> The basic set up is 3 partitions:

1) Root - where the applications and kernel reside.

2) Home - Where documents, photos, and music reside.

3) Swap


On a 250gb Hd.

So normally the root partition will be the biggest one.
Let's give him: 200gb.

I will save all docs and photos on a external drive, but occasionaly I will need some space between the switch.
48gb;

Question 1)
And for Swap we give it: 2GB (is this to mutch? I will have 4gb ram on my system, maybe I will never use the Swap partition anyway... ).


Question 2) If I'd like to install a Vista64 as virtual machine, I need to install it on Root partition? But doesn't windows need another kind of partion to running?


Thanks a lot once again,
MEM

---

