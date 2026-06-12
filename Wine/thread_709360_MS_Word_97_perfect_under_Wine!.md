---
title: "MS Word 97 perfect under Wine!"
date: 2008-02-27
forum: Wine
---

### Post by Anders J on 2008-02-27
This is not a problem, I need no help but would only like to share!

Found my old MS Office 97 SBE installation CD. Without any expectations I popped it into the CD drive. I didn't try to run the autorun feature but instead browsed to the Word 97 binder.

Found the "install.exe", right clicked and picked "Open with "Wine Windows Emulator"" and then just leaned back for the expected crash.

But it just came through the complete installation and it runs like a charm and resolves many of the issues I had where OO does not resolve formatting in the way the wrietr of the document expected.

Opens and saves, printing works and brings up the CUPS printer dialogue, although the "Print Now" icon has turned into a "instant close without saving". Even the much hated Office assistant appears.

Cheers to the Wine team!

---

### Post by wandalalakers on 2008-02-27
LOL!  That's great!

---

### Post by Sammi on 2008-02-28
Office 2000 should work just as well. 2003 is getting close, and a lot of people have it running quite nicely, but 2007 still won't run at all.

Just give it one or two years, and I think that 2003 will probably be running perfect, and 2007 running for most people, with some tweaking.

---

### Post by Ralph L on 2008-07-19
Has anybody managed to get the "help" feature in Word, PowerPoint, etc (Office 97) to work.  In my case the help files loaded (I see them in drive_c, but when I bring up help in Word, it just sits there.  When I try Search, it says "not implemented.  Running Hardy, Wine 1.1.1, and Office 97.

Also, I can't make Outlook 97 run, although it will run under Crossover.

Any help on help appreciated.

---

### Post by aceqbaceq on 2008-09-17
> **Anders J said:**
> This is not a problem, I need no help but would only like to share!

Opens and saves, printing works and brings up the CUPS printer dialogue

Cheers to the Wine team!

although in my case i cannot print. apppeard dialogue "printer not installed". while in the same system wine+office2003 works well and print :(. i can not find solution anywhere..

---

### Post by a1z on 2008-10-14
PART 1/3:

Installing Office 2K in Hardy is done with Wine v1.1.2.

1) install wine 1.1.2
2) extract office 2000 ISO (or zip or rar file)
3) install using setup.exe

====================
PART 2/3:

My question:

MS Word 2000 uses CPU all the time. My CPU meter on the task applet bar shows full usage of CPU when MS Word 2000 is opened and being used. The performance is smooth, nonetheless. When I minimize the window, the CPU relaxes.

What is going on? Is there a way to control the workload of CPU by MS Word 2000? Will this affect the performance of the word processor?

====================
PART 3/3:

SUMMARY:

I see this heavy usage of CPU under these conditions:

1) Hardy + Wine1.1.2 + Office 2000
2) Hardy + Wine1.1.2 + Office 2003
3) XP + Office 2000 (mentioned above)

But it is okay when I open and edit a document under these conditions:

1) XP + Office 2003
2) Hardy + Wine0.9.59 + Office 2003

Thanks in advance!

-a1z

---

### Post by flashdog on 2010-08-21
Hi,
I have Ms Office 97 Pro and I would like to use it with 10.04 Ubuntu.

In Internet I have found this Howto ( [http://www.junauza.com/2010/04/how-to-install-microsoft-office-on.html](http://www.junauza.com/2010/04/how-to-install-microsoft-office-on.html) ) and I would like ask whether is it how everybody did here this?

Thank you in advance.

---

### Post by ronnielsen1 on 2010-08-21
>  but 2007 still won't run at all.
I have 2007 running perfect. You just have to do some overrides on some of the libraries

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

---

