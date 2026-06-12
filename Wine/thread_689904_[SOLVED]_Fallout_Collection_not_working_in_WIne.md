---
title: "[SOLVED] Fallout Collection not working in WIne"
date: 2008-02-06
forum: Wine
---

### Post by Wylkar on 2008-02-06
I recently purchased the Fallout Collection DVD-ROM and both fallout 1 and fallout tactics work but when I try to run fallout 2 I get the error message 'could not find/load text fonts' does this mean I should do a medium install instead of my current small install?
thanks

---

### Post by dudeofthedead on 2008-02-06
Does it say which fonts are missing?  Please write the full output if you have it.

---

### Post by Wylkar on 2008-02-06
I go to applications>wine>programs>black isle>fallout 2>fallout 2 and when I do this my wine desktop comes up with a dialogue box marked error "couldn't find/load text fonts" this is the entire error message, and when I close the error box wine closes

---

### Post by dudeofthedead on 2008-02-08
Maybe Wine will tell you more about the problem if you run the game through a terminal, like this:

```
wine /path/to/the/.exe
```

If that doesn't give you more information, try and add some of the most common fonts (ttf files) used in Windows to your ~/.wine/drive_c/windows/fonts directory.  e.g.: Tahoma, Arial, Helvetica, Verdana, Courier... and report back.

---

### Post by Wylkar on 2008-02-08
I still get the same error message (I can post the Terminal output if you want). where would I find the fonts?

---

### Post by dudeofthedead on 2008-02-08
There's a reason behind my asking for the output, for it's probably the most efficient way to start looking for a fix - sometimes it's just begging to be solved, see it as an error log that tells you where what went wrong. But anyway, I think you already know that.

If you have a Windows partition, I'd suggest you go to c:/windows/fonts and copy all the .ttf files over to ~/.wine/drive_c/windows/fonts/.  Speaking of the latter, is this folder of yours empty or does it contain some files?

This, or I could try uploading the fonts.

---

### Post by Wylkar on 2008-02-09
I didnt see any error message in the terminal output, and the fonts folder is empty. Also I dont have a windows partition so if you could try and upload the fonts that would be helpful.

---

### Post by Yeeha on 2008-02-09
Well maybe installing msttcorefonts package helps? its suggested package when you install wine so i guess wine should start using those without any configuration needed.

---

### Post by Wylkar on 2008-02-09
I have msttcorefonts installed

---

### Post by dudeofthedead on 2008-02-09
I have found this [FAQ](http://www.nma-fallout.com/forum/viewtopic.php?t=5061), which hopefully will help you get through with this.

---

### Post by dudeofthedead on 2008-02-11
No news good news?

---

### Post by Wylkar on 2008-02-11
Thanks, it looks like this will work

---

### Post by Wylkar on 2008-02-11
I am having trouble finding one of the files mentioned (fallout2.cfg), I will also ask about this on the site you linked to to see if anyone else has had similar problems

---

### Post by dudeofthedead on 2008-02-12
Maybe it doesn't bear that name, and there may be other .cfg files as well, try this for a quick overview:

```
locate ~/.wine/*.cfg
```

---

### Post by Wylkar on 2008-02-12
I only get two results and those are /home/myusr/.wine/drive_c/Program Files/GSP/Fallout/fallout.cfg
/home/myusr/.wine/drive_c/windows/temp/I1200452747/Windows/resource/jre/lib/jvm.cfg
it looks like I only have the .cfg file for fallout 1

---

### Post by dudeofthedead on 2008-02-13
Then it appears your installation is not complete, and you may be required to do a fresh install of it.

Nonetheless, have you taken a peek inside this so-called fallout.cfg?

---

### Post by Wylkar on 2008-02-13
It's inside the fallout 1 folder I will try copying it into the fallout 2 folder and modifying it to work. I have also installed fallout 2 several times I have been unable to uninstall it because the uninstaller comes up with the message: Uninstaller could not open or cannot use the file 'C:ProgramFilesBlackIsleFallout2uninst.log' I have manually deleted the files and reinstalled fallout 2 and it made no difference

---

### Post by Wylkar on 2008-02-13
I got it working I had to copy the files MASTER.DAT and CRITTER.DAT from the CD to my fallout 2 directory. Thanks for all the help.

---

