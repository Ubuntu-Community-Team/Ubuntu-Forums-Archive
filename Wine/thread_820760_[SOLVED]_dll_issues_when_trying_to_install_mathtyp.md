---
title: "[SOLVED] dll issues when trying to install mathtype"
date: 2008-06-06
forum: Wine
---

### Post by gatorbrit on 2008-06-06
Hi, I am trying to install MathType (equation editor) in wine.  I am running the latest version of wine.

I can get mathtype to run from its location on the windows XP drive, but it won't install the necessary fonts, so I want to try and install it directly with wine.  

When I run wine on the mathtype executable I get this...

> err:module:import_dll Library riched20.dll (which is needed by L"C:\\windows\\system32\\riched32.dll") not found

As far as I can tell both riched.dll and riched32.dll are located in the wine windows/system32 directory.

Any thoughts?

Many thanks

Rich

---

### Post by cogadh on 2008-06-06
First off, don't run applications through Wine from an existing Windows installation. More often than not, it won't work and more importantly, it can screw up your Windows partition.

As for the DLL error, is that happening when you try to install it properly in Wine, or is it happening after the app is installed and you are trying to actually run it?

---

### Post by gatorbrit on 2008-06-06
Thanks, it happens when I run the initial installation exe file.  

And point taken on running from the windows partition -  I'll avoid that.  Thanks

---

### Post by cogadh on 2008-06-06
Have you installed any other apps in Wine already? If not, try deleting the .wine directory and creating a new one with winecfg.

---

### Post by gatorbrit on 2008-06-06
Yes I have installed office XP and stata using wine.  THey all run great.  I really don't want to start over if I can help it.

---

### Post by cogadh on 2008-06-06
Agreed, no need to mess up a good Wine install at this point. How about creating a separate .wine directory for troubleshooting MathType? Since you already have functional software installed, it might make it easier and less likely to break anything. Once you have figured out what is actually wrong with the install, then you can follow the same steps on your normal .wine directory and install it there. To make and use a separate .wine directory:
```
wineprefixcreate --prefix ~/.winemathtype
env WINEPREFIX=~/.winemathtype winecfg
env WINEPREFIX=~/.winemathtype wine <install executable>.exe
```

---

### Post by gatorbrit on 2008-06-06
Great - that worked and it installed fine.  Very curious.  It runs well now. I just have to figure out how to get it to find the true type fonts.  I copied the symbol.ttf file from my windows partition to the system32 fonts folder in the new winemathtype folder but it is not finding it - is there anything else I need to do.

THanks for your help!!!

Rich

---

### Post by gatorbrit on 2008-06-06
Actually - I got the fonts to work - had to select - "load factory settings" in mathtype to get it to work.  

This is soooo awesome.  Having access to an MS compatible equation editor is basically the must have for me and linux.  Now I am good to go!!!!

THanks again for your quick help.

---

