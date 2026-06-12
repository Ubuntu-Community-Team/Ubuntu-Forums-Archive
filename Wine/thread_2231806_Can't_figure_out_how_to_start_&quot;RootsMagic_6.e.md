---
title: "Can't figure out how to start &quot;RootsMagic 6.exe&quot; with Wine"
date: 2014-06-28
forum: Wine
---

### Post by dora5 on 2014-06-28
I appear to have successfully installed RootsMagic 6, which installs and runs wiht Wine, but I can't figure out how to run it.   There is a space in the file name.   

My specific problem is figuring out by what name Ubuntu wants me to start it.  I found it in the ~./wine/drive c/Program Files folder.   It shows in the directory variously as RootsMagic\ 6 with dir and RootsMagic 6 with ls.   

I have tried:

wine RootsMagic.exe
wine "RootsMagic 6.exe"
wine RootsMagic\ 6
wine RootsMagic 6.exe
wine "RootsMagic 6"

All get wine:  cannot find (whatever).   

What do I actually enter to run it?

---

### Post by dora5 on 2014-06-28
I figured it out.

Wine installs in an invisible folder .wine in the home folder, so you have to make invisible files visible before you can see it, and then look specifically for the folder name with the . in front of it. 

Then, after finding it in Program Files, RootsMagic 6 is the name of a folder.   You have to open it to get to the program to run it, which is RootsMagic.exe .   I right clicked and clicked open it with Wine software loader or whatever, and the program opened.

---

### Post by uRock on 2014-06-28
[s]While you wait for someone who may know more about the applicatrion you're seeking help with, Have you tried everything mentioned here? [http://students.cs.byu.edu/~jbejaran/RootsMagicWineUbuntu.php](http://students.cs.byu.edu/~jbejaran/RootsMagicWineUbuntu.php)[/s]

Glad you got it working.

---

### Post by deadflowr on 2014-06-28
Firstly, Thread moved to ***Wine*** subforum.

Secondly, is there no program listed in the menu for it?
Normally, when I installed(past tense) programs for wine, after installed I would be able to launch it for the systems normal menu system.
(In Ubuntu, I would simply open the dash --super key or click the top icon in the launcher, and do a quick search for the program.)

---

### Post by Mike_Walsh on 2014-07-11
Hi, dora5.

I would agree with deadflowr on this one. You SHOULD be able to find the item in the dash, by running a quick search. I left the 'sinking ship' of XP about 3 months ago; by and large, I can find an equivalent program to everything I used to use in XP, right there in the Ubuntu software center.

However, just occasionally, you want a specific Windows program...and ONLY that will do. My passions are photography, and graphic design. I used to use a nifty little lightweight program in XP called PhotoScape. While I very much enjoy using the Gimp (having been used to Adobe's PhotoShop for, like, YEARS), for certain things, I cannot find an exact equivalent to the way PhotoScape performs certain 'tweaks'.....so I looked into WINE.

I browsed the Wine AppDB; found the program & noted the version that would run it as Platinum (i.e., perfectly & bug-free; everything works!), installed it via Synaptic, and then launched my .exe file from the Backups I keep on an external hard drive. Having installed and launched the program, and after checking everything worked, I closed it down again.....to find that I now have an icon on the desktop, to launch it with; and this is what I now use.

Mike.

---

