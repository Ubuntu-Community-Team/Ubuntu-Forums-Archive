---
title: "Compaq Presario CQ60 - AMD Athlon X2 64 bit???"
date: 2009-01-09
forum: x86 64-bit Users
---

### Post by dBuster on 2009-01-09
I have just purchased a Presario CQ60 and it is said to have an Athlon X2 64 bit processor and in such I attempted to install 64bit 8.04.1.  I did this since my last laptop that I was having issues with the java took a dump on me and now is not functioning what so ever...

So any how, I have this laptop that hangs on booting off of the livecd.  When running verbose I get the following:

```
[  113.978568]
[  113.978569] HARDWARE ERROR
[  113.978570] CPU 0: Machine check exception:  4 Bank  4: b600000000070f0f
[  113.978825] TSC 35134dc47c  ADDR 900000c2004001
[  113.978076] This is not a software problem!
[  113.979042] Run through mcelog --ascii to decode and contact your hardware vendor
[  113.979130] Kernel panic - not syncing: Machine check
```

Is this telling me there is something wrong with the processor or that it can't run the 64 bit Ubuntu?  I can boot into 8.10 32 bit Ubuntu how ever I do not want to run 32bit!!!  To slow and choppy on this machine...

---

### Post by billt1 on 2009-01-09
I bought a Compaq some time ago and had exactly the same problem.

A Linux knowledgeable friend told me that many Compaq computers refuse to load Linux.

If possible you might return the Compaq and get a compatible laptop.  Check Ubuntu for compatibility before buying.

Good luck,

---

### Post by dBuster on 2009-01-09
> **billt1 said:**
> I bought a Compaq some time ago and had exactly the same problem.

A Linux knowledgeable friend told me that many Compaq computers refuse to load Linux.

If possible you might return the Compaq and get a compatible laptop.  Check Ubuntu for compatibility before buying.

Good luck,

I did check the Ubuntu compatibility list and there are numerous Compaq pc's listed there, however my particular one is a newer one and is not listed...  So I am not sure...

Strange how Compaq computers would refuse to load Linux, there must be something then in the bios?  Otherwise how else would it know??

---

### Post by dBuster on 2009-01-10
Here is a question for everyone, if I load 32 bit Ubuntu, which I do not want to do but if it loads..  Can I upgrade after it is installed to 64 bit?

---

### Post by drs305 on 2009-01-10
> **dBuster said:**
> Here is a question for everyone, if I load 32 bit Ubuntu, which I do not want to do but if it loads..  Can I upgrade after it is installed to 64 bit?

You won't be able to 'upgrade' from 32-bit to 64-bit. They are separate installs. If you have trouble installing the 64-bit version from the livecd you might try using the alternate cd instead. This often works but of course depends on what problems the livecd was having in the first place.

---

### Post by dBuster on 2009-01-10
> **drs305 said:**
> You won't be able to 'upgrade' from 32-bit to 64-bit. They are separate installs. If you have trouble installing the 64-bit version from the livecd you might try using the alternate cd instead. This often works but of course depends on what problems the livecd was having in the first place.

I appreciate the recommend.  This is so frustrating to not be able to get Ubuntu loaded!!!  I have searched and searched and from what I have discovered is that this model laptop is recommended and many others have it loaded with Ubuntu.  Just not sure why I am running into so much difficulty.  I have tried every combination of start up options for the live cd now I am getting the alternate and will give that a try.  

I can run the wubi, and I can also qemu run it in windblows however though since the vistdumb I have is only 32 bit the qemu will only use the 32 bit Ubuntu...  Frustrating!!!

---

### Post by dBuster on 2009-01-10
> **drs305 said:**
> You won't be able to 'upgrade' from 32-bit to 64-bit. They are separate installs. If you have trouble installing the 64-bit version from the livecd you might try using the alternate cd instead. This often works but of course depends on what problems the livecd was having in the first place.

Alrighty then...  I have downloaded and installed 64bit 8.04.1 without any hitches on the install using the alternate cd.  However upon rebooting it hangs at the same point about an interupt issue.  Something is not allowing it to proceed.  

Now downloading the 8.10 64 bit alternative to see if maybe that version will get past this issue...  My fingers are crossed!!  Would hate to have to return this laptop due to Ubuntu incompatibility!!!

***********************
Okay update time, I now have the 8.10 alternate distro installed and I have yet to make it to the desktop.  When booting into Ubuntu it hangs at the hardware initialization/loading drivers and then I get a bunch of numbers and then it just halts...

Something is not right.  I have even gone as far as removing the hp partition in which the restore is placed, do not worry I made the disks first.  So if I do not find a way to get Ubuntu working I am going to be forced to return this laptop.  I despise microsoft and this version of windblows really sucks.  Vista?!  Yeah right when I can run Ubuntu...  Just need to get it loaded.  I think though if I end up taking it back I am going to take my livecd with me and boot the pc's at the store to find the ones that will run Ubuntu!!!

So I will give it a week and suffer using windblows for that long..

---

### Post by dBuster on 2009-01-11
Well this is quite interesting.  I have downloaded and successfully ran, shh, mandriva 2009, on the laptop!!  I know mandriva is not based on the debian linux which I desire to run but I thought it was interesting that I had no issues what so ever running that flavor of distro.

I am going to hunt down today one or two debian based like Ubuntu distros and give them a shot.  I am definitely going to get away from this ridiculous vista and get back to Linux one way or another and hope that the next version of Ubuntu, JJ, will install for me!!  Anyone know of a pre-release yet???

---

### Post by drs305 on 2009-01-11
> **dBuster said:**
> I am going to hunt down today one or two debian based like Ubuntu distros and give them a shot.  I am definitely going to get away from this ridiculous vista and get back to Linux one way or another and hope that the next version of Ubuntu, JJ, will install for me!!  Anyone know of a pre-release yet???

Jaunty is in alpha2. Realizing it hasn't even made it to beta yet, if you want to give it a shot here is the download page:
[http://cdimage.ubuntu.com/releases/jaunty/alpha-2/]("http://cdimage.ubuntu.com/releases/jaunty/alpha-2/")

Good luck. I hope you get ubuntu to work for you.

---

### Post by dBuster on 2009-01-11
> **drs305 said:**
> Jaunty is in alpha2. Realizing it hasn't even made it to beta yet, if you want to give it a shot here is the download page:
[http://cdimage.ubuntu.com/releases/jaunty/alpha-2/]("http://cdimage.ubuntu.com/releases/jaunty/alpha-2/")

Good luck. I hope you get ubuntu to work for you.

Downloading it now to give it a try!  I will also look for a main jaunty page to see what changes there may be...  unless of course someone else knows of the page already? hint hint...
********************************

Okay, here is a thought, if this laptop does not have a pcmcia slot what so ever and the install starts does it not look for that hardware?  Would that possibly be causing my install to hang?  hmm found this hq-detect/start_pcmcia=false and will give that a try out on the 8.04.1.....  Any thoughts?

---

### Post by cholingo on 2009-01-11
I am having all the same problem with my cq60-210 and I have tried a lot of different things with no luck.:confused:

---

### Post by cholingo on 2009-01-12
Jaunty installed and booted on my cq60:p
thanks

---

### Post by dBuster on 2009-01-12
> **cholingo said:**
> Jaunty installed and booted on my cq60:p
thanks

Few questions for you!

1.  How stable is it?  Any noticeable bugs?
2.  Did you use the alternate cd to install or the regular one that is out now?
3.  Any issues that you had?

and the big one,

What were the configuration settings that you used to get it to boot up?  such as noapic nolapic and so forth....

Was it the 64 bit version?

---

### Post by dBuster on 2009-01-14
Jaunty didn't want to use the partitions I had already setup which was a hardy 95 gig install space and then a 5 gig swap space.  Couldn't get it to assign the swap space properly.  Ended up wiping out somehow the existing mbr in turn having me to restore the laptop to factory settings.  Actually twice I had to do that as I did not learn my lesson the first time and wanted to get back to Ubuntu in the worst way. 

I will suffer with windows vista for now and hope and pray that either the upcoming 8.04.2 will load correctly or just wait for April and Jaunty release...

So darned frustrating!!

FYI - Jaunty would run no problem in livecd mode for me!  Without any special boot configurations!!!

---

### Post by gwm on 2009-02-04
Thanks for recording all your spade work dbuster. I too have a presario cq60. I've never owned a 64bit pc before, let alone dual core. I was really looking forward to running a really zooty toot Ubuntu on it. Oh well ... 32 bit 8.10 seems to work okay. The live CD boots up fine so I'm going to install that.
:popcorn:

---

### Post by dBuster on 2009-02-05
> **gwm said:**
> Thanks for recording all your spade work dbuster. I too have a presario cq60. I've never owned a 64bit pc before, let alone dual core. I was really looking forward to running a really zooty toot Ubuntu on it. Oh well ... 32 bit 8.10 seems to work okay. The live CD boots up fine so I'm going to install that.
:popcorn:

Actually I am running Jaunty Alpha 3 right now!!!  64 bit and all!!!

Look for my other posts and you will see the work we went through to get it to work!

---

