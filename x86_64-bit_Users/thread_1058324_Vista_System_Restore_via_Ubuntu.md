---
title: "Vista System Restore via Ubuntu"
date: 2009-02-02
forum: x86 64-bit Users
---

### Post by dpmanthei on 2009-02-02
Hi everyone,
2nd poster here.  The issue:

I have VMware 6.5 on vista ultimate 64bit running on a Intel DP45SG mobo, Intel Q6600 proc, and 4gb DDR3 G.Skill.  I attempted an OS install in VMware only to find "boot failure, press any key to continue" when I rebooted.  Messed something up, not sure what or how.  EDIT: I must point out that the drive doesn't even show up in the bios any more, kinda scary!

Anyways, I have Linux Mint 6 on another drive.  It boots fine, and I CAN access the original 100gb drive...I can see files, open docs, etc.  Can I run the system restore program for vista using Wine in Mint (ubuntu essentially)?  I have Wine, and I have copied the system32 folder from an XP install to try to help with compatibility issues and required dll's.  But System Restore will not execute, it tries for a second, then it gives up without throwing an error message or anything.

I would just use my original Vista disk but when I boot from it I do not have the restore option, it just goes straight to the installer setup.  I wanted to just head to thepiratebay and get an ISO there that has the restore feature, but the site acts like its down, hopefully not forever.

Another reason to hate vista and the disgusting life-sucking monster that is Microsoft...."boot failure, press any key to continue"...CONTINUE WHAT?!?! MORONS!  IT WON'T FRIGGIN BOOT. 

thanks a lot for any help, I personally feel that the folks on this forum are among the most intelligent and helpful on the net, you guys are the tip of the sword!

Dylan M

---

### Post by cariboo on 2009-02-02
First off all you have to find out why the drive doesn't show up in the BIOS, go to your hard drives manafacturers web site and download the diagnotic tools and run them on the hard drive that Vista is installed on.

You can't run Windows restore from Wine, remember wines is and application layer that allows you to run some windows programs. It has nothing to do with Windows.

Jim

---

### Post by dpmanthei on 2009-02-02
SOLVED!

Thanks for your input Jim!

Just as you were contributing your post i solved it...somehow.  I was in Linux Mint and rummaging around my drive trying to figure out what to do.  I looked at the volume in GParted to check the flags and device info so I ran a volume check on each partition on that drive.  That somehow solved it, excellent!  Linux hands Windows its A$$, again.

For the record, I did not change IDE cables, jumper settings, PCI slots, IDE channels, or bios settings.  I planned on troubleshooting each of these one at a time, but didn't have to.  I am guessing it was an MBR issue?

Although the problem is solved, I am dumbfounded as to what would happen to the drive that is so catastrophic that it doesn't even show up in the bios...I mean some failed drives will even show up in the bios, depending on the type of failure.  

Thanks a lot to all of you readers and thinkers, and thanks Jim for your input,

Dylan M

---

