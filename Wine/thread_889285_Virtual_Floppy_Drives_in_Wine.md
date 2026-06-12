---
title: "Virtual Floppy Drives in Wine?"
date: 2008-08-13
forum: Wine
---

### Post by Tindytim on 2008-08-13
I have some SATA drivers I need installed in order to install my XP boot. Unfortunatly, it will only install to a floppy (already tried various other methods of installation).

How would I set up a virtual floppy drive so that the executable I need will install it's floppy image on it, and I can copy the files? I'm an Ubuntu noob so something simple would be preferable.

---

### Post by desertboy on 2008-08-14
Are you trying to install XP on wine as that will not work you virtualbox (Vmware style) which has an option for images as drives.

I slipstreamed my XP install to add sata drivers it was a pain in the a** makes terminal look like aqua.

---

### Post by Tindytim on 2008-08-14
No, I just need the SATA drivers, It's not going to be a virtual setup, it's a long story.

I need something that I can trick this .exe into believing is a floppy. Then I can take the files off of it.

---

### Post by dfreer on 2008-08-15
> **Tindytim said:**
> No, I just need the SATA drivers, It's not going to be a virtual setup, it's a long story.

I need something that I can trick this .exe into believing is a floppy. Then I can take the files off of it.

Off the top of my head, I believe this is what you want to do:
Open up winecfg, select the "Drives" tab. You should already see your ~/.wine/drive_c/ mounted as C:\, you'll want to create one that points A:\ to either your actual floppy disk drive folder or simply to a folder on your desktop. Either way, wine will see it as a Floppy, and when you execute the *.exe that contains your drivers you can tell it to extract them to the virtual floppy A:\ drive.

Hope that makes sense :D

EDIT: As I understand of it, the OP has a *.exe that contains the drivers required to install windows XP onto his SATA drive. The *.exe requires a floppy drive to extract the files onto, and the OP wants to know how to create a virtual Floppy drive in wine. Correct me if I'm wrong.

---

