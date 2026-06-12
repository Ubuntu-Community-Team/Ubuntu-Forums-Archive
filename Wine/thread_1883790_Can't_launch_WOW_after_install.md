---
title: "Can't launch WOW after install"
date: 2011-11-19
forum: Wine
---

### Post by Mazate on 2011-11-19
I just downloaded and (I think) installed via wine.  The problem is now, how do I launch it?  I searched for WOW and it showed me the WOW icon... I double clicked it and the cursor would spin for about 7-8 seconds and then stop.  Nothing started.  Did I miss a step?  After the downloader finished downloading the game, it just disappeared.

---

### Post by Dlambert on 2011-11-20
Tell us the output of 

```
cd /PATH/TO/YOUR/WOWFOLDER 
Then wine wow.exe
```

---

### Post by Dlambert on 2011-11-20
its usually /home/User/.wine/ etc

---

### Post by Mazate on 2011-11-20
> **Dlambert said:**
> its usually /home/User/.wine/ etc

I'm having trouble finding the wine directory.  I'm not real good with the linux file structure.  It is installed though.

---

### Post by Mazate on 2011-11-20
Ok, I found it.  I've hit a wall though.  I need to get into the Program Files directory.  I went into the drive_c directory.  Then there are three more directories.  Program Files, users, and windows.  I'm pretty sure I have to go into the program files directory but when I type "cd Program Files" it just says that there is no such directory.  Not sure if it has to do with the fact that the directory name is two words.

---

### Post by cwwilson721 on 2011-11-20
Try just ```
cd Pro*
```
If you just use the first few unique letters plus the '*' wildcard (which means 'anything after what I typed'), it can help.
Note the capitol 'P'. Linux, unlike Windows, DOES care about capitol letters in names.

---

### Post by Mazate on 2011-11-20
> **cwwilson721 said:**
> Try just ```
cd Pro*
```If you just use the first few unique letters plus the '*' wildcard (which means 'anything after what I typed'), it can help.
Note the capitol 'P'. Linux, unlike Windows, DOES care about capitol letters in names.


Okay, that worked.  I was able to go in and I typed, "wine wow.exe" and the game launched and it works perfectly.  The only problem is that I have to start the game in the terminal because the icon doesn't work.  Is there a way for me to create a new one that works?

---

### Post by Soulcage on 2011-11-20
If it's on the desktop you can open it using gedit and make the needed changes. [https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft")

---

### Post by Tweak42 on 2011-11-20
> **Mazate said:**
> Okay, that worked.  I was able to go in and I typed, "wine wow.exe" and the game launched and it works perfectly.  The only problem is that I have to start the game in the terminal because the icon doesn't work.  Is there a way for me to create a new one that works?

Right click the WoW icon, select Properties, edit the Command field with the appropriate command that works.  It's best to have wine to launch the wow.exe directly because there has been problems using wine to run launcher.exe to start wow.exe

Few tips:
Hit Ctrl-H in Nautilus file browser to unhide hidden directories (hidden directory names start with a period), hence why .wine and a bunch of other directories don't normally show up in your home directory.

In addition to bing capital sensitive, command line paths don't like names with spaces in them.  You need to use quotes " " to encapsulate paths. Thus:
```
cd "Program Files"
```

Hit <tab> key for auto complete while at command line.  This is useful when you need to type out long directory names with spaces.

---

