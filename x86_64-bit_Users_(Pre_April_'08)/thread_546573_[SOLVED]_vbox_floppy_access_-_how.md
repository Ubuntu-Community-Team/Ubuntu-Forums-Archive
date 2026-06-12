---
title: "[SOLVED] vbox floppy access - how?"
date: 2007-09-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-09-09
:confused:

Okay, I installed XP under vbox for a test drive.  I'm impressed.  One problem though.  I have my settings to mount the floppy drive.  The drive light comes on and never goes off.  Even so, I can't access the files on the drive.  I need to install an old DOS program, and the drive is misbehaving.

I installed the item under the device menu that lets me run full screen, and everything seems to work great except the floppy thing.

Oh, and also it can't see the ntfs drives attached to the system.  Is there anything I can or should do about that?

Thanks...

---

### Post by crjackson on 2007-09-09
.

---

### Post by crjackson on 2007-09-10
Anyone?

---

### Post by maybeway36 on 2007-09-10
It's probably a problem with the floppy drive.
As for the hard drives, are they real physical hard drives, or are they virtual hard drives?

---

### Post by crjackson on 2007-09-10
> **maybeway36 said:**
> It's probably a problem with the floppy drive.
As for the hard drives, are they real physical hard drives, or are they virtual hard drives?

The floppy drive works fine in real mode under Ubuntu and fine in XP real mode (not on vbox).  I'm thinking there is a setting somewhere I don't have right.

The hard drives are physical drives.

---

### Post by crjackson on 2007-09-11
[COLOR="Red"][SIZE="4"]Any other ideas?[/SIZE][/COLOR]

---

### Post by the_nite_owl on 2007-09-11
I only started looking at VirtualBox last night so I may not have any relevant input but...

Try putting the disk into the drive then telling VirtualBox to mount the drive before you start up the VM for Windows.  
It may be a matter of declaring a resource be available inside of vbox prior to trying to make the VM see it.

---

### Post by crjackson on 2007-09-11
> **the_nite_owl said:**
> I only started looking at VirtualBox last night so I may not have any relevant input but...

Try putting the disk into the drive then telling VirtualBox to mount the drive before you start up the VM for Windows.  
It may be a matter of declaring a resource be available inside of vbox prior to trying to make the VM see it.

Heading off to work right now, but I will gave that a shot when I get home tonight.  I can only hope it's that simple.

---

### Post by dabl on 2007-09-11
I haven't looked at VBox, but since I installed Gutsy Tribe 5, I find the VMWare Player in the repos is broken, and VMWare Player V. 2.0 requires a package named "glibc" that isn't in the repos, so I'm thinking I might give VBox a look while I'm waiting for the Gutsy release.

Has anyone benchmarked a Win app running under VBox against the same operation in a native Win installation?  I found mine ran 95% as fast in VMWare Player as it did on a native Win installation, and I'm wondering how VBox stacks up against that.  :)

---

### Post by crjackson on 2007-09-11
> **dabl said:**
> I haven't looked at VBox, but since I installed Gutsy Tribe 5, I find the VMWare Player in the repos is broken, and VMWare Player V. 2.0 requires a package named "glibc" that isn't in the repos, so I'm thinking I might give VBox a look while I'm waiting for the Gutsy release.

Has anyone benchmarked a Win app running under VBox against the same operation in a native Win installation?  I found mine ran 95% as fast in VMWare Player as it did on a native Win installation, and I'm wondering how VBox stacks up against that.  :)

I personally have not but, while searching for a resolution to my floppy problem I did come across a post where the OP said he got 100% identical performance on vbox xp with winamp and other encoders, as compared to native xp.

---

### Post by SteveHoffmanUK on 2007-09-11
I've only had VBox installed for a couple of days, so am no expert, but you might check this out:

After installing a Windows XP virtual machine in VBox, I had a lot of problems accessing my USB devices. I eventually sorted the problem, and the detailed solution isn't relevant here because USB devices are different from floppies, but one part of the solution was to unmount my USB devices in Ubuntu. This was necessary to allow my XP VM to install them.

Once I did that (as well as other USB-related steps), they all installed. After that, I don't need to unmount them in Ubuntu - if they are mounted, when the XP VM starts, it just grabs them and their icons disappear from Ubuntu.

If your floppy is mounted in Ubuntu, try unmounting it, then see if you can get XP to install it. With my floppy, incidentally, I found I had to ask VBox twice to mount it - the first time I heard a click, but I got an error message asking me to insert a floppy into the drive (there was already one in it), so I closed it and tried again and the second time it mounted and read the floppy.

---

### Post by crjackson on 2007-09-11
> **SteveHoffmanUK said:**
> I've only had VBox installed for a couple of days, so am no expert, but you might check this out:

After installing a Windows XP virtual machine in VBox, I had a lot of problems accessing my USB devices. I eventually sorted the problem, and the detailed solution isn't relevant here because USB devices are different from floppies, but one part of the solution was to unmount my USB devices in Ubuntu. This was necessary to allow my XP VM to install them.

Once I did that (as well as other USB-related steps), they all installed. After that, I don't need to unmount them in Ubuntu - if they are mounted, when the XP VM starts, it just grabs them and their icons disappear from Ubuntu.

If your floppy is mounted in Ubuntu, try unmounting it, then see if you can get XP to install it. With my floppy, incidentally, I found I had to ask VBox twice to mount it - the first time I heard a click, but I got an error message asking me to insert a floppy into the drive (there was already one in it), so I closed it and tried again and the second time it mounted and read the floppy.

Okay, thanks for the information.  I'll be looking into this in the next day or so.

---

### Post by dabl on 2007-09-12
Yes, thank you SteveHoffmanUK for that information.

I attempted my first VBox installation last night, on Gutsy Tribe 5+, and hosed things up real good in the process, but it was educational as well as "character-building".  I now know a whole bunch of things not to do, and I think it's going to go on just fine tonight.  Note to self: Xgl is NOT ready in Gutsy! :mrgreen:

---

### Post by crjackson on 2007-09-12
> **SteveHoffmanUK said:**
> I've only had VBox installed for a couple of days, so am no expert, but you might check this out:

After installing a Windows XP virtual machine in VBox, I had a lot of problems accessing my USB devices. I eventually sorted the problem, and the detailed solution isn't relevant here because USB devices are different from floppies, but one part of the solution was to unmount my USB devices in Ubuntu. This was necessary to allow my XP VM to install them.

Once I did that (as well as other USB-related steps), they all installed. After that, I don't need to unmount them in Ubuntu - if they are mounted, when the XP VM starts, it just grabs them and their icons disappear from Ubuntu.

If your floppy is mounted in Ubuntu, try unmounting it, then see if you can get XP to install it. With my floppy, incidentally, I found I had to ask VBox twice to mount it - the first time I heard a click, but I got an error message asking me to insert a floppy into the drive (there was already one in it), so I closed it and tried again and the second time it mounted and read the floppy.

Well I've tried everything I can think of.  I can get it to read the floppy, but if I have to insert a second floppy during the session, it does not recognize I have changed or even removed the 1st disk.  In fact, the floppy light comes on the second it's mounted in vbox and won't go off at all unless it's unmounted in vbox.

I'm giving up and removing vbox, and wine.  I have a duel boot system with xp so I can use that.  I just wanted to eliminate windows.  I guess that'll have to wait for a while.

---

### Post by AnRa on 2007-09-12
Make an image file of the floppy disk ```
dd if=/dev/fd0 of=floppy.img
``` and mount it under VirtualBox! ;)

---

### Post by crjackson on 2007-10-19
********************   Solved    ********************

Install Gutsy.....

---

