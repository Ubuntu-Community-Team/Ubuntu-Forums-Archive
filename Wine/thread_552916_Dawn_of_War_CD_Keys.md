---
title: "Dawn of War CD Keys"
date: 2007-09-17
forum: Wine
---

### Post by Arukas on 2007-09-17
Hello-


  I have everything installed with Wine, and DoW.  I have all the expansioins.  However, when I start Dark Crusade, it ask me for a CD for the Space Marines and Chaos, etc.  I enter my CD key correctly and it says its invalid.  I have upgraded to the latest patch.  I read somewhere, where you can modify your registry and enter the keys there but that didn't work, anyone have any ideas?

-Arukas

---

### Post by JBAlaska on 2007-09-17
I'm not sure if this will help, But on some other games people have installed on windoze and then copied the folders over to the wine c drive. You might give that a try.

It's nice to hear you have WH DoW running under wine, it's one of my favorite games. I'm going to try installing it tomorrow.

Good luck.

---

### Post by stinger30au on 2007-09-17
try "Vitrualbox" allows you to install a full version of Windows in Linux

---

### Post by cogadh on 2007-09-17
Unless something has recently changed, Virtualbox doesn't do hardware accelerated 3D, it won't work for games.

Arukas, how are you running the game and are there any errors produced by Wine when you try to run it?

---

### Post by Arukas on 2007-09-17
I apprecate the help.  I got the CD keys, don't know what i did, but when I tried again this morning they loaded up just fine and accepted the keys.  Now there are other issuse with my DoW:DC.  For instance, I download the patch, and it is installing, but to were I don't know at all.  


-Arukas

---

### Post by cogadh on 2007-09-18
Wine creates a hidden directory in your home folder named ".wine" (the period on the beginning makes it hidden). If you open the file browser and press CTRL+H, the hidden files and folders will be temporarily unhidden. Inside the .wine folder are two directories, "drive_c' and "dosdevices". The "drive_c" directory is just like the "C:" drive on a Windows PC; it has a "Program Files" directory where Wine normally installs everything.

---

### Post by apakatt on 2008-07-19
This is a old thread but I ran into the same problem and solved it.
You have to open the registry editor with "wine regedit".
Search for the keys "CDKEY" and "CDKEY_WXP". They are in a folder named "THQ/Dawn Of War".

The two keys will have values like "0000-0000-0000-0000". Change the "CDKEY" to the Dawn of War key, and the "CDKEY_WXP" to the Winter Assault key. Start the game and you will be propted to enter the keys again. They should now report as valid. :)

I wrote a tutorial on  this subject found here: _[http://www.kungfoocode.org/2008/07/22/fix-the-invalid-cd-key-bug-in-warhammer-40000-dawn-of-war/](http://www.kungfoocode.org/2008/07/22/fix-the-invalid-cd-key-bug-in-warhammer-40000-dawn-of-war/)_[]("http://blog.kungfoocode.org/2008/07/22/fix-the-invalid-cd-key-bug-in-warhammer-40000-dawn-of-war/")

---

