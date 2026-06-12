---
title: "Automatically Opening Microsoft Office Appliccations"
date: 2008-01-07
forum: Wine
---

### Post by Russianspi on 2008-01-07
So, I installed Microsoft Office 2000 under Wine - no problems.  Yes, I know about OpenOffice - I use it every day (and like it, usually).  That said, I'd like to figure out how to automatically open files with Microsoft Office file formats (.doc, .xls, .ppt, etc.) automatically when double clicked.  My wife gets E-mail updates from a friend in .doc format (yes, I know that she should send it in a better format, .pdf, .odf, etc., but she doesn't).

The trouble is, when you open it up with Open Office, the newsletter gets mangled.  It's a pretty complicated layout, so that's not surprising.  I'd like my wife to be able to download the newsletter and double click it to open it in Word (or just tell Firefox to automatically open it in Word).  I tried running a few different custom commands, but nothing seemed to do the trick.  Can anyone tell me the proper "custom command" to get it to open in MS Word (under Wine)?  Thanks in advance.

--Dan

---

### Post by gilf on 2008-01-07
Try:

1.) Right click on a .doc file
2.) select **Properties**
3.) select **Open With** tab
4.) click on **"Add"**
5.) click on twistie **"Use Custom Command"**
6.) Type in 

> wine *path-to-msword's-executable.exe *

7.) then click on the checkbox for wine in the **Open With** tab.

I believe that should work, but don't have Word installed to test completely.

---

### Post by Russianspi on 2008-01-08
I thought that I had tried that before, but apparently I hadn't.  Still though, it's not quite the result I'm looking for (although it's closer!)  Both:```
wine '/home/dalaina/.wine/drive_c/Program Files/Microsoft Office/Office/WINWORD.exe'
``` and ```
/home/dalaina/.wine/drive_c/Program Files/Microsoft Office/Office/WINWORD.exe'
``` as "Custom Commands" open the program, but not the file in the program.  So what I have is a blank document open in MS Word, but not the one I am trying to open.  How do I pass my filename to Word?  I know with Linux programs, if you open a file with a custom command, it automatically passes the file name to the program.  I would guess that it does the same here, but why isn't Word taking the file name?

---

### Post by gilf on 2008-01-08
Wish I could test it out for you, but lacking Word I can only make suggestions without giving results.

As I remember it in Windows there was an additional action in the definition of the extension -- maybe the word **open**. I'm guessing that the same will apply through wine.

So maybe try

> wine '/home/dalaina/.wine/drive_c/Program Files/Microsoft Office/Office/WINWORD.exe' open

The space is kind of closed up here but I mean there to be a space before the word open. I don't know if it should go in the ticks or not.

If that doesn't work, try getting into the extension definition in your windows version of Word to see what's actually used.

My wife has Word, but she's using it all the time (a professional editor working at home) so I can't check it myself.

---

