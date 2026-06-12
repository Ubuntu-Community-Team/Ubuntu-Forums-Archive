---
title: "64 bit raid 0 install via alternate disc?"
date: 2008-03-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by derailed1 on 2008-03-31
Hi everyone-

I new to ubuntu but not new to linux.  I've been playing around with Fedora through the years with a dual boot xp machine.

Upgrade time is near and its time to start from a clean install.  Completely clean hard disks.  So I read up on 64 bit and have decided to try ubuntu 7.10 64.  I know 8.04 is coming out next month but I can't wait that long.

I will be buying to identical 620 gig hard drives.  I want to configure them in raid 0 fashion.  The reason why I want to do that is to speed up the computer since I will be running mythtv heavily.

Now for the question.  Is there an easy way to install ubuntu 64 and configure raid easily?  I have read up that you can use the alt disc but I don't know it it will be more of a headache headache or not.  Can someone please confirm and help me out a little bit?  :)

I'm excited, my first pure linux box!

---

### Post by stefangr1 on 2008-03-31
Yes it's really easy! The best option is to make a software RAID0 array using the Ubuntu alternate install cd. Otherwise, switching to another motherboard could result in total data loss. 

Also, I warn you NOT to use the beta version of 8.04, see this post:
[http://ubuntuforums.org/showthread.php?t=740007](http://ubuntuforums.org/showthread.php?t=740007)

For a good tutorial of how setting up a RAID1 array works, see:
[http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)
The steps for RAID0 are basically the same, exept for off course the fact that it's RAID0 :)

When you partition your disks, you need to set up a separate /boot partition (50mb should be enough), configured as RAID1, while swap, / and the other partitions are RAID0.

---

### Post by fjgaude on 2008-03-31
You can't boot, AFAIK, using raid0... there's no way for the OS to get started. raid1 is okay, but not recommended, at least not by me.

---

### Post by stefangr1 on 2008-03-31
> **fjgaude said:**
> You can't boot, AFAIK, using raid0... there's no way for the OS to get started. raid1 is okay, but not recommended, at least not by me.

I agree with you that RAID0 is not to be recommended for its riskyness (total data loss if something goes wrong), and I wouldn't personally consider using it. I assume that derailed1 has already informed himself about the advantages (speed) and disadvantages (reliability) of RAID0. If that's not the case: bear in mind that it is, like bungeejumping and paragliding, meant for risk seeking people. If you're not one of those, don't use it.

Having said that, it's a fact that there are quite some people that use RAID0 nevertheless, and it's definately possible in Ubuntu. Only, you can't boot from a RAID0 array, so that you have to be sure to put /boot in a small separate RAID1 array.

---

### Post by derailed1 on 2008-03-31
Thanks guys for the links.  The raid 1 abstract is actually the guide I will be using.  I will be using 7.10.  Anything newer seems buggy.  I have been debating the risk/performance and I'm stumped.  I will be turning this into a mythbox and I will be needing as much speed as possible for HD content.  On the other hand, losing one disk means losing information from both.  What to do?

---

### Post by stefangr1 on 2008-03-31
> **derailed1 said:**
> Thanks guys for the links.  The raid 1 abstract is actually the guide I will be using.  I will be using 7.10.  Anything newer seems buggy.  I have been debating the risk/performance and I'm stumped.  I will be turning this into a mythbox and I will be needing as much speed as possible for HD content.  On the other hand, losing one disk means losing information from both.  What to do?

You do realize that the bottleneck for HD playback is your cpu? I have an E6750@2667Mhz, and I  can play only about half of the 1080p h264 files that are available trough Usenet. I don't think a raid 0 array is going to help you with this.

---

### Post by derailed1 on 2008-03-31
I guess you are right.  I figured that having raid0 will help with juggling huge files around.

---

### Post by wcorey on 2008-04-06
> **stefangr1 said:**
> I agree with you that RAID0 is not to be recommended for its riskyness (total data loss if something goes wrong), and I wouldn't personally consider using it. I assume that derailed1 has already informed himself about the advantages (speed) and disadvantages (reliability) of RAID0. If that's not the case: bear in mind that it is, like bungeejumping and paragliding, meant for risk seeking people. If you're not one of those, don't use it.
.

Oh c'mon. think of it as a dual controller single disk with double the capacity. You buy a good brand of disk, and it lasts. I've only lost one disk as soon as the Dell warranty was up. This is what backups are for. If you put two 250GB drives in raid1 you have 1 250GB drive with a mirror image just in case. 

Speaking for myself, I purchased the Dell Raid0 configuration because I wanted 500GBs with dual paths so multiple vms could be running simultaneously without bottlenecking on the single drive.

Vista but more importantly Fedora8 installed and ran just fine (to the degree Fedora runs fine) in the bios controlled raid 0 LVM ienvironment. So there is no reason why 8.04 couldn't install and run just fine in that environment. This is what I am looking for. Going with the "Ubuntu just works" mantra, there is no reason why a user must manually install Linux in order for it to see and use a raid0 LVM,

---

### Post by wcorey on 2008-04-06
> **stefangr1 said:**
> Having said that, it's a fact that there are quite some people that use RAID0 nevertheless, and it's definately possible in Ubuntu. Only, you can't boot from a RAID0 array, so that you have to be sure to put /boot in a small separate RAID1 array.
Perhaps that explains my grub 2 error when I first installed U8.04 with the alternate cd into the existing raid0 lvm. But, again, Fedora had no issues with the two drive Raid0 LVM. Given that neither should Ubuntu and I am at a loss to explain the difference.

Walt

---

### Post by wcorey on 2008-04-06
> **derailed1 said:**
> I guess you are right.  I figured that having raid0 will help with juggling huge files around.

If you haven't committed to this yet I disagree with the RAID1 argument. Ask yourself this, when was the last time one of your hard drives failed? What is your existing backup plan? Even though hard drives per GB are inexpensive (relatively) how do you feel about having a 500GB drive spinning ildely for days/weeks/years on end, 'just in case'? It's 500GB of space you can not use for anything. Here's the thing as it relates to the Windows world. Virtually any third party software you install on a given box is forever tied to that box. This is why I strip the box down to only what is requred and ghost it. As the hardware improves I create a VM and restore that image, with saved apps to the newer, better, faster, cleaner, (insert Tim, the ToolMan Taylor, laugh here). and those apps benefit from the speed increase. This is why I went with raid0, I want that other 512GB of usable space for the VMs. But, you know, your mileage may vary.

Walt

---

### Post by GTengineer on 2008-04-06
Some Intel chips (like the P35 mobos) allow you to run Intel Matrix RAID where you have have part of it RAID0 and part RAID5. I am running a 4 hard drive RAID setup like this with 70GB RAID0 for OS and things I don't mind losing and 650GB of RAID5. That said I have been running RAID0 for over 6 months and have had zero problems.

---

### Post by fjgaude on 2008-04-06
> **GTengineer said:**
> Some Intel chips (like the P35 mobos) allow you to run Intel Matrix RAID where you have have part of it RAID0 and part RAID5. I am running a 4 hard drive RAID setup like this with 70GB RAID0 for OS and things I don't mind losing and 650GB of RAID5. That said I have been running RAID0 for over 6 months and have had zero problems.

Would you give us more details of how you do this? With raid0 as the boot partiton, for the OS? You are talking about Linux and not Windows, eh?

Thanks you.

---

### Post by Jovec on 2008-04-06
I'm going to throw my hat in with those who said avoid Raid 0.  Although rare, you do double your chance of data loss as either drive failing will lose the data on both.  Backups are not much of an option here since this is going to be a HTPC and backing up that much data is not pratical for most users ( My HTPC setup is at 500GB and growing).  Software Raid 0 does not provide the speed benefits many seem to think it does, and in any case HDD speed with a 7200RPM 3Gbps Sata drive is not going to be your bottle neck in HTPC applications.  It will write plenty fast enough to record/encode and read fast enough to playback.  For 1080p and x.264 content, your bottleneck will be your CPU and how much your video card can offload playback.  If you don't want to mirror or need the extra space, you can simple mount your second/third drives as normal (example: I mount one drive under videos/movies and another under videos/television).

---

