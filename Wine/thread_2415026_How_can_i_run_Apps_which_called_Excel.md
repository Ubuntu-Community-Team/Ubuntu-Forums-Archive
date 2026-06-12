---
title: "How can i run Apps which called Excel"
date: 2019-03-19
forum: Wine
---

### Post by ceng.meng on 2019-03-19
Recently we are going to move our windows ENV to Ubuntu,  after study, we found we have a very old tool(lost source code) which run perfect on windows cannot run on ubuntu, and we dont have the linux version. 

after study, i choose to try Wine to run this apps on ubuntu, after successfully installed wine via [https://wiki.winehq.org/Download](https://wiki.winehq.org/Download) i can run notepad via WINE, basically i would say Wine is OK on my PC. 


However, when i am trying to run my app on Wine, it failed, error notes says Excel.application failed.  Seems this app will call excel, now question is how to fix this?

here is my assumption: 
option 1 : modify wine configuraiton to let my app call open office
Option 2: install office in Wine, does this work?

---

### Post by TheFu on 2019-03-19
If the first program is just making CSV files to be loaded into any spreadsheet, then it might not be much work to get that integration working.

Excel has a proprietary scripting language which is not compatible with any other programs.  Also, instead of openoffice, LibreOffice is normally preferred.
Getting notepad to work in WINE is trivial. Most non-trivial applications require much more setup to work.

There's no way to know if Excel is actually required from the information required.  MS-Office is one of the main programs continuously ported to work with WINE, but it is complex to get working manually and each version has different WINE setup requirements. Many functions don't work 100%, but the main ones do. Many people will choose to pay $20 for a WINE helper program which has hundreds of pre-configured setups for the most popular programs.  Crossover Office and Playonlinux are the big players.

However, depending on the programs involved, the easiest answer might be to setup a single Windows computer on the network with RDP enabled that has MS-Office and the program you need, then have the Linux systems remote into it to use those programs.  Of course, you'll want to find and fund a Linux solution long term.

After years of fighting to get MS-Office and a few other programs working under WINE, I gave up and just keep a Win7 virtual machine around with those programs loaded.  It is accessed using RDP over the network.  I stopped using Excel long before then, but haven't found a good replacement for MS-Visio, which is Windows only still and for some accounting and tax programs.  $120 and a virtual machine loaded every 10 yrs for Windows-Something which gets used a few times a week for an hour, isn't really that much of a commitment for us.  

OTOH, if you need 50 people setup this way and their main job is to use that application all day, that's a very different problem than what we have here. I wish you well.

---

### Post by mastablasta on 2019-03-20
ms office up to about version 2010 works relatively well in wine. older run better.

another option is virtualbox and windows within virtualbox. not sure what exactly you need in your case.

---

### Post by ceng.meng on 2019-03-24
> **mastablasta said:**
> ms office up to about version 2010 works relatively well in wine. older run better.

another option is virtualbox and windows within virtualbox. not sure what exactly you need in your case.

Hi,

thanks for your sharing, it is very helpful, firstly i would say VirtualBox is not a good approach because our server is located on AWS. 

What i am concerning is that, my APP will directly call MS office API to transfer one Excel to a binnay file. even i setup office in WINE, the correct way to call Office should look lie "Wine Excel" or something like that(with wine prefix), but my app doesnt might be directly call excel. and i dont have the source code of that app.  does anyone have experice on this?

---

### Post by TheFu on 2019-03-25
Long ago, many jobs ago, we were switching from plain FTP to sftp.  Some of the software was hard coded to only use plain FTP.   See, sftp is designed to behave just like plain ftp, using the same commands, so the only real challenge was to ensure that the system() call to "ftp" found a version of the sftp binary 1st in the path that was named "ftp" - that was easy. We just modified the PATH and made a symbolic link from the sftp to ftp that was found first in the PATH.

You can do the same thing with a little script that actually calls sets the PATH and WINEPREFIX before called /usr/bin/wine with excel and $@ arguments.  Just name the script to be the program hard-coded name of the program, perhaps excel.exe is the name you need?  Or does the setup just try to open "file.xlsx" and expect the file associations to open excel automatically?

That's the theory.

I would hate to try to run any GUI programs on AWS.

---

