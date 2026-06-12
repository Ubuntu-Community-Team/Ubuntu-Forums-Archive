---
title: "Sharing uTorrent settings with Windows &amp; Wine"
date: 2008-07-28
forum: Wine
---

### Post by alsoknownas on 2008-07-28
Right here is my problem (and the annoying thing is I read a guide on how to do it a while back), I can install uTorrent in wine and get it working, what I want to do is it to work alongside the copy I run in Windows.

An example of this would be that a torrent I started downloading in uTorrent in wine, would resume from the same place.

For people who don't know much about torrenting, I want the diretory for the configuration to be the same in Windows and Wine.

I have already been running uTorrent in Windows XP for a few months now, but would like to run them side by side in my dual-boot.

---

### Post by xnostradamusx on 2008-07-28
try making both windows and linux with the same download folder and make both of them run the torrent link first so the tracker would be saved inside the programm utorrent.

then when youre using your windows just right click on the file and choose force recheck after it finish it will resume where the linux has stop downloading the file and vice versa.

hope it could help you

---

### Post by alsoknownas on 2008-07-28
Hmm, could work but was thinking of a more automated solution, where the the **Application Data/uTorrent** folder was the same for both systems.

Currently the Windows uTorrent settings folder is /media/XP/Documents and Settings/username/Application Data/uTorrent and the wine uTorrent settings folder is /home/username/.wine/drive_c/windows/profiles/username/Application Data/uTorrent - I want wine path to be the same as the Windows path.

If that makes any sense at all :p

---

### Post by kdorf on 2008-07-28
Make a symlink from the wine path to the windows path.

cd "/home/username/.wine/drive_c/windows/profiles/username/Application Data/"
ln -s "/media/XP/Documents and Settings/username/Application Data/uTorrent" uTorrent

---

### Post by Icculus on 2011-08-30
> **kdorf said:**
> Make a symlink from the wine path to the windows path.

cd "/home/username/.wine/drive_c/windows/profiles/username/Application Data/"
ln -s "/media/XP/Documents and Settings/username/Application Data/uTorrent" uTorrent


I am currently trying the same thing (as I resurrect this topic from 2008)

I think I've attached a screenshot of uTorrent when it starts running. It has a black background and seems to crash quickly with this error:


fixme:ntdll:server_ioctl_file Unsupported ioctl 940cf (device=9 access=1 func=33 method=3)
err:ntdll:RtlpWaitForCriticalSection section 0x5185e8 "?" wait timed out in thread 0009, blocked by 001d, retrying (60 sec)


I created a symbolic link in .wine/drive_c/users/USERNAME/Application\ Data to the correct location. Also, I added in the .wine/dosdevices a soft link to my media drive location (Drive E). I have tried different permutations of having drive_c and c: mounted to their respective locations, all to the same avail. If I run uTorrent without these changes it seems to run fine.


I'll play around with the settings a little bit more and look deeper into the errors, but if someone has any advice I'd appreciate it.

---

