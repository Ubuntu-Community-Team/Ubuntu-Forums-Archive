---
title: "Beginner's questions"
date: 2008-07-12
forum: Wine
---

### Post by le singe on 2008-07-12
So I have a dual boot winXP and ubuntu Hardy, and I want to install a game (HL 2) but onto my ubuntu partition directly (I no longer want to use windows much).  I managed to open the installation exe fine through wine, and I'm only getting stuck not knowing where to install to.

The installer only recognizes the C: drive, and I'm wondering if wine works such that it recognizes dual boots and I would be installing the game onto my windows partion, and then accessing it on ubuntu through wine? 

And then, is my entire drive considered the C drive, or having a partition are the two halves assigned different letters?  In that case, is it a matter of checking what letter's assigned to the ubuntu partition then typing this in at the installation prompt?

I admit I don't know these basics at all, but I did look around a bit.

---

### Post by upchucky on 2008-07-12
currently I am able to use gnome commander to browse to my windows partitions and the various programs and files, then right click them, then choose to start them with wine. so far all the ones I have tried are starting and running in wine just fine.

---

### Post by Kinst on 2008-07-14
In your home folder there's a hidden folder called .wine. Your fake wine C drive is:

/home/you/.wine/drive_c/

---

### Post by jomiolto on 2008-07-14
The drives can be assigned the way you want to. By default C: drive points to /home/username/.wine/drive_c and there is also a Z: drive that points to root (ie. just / ). So, if you haven't changed the settings, and install games on C: drive, then it will be on your Ubuntu partition.

You can change the settings from Applications -> Wine -> Configure Wine (select the Drives tab) if you wish, although, at least for me, it doesn't allow changing the C: drive location.

---

