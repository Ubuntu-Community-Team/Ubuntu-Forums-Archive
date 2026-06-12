---
title: "guide in installing outkafe from cappy"
date: 2008-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Script Warlock on 2008-01-05
Re: outkafe
Quote:
Originally Posted by boyet
do you have any guide for me on how to install outkafe for my ubuntu gibbon? i haven't decided yet on what type of processor i'll be using for my internt cafe this coming february..but sure enough ubuntu is my server....
Download [http://outkastsolutions.co.za/outkas...d=13&Itemid=31](http://outkastsolutions.co.za/outkas...d=13&Itemid=31)
Extract outkafe-linux-5.2.3-x86_64.run.bz2
Change to the directory in terminal and run
Code:

sudo sh outkafe-linux-5.2.3-x86_64.run

If you get library errors try getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
Code:

sudo getlibs -64 -l libraryname.so.1 anotherlibrary.so.2

if that doesn't work and it needs 32-bit libraries instead use
Code:

sudo getlibs -l libraryname.so.1 anotherlibrary.so.2
:guitar:

---

