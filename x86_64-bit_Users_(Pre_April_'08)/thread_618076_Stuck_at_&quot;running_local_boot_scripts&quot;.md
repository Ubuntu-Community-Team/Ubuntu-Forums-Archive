---
title: "Stuck at &quot;running local boot scripts&quot;"
date: 2007-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by MI123645 on 2007-11-20
I'm installing Ubuntu 7.10 and somewhere in the installation it loads local boot scripts and it just stops there. I pressed enter but it only moved my cursor down a line and didn't help. 

My specifications:

E2160 Processor
P5K Premium mainboard
2GB of RAM
2 SATA Hard drives
ATI 2600XT

Thanks!

---

### Post by jon557 on 2007-11-21
I get the exact same problem. All installed ok, but pauses on Running local boot scripts (/ect/rc.local) when i try to boot it up.

In fact, asfter starting writing this it has done something. I said password and then 60 timedout, and wants me now to login.

Just logged in, but I only get a command line. I will investigate further...

Jon

---

### Post by jon557 on 2007-11-22
hmm...

Well after speaking to a Linux expert at uni, he said ubuntu was based around a network and to get any updates it needs a network, well the internet.

And in my case startx is not installed and most likely needs updating from the internet.

It says I need to type in: apt-get install xinit
when i enter startx to try and get the gui going.

but it keeps saying to put the cd in, but this laptop doesnt have a cd or floppy!

Anyways, that my update.

Jon

---

### Post by jon557 on 2007-11-23
ubuntu is ****, im getting bored of this.

---

### Post by StJack on 2007-11-23
I'm having the same problem.  Fresh install of server 7.10 on an old K7 machine.

I thought at first that it might have been the pci wireless card, but i took it out and had the same problem.

Tried startx, but it's not installed.

I tried: apt-get install xinit

Reply:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I didn't remember setting a root password during installation, except for the mysql server.  

I logged in with the user i created during installation, and the password i set for that user worked, so i got a command prompt.

I tried to su, using all the passwords i might have used and somehow not remembered ten minutes later, including the one i remember setting for the mysql server, to no avail.

My instinct is to reinstall and make sure that I get a chance to create a root password so i can at least install an x server if for some reason install doesn't install it.

Any ideas?

My specs, as far as I can remember or see with the thing running: AMD K7950 processor, maybe 512M, an 80G Maxtor HDD and what I think is a chaintech mobo.

update:  I should mention, no network connection right now.  my dog ate my only long network cable.  :(

---

### Post by StJack on 2007-11-23
See this thread:

[http://ubuntuforums.org/showthread.php?t=413975&highlight=boot+script+hang](http://ubuntuforums.org/showthread.php?t=413975&highlight=boot+script+hang)

---

