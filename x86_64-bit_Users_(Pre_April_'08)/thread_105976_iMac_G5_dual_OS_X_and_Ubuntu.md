---
title: "iMac G5 dual OS X and Ubuntu?"
date: 2005-12-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by ctt1wbw on 2005-12-19
It's been a while since I used Ubuntu.  I had a dual boot system on my Dell laptop and I can't remember if Ubuntu install cd partitioned my drive or not.  Does the Mac install disk allow you to do this, or do you need to do it prior to install?

---

### Post by tmeier on 2005-12-19
You are best to start with the OS X CD and make two partitions one for your OS X and the other for ubuntu.  The OS X CD starts and brings you to the first screen at this point go to File and select Open Disk Utility.  Disk Utility will allow you to repartion and format your hard drive.  Format the OS X partition with hfs+ and leave the ubuntu partition as free space.  MAKE SURE TO INSTALL OS X FIRST.  Once OS X is installed, the put in your ubuntu CD and boot off of the CD and it will find the free space and partition it for you and make the install process very painless.  Just remember to do os X first, if you don't you will have to find a way to edit the yaboot.conf file.  That is how it worked best for me.  Good Luck.

---

### Post by ctt1wbw on 2005-12-19
Thanks for that help.  I would like to repartition and lose my OS X side.  I have way too much time in that setting it up...  Possible?

---

### Post by felix_stegerman on 2005-12-19
From [http://sowerbutts.com/linux-mac-mini:](http://sowerbutts.com/linux-mac-mini:)
A word of caution: I found that Disk Utility would sometimes "lose" some space, presumably this is a bug in the software. Check that the partition sizes add up to the right amount when you're done resizing them. And remember than an 80 "marketing-gigabyte" disk contains only 74.5 "real-gigabytes". I had to quit and re-start Disk Utility several times before I managed to make it work right. I think the trick was to do the last partition first, then start down from the first one.

I can confirm this. I'd recommend using the Ubuntu partitioner if you can.


Felix

---

### Post by tmeier on 2005-12-20
Did you want to keep your current os X install?  If so, you can back it up using Carbon Copy Cloner from "http://www.bombich.com" and backup your entire os X setup to a second hard drive (internal, external or ipod) then repartition your hard drive as we have stated before and then boot from your second hard drive and using Carbon Copy Cloner again to setup your os X without losing anything, and then you can install Ubuntu into the proper partition.  That is how I setup my Powerbook.  If you need more specifics let me know.

---

### Post by pauljwells on 2005-12-20
I would agree absolutely with tmeier. Carbon Copy Cloner is an essential piece of software for OSX. I regularly use it to backup my OSX partition (after every point upgrade, use it for a few weeks and see if anything breaks - if it does, copy back the previous version from the backup, if it doesn't, backup this new version). I seem to remember that although you want to install OSX before Ubuntu, you want to install it on the second partition and leave the freespace on the first partition for Ubuntu to find. Is this still necessary? I don't know, but it's what I did and it worked fine. I had random system hangs on a G4PB, eventually cured by removing powernowd. Your mileage may vary...

---

