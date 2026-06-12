---
title: "&quot;Installation language not supported error&quot; MS Office 2010 Professional Plus"
date: 2013-02-04
forum: Wine
---

### Post by lviggiani on 2013-02-04
Hallo,
In the past I successfully installed MS Office 2010 Professional Plus either in Ubuntu 12.04 and 12.10 x64 and wine 1.4 and 1.5 many times.

Now I got a new computer and I did a new installation of Ubuntu and I want to reinstall MS Office 2010 (same source) but it gives me "Installation language not supported" error.

I tried with wine 1.4 and wine 1.5 and I also read many posts on this forum... this is what I did:

Deleted any previous installation of wine, including ./wine prefix
Installed wine-1.5.22
Installed ia32 libes
Created prefix with WINEARCH=win32 winecfg
Installed dotnet2.0, msxml6 and core fonts in winetricks
Set msxml6 to native (windows)

when I run the installer it gives me the "Installation language not supported error". This happens with wine 1.4 and wine 1.5

The only thing different from my past successfull installations is that in the past I used to install from DVD, now since I don't have a DVD drive I made and iso image out of the same DVD used in the past and mounted under /media folder.

System language is Italian, but it worked in Italian even in the past.

Any idea?
Thanks.

---

### Post by lviggiani on 2013-02-05
UPDATE:

After trying, searching and trying again without success, I decided to "exhume" my old computer that fortunatelly has a DVD drive.
First I tryied to install Office 2010 from the same ISO that failed on my new computer and I got the same error.
So I run the installer from the original DVD where I extracted the ISO and the installation whent fine as expected.

This confirmed me that the way Ubuntu mounts the ISO files is not ok to the installer that detects that the contents have been altered as sais in Miscrosoft support pages.

The thing that sounds strange to me anyway is that the same ISO mounted in WIndows 8 allows succesful installation on that system.

Has someone faced the same issue?

Now, as a workaround for installing Office on my new computer (that hasn't got a DVD drive) I'll try to copy the entire .wine prefix from my successfull installation and see if works.

---

### Post by srekcahrai on 2013-02-05
Open winetricks and "Select the default wineprefix" choose "install a font" and select the **corefonts**.

---

### Post by lviggiani on 2013-02-09
> **srekcahrai said:**
> Open winetricks and "Select the default wineprefix" choose "install a font" and select the **corefonts**.

Naaaa nothing to do with winetricks. The dvd installs fine on a clean prefix. It has to do with the way Ubuntu mounts ISO files as the same ISO mounted in win 8 with native tools installs fine as well. Thanks anyway for your hint. Also when you install wine it automatically installs core fonts package

---

