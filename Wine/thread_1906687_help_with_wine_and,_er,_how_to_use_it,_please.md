---
title: "help with wine and, er, how to use it, please"
date: 2012-01-09
forum: Wine
---

### Post by Guy Secretan on 2012-01-09
greetings all

i realise that i will probably come across as a total moron here but can someone please help me get my head round wine.

basically, i've been trying to install serif pageplus as i don't really get on with scribus (but that's another matter). do i just click on the pageplus.exe jobbie or do i have to run something (ie wine) first? and if so, how?

have tried various things but cant get pageplus to install (although this is may well be a serif rather than linux thing). am i missing something (other than a brain, obviously)?

cheers

guy

---

### Post by cortman on 2012-01-09
> **Guy Secretan said:**
> greetings all

i realise that i will probably come across as a total moron here but can someone please help me get my head round wine.

basically, i've been trying to install serif pageplus as i don't really get on with scribus (but that's another matter). do i just click on the pageplus.exe jobbie or do i have to run something (ie wine) first? and if so, how?

have tried various things but cant get pageplus to install (although this is may well be a serif rather than linux thing). am i missing something (other than a brain, obviously)?

cheers

guy

There are no dumb questions, and asking questions won't make you look dumb- EVERY single one of us here started out totally new. We're glad to help!

If you have Wine installed, right click on the .exe and select Open With> Wine Windows Program Loader. If your Windows software is Wine-compatible (not all Windows programs play nicely with Wine) it should bring up the standard Windows installation process.
The program will be listed with all your other Linux applications once it's installed, and you can launch it just like any other application.

Best wishes!

---

### Post by Paqman on 2012-01-09
Wine is a "compatability layer", it basically translates the input and output of Windows programs into a form that Linux understands. With it installed you should simply be able to click on an .exe installer and run it. You might want to right click and make sure that the system is going to try and open it with Wine instead of something else like Archive Manager.

Your PagePlus app seems to have some pretty variable results reported in the [Wine App DB]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=999"). Wine is a bit hit-and-miss, if you can find a native Linux DTP app you like it might be better to use that.

---

### Post by oldos2er on 2012-01-09
Thread moved to Wine.

---

### Post by Guy Secretan on 2012-01-09
thanks very much for all your help. 

i had been trying the old right click  Open With> Wine Windows Program Loader but nothing happened. it seems that it's not wine nor me that's at fault after all. instead, it appears that my version of pageplus just doesn't like wine.

this is a pity from the dtp point of view but at least i don't feel so stupid any more!

thanks again and Happy New Year to you all.

cheers

Guy

---

### Post by cortman on 2012-01-10
> **Guy Secretan said:**
> thanks very much for all your help. 

i had been trying the old right click  Open With> Wine Windows Program Loader but nothing happened. it seems that it's not wine nor me that's at fault after all. instead, it appears that my version of pageplus just doesn't like wine.

this is a pity from the dtp point of view but at least i don't feel so stupid any more!

thanks again and Happy New Year to you all.

cheers

Guy

If right click Open With> Wine doesn't work, that's a pretty good indication that for whatever reason, your program just doesn't play nicely with Wine.

Best of 2012 to you as well.

Cheers!

---

### Post by Romeo9 on 2012-01-10
What you could also do to make any future uses of wine as smooth as possible is:
1) Go to Configure Wine and under the Graphics tab tick the "emulate a virtual desktop" box and input the resolution you wish the application to open in, if full screen input your current resolution.
2) Once done right click any .exe file and select properties, under the permissions tab select the "execute" box and under the Open with tab select "Wine windows program loader"

Now any .exe, .sh, .run or any other executable file should just open without any hassle. Although .run files will most likely still ask you whether you'd like to open the file via a terminal session or simply execute the file, but that's not really an issue at all. 
Hope this helps.

---

