---
title: "Moved files and now nothing works.."
date: 2007-08-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by ShaolinF on 2007-08-09
Hi,

Well I'm quite pi$$ed off because Linux is giving me a hard time. I wanted to move some icons from my desktop to the usr/share/icons folder and this is exactly what I did:

cd Desktop/OSX_Theme/icons
mv /* /usr/share/icons

I did that, and all my custom layout modifications dissappeared, and whenever I try to open ANYTHING I get the following error: 

Could not launch application
Details: Failed to change to Directory '/home/admin' (No such file or directory)

Anyone know how to fix this ?

---

### Post by ShaolinF on 2007-08-09
Argh, restarted and getting error 15 ! I've got some very important work whcih by the looks of it I have lost!! Argh!

---

### Post by aysiu on 2007-08-09
Uh, moving everything in /* is bad.

/* means everything in the entire installation. It does not mean everything in the directory you're currently in.

So you moved everything from / to /usr/share/icons, at least the files you had permission to move. If you're modifying /usr/share/icons, I'm assuming you did this as root, so you basically moved *everything* frm / to /usr/share/icons, which is not possible, since /usr/share/icons itself is a subset of /. So I basically have no idea what happened.

---

### Post by ShaolinF on 2007-08-09
Thanks, can I get my work back ? Im not bothered about the OS, I just want my work. I'm using vmware which makes it alittle more complicated because I can't boot it up as a second drive/ Man, this sucks.

---

### Post by aysiu on 2007-08-09
> **ShaolinF said:**
> Thanks, can I get my work back ? Im not bothered about the OS, I just want my work. I'm using vmware which makes it alittle more complicated because I can't boot it up as a second drive/ Man, this sucks.
Oh... that *is* tricky. If it's in VMWare, you can't really boot up a live CD and mount the partition to get the data... or can you? 

If it's a .vmdk file, maybe [this](http://ubuntuforums.org/showpost.php?p=1928339&postcount=5) might help.

Best of luck!

---

### Post by ShaolinF on 2007-08-09
tbh I have no idea what the guy is going on about in the link. I quite new to linux as you probably guessed.

---

### Post by aysiu on 2007-08-09
Are you running a Ubuntu VM session inside of a Windows environment or inside another Linux? Or inside Mac?

---

### Post by ShaolinF on 2007-08-09
Inside windows.

---

### Post by aysiu on 2007-08-09
> **ShaolinF said:**
> Inside windows.
Maybe [this](http://www.petri.co.il/virtual_mount_vmware_virtual_disk_without_vmware.htm) might help, then.

---

### Post by ShaolinF on 2007-08-09
Thanks, Ive mounted the partition but when I try to access it I get a "Drive is not formatted. Would you like to format now ?". Im guessing this is because ubuntu  is using a partition which windows cannot read ? Any ideas?

---

### Post by aysiu on 2007-08-09
> **ShaolinF said:**
> Thanks, Ive mounted the partition but when I try to access it I get a "Drive is not formatted. Would you like to format now ?". Im guessing this is because ubuntu  is using a partition which windows cannot read ? Any ideas?
I'm not sure, but *maybe* this might help (fingers crossed for you):
[http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by ShaolinF on 2007-08-09
Ah, no it didn't. :(

EDIT: Cant I do a repair install like XP ?

---

### Post by aysiu on 2007-08-10
> **ShaolinF said:**
> Ah, no it didn't. :(

EDIT: Cant I do a repair install like XP ?
You might have been able to ordinarily, but I don't know what to do with a screwed up virtual machine installation.

---

### Post by ShaolinF on 2007-08-10
> **aysiu said:**
> You might have been able to ordinarily, but I don't know what to do with a screwed up virtual machine installation.lol, a year's worth of c++ programming going down the drain! 
What's the procedure for repair install ? I'll duplicate the files and test it out.. Also, Im installing ubuntu 7.0.4 32bit now, so anything I could try on this setup ?

One thing I would have really appreciated now before I got into this mess is video tutorials, I personally don#t like reading long articles and rather press the play button and have the developer go through the OS  with me. And as ubuntu is now going mainstream it would be ideal that the ubuntu team start making easier ways for newbies, otherwise they'll either give up or find out the hard way.

---

### Post by aysiu on 2007-08-10
I don't really know the *exact* procedure for repairing installations, but I do know there is a *repair* option on the Ubuntu CD.

As for video tutorials, there are plenty out there. One is a website devoted to Ubuntu video tutorials:
[http://ubuntuclips.org/](http://ubuntuclips.org/)

But you can also search for the word *Ubuntu* on Google Videos or YouTube.

---

### Post by ShaolinF on 2007-08-10
Ok, I'll give it a shot.

Thanks for the links. I couldn't find them on your website.

---

### Post by ShaolinF on 2007-08-11
Well, Im going to try something alittle different. I've moved my corrupt VM to a linux OS and want to mount it as a VM but don't know how to. I heard that the vmware mount utility is built into linux but I can't seem to find it.. Its meant to be called vmware-mount.pl or something along those lines. Anyone have ideas on how to install and run it ? Note that Im still a newbie and don't understand complicated stuff yet, so a plea for you guys to keep it simple.

---

### Post by ShaolinF on 2007-08-11
Ok, I managed to find out how to get the vmware-mount.pl working. Its working now, but I dont know how to use it. Any ideas?

---

### Post by jpkotta on 2007-08-11
Shouldn't it be possible to use a live CD to boot the VM, then mount the virtual disk from the live CD?  You can make it boot from a live CD by setting the virtual BIOS to boot from the CD drive first, and specifying an .iso image as the CD drive.

---

