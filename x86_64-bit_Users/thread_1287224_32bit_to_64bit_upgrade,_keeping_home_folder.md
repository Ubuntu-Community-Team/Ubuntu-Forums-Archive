---
title: "32bit to 64bit upgrade, keeping home folder"
date: 2009-10-09
forum: x86 64-bit Users
---

### Post by theparticle010 on 2009-10-09
I am planning on upgrading to 64 bit, and I'm writing this not to get advantages / disadvantages, with 4gb of ram, and a descent cpu I really want to upgrade, not to mention that 32 bit ubuntu lags a lot even when comared with my 64 bit vista so I kinda think that it's time to upgrade... but I hate messing around with the all in one home and root directory that is by default provided in most distros, although I would of been lost as a new user myself if a seperate home partition was the default option ^_^ now... here is what I want to do:

Backup home dir to seperate hard drive : done easy :)
Delete home dir : not done as of writing of this.
New Partition, Placing all home dir's files inside
Having both my current and, a new 64 bit ubuntu install ( of the same version 9.04 ) dual booting of of the hard drive, reading the same home dir.

Now I know in theroy this is quite possible, but the only problem I have is setting up grub, ( as I am not good with boot managers. ) Editing the /etc/fstab file(s) although I have a basic understanding I still want a small guide to make sure I get it right ^_^

The only other question I have is when I install the 64 bit version I want to be able to set it up where I only have a root account before I edit the /etc/fstab file to mount the home dir partition, if this is possible.

Any further information you might be able to add would be greatly appreciated cause I don't usually have good luck with things "just working" on the first try. ](*,)

---

### Post by dcstar on 2009-10-10
> **theparticle010 said:**
> I am planning on upgrading to 64 bit, and I'm writing this not to get advantages / disadvantages, with 4gb of ram, and a descent cpu I really want to upgrade, not to mention that 32 bit ubuntu lags a lot even when comared with my 64 bit vista so I kinda think that it's time to upgrade... but I hate messing around with the all in one home and root directory that is by default provided in most distros, although I would of been lost as a new user myself if a seperate home partition was the default option ^_^ now... here is what I want to do:

Backup home dir to seperate hard drive : done easy :)
Delete home dir : not done as of writing of this.
New Partition, Placing all home dir's files inside
Having both my current and, a new 64 bit ubuntu install ( of the same version 9.04 ) dual booting of of the hard drive, reading the same home dir.

Now I know in theroy this is quite possible, but the only problem I have is setting up grub, ( as I am not good with boot managers. ) Editing the /etc/fstab file(s) although I have a basic understanding I still want a small guide to make sure I get it right ^_^

The only other question I have is when I install the 64 bit version I want to be able to set it up where I only have a root account before I edit the /etc/fstab file to mount the home dir partition, if this is possible.
........

When you install the second Ubuntu, simply specify the correct partition (which you will have noted when running your original Ubuntu system) as the /home partition. That will set the correct fstab entry.

There are many HOWTOs on setting up separate /home partitions.

---

### Post by mikewhatever on 2009-10-10
Grub can be a bit tricky with multiple hdds, but if you have a problem with it, just post the relevant info.
I don't know why the 32bit installation lags, but it's probably not because of 32bit, which probably means switching to 64bit will not solve the problem.
As you might know, the root account is disabled in Ubuntu.

---

### Post by theparticle010 on 2009-10-11
Thanks, I have had no problem with grub, and the 64 bit version still lags a little bit on 10gb file transfers, but not even close to crashing the entire system like ubuntu 32 bit did, recreating the home folder on a separate partition was no problem at all and as for after the 64 bit install itself, I had no problems with telling it where the partition was, it was much easier than dual booting with windows... the last time I tried that I wiped out the disk... but that was a long time ago, now if I use Ubuntu it's on a separate hard drive. And I haven't used windows in over a year.

---

