---
title: "file copy problem: copy stops and all windows close"
date: 2008-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mookinator on 2008-02-14
just installed 7.10 x64 onto my system. i have a 1Tb RAID5 array i'm trying to backup onto a 1Tb external USB hard drive. (the RAID5 is formatted NTFS) i drag the folders from the RAID array to the empty USB drive. it'll start copying then about 5 mins into it the copy will stop and the transfer windows, as well as both directory folders will just dissapear. no error message, nothing. after a few seconds the file browser will open up and display my home folder. 

any idea what's happening here? i've got a terrabyte of data i gotta transfer and many of the files are >4Gb. thank you.

~Mike

---

### Post by gsmanners on 2008-02-14
What format is the USB drive? You should be aware that FAT32 does not handle files > 4GB.

If the USB drive is a proper format, I would assume there is some problem with permissions or the /etc/fstab isn't set up correctly.

---

### Post by Yellow Pasque on 2008-02-14
You'll get better feedback from the command line rather than the GUI. Use a cp -rv command (v=verbose, r=recursive, i.e. copy all child directories, children of those directories and so on...): Example:
```
sudo cp -rv /sourcepath /destpath
```

---

### Post by chrisccoulson on 2008-02-15
It looks like Nautilus is crashing. You'd probably get more info if you run Nautilus from the terminal and try the copy with it again (as opposed to running cp direct from the command line). Are there any crash dumps in /var/crash? What about any debug logs in your home folder?

---

