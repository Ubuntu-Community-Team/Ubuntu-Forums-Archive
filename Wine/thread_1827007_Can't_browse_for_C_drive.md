---
title: "Can't browse for C drive"
date: 2011-08-17
forum: Wine
---

### Post by emcphers on 2011-08-17
Hi, I wonder if somebody can help me...

I'm trying to use Wine to install some windows applications (can't help it, my boss loves track changes) by following these directions [http://maketecheasier.com/linux-howto-miss-your-windows-application-try-wine/2007/12/15](http://maketecheasier.com/linux-howto-miss-your-windows-application-try-wine/2007/12/15)

It all goes fine until I try to look at the C drive I created using "winecfg", but the browse button is greyed out. Any idea why this could be? Also, when I do become able to browse, I'm not sure where my C drive would be.

Thanks in advance for your any advice you can offer.

Emily

---

### Post by DoktorSeven on 2011-08-17
The "browse" under winecfg's drive mappings is to set (not look at) a path for a drive, and C is now something that can't be changed -- those instructions must be from an old version of Wine where you can.  By default, it's located under your home directory in .wine/drive_c/ (note that since .wine starts with a dot, it's a "hidden" file and you'll have to enable hidden files in your file manager to see it).

(You can change the directory drive_c gets created in with the environment variable WINEPREFIX but this has to be set each time you use it so you'll have to specify it because Wine defaults to .wine unless told otherwise).

Wine does have a built-in file manager that works like the very old Windows file managers; you can run this by running **winefile** (click C: on the menu bar to get to your Wine C drive).

I always use symbolic links to better access my Wine directory:
**ln -s ~/.wine/drive_c/ ~/wine/** 
That way, your wine C drive just shows up in "wine".

---

### Post by emcphers on 2011-08-18
Thanks, DoktorSeven! I didn't realize that post was from 2007...

When I try to use my .exe to install an application ("wine the-name-of-the-application.exe") the terminal says it cannot find the specified file. This makes sense as I just have the .exe on my desktop, not in the C drive I can see using winefile. Is there a way to use winefile to move the .exe to the C drive? Or maybe there's something else I have to do?

Thanks again for your help,
Emily

---

### Post by raja.genupula on 2011-08-18
```
When I try to use my .exe to install an application ("wine  the-name-of-the-application.exe") the terminal says it cannot find the  specified file
```


no man your .exe file should be in your home folder if you're running as above . other wise just let it be . 

```
cd Desktop 
```
then run above process above again . 

c drive will be at ```
.wine
``` folder . its a hided folder in your home directory . 
press ctrl+h to hidden files

---

