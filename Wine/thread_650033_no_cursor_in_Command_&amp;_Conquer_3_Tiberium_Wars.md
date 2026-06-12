---
title: "no cursor in Command &amp; Conquer 3: Tiberium Wars"
date: 2007-12-25
forum: Wine
---

### Post by cameran on 2007-12-25
hello,

been struggling with this all day - there's no cursor in C&C 3 Tiberium Wars.  Is there any way to get a cursor in the game?

thanks!

Cameran

---

### Post by cameran on 2007-12-26
does anyone know how to force the xcursor to appear?  i don't care about the fancy c&c3 cursor but just the regular ubuntu cursor would be fine.

have read several reports of people on winehq that have their regular cursor for this game

thanks :(

cameran

---

### Post by SaMuRaI_777 on 2008-01-10
Are you using wine?
Or, rather have you checked wine?
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7440](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7440)
and scroll down to 
Patching for Cursor Support
(If you haven't done this already ) :-k

---

### Post by yowshi on 2008-02-24
can someone help me do this in a SIMPLE way? i have tried what it says non the wine page but the command for patching , the first one you are supposed to run after entering the unzipped winre package directory in the cli, just asks me what file to patch and i dont know what file i am supposed to patch so i am stumped

---

### Post by happyhamster on 2008-02-24
Are you sure everything is as described in the howto? Folder names have to be exact, folder locations have to be right (wine and patch folder must be in the same parent folder). Wine version has to be wine 0.9.50, etc?

You can always try again (delete the wine-0.9.50 folder first, and re-extract the archive).

---

### Post by yowshi on 2008-02-24
you mean it wont work with the latest wine? so i have to downgrade to get a cursor patch? i wonder why they just didnt write this patch into wine with one of thier updates. aside from me using the latest wine instead of .50 (i am using .55 64bit) everything else is as it says on the page

---

### Post by rasmus91 on 2008-02-24
hmm... i seemed to have the same problem in Guild Wars... all i have to do is to right click a lot of times in a row, then the cursor will apear after around 5-10 seconds...

---

### Post by happyhamster on 2008-02-24
> **yowshi said:**
> you mean it wont work with the latest wine? so i have to downgrade to get a cursor patch?
Perhaps, it's at least something you could try. If the files that need to be patched have changed too much from wine version to wine version, then the patch can't be applied successfully. I think :)

>  i wonder why they just didnt write this patch into wine with one of thier updates.
It will probably break other applications.

---

### Post by yowshi on 2008-02-24
yeah but so would downgrading my wine *sighs and grumbles*

---

### Post by Tabulator on 2008-10-13
I've got an easy solution for the cursor problem:

Download [this file]("http://www.4shared.com/file/66778833/22e3294e/cnc3-cursorstar.html") and replace the containing .ani files with the ones in your Cursors folder. (/RetailExe/1.9/data/Cursors/)

(Tested on Command & Conquer 3: Tiberium Wars v1.9 on Ubuntu v8.04, Wine v1.1.5)

These are pictures from the animated cursors (.ani) converted to normal cursor (.cur) files and then renamed back to the .ani files.

It works like a charm without changing your Wine version or patching and compiling. The only disadvantage is that the cursors don't animate :)

---

### Post by alimansoor500 on 2011-05-11
i was having the same problem ..i replaced all the .ani files but nothing happened then i turned of the cursor trails in the mouse option in control pannel thinking it may work and it did...

---

