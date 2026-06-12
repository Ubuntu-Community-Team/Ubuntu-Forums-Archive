---
title: "Uninstalling without install disc"
date: 2006-10-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Vekemi on 2006-10-22
I'm trying to uninstall Ubuntu from my laptop. I had originally installed it only as a test to see if I liked it or not, and I don't particularly feel an immediate need to have Ubuntu over Windows. However, I do not have a Windows XP OS repair disc, only a recovery disc, so I'm unable to access the repair console to get grub to stop loading. I don't want to remove the partitions yet either because then grub will get an error.

Can anyone help me?

---

### Post by catlett on 2006-10-22
You could try GAG. It should install and give you access to windows without needing grub.
First download and run GAG.[http://gag.sourceforge.net/](http://gag.sourceforge.net/) If it works and gives you access to windows, then go ahead and delete ubuntu's partitions. Then you can reformat them as data partitions for windows. Use gparted live for the partition work. Download the iso and burn it to disk, then boot to it. It is a live cd. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Vekemi on 2006-10-23
I don't have a floppy drive on my laptop for GAG to run on.

---

### Post by catlett on 2006-10-23
> **Vekemi said:**
> I don't have a floppy drive on my laptop for GAG to run on.

When you extract the compressed file, there will be an iso as well as rawrite. Just burn the iso to a cd and boot. Here is the folder after it is extracted.
[IMG]http://i80.photobucket.com/albums/j180/brthomas503/gag.jpg[/IMG]

---

