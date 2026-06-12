---
title: "Ubuntu 8.04.1"
date: 2008-07-29
forum: x86 64-bit Users
---

### Post by Maidendave on 2008-07-29
I have recently downloaded the above iso image (from this site) and wanted to try to run on my desktop as part of windows xp media center with service pack 3. I can only get so far and then windows informs me that it cannot access the dvd drive as it is in use by another program. Nothing is using the dvd drive and therefore it looks like either there is protection within windows or the ubunto program has a fault of some type. Can anyone help here please?

Thanks
Dave

---

### Post by gjoellee on 2008-07-29
you have to burn the iso file to a CD I would recommand to use isoburn to burn with...takes a lot less time! download it here: [http://sourceforge.net/project/downloading.php?groupname=isoburn&filename=isoburn_app_1_0_10.zip&use_mirror=surfnet&abmode=1](http://sourceforge.net/project/downloading.php?groupname=isoburn&filename=isoburn_app_1_0_10.zip&use_mirror=surfnet&abmode=1)

now burn it to a CD and put the CD in to your floppy drive and reboot...then select your language and go to Try Ubuntu...this will make Ubuntu run from the CD without doing anything bad to your computer (now notice that the speed is many, many, many times slower when you are running live CD). IF you want to install Ubuntu click on the install icon on your desktop.

NOTE! Before installing check that vital parts like Internet works etc...

---

### Post by Sef on 2008-07-29
Read [How can I write (burn) ISO files to CD?]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm"), and to burn the iso, download [ISO Recorder]("http://isorecorder.alexfeinman.com/isorecorder.htm").

---

### Post by tuxxy on 2008-07-29
You could download virtualbox in windows and try it on a virtual drive first or even run the live CD option to see if you like it, im sure you will :)

---

### Post by Maidendave on 2008-07-31
Tried it but it doesn't work - not sure why i downloaded it and then updated to.NET v 2 and still won't work - is it because i already have nero 8

---

### Post by Jokimoto on 2008-07-31
You mean you tried burning it and it wouldn't work? Hmm, Nero should be able to handle that. I use ImageBurn myself.
Or did you mean you're still unable to get the disk to load? Check your BIOS, if that's the case, and make sure it's set to "boot from cd/dvd" drive if there's a disk there, and HD if there isn't. Reboot and the Ubuntu screen should come up giving you the option to "start or install", just select that and run it Live.

---

### Post by tuxxy on 2008-07-31
Switch on your computer and let it boot from CD to install

---

### Post by Maidendave on 2008-08-01
I do not want to install it in that way, this version is supposed to "emulate" in windows and it goes through checksum and full instatll almost to the end and then says that it can't access the dvd drive - which it has been accessing all the way through whilst the attempted install to windows. I know that the cd is ok as I have installed it complete on another sata2 drive. So all I do not understand is what is preventing it from installing to windows itself. Hope that this is clearer.

Thanks
Dave

---

### Post by damvcoool on 2008-08-01
Windows XP SP3 still has some bugs to be worked out, that this is a example of one, for some reason windows is taking ownership of the DVD drive, and is not letting the installer to access it. it does not matter if you burn another one it will not work.

if you try it on a PC with Windows XP SP2 i pretty sure it will work with no problems at all.

Change your BIOS to boot from CD and try ubuntu as LiveCD, it will not be installed on your PC and you will be able to check out all the features.

---

### Post by Maidendave on 2008-08-01
Thanks for that I had a suspicion that it was SP3 causing this but could not be sure. Yes I have tried the other option and that works fine.

Once again thank you for your time.

Dave

---

