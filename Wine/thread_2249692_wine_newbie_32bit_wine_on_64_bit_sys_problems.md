---
title: "wine newbie 32bit wine on 64 bit sys problems???"
date: 2014-10-24
forum: Wine
---

### Post by einstein**-7 on 2014-10-24
Sys:       clean Ubuntu 14.04.1 with Nvidia 340 driver

Hi there I'm a wine newbie and trying to install The Witcher 2 ''steam edition'' with playonliux....  
Steam install fine operates but the game wont start due to missing drivers/libs directx9 and .net among others,  trying to install missing libs with playonliux results in runtime errors so i tried to install through winetricks and says not supported on 64bit system.  
Been reading up here [https://wiki.archlinux.org/index.php/wine](https://wiki.archlinux.org/index.php/wine) but confused as to how to get a 32bit version of wine installed and working -- it says something about enabling a Multilib repo by editing /etc/pacman.conf but no such file??

Any help would be greatly appreciated!

---

### Post by mastablasta on 2014-10-24
> **einstein**-7 said:**
> it says something about enabling a Multilib repo by editing /etc/pacman.conf but no such file??


makes sense. since you are using Ubuntu. I am not sure why you are looking for instructions for Arch Linux because you say you are using Ubuntu ?!?!

what you probably need is a 32 bit wineprefix: [http://askubuntu.com/questions/177192/how-do-i-create-a-32-bit-wine-prefix](http://askubuntu.com/questions/177192/how-do-i-create-a-32-bit-wine-prefix)
[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)


also I believe Witcher 2 has a Linux port, so why are you using wine?

---

### Post by einstein**-7 on 2014-10-24
> **mastablasta said:**
> makes sense. since you are using Ubuntu. I am not sure why you are looking for instructions for Arch Linux because you say you are using Ubuntu ?!?!

what you probably need is a 32 bit wineprefix: [http://askubuntu.com/questions/177192/how-do-i-create-a-32-bit-wine-prefix](http://askubuntu.com/questions/177192/how-do-i-create-a-32-bit-wine-prefix)
[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)


also I believe Witcher 2 has a Linux port, so why are you using wine?

Good point about the arch linux! was thinking linux archive, didn't realize it was a build of linux.
Oh and im trying to run TW2 in wine because all the reviews I came  across said the ported version was slower than the wine annd steam  doesn't seem to offer it in my steam lib and I'm not about to purchase  it again..

Tried the commands in the link and here is what i got.. not sure what to think errors both ways??


```
crush@crushmob:~$ WINEARCH=win32 WINEPREFIX=~/.wine winecfg
wine: WINEARCH set to win32 but '/home/crush/.wine' is a 64-bit installation.
```

```
crush@crushmob:~$ WINEPREFIX=/home/crush/win32 WINEARCH=win32 wine wineboot
wine: created the configuration directory '/home/crush/win32'
fixme:storage:create_storagefile Storage share mode not implemented.
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:iphlpapi:NotifyAddrChange (Handle 0x10ee890, overlapped 0x10ee89c): stub
wine: configuration in '/home/crush/win32' has been updated.

```

---

