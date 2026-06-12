---
title: "wine doesnt install but plays game"
date: 2008-11-27
forum: Wine
---

### Post by tgpraveen on 2008-11-27
so i have adual boot system between ubuntu 8.10 and xp.
when i try to install a game like halo 1 which i tried today, then the setup gives a error in between that setup couldnt find pidgen.dll and setup stops but then i installed it in in my xp partition using xp and then rebooted into ubuntu and clicked on halo.exe in the folder where it had been installed and then i can play it fine. :-)

so this might be a tip for those who cant get their games working.

but am i doing anything wrong here. i want to install games and play from ubuntu itself so please help using latest wine IMO

is the process that i am adopting of open with wine for the setup file wrong?

this thing has happened with many more games in the past.

in the end i would like to say wine rocks.

---

### Post by cogadh on 2008-11-27
To quote from the Wine FAQ:
> **3.1. I have lots of applications already installed in Windows. How do I run them in Wine?**

Short answer: You have to install them in Wine just like you did in Windows. Applications usually have a setup or installer program.

Long answer: Some applications can be copied from Windows to Wine and still work, but don't try this unless you like tinkering under the hood of your car while it's running.

**Wine is not designed to interact with an existing Windows installation.**

**WARNING**: Do not try to configure Wine to point to your actual Windows C:\ drive. We have tried to make this hard to do so you probably cannot do it by accident. If you do this, Wine may or may not continue to operate. Your Windows install will be 100 percent dead due to wine overwriting critical Windows files. The only way to fix Windows after this has happened is to run a reinstall of Windows.
In the case of Halo, there are some specific things you need to do to make it install and run in Wine, such as copying mfc42.dll from an existing Windows installation into Wine and using a no-CD patch:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720)

---

### Post by tgpraveen on 2008-11-27
well i think u didnt read my post carefully 
i have clearly said that i installed halo on windows xp partitiopn using xp
and then in ubuntu using wine i could play halo automatically jsut by selecting open with win for halo.exe in the installed folder.

and i have done this many times. no probs till now.

and this way that extra dll file is not reqd.

so maybe this can be confirmed by more people as this will help newbies too.

---

### Post by cogadh on 2008-11-27
And you did not read mine carefully. Although it may have worked this time, it is not the way Wine is meant to work and in many cases, it will cause problems with your Windows partition. In fact, it is still entirely possible that you will encounter problems if you continue to use it that way, you may have just been lucky up till now. 

The proper way to use Wine and Halo is with the overrides as described in the AppDB page I linked to. Recommending to anyone, newbie or otherwise, the improper usage of Wine is never a good thing.

---

### Post by tgpraveen on 2008-11-27
hmm.. see ur point now. but still maybe a second opinion could be helful.

---

### Post by Brynster on 2008-11-28
2nd opinion granted 

cogadh is right.

Wine goes into great depth on there site about not doing what your doing.

Sorry thats just the way it is.

---

### Post by tgpraveen on 2008-11-29
hmm.. ok understood thx all for ur help.

---

### Post by david_kt on 2008-11-29
> **Brynster said:**
> 2nd opinion granted 

cogadh is right.

Wine goes into great depth on there site about not doing what your doing.

Sorry thats just the way it is.

Not really. If we double click any exe file, wine would run on default prefix i.e. /home/username/.wine

So, at least what tgpraven do is not the same as in the warning:

```
WARNING: Do not try to configure Wine to point to your actual Windows C:\ drive....
```

And if the installer have problem, off course it is good to troubleshoot the installer itself. But to copy over installed application to wine it is better than nothing. But for me I will copy it to wine directory and not run it on windows partition.

If there is a problem, worst case is I would delete the wine directory and maybe reinstall wine (never happen to me so far). And to make it easy, if you want to experiment with new program, use separate wineprefix, so it would not interfere with other windows program and you would not hesitate to delete the whole wineprefix if something goes wrong.

DK

---

### Post by tgpraveen on 2008-11-30
[QUOTE]> **david_kt said:**
> Not really. If we double click any exe file, wine **would run on default prefix i.e. /home/username/.wine**

So, at least what tgpraven do is not the same as in the warning:



exactly my point so what do u ppl say...????

---

### Post by jorj82 on 2008-11-30
When you install a game in Windows, chances are it will be set up to look for Windows files to run(i.e. real DirectX).  When you move that folder to a linux partition, those files are no longer accessable.  Wine runs differently than Windows, it is not an emulator.

Listen to cogadh, he knows his stuff.

---

### Post by david_kt on 2008-11-30
> **jorj82 said:**
> When you install a game in Windows, chances are it will be set up to look for Windows files to run(i.e. real DirectX).  When you move that folder to a linux partition, those files are no longer accessable.  Wine runs differently than Windows, it is not an emulator.

Listen to cogadh, he knows his stuff.

We could make a test i.e copy it over to linux, and unmount windows partition. If the game still run, it is safe to run. Long time ago, when Lotus notes installer did work in wine, I copy it from other box to linux box (not dual boot), and it run.

To point wine to windows partition is definitely not good. So, it should be copied over to wine directory (or better still, a special wineprefix).

DK

---

