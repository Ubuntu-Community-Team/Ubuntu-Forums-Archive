---
title: "[SOLVED] How do I UNINSTAL a program running under WINE 64"
date: 2007-07-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-07-15
I installed Serv-U FTP server under wine.  It installed fine but I can't get it to put my domain online, so I want to uninstall it.  the UNWISE.EXE uninstaller won't do it.

So how do I uninstall this FTP program properly?

Thanks

---

### Post by sfarber on 2007-07-15
Hi.

Open Terminal and write :
uninstaller

---

### Post by crjackson on 2007-07-15
> **sfarber said:**
> Hi.

Open Terminal and write :
uninstaller

What now?

---

### Post by Mr_bleu on 2007-07-15
Have you tried the Application Uninstaller in wine?  I know not all installations have that option.  
Applications>Wine>Programs>application uninstaller

---

### Post by crjackson on 2007-07-15
Yeah, did that.  It gives the same error.

---

### Post by Kilz on 2007-07-15
How many programs do you have installed to wine?

---

### Post by crjackson on 2007-07-15
> **Kilz said:**
> How many programs do you have installed to wine?

Just two.

---

### Post by Kilz on 2007-07-15
> **crjackson said:**
> Just two.

If you didnt have a lot of problems installing the other programs you can either rename (while you reinstall the applications to make sure you have all the files) or delete the .wine folder in your home folder. Wine will recreate it again when it starts. This will remove all applications installed. You could alternately delete the application folder from the .wine/c_drive/Program Files folder.

---

### Post by crjackson on 2007-07-15
> **Kilz said:**
> If you didnt have a lot of problems installing the other programs you can either rename (while you reinstall the applications to make sure you have all the files) or delete the .wine folder in your home folder. Wine will recreate it again when it starts. This will remove all applications installed. You could alternately delete the application folder from the .wine/c_drive/Program Files folder.

I actually didn't know what to do, so I wiped the partition and reinstalled the OS.  It for sure gone now... :)

---

### Post by Kilz on 2007-07-15
> **crjackson said:**
> I actually didn't know what to do, so I wiped the partition and reinstalled the OS.  It for sure gone now... :)

After doing that a few times you will get to be an expert at installing Ubuntu. :D  But just for future reference , Wine dosent actualy install applications into the linux system, but into a folder in your home folder. Wiping it out is just as effective.

---

### Post by crjackson on 2007-07-16
> **Kilz said:**
> After doing that a few times you will get to be an expert at installing Ubuntu. :D  But just for future reference , Wine dosent actualy install applications into the linux system, but into a folder in your home folder. Wiping it out is just as effective.

Okay good to know.  I just didn't want anything clogging up a registry or anything.

---

