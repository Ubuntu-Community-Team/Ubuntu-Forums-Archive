---
title: "harmony.dll - RPG Maker 2003"
date: 2008-02-10
forum: Wine
---

### Post by Squish on 2008-02-10
Hi, I have downloaded RPG Maker 2003 for a project I am doing, and I have a few errors, to which I think can be solved. Right now, I can install pretty much fine. I downloaded the program here:
[http://www.fantasyanime.com/images/RPGMaker2003English.zip]("http://www.fantasyanime.com/images/RPGMaker2003English.zip"), and its only about 25 megabytes.

I am using Ubuntu Gutsy Gibbons 32bit, with wine 0.9.54, running in windows 2003 mode

So heres how it goes:

Install:
```
kris@kris-laptop:~/Gaming/Wine/RM2K3$ wine ./rm2k3-install.exe
err:winedevice:ServiceMain driver L"Aspi32" failed to load
fixme:spoolsv:serv_main (0 (nil))
err:winedevice:ServiceMain driver L"Vax347s" failed to load
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
fixme:advapi:CheckTokenMembership ((nil) 0x151d80 0x34fb94) stub!
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
```

After this, the program seemed to have installed fine, with no pop up errors.

When I try to run the game:
```
kris@kris-laptop:~/.wine/drive_c/Program Files/rpg2003$ wine ./RPG2003.EXE 
err:winedevice:ServiceMain driver L"Aspi32" failed to load
fixme:spoolsv:serv_main (0 (nil))
err:winedevice:ServiceMain driver L"Vax347s" failed to load
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!

``` And a window pops up stating:
> Harmony.dll not found.
The Harmony.dll was something easy to find:
[http://www.driverskit.com/dll/harmony.dll/4434.html]("http://www.driverskit.com/dll/harmony.dll/4434.html")


These errors seem simple enough to understand. My thinking first is to see where I can still that Harmony.dll file so it reads it.

Cool:guitar:

---

### Post by happyhamster on 2008-02-10
My first try would be the .wine/drive_c/windows/system32 folder.

---

### Post by happyhamster on 2008-02-10
Your link didn't work so I did a search and found a working one on this page:
[http://www.solarsoft.nl/overig/rpgmaker.php](http://www.solarsoft.nl/overig/rpgmaker.php)

The installer (rm2k3109aefull.exe) installs fine using wine-0.9.52 and the program appears to run fine as well. (Harmony.dll is located in the RPG2003 folder BTW).

Perhaps you downloaded a broken archive, or perhaps wine-0.9.54 causes trouble (lots of programs won't install with wine 0.9.54/53). So you could also try wine 0.9.52, or wait a day(?) or so until wine 0.9.55 is available (most install problems are fixed in that version AFAICT).

---

### Post by Squish on 2008-02-10
Ok great, 

Wine .55 is out, so I will get that first, then I will do a reinstall, and then download the dll to that directory.

What the dll is for actually is a midi device, to which is somehting my computer cannot do at the moment. I am looking into that as well, but have had no luck.

Lets hope!

---

### Post by jayzoy on 2011-02-11
Ok good deal,

Was looking into the Harmony.dll not found error,my son and i are doing a little project together and found this thread.We used the install code on this page and seems to work fine for the moment.Thanks for the post and we will be back in the near future because it seems like there is some good information here that we have not found before.:D

---

