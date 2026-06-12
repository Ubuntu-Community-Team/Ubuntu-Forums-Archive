---
title: "Login Failure - HELP!"
date: 2006-09-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-09-22
I was trying to use rsync to copy everything on my laptop's Ubuntu-64 partition (hda2 -- hda1 is a swap partition) to an external 60 GB USB disk. Rsync appeared to do the job, but it ended with an error that the disk was out of space. The USB disk had lots of space, but I also got several popups in the corner of the screen that I was running out of disk space. In other words, evidently it was hda2 that was running out of space, not the USB disk. I don't understand that, as all rsync should be doing is reading the files. 

When rsync finished I discovered that the keyboard and mouse were locked up. I had no choice but to hit the power button. When I restarted I got the following error message when I tried to log in:

"GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any event, it is not possible to log in. Please contact your system administrator."

I used Ctrl-Alt-F1 to exit to a shell, whereupon I logged in and then deleted a number of large files that I knew I had backups of elsewhere -- about 300 MB worth. Then I went back to the login screen and tried to log in again. But I still got the same error message.

I went back to the shell and did "sudo chown jjj:jjj /home", thinking that perhaps permissions had gotten screwed up. The command executed normally, but I still cannot log in.

A possible part of the problem: There appears to be a file or folder (colors are not working in the shell) named "--exclude=media." This was part of the rsync command I used. I have tried to remove this file or folder, but I cannot do so. 

Someone please give me some suggestions! I am stuck having to write this on a Windows desktop because I can't get into my Linux computer!

---

### Post by John Jason Jordan on 2006-09-22
OK, I solved the problem and it was a stupid mistake that caused it. I tried to delete this message and thread, but can't figure out how to do so. The scissors icon says "edit/delete" but all it seems to allow is edit. 

So if there is a moderator around, please nuke this thread. Thanks.

---

