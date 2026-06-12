---
title: "Manually putting a program icon under Wine's &quot;Programs&quot; folder"
date: 2013-07-08
forum: Wine
---

### Post by Tom_ZeCat on 2013-07-08
You won't believe what I got to run under WINE.  WordStar for Windows 2.0!  It was the last version of WordStar and it came out in 1992.  It was a 16-bit program.  I installed it because I have old WSWin files I want to convert over.  It runs under WINE's Windows 3.1 setting.  

The WSWin installer did not, however, put the WordStar icon under the programs folder.  I'd like to do so.  I'm also going to attempt installing a French/English -- French/German dictionary named Ultralingua.  However, what I have is a portable edition.  In Windows I would simply make a folder under "Program Files (x86)" and copy all the files there, then make a shortcut on the desktop.  This program has no installer -- or at least I lost the copy I bought that did and later made this one into a portable copy.  So I'm thinking, as is the case with WordStar for Windows, I'm going to need to somehow manually put an icon under "Programs".

Edit: An update -- I found these instructions here: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)
> Changing application specific settings
Type this command into your terminal.

winecfg
Click on Add Application...

Navigate to where the .exe is and choose that program
The dropdown at the bottom allows you to choose which version of Windows Wine should emulate. Also, any changes to the Libraries and Graphics tabs will only affect the chosen application in the Applications tab.
Using Windows Themes/Skins In Wine

I did that, but no WordStar for Windows program group or icon shows up under WINE.  I also went to WSWIN.EXE and right clicked and linked it to the desktop, but no desktop shortcut shows up.  Maybe the program is just to old?  I can run it by surfing to WSWIN.EXE and double clicking.

---

### Post by CatKiller on 2013-07-10
Work out the command to run the program in Wine on the command line (it'll be something like wine /some/path/MSWIN.EXE - case is important) and then create a launcher on the Desktop or menu that runs that command.

---

### Post by Tom_ZeCat on 2013-07-10
> **CatKiller said:**
> Work out the command to run the program in Wine on the command line (it'll be something like wine /some/path/MSWIN.EXE - case is important) and then create a launcher on the Desktop or menu that runs that command.

That worked!  Thanks.

---

