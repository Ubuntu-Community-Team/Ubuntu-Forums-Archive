---
title: "[SOLVED] Move to 64 from 32 keeping /home...?"
date: 2007-12-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by gn2 on 2007-12-31
I currently have 32-bit Xubuntu 7.04 with a separate /home partition.

I have decided it's about time I went 64-bit, I've tried out the 64-bit Live CD and it's working fine.

Is it possible to install 64-bit Xubuntu 7.10 and keep the existing /home partition without formatting it?
(I know how to re-install keeping the /home partition using 32-bit)

I would be OK with just deleting all the hidden files in /home, apart from the Mozilla folder which I would like to keep, but would it have to go and be replaced by a 64-bit version?

---

### Post by insane_alien on 2007-12-31
yes it is possible.

when you use the installer on the live CD and you get to the partitioning stage, select the manual option. just use the same scheme as the current one(so no repartitioning) select the mount points and only click the format option on the root drive and make sure it is unticked in the /home partition.

this should work fine(did for me).

if you boot up and get errors you may need to delete the configuration files in the home folder or soemthing(i can't remember the exact rememdey but it only happens rarely anyway)

---

### Post by Kilz on 2007-12-31
> **gn2 said:**
> I currently have 32-bit Xubuntu 7.04 with a separate /home partition.

I have decided it's about time I went 64-bit, I've tried out the 64-bit Live CD and it's working fine.

Is it possible to install 64-bit Xubuntu 7.10 and keep the existing /home partition without formatting it?
(I know how to re-install keeping the /home partition using 32-bit)

I would be OK with just deleting all the hidden files in /home, apart from the Mozilla folder which I would like to keep, but would it have to go and be replaced by a 64-bit version?

Yes, its been done before. But as always backup what you cant afford to loose just to be safe.

---

### Post by gn2 on 2007-12-31
Thanks both, I will be going ahead tomorrow after I make sure that my weekly back-up is in place on the external drive.

---

### Post by thekat on 2007-12-31
I have done that several times in the past.. more on servers.. i.e. my email server..
Just use the same username during installation..

I am currently loading 64-bit Ubuntu as I type this.. I did have Kubuntu 32 previously..
About all I save is my profile.. since I don't want to have to re-configure ThunderBird and FireFox.. 

good luck
tk

---

### Post by ~LoKe on 2007-12-31
I just did this last night.  Be sure to select your mount points and make sure you're not FORMATTING ANYTHING except / and swap.

For me, this is how my partition layout was

/dev/sda1 233GB **/home** -- No format
/dev/sda2 10GB **/** -- Format
/dev/sda3 514MB **swap** -- Format

---

### Post by ARhere on 2007-12-31
Ignore This Post

---

### Post by gn2 on 2008-01-01
Hmmm....

Flash problems...

Despite being assured that after installing, Flash installation would work, it hasn't.

The plug-in finder has found and installed Adobe Flash, but it will not work, when I attempt to use Flash on YouTube I get a message saying I need Flash installed.

It is installed I've checked Synaptic and it's listed as having been installed.... Confused.

---

### Post by Kilz on 2008-01-01
When Gutsy was released Flash was a feature of 64bit that "just works". Then Adobe released an update. The developers are just taking forever to fix a minor problem. But you dont have to wait. If you do a search or even look at the top page of this section odds are you would find [this post of mine. ]("http://ubuntuforums.org/showthread.php?t=476924")

---

### Post by gn2 on 2008-01-01
> **Kilz said:**
> When Gutsy was released Flash was a feature of 64bit that "just works". Then Adobe released an update. The developers are just taking forever to fix a minor problem. But you dont have to wait. If you do a search or even look at the top page of this section odds are you would find [this post of mine. ]("http://ubuntuforums.org/showthread.php?t=476924")

Thanks Kilz for your help with this issue, I ran the older r48(recommended) script for the older version and it's working just fine now.

I'm a happy chappie! :)

---

