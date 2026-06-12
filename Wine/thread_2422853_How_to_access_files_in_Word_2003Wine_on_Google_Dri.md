---
title: "How to access files in Word 2003/Wine on Google Drive"
date: 2019-07-13
forum: Wine
---

### Post by wjbmd48 on 2019-07-13
Hi:

I'm trying to access files in Word 2003/Wine on my Lubuntu 18.04 system, 64-bit, in my google drive account. I've successfully set up online accounts on the system so's I can see the google drive folders and riles in the PCM File manager, but for the life of me can't figure out how to navigate from the Word/Excel file menu to open them.

Supposedly, there's a Microsoft utility that does this, installbackupandsync.exe, but when i fire this up with Wine it tells me it can't connect to the internet, tho I'm clearly online.

I'd also be happy with automatic folder synchronization, but can't find a GUI based app that does this. Supposedly unison is GUI, but I can't get it to fire up.

Thanks!

Bill

---

### Post by sevendogs1337 on 2019-07-14
Is there a way to open the file the other way around, instead of through word, right click on the file in your google drive from your file manager and say "open with" wine/wordxxx? Does that make sense?

---

### Post by wjbmd48 on 2019-07-15
Great idea, but, no, when I do that, it fires up Word 2003, but I get a grey page, the file doesn't load into Word, and it freezes Word up, have to do a manual kill to close it.

Bill

---

### Post by mastablasta on 2019-07-16
the 2003 format is well supported by libre office. not sure why you would need word.

otherwise you can get the files into the wine prefix and open them there. i am not sure why you wouldn't be able to open them outside of prefix, but it's possible it doesn't see the folder. symlink could help here. however i cna see in some of the games that there is already something like that linking my documents in wine with folders in home. could it be home/documents? not sure and i am on windows 10 at work.

---

### Post by wjbmd48 on 2019-07-16
Again, thanks!

Libreoffice doesn't quite hack it for the detail of use I need, which is publishing related, where Word, no matter how old, seems to be the standard.

Installed symlinks, which doesn't seem to add a path for Word to open a file in a google drive folder.

Meantime, I've solved the "real" problem, which is the limitation of Dropbox free to 3 devices, by adding a new Dropbox account to my new system, then sharing it with the old accounts on the old systems.

Bill

---

### Post by mastablasta on 2019-07-17
that's is what i meant - old word 2003 should be covered by all details in Libre office. it's the new word file versions that have the issues. have you tried it? did you save as word 2003 file?

and if libre office still has some issues, then WPS office should definitely work.

in any case use what works best for you.

---

### Post by wjbmd48 on 2019-07-19
Thanks all, for your help. The two workarounds are to use libreoffice and to link dropbox accounts, though I never could figure out how to open Office 2003 files under WINE from google drive.

Bill

---

