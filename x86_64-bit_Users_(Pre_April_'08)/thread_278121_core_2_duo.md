---
title: "core 2 duo"
date: 2006-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by dhawk312 on 2006-10-15
I just bought a sony fe-790 with a core 2 duo.  i read and think that the core 2 series intel chips support 64-bit processing by default but can someone clarify this for me?  and if so should i install the ubuntnu amd64 fork on my pc?
-dhawk312

---

### Post by kuja on 2006-10-15
Yes, it supports 64-bit. Whether you want to install a 64-bit OS or a 32-bit OS is up to you.

---

### Post by dhawk312 on 2006-10-15
thanks for the reply.  i want to install a 64-bit os since i paid for this brand new tech there is no point to use stuff my old technology would run.  is the 64-bit fork ANY different than the 32-bit cosmetically?

---

### Post by RAOF on 2006-10-15
> **dhawk312 said:**
> thanks for the reply.  i want to install a 64-bit os since i paid for this brand new tech there is no point to use stuff my old technology would run.  is the 64-bit fork ANY different than the 32-bit cosmetically?

No.  Also, it's not a fork (a word which has a specific meaning).  It's exactly the same code, built for x86-64, in the same way as the PPC version is exactly the same code, built for (older) Macs.

The problems you might run into are that programs which aren't in the repositories may be more difficult to install, and closed-source, proprietry stuff will require work-arounds.

Your new processor **also** runs 32bit code faster than the old one; the performance gains for x86-64 over x86 shouldn't be noticable on a typical desktop usage.  On the other hand, encoding/decoding, and other such CPU intensive tasks **do** see substantial performance gains.

---

### Post by DJiNN on 2006-10-16
> **RAOF said:**
> Your new processor **also** runs 32bit code faster than the old one; the performance gains for x86-64 over x86 shouldn't be noticable on a typical desktop usage.  On the other hand, encoding/decoding, and other such CPU intensive tasks **do** see substantial performance gains.

I have just bought (But not collected yet) 2 new systems. 1 is an AMD 64 X2 system with a 4400 X2 CPU and the other is a Core 2 Duo Laptop. 

I will be putting Ubuntu on both if possible. Would it be less hassle at this stage, to just stick the normal 32 bit version of Ubuntu on, rather than trying to get the 64 bit version working, or does the 64 bit version work just fine most of the time?

Standard desktop useage.... nothing fancy. Any help or info would be much appreciated.

DJiNN

---

### Post by RAOF on 2006-10-16
> **DJiNN said:**
> I have just bought (But not collected yet) 2 new systems. 1 is an AMD 64 X2 system with a 4400 X2 CPU and the other is a Core 2 Duo Laptop. 

I will be putting Ubuntu on both if possible. Would it be less hassle at this stage, to just stick the normal 32 bit version of Ubuntu on, rather than trying to get the 64 bit version working, or does the 64 bit version work just fine most of the time?

Standard desktop useage.... nothing fancy. Any help or info would be much appreciated.

DJiNN

Yes, it'll be less hassle, but only for things outside the repositories.  If all you need are not-rediculously-obscure open-source programs, you shouldn't have any problems with the 64bit version.

Pretty much anything closed-source requires workarounds, because they tend not to build 64bit binaries.  This also applies to Wine, because it needs to run 32bit Windows binaries.

So, if you don't want Flash, or Wine, or Skype, etc, the 64bit version is just better.  If you **do** want some of those, then it's a trade-off between ease-of-use and performance gains.  And on a standard desktop load, the performance gain will not be substantial.

---

### Post by dhawk312 on 2006-10-16
thank you guys for all the feeback.  i have been trying to install ubuntu 64 and xp pro 64 bit edition.  xp pro wont even start the installer and ubiquity has stalled 3 times at about 54%.  this is my first venture into 64 bit processing.  should i be having these problems installing a 64 bit OS with an Intel T7200 Core 2 Duo @ 2.o Ghz?

---

### Post by DJiNN on 2006-10-17
> **RAOF said:**
> Yes, it'll be less hassle, but only for things outside the repositories.  If all you need are not-rediculously-obscure open-source programs, you shouldn't have any problems with the 64bit version.

Pretty much anything closed-source requires workarounds, because they tend not to build 64bit binaries.  This also applies to Wine, because it needs to run 32bit Windows binaries.

So, if you don't want Flash, or Wine, or Skype, etc, the 64bit version is just better.  If you **do** want some of those, then it's a trade-off between ease-of-use and performance gains.  And on a standard desktop load, the performance gain will not be substantial.

Thanks for the info RAOF, it's very helpful. I haven't even seen a 64bit system running yet so i don't know if i would benefit at all. But i'm sure that i'll benefit from just having the normal 32 bit running a lot faster, and that will do OK for me, for now. 

I take it that the 686 kernel (With SMP support) will be the one to go for, and that both cores can & will run (Independently?) on a 32 bit system, or am i missing something important?

Thanks once again for your time & help.

DJiNN

---

### Post by RAOF on 2006-10-17
I'm running Edgy now, so I'm not sure if the Dapper kernels have also been changed to the -generic system.

If so, the kernel you want is in the **linux-generic** package.  If not, the kernel you want is in the **linux-686-smp** package.  You don't miss out on anything running the 32bit version.

---

### Post by DJiNN on 2006-10-17
> **RAOF said:**
> I'm running Edgy now, so I'm not sure if the Dapper kernels have also been changed to the -generic system.

If so, the kernel you want is in the **linux-generic** package.  If not, the kernel you want is in the **linux-686-smp** package.  You don't miss out on anything running the 32bit version.

Thanks for the quick reply.  That's good to hear. As i'll be doing a fresh install on both machines, i'm not at this moment sure if i'll be installing Dapper or Edgy, as i don't know if the difference is worth the potential problems that could arise with an Edgy install. 

Good to hear that i won't be missing out on anything with the 32 bit version. :D

---

### Post by bdb on 2006-10-17
> **kuja said:**
> Yes, it supports 64-bit. Whether you want to install a 64-bit OS or a 32-bit OS is up to you.

Wow I am confused now.  So I can install a 32 bit OS on my AMD64?  I thought I had to install a 64 bit.

Now I feel like a real noob.  I am not even sure now if I have a 32 bit Ubuntu installed or a 64 bit.  How do I find out?

I installed the  [AMD64 alternate ISO]("http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-alternate-amd64.iso")

Thanks for any help.

---

### Post by kuja on 2006-10-17
> **bdb said:**
> Wow I am confused now.  So I can install a 32 bit OS on my AMD64?  I thought I had to install a 64 bit.

Now I feel like a real noob.  I am not even sure now if I have a 32 bit Ubuntu installed or a 64 bit.  How do I find out?

I installed the  [AMD64 alternate ISO]("http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-alternate-amd64.iso")

Thanks for any help.
Go into a terminal and type "uname -m"

---

### Post by kuja on 2006-10-17
:???: > **bdb said:**
> Wow I am confused now.  So I can install a 32 bit OS on my AMD64?  I thought I had to install a 64 bit.

Now I feel like a real noob.  I am not even sure now if I have a 32 bit Ubuntu installed or a 64 bit.  How do I find out?

I installed the  [AMD64 alternate ISO]("http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-alternate-amd64.iso")

Thanks for any help.The AMD64 iso would install the 64-bit version. If you're still unsure for any reason type "uname -m" in a terminal.

---

### Post by Bardia on 2006-10-18
I'm a fairly new linux user, and completed 5-6 installs of 64bit Ubuntu on my custom build MS-1057 notebook with a T5600 Core 2 Duo.  I didn't have any trouble at all other than just being a noob and breaking stuff several times trying to figure it out :)

The flash thing seems to be a rather difficult problem in 64bit Firefox, but installing a 32bit version of Firefox with 32 bit plugins was simple and worked flawlessly.

I tried installing the 32bit version of Ubuntu once when I got frustrated with some of my mistakes, but it actually only activated one core of the processor, so in my opinion the 64bit version is a bit easier to set up for a new Ubuntu user with Core 2's than the 32.

---

### Post by DJiNN on 2006-10-18
> **Bardia said:**
> 
I tried installing the 32bit version of Ubuntu once when I got frustrated with some of my mistakes, but it actually only activated one core of the processor, so in my opinion the 64bit version is a bit easier to set up for a new Ubuntu user with Core 2's than the 32.

Hmmm, that's interesting. I thought that the 32 bit version would run both CPU's, & that's why you had to install either the 686 kernel with SMP support. or the Generic Kernel, which i think is in Edgy but possibly not Dapper. 

This is all speculation on my part of course, as i haven't even installed it once yet. I'm trying to find out as much as possible before i do the first (of many?) installs in about a week or so. :)

---

