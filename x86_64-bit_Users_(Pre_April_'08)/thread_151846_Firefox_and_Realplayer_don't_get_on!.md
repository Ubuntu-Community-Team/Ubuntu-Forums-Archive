---
title: "Firefox and Realplayer don't get on!"
date: 2006-03-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by drpepper on 2006-03-28
Hi I'm a newbie to this, and i'm sorry my first post is a question! I had the firefox that comes standard with ubuntu breezy, ver 1.5 i think it is. I tried to install real player. And not only did that not work (after install no new menu icons, and didnt recognise the .ram file format) but firefox stopped working too?! When I go to load it, an item appears in the task bar, saying 'Starting Firefox' and then vanishes without loading firefox. I tried re-installing the firefox by downloading ver 1.5.0.1, followed the instructions to install and it appears to complete with no errors. but when I go to load firefox I still have the same problem! I'm running AMD64 3500, 1GB ram and Nvidia Graphics. My kernel is Linux Linux 2.6.12-10-amd64-generic. Thanks for reading!

---

### Post by rplantz on 2006-03-29
If you go to my post at [http://www.ubuntuforums.org/showthread.php?p=701221&highlight=firefox#post701221](http://www.ubuntuforums.org/showthread.php?p=701221&highlight=firefox#post701221), you will see how I got Firefox to run again.

I set up a chroot environment for RealPlayer. I actually use it as a stand-alone program. With a little searching, I found the urls of the programs I like. I simply start RealPlayer and enter the url.

---

### Post by drpepper on 2006-03-30
I tried what it said in that post and alas, it didint work! I ran firefox from terminal and got the following error: 

LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory] 

LoadPlugin: failed to initialize shared library libXext.so [libXext.so: cannot open shared object file: No such file or directory] 
Segmentation fault 

so i searched google for libxt.so and tried a few things, including deleting a file in the mozilla directory called compreg.dat and two files in the /usr/lib/mozilla-firefox/plugins/ directory, with extensions .so and .xpt. these did nothing! I still got errors on both files.

---

