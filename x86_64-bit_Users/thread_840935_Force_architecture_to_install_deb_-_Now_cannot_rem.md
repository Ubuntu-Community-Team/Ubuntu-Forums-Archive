---
title: "Force architecture to install deb - Now cannot remove!"
date: 2008-06-25
forum: x86 64-bit Users
---

### Post by Ozdemon on 2008-06-25
Based upon the forum at Mailwasher, I downloaded and attempted to install mailwasher_2.0.0_ubuntu6.10_7.04.  Install failed with the i386 error (I have an amd64 laptop).

So I found the terminal commmand to force the install.  That worked, but Mailwasher doesn't.  Now I can't remove the damned thing.

I have tried the rm command and the -r, but I think I am not getting the name of the program right.

How do I find out the exact name of the application for the purpose of using a command to get rid of it?  I have tried a few variations of the pkg name, but all failed.

All help appreciated.

---

### Post by pixel :-) on 2008-06-25
first try 
sudo apt-get install ia32-libs
this will install 32bit libraries,it may work with them.
and then reinstall mailwasher

You can try the windows version under wine
sudo apt-get install wine

for removal
sudo dpkg -r mailwasher

rm is for files,like erase or delete in dos(don't remember what it was).

---

### Post by Ozdemon on 2008-06-26
Thanks a heap!  Mailwasher removed.  I will try again to install it with your first suggestion once my blood pressure is closer to normal.

---

