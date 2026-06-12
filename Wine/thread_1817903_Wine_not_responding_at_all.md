---
title: "Wine not responding at all?"
date: 2011-08-03
forum: Wine
---

### Post by errbee on 2011-08-03
Hey guys,

I've installed wine and winetricks to help run iTunes on my ubuntu system. I'm pretty sure everything I need is up to date. I'm using [http://www.ehow.com/how_5947302_install-itunes-ubuntu.html](http://www.ehow.com/how_5947302_install-itunes-ubuntu.html) as a reference. The process is dandy until I get to the terminal part, where I run wine iTunesSetup.exe. Instead of the installation program launching, I get this: 

wine: cannot find L"C:\\windows\\system32\\iTunesSetup.exe"

It clearly is there though. Even when I click the setup manually, it shoots me an error saying that wine cannot open it. Help please, for this might help me download other Windows programs as well!

Lucas

---

### Post by x-D on 2011-08-06
Have you tried right clicking on the iTunes setup .exe file, going to properties, the permissions tab, and clicking allow executing as program? (OR if you go to the terminal and do chmod +x /DIRECTORY/WHEREITUNES/ISINSTALLED!)

If you do that and then try either opening it or using the terminal, it should work? Post back if it doesn't :)

Hope this helped.... :)

x-D :guitar:

---

