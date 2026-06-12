---
title: "Powerpoint can't save files within wine"
date: 2008-10-18
forum: Wine
---

### Post by Markelecguitar on 2008-10-18
I installed office 2003 quite easily without any hiccups using wine in a ubuntu hardy heron system. However, now using powerpoint im getting an error when i try to save files.

When i try to save a popup appears saying "There was an error accessing "filename" ", where file is the folder im trying to save it too.

When i try to email the file as an attachment it says there is an error accessing a temp file

and when i try to save as bundle for cd it brings up a disk full error

Basically it means im stuck and can't save my work :S

Anyone got any ideas what exactly is the problem?

---

### Post by ooobuntooo on 2008-10-18
have u tried installing Office 2003 with Crossover 7?

---

### Post by Markelecguitar on 2008-10-18
No havent as of yet, but isnt crossover a paid application?
Also seeing as the rest fo the officesuite works i'm hoping that means i can get powerpoint to work too

maybe not but if anyone has any idea please do tell

---

### Post by Puxbunny on 2009-01-03
same here with an up-to-date wine install (1.1.12).

---

### Post by dragos_iliescu_2005 on 2009-01-03
Try install office under Virtual Box. It work for me.

---

### Post by JonathanCasey on 2009-02-23
I have the same problem, but if you click ok and save again, after about the 3rd or 4th time it will save successfully. (I have no idea why)

I find its not that much of a problem if you use hotkeys,
just press space, then ctrl+s, then space, then ctrl+s (repeat till it finally saves).

I would like a fix however as it makes me more reluctant to save regularly as its still a small hassle.

Hope that helps,

Jonathan.

---

### Post by Artemis3 on 2009-02-23
Try this: Open a terminal window and:

wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
sh ./winetricks

Mark dcom98 and apply.

---

### Post by abn91c on 2009-02-23
openoffice.org 3.0 will open/save MSO 2007 files. The default OOo 2.4 will run/save MSO 2003 including powerpoint

---

### Post by david_kt on 2009-02-24
> **Markelecguitar said:**
> 
When i try to save a popup appears saying "There was an error accessing "filename" ", where file is the folder im trying to save it too.

When i try to email the file as an attachment it says there is an error accessing a temp file

and when i try to save as bundle for cd it brings up a disk full error

Try to use dlloverrides:

1. Launch winecfg (either from menu or terminal)
2. Click on library tab
3. Type riched20 and click add
4. Click apply and close winecfg

Launch again power point and hopefully now you could save your work.

DK

---

### Post by pauljohn32 on 2009-08-19
I have this same problem, but notice that I am able to save the same file with a new file name.  Not every File/Save fails, possibly every other one.  As long as you don't mind having a directory fill up with version-1.ppt, version-2.ppt and so forth, it is kindof nice.  Free, mandatory backups :)

PJ

PS. I see same with Crossover or with wine in Ubuntu 9.04

---

### Post by kfsorensen on 2009-10-14
I tried both the "winecfg" technique and the "dcom98" technique and neither worked for me.  I'm running Office 2003 under Wine in Karmic.  Any suggestions?

---

### Post by david_kt on 2009-10-14
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3214&iTestingId=42760](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3214&iTestingId=42760)

Current versions of Wine do not require any overrides to install Office 2003 Pro.  Install as you would in Windows: insert th*e cd and run setup.exe.

Do not report bugs for the installer if you have used any overrides. 

If you are using a version of Wine older than 1.0, you should upgrade to either the current stable or development release. 

Once Office 2003 is installed, you may wish to set an override for riched20.dll so that Office will use the riched20 that it installs itself. (There is no need to copy the file or use winetricks--just set the override in winecfg.)

 

Known regressions (do not attempt to install in these versions):

    * 1.1.17 through 1.1.23
    * 1.1.1 and 1.1.2
    * 1.1.2 through 1.1.9  (German and Spanish versions of Office 2003)

---

### Post by kfsorensen on 2009-10-15
Still no luck.  I overrode riched20 in winecfg and then opened Powerpoint and tried to save a file, without any success.

---

### Post by david_kt on 2009-10-15
> **kfsorensen said:**
> Still no luck.  I overrode riched20 in winecfg and then opened Powerpoint and tried to save a file, without any success.

What is your wine version? Try wine 1.0.1 or 1.1.16

DK

---

### Post by kfsorensen on 2009-10-27
> **david_kt said:**
> What is your wine version? Try wine 1.0.1 or 1.1.16

DK

wine-1.1.30

I've found that I can save in Word and Excel (under Wine) but not in Powerpoint.  Which makes this even more confusing.

OpenOffice mangled an important presentation that I did yesterday, so it's very important to me to get this to work properly.  Otherwise I might be back to dual-booting Windoze.

---

### Post by david_kt on 2009-10-27
> **kfsorensen said:**
> wine-1.1.30

I've found that I can save in Word and Excel (under Wine) but not in Powerpoint.  Which makes this even more confusing.

OpenOffice mangled an important presentation that I did yesterday, so it's very important to me to get this to work properly.  Otherwise I might be back to dual-booting Windoze.

Have you tried to downgrade to wine 1.0.1 or 1.1.16 as I suggested before?

DK

---

### Post by kfsorensen on 2009-10-27
When in doubt, just do a complete reinstall--I ripped Wine out and MS Office and reinstalled and now everything works fine...still have no idea what was wrong before.

---

