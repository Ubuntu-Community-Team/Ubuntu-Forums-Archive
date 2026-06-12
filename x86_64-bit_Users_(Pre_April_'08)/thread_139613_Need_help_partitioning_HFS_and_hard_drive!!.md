---
title: "Need help partitioning HFS and hard drive!!"
date: 2006-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Madman68 on 2006-03-04
I tried to resize my HFS (I think thats what it is) hard drive on my iBook G4 with the How To from here: [http://ubuntuforums.org/showthread.php?t=89960]("http://ubuntuforums.org/showthread.php?t=89960") When it was finished it told me there was an errer saying something like it failed becouse something wasn't moved or something. I followed all the directions exactly as the How To said but still got the same errer. This was really disappointing. I have an 80GB hard drive in my iBook and I am only using around 70GB so I wanted to assign the other 10 GB to Ubuntu. I tried resize it but it didn't work and luckely it didn't do anything to the OS X partition. I just wanted to know if anyone had another way to do this, if you do PLEASE let me know. I'll try to get the actual errer message up as soon as I can. Thanks!

---

### Post by jdp on 2006-03-04
You seem to be running close on free space.  Are you sure the size you tried to make the OSX partition is larger than the space you have used?  You might try leaving a free GB ro so on the OSX side, and just assign Ubuntu 9GB or less.  Ubuntu will run great with anything over 4GB anyway.

---

### Post by Madman68 on 2006-03-04
ok, thanks, I try that and post my results!

---

### Post by BoneKracker on 2006-03-04
From your duplicate post about this, it sounds like you may have hosed your data while trying to resize the partition.  Did you back up your important files before re-partitioning?

Were you able to complete the repartitioning and reboot?

---

### Post by Madman68 on 2006-03-04
No, my mac os x data is still there, I am posting this form OSX. It says the resizing has failed because an extent was not replaced. It also says that some data files (doesn't give names) haven't been replaced. Then it just gives me the parted prompt again. I've tried and retried but can't seem to get it to work. Is there another free way to resize my OSX HFS+ partition so I can use the free space to install Ubuntu?

---

### Post by Madman68 on 2006-03-06
I tried and retried to folow the directions in my original post but it keeps giving me the same errer message. Just before it starts to try to resize the partition it gives me a message that goes something like> I have detected an HFS+ partition with characteristick I have not incountered befor.Even thought it says this it doesn't do anything to the mac partition becouse that is what I am posting this from. It says this everytime I try to resize my mac os x partition.Any ideas as to what this means?

---

### Post by linear on 2006-03-06
1. Have you tried using Disk Utility to check for errors on your HFS+ partition?
 
2. Absolutely sure journalling is turned off?

---

