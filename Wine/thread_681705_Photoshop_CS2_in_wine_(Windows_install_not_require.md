---
title: "Photoshop CS2 in wine (Windows install not required!)"
date: 2008-01-29
forum: Wine
---

### Post by litium on 2008-01-29
Well, it easy to do. Thanks to the newer version of wine (0.9.54). So now, how do we do this?

**You'll need:**
-_Wine installed_ (the lastest version)
-_Recode installed_ (get it via apt-get or synaptic)
-_Photoshop cs2 portable_ (you can google it, ussually about 60mb comes whit a .reg file and all)
-**_Patience_**

**Now, the steps:**
1- Go to winehq homepage and follow the steps to update or install the lastest wine version.

2- Now, extract the files from, most likely, the zip file that you've downloaded with P-CS2. After that, copy the .reg file to you Personal directory (mine's */home/litium*).

3- Fire up a terminal and type: *recode ucs-2-internal YOUR_REG_FILENAME.reg*. It shouldn't take long.

4- If you dindt configured wine yet, do a winecfg to setup the directory structure, etc,etc. Read some wine installation manuals. So now, you should type in a terminal: *wine regedit.exe YOUR_REG_FILENAME.reg*. Done, you've got the CS2 reg file on wine.

5- Open up Photoshop.exe with wine and test it (it'll probably take some time to load up, and i recomend running it on a Virtual Desktop, i use a 924x663 desktop whit wine) 

6- If you want, you can add a launcher in your menu under the graphics submenu.

So, hope it helped. If you want to see how it looks, [**here**]("http://img297.imageshack.us/img297/9042/cs2sd1.png").

PD: Now whit the new wine version, you don't even have to delete the Preferences!

---

### Post by MRlaith on 2008-02-03
cool
definitely gonna try that!
were the hell can I find a download for the photoshop cs2 portable:confused:
I searched  around in google but didn't find eny thing...

---

### Post by Crossover on 2008-02-04
contact me I will give you the CS3 portable

---

