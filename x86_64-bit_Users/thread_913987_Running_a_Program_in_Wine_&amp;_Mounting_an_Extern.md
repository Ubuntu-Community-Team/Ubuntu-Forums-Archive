---
title: "Running a Program in Wine &amp; Mounting an External HDD"
date: 2008-09-08
forum: x86 64-bit Users
---

### Post by Lee05162004 on 2008-09-08
Hi. I just installed the Ubuntu 64 bit edition on my HP laptop and I was able to get everything to work. I also installed Wine and I want to run a windows program but I'm not sure if I'm doing something wrong or not. Basically I assume that you click the .exe and it should open in Wine and prompt to install. Are there other steps I'm missing? Do I have to configure it first or something? 

Also I have a 80gb usb hdd that is formatted in ntfs and it has all my personal data on it including 40gb of music that I don't want to loose but when I start up the hdd in Ubuntu it tells me that it can't mount it. This is the message I get.

"$LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/sdb1'; Operation not supported Mount is Denied because NTFS is marked to be in use. Choose one action: Choice 1: if you have Windows then disconnect the external device by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choise 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-2g /dev / sdb1 /media/EDGE -o force. Or add the option to the relevant row in the /etc/fstab file/dev/sdb1/media/EDGE ntfs-3g force 0 0".

Again I have tried both options it gives me and it gets me no where. Thanks for your help.

---

### Post by Thelasko on 2008-09-08
> Are there other steps I'm missing? Do I have to configure it first or something?
[This link]("http://ubuntuforums.org/showthread.php?t=497332") contains just about everything you need to know about using Wine.

I'm guessing to fix the external HDD you need to boot into windows and unmount the disk, and then restart into linux. (I have no experience in this area, but it's what I hear from reading the forums)  Also, this part of the message you are receiving is the big tip:
> if you have Windows then disconnect the external device by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly.

---

### Post by Lee05162004 on 2008-09-09
Ok so I tried connecting the HDD to a Windows PC that I have and once it was connected I waited a little and then I went to the "safely remove hardware" option and it said the the device could not be stopped and to try again later. I waited and attempted it again only to get the same results. I've pretty much given up on Wine also. I just installed Virtualbox and am running Windows XP inside that to run the programs I need. I guess, if anything I will burn all the data to a dvd off of the HDD and manually move it over and then format the drive and just use it as a backup on my Ubuntu system it's just that i have about 40gb of music that's going to be a pain to burn and copy.

---

### Post by Thelasko on 2008-09-09
> I went to the "safely remove hardware" option and it said the the device could not be stopped and to try again later.
That means that some program is using the drive.  You need to figure out what program it is and close it.  It could be an anti-virus program or something similar.  [This link]("http://www.geekyramblings.org/2004/09/21/cannot-stop-device-right-now/") says Norton Utilities may be the culprit.

---

### Post by Lee05162004 on 2008-09-11
> **Thelasko said:**
> That means that some program is using the drive.  You need to figure out what program it is and close it.  It could be an anti-virus program or something similar.  [This link]("http://www.geekyramblings.org/2004/09/21/cannot-stop-device-right-now/") says Norton Utilities may be the culprit.

I was able to get that fixed. The application I wanted to run in Wine was iTunes because I have an iPod but I have justswitched over to Amarok. I've used it before but I didn't want to go through the hassle of recreating the play lists I have and stuff like that.

---

### Post by Thelasko on 2008-09-12
Excellent!  Is everything solved?  If so, please go up to thread tools and mark the thread solved.

---

