---
title: "Moving /lib"
date: 2008-03-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by nschubach on 2008-03-17
I have something interesting.  Figuring that I would store all my programs and data in the /usr and /home folders, I figured a nice small / partition would be good enough.  So I made it 256MB.  What I should have done is create a separate /lib folder as well when I installed.  I didn't.  Anyway.  I figure with the ability to mount folders, I'd partition off 3GB of some of my remaining drive and mount it to /lib.  I ran our of room on my / mount.  I didn't realize it until I started the install for Hardy.  The only thing that did not install was the new kernel and it's dependents because they ran out of space.  :(

I created the partition (/sdb11 if it matters) and mounted it to /libnew, cp -r -p /lib/* /libnew/*, edit etc/fstab and set /dev/sdb11 to mount to /lib (copying the options form the root mount.  I don't remember what it is now, but it seemed to make sense, default, onerror=ro or something) and I rebooted.  The machine would boot to the splash screen and stop.  I figured, ok.  I screwed up.  Boot to the CD, mount the drives, make sure all the files are in the new partition by copying them again, recursive, same rights.  I renamed /lib to /libold to make sure it's trying to boot off the new /lib partition.  Nothing.  It froze even earlier.  I forget where it stops, but it just freezes on boot.

I'm sure it has to do with a mount library file or something that's in /lib causing my boot to fail.  Besides re-installing the OS again, does anyone have any clues on how I can get it to properly boot to the new /lib partition?  Is there any particular command I'm missing to compare the ...sdb11 mount and /libold to make sure I got all the files?  Is there a particular set of files that I can copy out of the /lib to another folder so they will be seen?

---

### Post by Ehtetur on 2008-03-23
Hi nschubach... I have some bad news for you... You can't move /lib to a partition separate from the root file system. The kernel needs /lib /sbin/ /dev /etc all to be on the root partition in order to boot...

The kernel reads /etc/fstab after it's in userspace and then it's too late to "see" the new /lib mount point... and you'll get the problems you're seeing...

I think you may have a reinstall in your future.   :evil:

---

