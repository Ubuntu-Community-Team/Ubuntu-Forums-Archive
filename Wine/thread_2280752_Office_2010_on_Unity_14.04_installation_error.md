---
title: "Office 2010 on Unity 14.04 installation error"
date: 2015-06-02
forum: Wine
---

### Post by toby8 on 2015-06-02
I installed wine 32 bit version according to this thread, and it is working:
[http://askubuntu.com/questions/483636/installing-32-bit-wine-1-7-19-on-64-bit-ubuntu-14-04](http://askubuntu.com/questions/483636/installing-32-bit-wine-1-7-19-on-64-bit-ubuntu-14-04)

However, I could not install MS Office 2010 successfully. While the installing process started for a short time, it popped out: encounter an error during setup.

Can anyone give me some advice? Thanks :)

---

### Post by leunam12 on 2015-06-15
Did you install any additional libraries? Read this from WINEHQ

> [B]Make sure all dependencies of Wine are installed on your system, including winbind.     
[/B]Install Office 2010 to a clean wineprefix--no winetricks or other  tweaks, and no other applications installed. Do not change the Windows  version in winecfg; it should remain at the default setting of XP.

After installing, set riched20 to native, builtin in winecfg to enable  Powerpoint to start and selection boxes to display correctly. Do not use  winetricks; Office installs its own riched20 to a private directory,  and the one installed by winetricks is insufficient. This override may  be set globally if Office is installed to a separate wineprefix  (recommended). If other applications are installed to the wineprefix  (strongly discouraged), either set the override individually for each  Office application, or set riched20 to builtin individually for the  non-Office applications, as non-Office applications will not be able to  find the riched20 installed by Office.

---

### Post by cmcanulty on 2015-06-15
yes I followed the directions very carefully from wine HQ

---

### Post by leunam12 on 2015-06-15
The only way I can install MS Office in my computer is if I run the setup.msi file instead of the setup.exe, like this:```
wine start setup.msi
```you have to be in the same directory where the msi file is. Worth a try.

---

### Post by cmcanulty on 2015-06-15
OK I will try that next time I am at the library, thanks

---

