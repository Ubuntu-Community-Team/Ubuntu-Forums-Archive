---
title: "ubuntu 64 bit in raid 0"
date: 2009-11-14
forum: x86 64-bit Users
---

### Post by smiley1958 on 2009-11-14
i have read that it is hard to install i9n raid mode using the onboard raid controller if i us a add on pci raid controller would it be better

---

### Post by smiley1958 on 2009-11-14
and what are the speed gains if there is any and is it worth it to  run in raid 0

---

### Post by stevepaul on 2009-11-14
It's not actually that hard to install to a Raid0 configuration ...

You need to use the Alternate ISO though ..

In my experience rather than trying to create a partition and install to it, it is far easier to let the install do it itself by choosing to install to the largest 'Free' space ...

Be aware that there was an issue installing Ubuntu 9.10 AMD64 version to Raid (not sure if its fixed yet) it crashed my system !!...

However what I did was to install 9.04 and update to 9.10, had no problems using this approach ...

As for the advantages of Raid0, it is supposed to be faster because it uses *'striping'* which means it writes alternately to each disk in the Raid array configuration ..

Only problem with this is that there is no 'fault tolerance', if one disk crashes you lose the whole lot ;-(

You'll find this interesting reading ...

[http://www.acnc.com/04_01_00.html](http://www.acnc.com/04_01_00.html)

---

### Post by smiley1958 on 2009-11-15
thanks and i will read that now

---

