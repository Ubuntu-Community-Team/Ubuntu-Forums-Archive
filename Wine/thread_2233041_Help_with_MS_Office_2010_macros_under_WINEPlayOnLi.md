---
title: "Help with MS Office 2010 macros under WINE/PlayOnLinux."
date: 2014-07-05
forum: Wine
---

### Post by adamwright609 on 2014-07-05
I recently purchased an Acer c720 Chromebook and proceeded to wipe out ChromeOS and install Xubuntu 14.04 and I love it except for one thing.  This was meant to be used for work but my job uses Excel spreadsheets with macros (check boxes, buttons that add pages, text boxes, etc.) that I can not get working in LibreOffice.  I've managed to install Office 2010 via PlayOnLinux however none of the macros work.  Yes, I enabled them in the trust center.  Initially I just installed Word/Excel and I would get an error along the lines of: "Excel was able to open the file by repairing or removing the unreadable content. This workbook has lost its VBA project, ActiveX controls and any other programmability-related features".  After some Googling, I figured it was missing the VBA component, so I re-installed using all default settings.  This disabled the message, however the macros will still not work.  According to the wine database, Macros are working in Office 2010 so I'm not sure what is wrong.  I'd really like to continue to use this laptop because at the $150 for it, it does everything else I need and it has specs I would have to shell out $250-400 for a similar Windows laptop.  Unfortunately being able to use my work's reports is a necessity for me.  Any ideas?

---

### Post by Mark Phelps on 2014-07-06
Don't use Wine anymore -- far too many thing barely work or don't work at all -- but according to the linked page, the Excel macro crashing problem  was fixed in Wine v1.7.2: [http://www.playonlinux.com/w/wine-1.7.2]("http://www.playonlinux.com/w/wine-1.7.2")

---

### Post by adamwright609 on 2014-07-06
Thanks, is there another option?

---

### Post by Mark Phelps on 2014-07-07
> **adamwright609 said:**
> Thanks, is there another option?

As far as I know, no. Lots of postings can be found about Macros NOT working; have not found any about them working properly.

---

### Post by apos on 2015-03-04
Hi,

> As far as I know, no. Lots of postings can be found about Macros NOT working; have not found any about them working properly. 

I can report, that under wine 1:1.7.34-0ubuntu1~ppa1 (ubuntu wine ppa under Ubuntu 14.04.2 LTS)

[1] my Word 2010 Macros work ALL like expected.
[2] my Excel 2010 Makros work ALL like expected.

Please follow EXACTLY the OFFICIAL advisory installing MS Office in wine at the appdb of winhq:

* [https://appdb.winehq.org/objectManager.php?sClass=version&iId=4992&iTestingId=83074](https://appdb.winehq.org/objectManager.php?sClass=version&iId=4992&iTestingId=83074)

EXCACTLY follow step by step.
DON'T use winetricks to install any DLL's, unless you know exactly what you are doing!
ONLY use a win32 wine prefix and ONLY use this prefix for MS Office, nothing else.
DON'T use or install old comctl32ocx ActiveX Controls (like the datepicker) with winetricks. This will crash your Office!

See also at my site
* [https://wiki.blue-it.org/Wine_-_Crossover_Office#MSOffice_2010_and_Wine](https://wiki.blue-it.org/Wine_-_Crossover_Office#MSOffice_2010_and_Wine)

Greets Axel

---

