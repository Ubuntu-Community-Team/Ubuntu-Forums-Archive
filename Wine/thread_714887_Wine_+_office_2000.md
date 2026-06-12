---
title: "Wine + office 2000"
date: 2008-03-04
forum: Wine
---

### Post by georgefairbanks on 2008-03-04
I've had Office 2000 working fine with wine for a year.  In the past week or so I've been having the problem that the office apps hang shortly after running them.  Here's an example error log from the console:

[FONT="Courier New"]$ msexcel                                                                
fixme:storage:StgCreateDocfile Transacted mode not implemented.
err:ntdll:RtlpWaitForCriticalSection section 0x13b728 "moniker.c: RunningObjectTableImpl.lock" wait timed out in thread 0009, blocked by 0000, retrying (60 sec)
wine: Critical section 0013b728 wait failed at address 0x7bc39110 (thread 0009), starting debugger...
Unhandled exception: wait failed on critical section 0x0013b728
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc39110[/FONT]

Any ideas?  Thanks!

---

### Post by georgefairbanks on 2008-03-04
Ok, so I followed the instructions in the "sticky" post on how to install the bleeding edge wine stuff.  Things work fine now.

---

### Post by georgefairbanks on 2008-03-05
... well, it works except that it won't save files, saying that the disk is full :-)

---

### Post by nowaycomputer on 2008-05-12
Hi, has anyone had any luck sorting the 'disk full' error?

I was using wine and excel fine under Gutsy, but upgrading to Hardy has caused me to get this error, which makes excel unusable. I've updated to the wine RC 1, but still no joy.

I have a guess that it might be to do with the way wine handles the file permissions? Mabye when wine opens excel it isn't getting write permissions, and excel handles this as 'disk full'? Just a guess, likely wrong, but any suggestions would be appreciated.

---

### Post by AciiiD on 2008-05-27
same problem here, first I couldn't use Excel anymore with hardy (though it was working like a charm if I copied the .cxoffice and .wine directories under a Gutsy).

Then I saw your post and tried with the last version of wine (1.0rc2) and it now work ! But only half the time ; for some obscure reasons, some xls files can't be saved anymore without getting the "disk full" error message...

Any luck on your side resolving this problem ?

---

### Post by AciiiD on 2008-06-01
the "disk full" problem is still present with the last version of wine : 1.0~rc3~winehq0~ubuntu~8.04-1


:\

---

### Post by joechummer on 2008-06-13
I can't say that this will work with Excel 2000, but I had the exact same "disk full" problem with Excel 2003 (and some people have had with Excel XP/2002 as well), and here's what I did.

I took the file I had open (an .xls file created natively on a Windows machine), copied the entire contents to the clipboard, opened a new workbook, pasted the contents, and saved.

The weird thing is the original file which Excel couldn't save changes to is 117K.  The new WINE-Excel created file that I pasted the contents into is only 29K.  That's a pretty big difference for a copy/paste, if you ask me.

I wonder if Excel files are over a certain size (100K perhaps?), Excel can't handle writing them to the disk any more because for some reason WINE isn't giving enough memory space in which to work?  Or maybe it didn't like my original file because somehow it KNEW it had been created on a Windows box?  *cue scary music*

---

### Post by AciiiD on 2008-06-18
I've filled a bug on wine bugzilla ([http://bugs.winehq.org/show_bug.cgi?id=13822](http://bugs.winehq.org/show_bug.cgi?id=13822)) but there is no activity on it has it's still "Unconfirmed".

Please go there and vote for the bug if you want it to get solved ! :>

By the way, the bug is still present in the following wine versions : rc4, rc5 and 1.0.0.


About the file size workaround, I tested many files and yes, using Excel files created with another version sometimes leads to that bug, while creating the file with the current version on Excel doesn't. BUT, it's not file-size related has I have some very big and small files which bug, or not.

Copying by hand some of those huge files is a PITA, to say the least.

---

### Post by skolnick on 2008-07-07
I saw this bug with Excel 2003. I created a file with it and saved it, no problem. Later, I edited the file with openoffice. After that, Excel would report the "disk full" when saving the file. I had to create an empty file, copy all the information and save it with a new name. No problem there. Somehow, editing the files with something different than Excel 2003 itself leads to this bug.

Regards.

---

### Post by hatguy on 2008-07-13
Comment #10 at wine's bugzilla ([http://bugs.winehq.org/show_bug.cgi?id=13822](http://bugs.winehq.org/show_bug.cgi?id=13822)), dated 13 July, suggests the problem can be fixed by installing MSIE 6 under Wine. The steps are given, and the fix was tested under Debian Lenny.

hatguy

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

