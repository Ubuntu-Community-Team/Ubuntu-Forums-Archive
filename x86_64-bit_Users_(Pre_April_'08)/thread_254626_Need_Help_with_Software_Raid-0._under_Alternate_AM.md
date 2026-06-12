---
title: "Need Help with Software Raid-0. under Alternate AMD64 install disk."
date: 2006-09-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ausus on 2006-09-10
Hi All,

Did someone managed to install raid-0 with Ubuntu alternate amd 64 disk.
Is their a how-to some where.
I'm stuck grub does not now where he wants to be installed.
I posted a simalar tread under Hardware Help.
So far now reply.

regards

:frown:

---

### Post by Ausus on 2006-09-10
Hi All
This is how far I got.

I need help pease.

Steps which I followed:
Step 1)
Bios set two 80 gig's as raid 0.
Motherboard see's raid system.

Step 2:
Used alternate amd64, boot via CD-Rom.
When through various stages off setting up system.

Step 3:
Select two HD and set them up as Raid HD.(Shows up as K-Raid)

Step 4:
Create now raid partion.
HD-1 /boot 10Gig select as boot,/ root 30Gig, 39Gig /home and 1Gig /swap.
HD-2 setup same as above.

Step 5:
Use software raid tool now.
Set up 4 raid devices if I may call it that way.

Step 6:
Select each created sotware raid device and configure.
As ext3 etc.The only thing which I battle with is.Their is no-way that I can tell the /boot partion to be bootable.Under step-4 is the only place where I can select bootable.

Step 7:
Finish off.
Now the fun starts, grup-loader does not now where to be installed.It wants to be installed hd0.

So I need some help.

Regards
I not in front of my PC to supply more info.:frown:

---

### Post by RAOF on 2006-09-11
Check out the FakeRAID howto: [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)
It covers exactly what you want to do.

---

### Post by kuja on 2006-09-11
I'm not sure it does. It looks like he's trying to setup software raid with mdadm, not use the motherboards built-in fake-raid controller and use a device mapper raid setup.... 

Besides... the fake-raid setup is a very big pain in the butt. (I set it up a while back, so I know from experience.)

Anyway, for the RAID0 setup specifically , to get all the data in, and to have it bootable, is a bit tricky, but certainly doable. 
I'll have to find the howto I saw for doing this with RAID0... I'll post again once I find it.

---

### Post by Ausus on 2006-09-12
Hi RAOF and kuja,

Correct me if I'm wrong, you need internet access.
I followed a Finish chaps installation guide.
He is using Raid-1 settings.
I tried Raid0 and 1, no success.

I get to to the point where grub get's up to 50%, then it sit their for ever.

It seem's my Raid partions never get mounted.
For my late reply, I was away to Cape-Town on company business.

It seems what ever you do in linux the more difficult stuff, you need internet access. The installation assumes you have a available connection to the internet.


Regards](*,)

---

### Post by kuja on 2006-09-12
You shouldn't need internet access to set up software raid with the alternate cd (fake raid using the live cd is another story, it would require an internet connection). It's rather difficult to get your software raid setup to boot though, when the root partition is a part of the software raid. I forget where I found the workaround for it, but if I remember right it involves something along the lines of setting it up on a small, dummy partition, then copying things to the permanent raid md device later (in short, a pain). 

Now if I could just find that little howto....

---

### Post by Ausus on 2006-09-12
Hi kuja,

Quote:
[HTML]You shouldn't need internet access to set up software raid with the alternate cd [/HTML]

Yes i'm using the alternate cd for indstallation.

I'm using Nforce4 chipset, could this be a problem.

When i'm done with the raid partioning, then the software setup continues with al the next steps.
Then at last grub is being installed up to 50% this is where it sits for hours.](*,) 
This happened with Raid0 and Raid1.

About the Finish quy who also just used alernate install CD.
After the installation he carry's on how to test your Raid1 setup and by disconnecting one drive, etc.


Regards:frown:

---

