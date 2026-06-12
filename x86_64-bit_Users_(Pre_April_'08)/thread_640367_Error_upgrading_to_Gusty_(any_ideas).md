---
title: "Error upgrading to Gusty (any ideas)"
date: 2007-12-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by lavikl on 2007-12-14
got this messsage :

> Please report this bug against the 'update-manager' package and include the following error message:

'E:Dynamic MMap ran out of room, E:Dynamic MMap ran out of room, E:Error occurred while processing phpgroupware-headlines (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

Lavik

---

### Post by crjackson on 2007-12-14
> **lavikl said:**
> got this messsage :



Lavik

Do you have packages installed that are from sources outside the repositories?  I would backup the home directory and do a clean install of Gutsy rather than upgrade.

---

### Post by lavikl on 2007-12-14
I don't have any important files anyway... I'm just "playing" with linux to get used to it...

I'm using a dual-OS system (win XP and Linux), how do i clean up the linux OS so i could fresh start with Gusty ?

---

### Post by Sukarn on 2007-12-14
> **lavikl said:**
> I don't have any important files anyway... I'm just "playing" with linux to get used to it...

I'm using a dual-OS system (win XP and Linux), how do i clean up the linux OS so i could fresh start with Gusty ?

If you want to do a fresh install of Gutsy and don't want to backup your current data, then just get a gutsy disc, and during install select manual editing of partition table.
Set your current linux partition to be formatted and mounted at **/**

---

