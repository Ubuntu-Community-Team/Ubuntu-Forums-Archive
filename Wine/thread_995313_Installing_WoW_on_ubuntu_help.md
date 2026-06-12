---
title: "Installing WoW on ubuntu help"
date: 2008-11-27
forum: Wine
---

### Post by zau64 on 2008-11-27
To start off, im a complete Linux and Ubuntu noob. I know very few commands. Now that you know that...

I was trying to get WoW running on Ubuntu and I got wine. I tried copying the files over form my windows partition into the mock C drive wine uses but when i ran WoW.exe it crashed before anything would come up. launcher.exe did work until i hit play then it crashes all the same. I have WOTLK if that makes any difference. I have gotten the Linux drivers for my graphics chip. And if it helps I have Ubuntu 8.10 and Windows Vista Home premium 64bit.

BTW WoW on vista now goes under C:/Users/Public/Games/World of Warcraft
instead of the usual program files.

BTW downloading doesnt help any more. The "i agree" button doesnt allow you to click it even after scrolling down. This is how I got it on Ubuntu the first time before WOTLK.

And I do have the DVDs for WoW and the expansions. But I cant find the installer executable.

Thank you for taking a look, regardless if you can help or not.

---

### Post by HoppingWombat on 2008-11-27
There may be a problem with files that were not copied over -- some times, if not most of the time, applications will put files in places other then "Program Files."

Try installing from the DVD.

Insert the DVD, open a terminal and type:
**cd /media/cdrom0**

As I don't know how much of a new user you are, I will explain every step.
/media/ should be self-explanatory: it contains system media. Computers start counting at 0 instead of 1, so cdrom0 indicates the first cd-rom you have active. **cd** is "change directory." (If you have any questions about commands, type **man command**)

Now type **ls**. This will display the files in the current directory.

There should be some file named something like **setup.exe**. Type **wine filename.exe**, where filename is the setup executable.

If all goes well, great!

For additional resources on getting WoW to work in WINE, look at the application page in [http://appdb.winehq.org](http://appdb.winehq.org) (the WoW page is: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154))

Good luck! Post here again if anything didn't go right.

---

### Post by zau64 on 2008-11-27
Thanks i'll try that... I'll be back if it doesnt work XD

---

### Post by zau64 on 2008-11-27
this is what i got... i even tried ls -a



Installer Tome 2.mpq  Installer Tome 5.mpq  World of Warcraft (OS X).app
Installer Tome 3.mpq  Installer Tome 6.mpq
Installer Tome 4.mpq  Installer Tome.mpq
daniel@daniel-laptop:/media/cdrom0$ ls -a
.                     Installer Tome 4.mpq  .Trashes
..                    Installer Tome 5.mpq  .VolumeIcon.icns
Installer Tome 2.mpq  Installer Tome 6.mpq  World of Warcraft (OS X).app
Installer Tome 3.mpq  Installer Tome.mpq
daniel@daniel-laptop:/media/cdrom0$

---

### Post by HoppingWombat on 2008-11-27
Hmm ... Are you sure that's the right DVD? The one for installing the main game? You should be installing the game just as you would on Windows, if you installed it manually, instead of using AutoRun.

---

### Post by Nihilis on 2008-11-27
If you go to the wow website go to your account page and download the on harddrive installer for vanilla wow - burning crusade - and lich king and install it in wine. Also to fix the weird ground textures, go into wine settings and click off allow pixel shaders and you will be good to go.

---

### Post by zau64 on 2008-11-29
They have changed their download client. Now for some reason i can never click agree to the user agreement even after scrolling down.

---

### Post by HoppingWombat on 2008-11-29
Did you ever get it to install?

---

### Post by Silenus on 2008-12-01
You have to remout it once you insert the cd, open a terminal than do this command:

  sudo umount /dev/cdrom

Then this one

  sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/


Should work fine then.

---

### Post by Blacktalon on 2008-12-01
Well that worked for seeing the installer.exe file, but now have an error:  "You are not privileged to unmount the volume 'WoW DVD'."

Any ideas on how to fix this tiny issue?

---

### Post by Silenus on 2008-12-02
Copy all of the files to a folder on your desktop you name World of Warcraft, then open your terminal and do

cd /home/<yourusername>/Desktop/World of Warcraft
sudo wine Installer.exe or whatever it is called, I just installed it using those steps.

---

### Post by Silenus on 2008-12-02
Copy all of the files to a folder on your desktop you name World of Warcraft, then open your terminal and do

cd /home/<yourusername>/Desktop/World of Warcraft
sudo wine Installer.exe or whatever it is called, I just installed it using those steps.

If it doesnt work here is a video

[http://www.youtube.com/watch?v=DIzgUq4Lpa4&feature=related](http://www.youtube.com/watch?v=DIzgUq4Lpa4&feature=related)

---

