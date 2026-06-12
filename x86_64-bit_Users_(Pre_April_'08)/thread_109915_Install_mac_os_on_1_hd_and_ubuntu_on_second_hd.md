---
title: "Install mac os on 1 hd and ubuntu on second hd?"
date: 2005-12-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by rancam on 2005-12-29
I currently have (3) hard drives in my 1.467 g4 quicksilver and am trying to install linux on one of my hard drives that I have spare.  Every thing I read is regarding setting up partitins and having the linux installed on the 1st partition and mac os x on the second.  

I have been unable to find any information for an installation for my setup.  What do I need to do be able to dual boot both?  From what I read on the wiki yaboot installs automatically, will it be able to be adjusted to select which internal hd to boot off?

Thanks in advance for any help,

rancam

---

### Post by Rxke on 2005-12-30
I have an old B&W G3, which I use on a daily basis, that has its primary disk (disk0) as OSX, and secondary (disk1) partitioned partially (X)Ubuntu and partially OSX (Hfs+) formatted. Works like a charm for me. I see no reason a secondary disk being 100% Ubuntu would cause problems...

During install, you get a choice to completely wipe a disk, in your case you'll get to choose from three disks, select the one you want and then let it automatically partition it for you. 

Disclaimer: this works for me, but I run 10.3, not 100% sure it works with 10.4 (but again, I really see no reason why it wouldn't)

Let us know if you're succesful or not.

---

### Post by autocrosser on 2006-01-01
Works just fine for me--I triple-boot--Dapper-testing, Breezy--OS10.4--all configured thru one yaboot.conf--I color-coded my yaboot(s) on both Breezy & Dapper--So I'm sure that the yaboot.conf (in my case) is in Breezy's /etc--took some time to get it sorted out so my wife could use it:rolleyes:........I've got Breezy on one internal with a OSX4 install & Dapper on another internal with a "backup" install of OSX4--I seperated my /home(s) on seperate partitions in case I have a crash or want to update my system--keeps my user accounts easy to backup also.

---

### Post by Rxke on 2006-01-01
[QUOTE=autocrosser]I color-coded my yaboot(s) on both Breezy & Dapper--So I'm sure that the yaboot.conf (in my case) is in Breezy's /etc-[/QUOTE]

How did you do that? would be a nice how-to, heehee.

---

