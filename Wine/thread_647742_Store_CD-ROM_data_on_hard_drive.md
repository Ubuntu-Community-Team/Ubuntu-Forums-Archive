---
title: "Store CD-ROM data on hard drive?"
date: 2007-12-22
forum: Wine
---

### Post by avik on 2007-12-22
I've gotten Starcraft running great using WINE, and there don't seem to be any big issues on that front.  However, I was wondering if it was possible to store the CD-ROM data on the hard drive so I wouldn't have to put in the CD all the time.

In the WINE configuration tool, I changed the mapping of the E: drive to another folder (instead of /media/cdrom0), and I copied the CD data to that folder.  That "drive" is set as a CD-ROM drive, and the label and serial are set to the exact same as it was when WINE auto-detected the actual CD-ROM drive, so Starcraft (and any Windows program that works on WINE) should think that the folder in question is the CD-ROM drive.  However, Starcraft still asks me to insert the CD.

Reverting the mapping in the configuration tool and using the real CD works fine.

Has anyone gotten this working?  Is one of the issues that I just copied the data directly from the CD?

---

### Post by heatpumpcontrol on 2007-12-22
There are some registry settings that have to be changed. You may want to do search in the registry to locate the reference point where the game is told to search for the cd in the cdrom and change it to the respective location in wine.. I did this once for a program and it worked.

---

### Post by avik on 2007-12-22
Thanks.  I did change it, but it didn't work.  I'll see if a reboot helps (it is a Windows program after all).

---

### Post by cogadh on 2007-12-22
You need to create an ISO image of the CD, then mount that ISO in Linux and set up Wine to use the ISOs mount point as a CD-ROM drive.

---

### Post by Rizado on 2007-12-23
```
dd if=/dev/pathtocdrom of=cdimage.iso bs=2048
```
This creates a iso image of the cd.

```
sudo mount -o loop cdimage.iso /media/iso
```
And this mounts the iso in /media/iso.

---

### Post by avik on 2007-12-27
Sorry for not replying before.  I'll definitely look into that.  Thanks, all of you.

EDIT: It worked.  Thanks.

---

