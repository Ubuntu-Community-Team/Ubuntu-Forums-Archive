---
title: "Major lag when copying files"
date: 2008-05-31
forum: x86 64-bit Users
---

### Post by Moustacha on 2008-05-31
Does anyone else get real big lag when copying large files? The desktop is almost unusable when copying files in the background. I'd hazard a guess at the nvidia driver, since it's pretty terrible in the first place.

Just then, was copying files in the background, go to open FF (it's already been opened a few times before so it should be in memory) and it sits there for 10 seconds or so saying opening firefox. then wait a few more seconds and it eventually comes up.
Then in amarok, i want to delete some entries from my playlist, pretty much causes it to hang (goes grey) waiting for it.

The reason why I reckon it's the nvidia driver, is when watching a video, and have a webpage load in the background it starts dropping frames everywhere and skipping back and forth over the previous second, it's horrible.

Does anyone else have any issues like this?

---

### Post by paulisdead on 2008-05-31
I've noticed this as well, even with my recent upgrade to 4GBs of 1066mhz RAM.  I too have an nvidia video card.  The chipset's an Intel P35, with a core2 duo 6420 overclocked to 3.36ghz, so that shouldn't be the bottleneck.  I've got a raptor 150 for the OS drive, and a 200GB seagate where my home directory resides, so the disks are pretty quick.

---

### Post by ingrid_ozikem on 2008-05-31
Hey paulisdead,

 I am looking to build a very similar machine to yours ( Core 2 Duo Q6600 (hopefully overclocked) with a Raptor drive + another HDD + nVidia graphics card) -- 
Could you tell me if you have performance issues like what Moustacha is talking about? Graphics problems in videos while doing something else in the background? Can you give more details on this problem with copying files -- how large a file are we talking about and how severe is the problem?

This would be a thread hijack but I'd be *REALLY* interested in hearing more from you about how your machine performs with several programs running at the same time.. maybe you could at least reply here about the video and/or HDD related aspects?

Thanks a lot!!!

---

### Post by philinux on 2008-05-31
Dead right there is. I used nautilus to copy my mobile phone pics to home and it took ages. When it had finished I also noticed it had lost the creation date. So I deleted them and thought I'll use cp with preserve timestamp.

Guess what it copied all the files in milliseconds.

I'm going to use cp or gnome-commander till nautilus is fixed.

---

### Post by simpsonsfan74 on 2008-06-27
I'm experiencing the same thing.  I have an ATI graphics card, however.  I'm trying to copy a 6 GB file from an external drive through USB to my laptop's drive.  The system becomes extremely slow and unresponsive.  I've searched the forum for over an hour and found nothing helpful.  Anyone?

Thanks!

---

### Post by tenmoi on 2008-06-28
Same here!

I was trying to copy a folder of 5.2 Gigs and Hardy 64 bit crashed halfway. I did a ctrl + Alt + F1 then sudo /etc/init.d/gdm stop - I thought gnome was interfering - and copied the folder with the cp command, still I had no luck. After a while bunches of lines of errors sprung up, and Ubuntu died like a dodo.

I had to copy 400 Meg of files per copy and ubuntu worked fine.

I am installing fedora 9 to see if it shares Ubuntu's karma.

---

### Post by Moustacha on 2008-06-28
tenmoi, that just made me think, is this a 64-bit problem? Is everyone else getting this problem using the 64-bit version?

---

### Post by tenmoi on 2008-06-28
> **Moustacha said:**
> tenmoi, that just made me think, is this a 64-bit problem? Is everyone else getting this problem using the 64-bit version?

Sad to say but it's all Ubuntu's fault. I have just copied three folders of 5 Gigs each. And all the while running firefox 3 beta and updating fedora9 64 bit I was not experiencing any lockups or crashes whatsoever.

They all share the same karma: System locks up if firefox has java and javascript on.

---

### Post by soxs on 2008-06-28
> **Moustacha said:**
> tenmoi, that just made me think, is this a 64-bit problem? Is everyone else getting this problem using the 64-bit version?

This i the 64 bit subforum, so do not expect 32 bit users to post here...

---

### Post by fjgaude on 2008-06-28
Can't say I could prove Nautilus is slow copying big files... I did two in the 12GB range and the speed was about equal to the read/write speed of the Raptor drives... in the range of 40MB/sec.

What I did notice is the modification times all changing, which is no good, no good! I now use rsync to do this kind of copying.

Hope I have the energy to report this feature as a serious bug of Nautilus.

---

### Post by doorknob60 on 2008-06-28
Maybe a nautilus problem? Konqueror and Dolphin work fine. (KDE3 and KDE4 on Kubuntu Hardy AMD64).

---

### Post by fjgaude on 2008-06-28
I think it is safe to say that it is a Nautilus problem... must file a bug report... must do that. <smile>

---

### Post by blastus on 2008-07-01
I have a Q9450 (which is about 30% faster than a Q6600) and I notice slowness also when copying files. Copying large files seems to consume a large amount of CPU resources and bogs the system down. I don't think this issue is specific to 64bit though.

---

### Post by Kilz on 2008-07-01
> **blastus said:**
> I have a Q9450 (which is about 30% faster than a Q6600) and I notice slowness also when copying files. Copying large files seems to consume a large amount of CPU resources and bogs the system down. I don't think this issue is specific to 64bit though.

I think its something about the file system. I have read that ext3 is not as good with large files as say jfs or xfs.

---

### Post by blastus on 2008-07-01
> **Kilz said:**
> I think its something about the file system. I have read that ext3 is not as good with large files as say jfs or xfs.

I think it's more than just the file system type as it happens with xfs also but xfs is faster with larger files than ext3.

---

### Post by Yellow Pasque on 2008-07-01
Please, folks, do yourself a favor and take a 10-20 minute tutorial on basic Linux/UNIX commands. The cp command is very useful. Or, if you prefer paper, I have a 'UNIX for Dummies' book that my father bought in the early 90's that got me up to speed when I went to Penn State for Computer Science and they had SPARC workstations. If you're willing to pay shipping, you can have it.

---

### Post by cariboo on 2008-07-02
I don't use nautilus to transfer a lot of files, but from what I've seen it seems to work just as fast using it as it does using a terminal or mc. In mc I've seen transfer rates of 30 to 40 MB per second. I am using a mix of ATA, SATA and eSATA drives and I can definitely see a difference between the ATA drive and the others.

Jim

---

### Post by Moustacha on 2008-07-02
I'm using XFS and when I was using cp it would bog the system down

---

### Post by bihe on 2008-10-26
Got the same problem - it's not nautilus related, just using terminal and cp.
Related? [http://ubuntuforums.org/showthread.php?t=913118]("http://ubuntuforums.org/showthread.php?t=913118")

This helped: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094/comments/112]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094/comments/112")

---

