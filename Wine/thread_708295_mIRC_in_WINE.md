---
title: "mIRC in WINE"
date: 2008-02-26
forum: Wine
---

### Post by Allus on 2008-02-26
I installed WINE today and then installed mIRC.  I have nothing at all against XChat or other irc clients, but I am familiar with mIRC and am working with someone on line on mIRC specifics. So...

It's up and except for a small glitch when first logging on, it works great.

My only real complaint is that colors and text seem to be smaller and faded in the WINE client. A bit hard on the eyes.

Is this something I can change or is this just the result of translation in WINE?

---

### Post by happyhamster on 2008-02-26
- Perhaps installing the windows truetype fonts will help:

sudo apt-get install msttcorefonts

- When running 'winecfg', in the graphics tab, there's an option to increase the wine-screen-resolution (usual default setting = 96 dpi)

- It's also possible to theme wine, but it could cause slowdowns and crashes IIRC.

---

### Post by Allus on 2008-02-27
Happy, thanks a lot!

That works perfectly. I can't believe the difference.\\:D/

Hey, since you're so good at this, how about one more question:

The Wine pkg is a hidden folder in my home directory. And that's where the C drive hides and the Program Files.  That's fine and I kind of like that. 

But, when I'm using a Windows application, (currently I'm using MultiProxy), I need to navigate to that folder to open up a file.  But navigation window will not show hidden folders/files.  How do I get around that?

Hey, thanks again for the font solution!):P

---

### Post by notwen on 2008-02-27
If your wine dialog windows are similar to Nautilus dialog windows, you may want to try right clicking and see if the sub-menu offers you a hide/unhide hidden folders/files option.  Other than that maybe try CTRL+H.  These are both ways to hide/unhide hidden folders/files in Nautilus.  I don't use WINE enough to recall what a open/save dialog windows looks like under WINE.  Post back and let me know if this works for you.  =]

---

### Post by Allus on 2008-02-27
Hello Notwen.   Nope that didn't work.  The 'open file' window is just like the way it is in Windows.  If a file or folder is hidden it won't show up in a navigation window.

I see what you mean, though.  When I try Ubuntu's navigation window right clicking does give me the option to show the hidden files. 

The thing is if you select to show hidden files in Windows, those files and folders will show up in a navigation window. But the wine version will not have them show up at all. 

Thanks though for the suggestion.

---

### Post by happyhamster on 2008-02-27
I'm not really sure I get the situation. The way I understand it is: you have an application (Multiproxy) which has to open a file. When you use Multiproxy to open that file, you can't because it won't see hidden folders. Is that correct?

If so, where does Multiproxy start navigating? In your home folder perhaps? (You would expect it would start in /Program File/Multiproxy or something, and that it would at least find a c: drive or such.)
Where is Multiproxy installed BTW?

---

### Post by Allus on 2008-02-28
Hiya happy.   Yes, you pretty much get the picture.

Actually, in MultiProxy I had to import a proxy list.  So, by putting that list in /home/me  I was able to navigate to it.  So, my immediate problem is solved.  But if I ever have to navigate to a file or folder that MUST reside on the 'virtual' C drive I won't be able to.

WINE exists as a hidden folder in my home directory: .wine

Inside that folder are the folders dosdevices and drive_c.

Inside drive_c you have the Program Files which contain all the programs.

So, if I'm using one of the windows programs and have to navigate to one of those directories, I won't be able to because the .wine folder will not show up in the "Open" window.  

I tried renaming the .wine to wine, to make it unhidden. But I guess that screws up paths set up by the emulator, and I couldn't run any of the programs.  Had to re-install them. 

So, at this point it's hypothetical, (for me anyway), but I'm still wondering if this is a bug in the wine package.

---

### Post by Allus on 2008-02-28
> **happyhamster said:**
> 

If so, where does Multiproxy start navigating? In your home folder perhaps? (You would expect it would start in /Program File/Multiproxy or something, and that it would at least find a c: drive or such.)
Where is Multiproxy installed BTW?

Sorry, I didn't address this.  The Open window starts in my home folder.  Yes, it would be more logical for it to start on the C: drive.

MultiProxy is installed at :

 /home/me/.wine/drive_c/'Program Files'/MultiProxy

I don't believe I had any choice in this, but I'm not sure now. :oops: Anyway that was the default path.   The next time I install a windows pkg I'll have to pay more attention and see if they give me a choice on the path.

---

### Post by happyhamster on 2008-02-28
- How do you run the application? If you start it from a terminal (preferred method IMHO) then make sure that you run Multiproxy from within its own folder. In other words: always navigate to the correct folder first, then run the executable:

wine MProxy.exe

- (that's the way windows applications expect to run). And don't use:

wine ~/.wine/drive_c/Program\ Files/MultiProxy/MProxy.exe 

- from somewhere else (your home dir for example).

---

### Post by Allus on 2008-02-28
> **happyhamster said:**
> - How do you run the application? If you start it from a terminal (preferred method IMHO) then make sure that you run Multiproxy from within its own folder. In other words: always navigate to the correct folder first, then run the executable:

wine MProxy.exe

Well, that doesn't work.  When I try that in a terminal I get:

wine: could not load L"c:\\windows\\system32\\MultiProxy.exe": Module not found

Actually, I start the programs with keyboard shortcuts I create in gconf-editor.
But, there is also a Wine drop down menu in the desktop toolbar that lists the applications.

---

### Post by happyhamster on 2008-02-29
> **Allus said:**
> Well, that doesn't work.  When I try that in a terminal I get:

wine: could not load L"c:\\windows\\system32\\MultiProxy.exe": Module not found
That error appears when the file isn't found in the current folder. So either the file isn't there, or there was a typo in the filename.

> 
Actually, I start the programs with keyboard shortcuts I create in gconf-editor.
But, there is also a Wine drop down menu in the desktop toolbar that lists the applications.
When using launchers, it helps if you write the path the windows way. Instead of:

wine "/home/username/.wine/drive_c/Program Files/MultiProxy/MProxy.exe"

use:

wine "C:\Program Files\MultiProxy\MProxy.exe"

(Naturally the actual filenames etc. will be different in your case.)

---

### Post by johnnylavah on 2008-09-03
has anyone ever tried to run xdcc browser in mirc?  i can install it, but cannot get the script to run...

[http://www.mirc.net/projects.php?go=1063381627&get_desc=1](http://www.mirc.net/projects.php?go=1063381627&get_desc=1)

---

### Post by kdorf on 2008-09-03
Try making a symbolic link to the hidden folder in your home directory.

ln -s .wine/drive_c/path/to/folder name_of_folder

name_of_folder will now be a folder in your home directory which points to the hidden folder you want.

---

