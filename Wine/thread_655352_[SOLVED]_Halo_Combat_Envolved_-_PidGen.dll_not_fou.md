---
title: "[SOLVED] Halo: Combat Envolved - PidGen.dll not found"
date: 2008-01-01
forum: Wine
---

### Post by b0rka7a on 2008-01-01
I have problem with the installation of Halo under Wine 0.9.52.
After I type the serial number and click Next, Halo says: "Cannot load PidGen.dll", but it's in the folder.
(I tried copying the files from the CD to the hard drive, but it still gives me that error)
Here's the output of Wine during the install:
```

fixme:system:SystemParametersInfoW Unimplemented action: 110 (SPI_GETSHOWIMEUI)
fixme:system:SystemParametersInfoW Unimplemented action: 110 (SPI_GETSHOWIMEUI)
fixme:system:SystemParametersInfoW Unimplemented action: 110 (SPI_GETSHOWIMEUI)
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\media\\iso\\PidGen.dll") not found
fixme:system:SystemParametersInfoW Unimplemented action: 110 (SPI_GETSHOWIMEUI)
fixme:system:SystemParametersInfoW Unimplemented action: 110 (SPI_GETSHOWIMEUI)
fixme:system:SystemParametersInfoW Unimplemented action: 110 (SPI_GETSHOWIMEUI)

```
Any ideas ?
Thanks in advance!

---

### Post by happyhamster on 2008-01-01
Get a native windows file MFC42.DLL (from a windows computer, or download it), and put it in wine's system32 folder. Location is usually:

~/.wine/drive_c/windows/system32 

(a hidden folder in your home dir)

---

### Post by happyhamster on 2008-01-01
Also, go here for more info:

[http://ubuntuforums.org/showthread.php?t=486986](http://ubuntuforums.org/showthread.php?t=486986)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720)

---

### Post by b0rka7a on 2008-01-01
Thanks. The installation went good, but as every other product of Micro$oft, Halo isn't working :)

---

### Post by s3a on 2008-06-25
Thanks! Downloading that dll file and placing it in the system32 folder made the installation succesful!

And by the way, it works on Wine 1.0 but on my comp it uses 100% cpu (Pentium 4, 3 Ghz CPU) and it freezes alot until it stops working, I don't know if that's because I'm using 64-bit (Gutsy) or if it's a Wine problem but if you have a better CPU, it should work for you! (Earlier versions of Wine apparently can be made to use Halo without this high CPU usage I am talking about)

Once you solve that dll problem (which you did), get Wine 0.9.39 and follow this guide --> [http://ubuntuforums.org/showthread.php?t=486986](http://ubuntuforums.org/showthread.php?t=486986)

P.S.
I think you'll need proprietary video drivers too.

---

### Post by zimany on 2010-05-12
Thanks.:) it took me a while to find this. #-o

---

### Post by aidenscool09 on 2010-07-24
umm, s3a was using 64-bit on a Pentium 4? Thats stupid. Pentium 4s don't support 64-bit, they only go as low as Celeron and Core 2 series.

---

### Post by Arthur_D on 2010-12-25
Hi, I did as suggested in this thread to move the dll into the wine dir, and that helped me move past the "can't find dll" bit, but now it complains about pidgen.dll being in use by another application. Any idea how to solve that? Tried looking around, but haven't found any solution yet.

---

### Post by Wolfybear on 2013-01-28
Hello, 

Sorry if this is a silly question (which I'm sure it is) but how do you view the console output as shown in the first post? It would be very helpful in figuring out what errors are cropping up while using WINE.

Thanks,
Wolfy

---

### Post by lisati on 2013-01-28
Old thread closed.

---

