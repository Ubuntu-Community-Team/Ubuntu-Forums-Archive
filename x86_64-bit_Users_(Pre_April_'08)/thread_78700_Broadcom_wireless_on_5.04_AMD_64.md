---
title: "Broadcom wireless on 5.04 AMD 64"
date: 2005-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by sman88 on 2005-10-18
Hi all, I used to play around with linux but it never really cought on with me, now my cousin has reintroduced it to me and I have set up a dual boot on my Compaq Presario R3000Z laptop. I REALLY like ubuntu, it is much nicer than slackware (what I used to use). Everything else in the install went great, except my broadcom wireless card. I know there are ALOT of threads about this issue, but I am unable to make any sence of them. I am a total NOOB to the MAX! Please treat me like one! Could someone please tell me how to install and configure my broadcom card, and please dont tell me to look at other threads. I have gotten as far a downloading Ndiswrapper and unzipping it, that is all, im not used to this whole command line thing.

I really apreciate all your help and hope and can fit in in this little comunity of yours!
Thanks in advance all!

---

### Post by sman88 on 2005-10-19
Can someone atleast tell me how to install ndiswrapper?

---

### Post by NickB on 2005-10-19
If you want to use ndiswrapper on hoary, you need to download the source and compile (you'll want 1.1).  However, you can solve this problem (and many others) by upgrading to breezy (5.10), which solves many problems out of the box (like a working fglrx driver, ndiswrapper, fireglcontrol [for dual monitor setup], etc.)

Nick

---

### Post by sman88 on 2005-10-19
Can I upgrade or do I have to do a complete install? BTW, thanks for your post.

---

### Post by NickB on 2005-10-19
If you've got a clean install of hoary, you're probably better off just re-installing breezy from scratch.  However, you can change the distribution settings to breezy either in /etc/apt/sources.list or by using synaptic.  It'll take a while to download and install the updates. however.

Nick

---

### Post by sman88 on 2005-10-19
Ok I have Breezy installed, now what do i do?

---

### Post by NickB on 2005-10-19
ndiswrapper should be included with the kernel.  It's just a matter of installing ndiswrapper-utils (if it's not already installed) and installing the driver.

See here [https://wiki.ubuntu.com/?action=fullsearch&context=180&value=ndiswrapper&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=ndiswrapper&titlesearch=Titles) for info.

Nick

---

### Post by sman88 on 2005-10-19
I am a total noob, someone cannot tell me to install something, they have to tell me to click here type this and then press enter. I could not make any sence out of those instructions, could someone please translate them, i would GREATLY apreciate it.

Also if anyone can help me find a way to edit my xorg.conf file that would be sweet, it says since Im not the owner of the file its read only. And I need it to setup twinview on my laptop for a presentation tomarow (worth 250pts), so if anyone has any info I would really apreciate it!

---

### Post by sman88 on 2005-10-20
Can someone please tell me how to install ndiswrapper?

---

### Post by Tass on 2005-10-29
OK - I've got past the part you're stuck on, but still can't get my connection to connect.  I'll try get you there, and maybe you'll have more luck.

First off, have you got your windows x64 drivers somewhere where you can access them?

Secondly, you'll need to go to System > Administration > Synaptic Package Manager, select "All" on the left hand side, sort by package name (clickon the package column) and scoll down & check the ndiswrapper-utils and wireless-utils checkboxes.  This should download and install the utilities.

Do that, find the local path where your drivers are, and get back to me

---

### Post by byen on 2005-10-30
well...this is what helped me.... try it out....might just work....goodluck!
[http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

also..here is a thread which had a similar issue..see if that helps
[http://ubuntuforums.org/showthread.php?p=328107#post328107](http://ubuntuforums.org/showthread.php?p=328107#post328107)

---

