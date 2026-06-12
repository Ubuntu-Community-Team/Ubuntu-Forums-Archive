---
title: "Dual boot xp and Ubuntu"
date: 2007-05-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by gitosh on 2007-05-30
Hey people, I'm new to Ubuntu and linux for that matter. I have an IBM desktop computer 40 GB with two partions (C and D) and it's currently running windows xp proffesional. I need to install ubuntu-7.04-desktop-i386 (dual boot). I've rebooted the computer with the Ubuntu cd, and Ubuntu is loaded, but when I double click on the install icon, nothing happens. The current partion is NTFS. Any ideas will be appreciated.

---

### Post by jusmurph on 2007-05-31
Did you do an md5 check on the downloaded iso?

---

### Post by ronocdh on 2007-05-31
> **jusmurph said:**
> Did you do an md5 check on the downloaded iso?
Absolutely crucial. This is to confirm that the ISO you downloaded is as it should be. Usually torrent files are sound, but you can always check again with the checksum or by choosing "Verify disc integrity" on the main screen of the live CD.

---

### Post by gitosh on 2007-05-31
> **jusmurph said:**
> Did you do an md5 check on the downloaded iso?

yes I did and it was ok

---

### Post by laredo7mm on 2007-05-31
Try going to the top drop down menu under System, then Administration, there should be a menu item for Install.  Select install and see if it will run.

I remember having issues with the Install Icon on Feisty Alpha so I have always done the above method ever since without any problems.

Hope that helps.

---

### Post by ronocdh on 2007-05-31
> **laredo7mm said:**
> Try going to the top drop down menu under System, then Administration, there should be a menu item for Install.  Select install and see if it will run.

I remember having issues with the Install Icon on Feisty Alpha so I have always done the above method ever since without any problems.

Hope that helps.
Try this, but then there's always the "alternate" install disc, which I myself like to use because it's faster. It's a text-based installer, but you shouldn't have any problem with it. If something's not loading right on the live CD, the alternate may be your answer (that's why it's there!). Good luck.

---

### Post by gitosh on 2007-06-04
Hey people, I used the alternate CD installlation successfully apart from 'install other softwares' section which was failing. so I decided to continue with the installation and install these other softwares later. The problem is instead of being presented with a GUI after rebooting my computer, I'm presented with bash. Well, as I said earlier I'm totally new to linux and I don't know how to operate in a command enviroment. How do I load the GUI? all help will be appreciated.

---

### Post by ©TriMoon® on 2007-06-04
You might try to install the graphical desktop :)
[FONT="Fixedsys"][SIZE="3"]sudo apt-get install ubuntu-desktop[/SIZE][/FONT]

---

### Post by gitosh on 2007-06-05
hello guys, I'm back again. I tried 'sudo apt-get install ubuntu-desktop' and all went well upto 93% mark. The system gave me some errors and so I decided to perform a CD integrity check, and this is the error that I got. "The ./pool/main/t/ttf -indic-fonts/ttf-bengali-fonts_0.4.7.3_all.deb file failed the md5 check sum verification. your CD_rom or this file may have been corrupted" I did the check on a different computer and the same error showed up so I concluded that the file may have a problem. But I did an md5 checksum on the ubuntu iso image I dowloaded and it's fine, so I concluded there could have been a problem when I was writing it to CD. So my question is, is there and alternative to installing the GUI from the CD? Any help will be greatly appreciated as usual. Thanks people

---

### Post by fumduck on 2007-06-05
[URL="http://apcmag.com/5162/the_definitive_dual_booting_guide_linux_vista_and_xp"]

this is the guide i used maybe that will hgelp you.. I thought the partition needed to be  ext3 or ext2..??? But I am a noobie...   Peace goodluck  It took me a couple different tries  I had an extra harddrive to test was my luck...

---

