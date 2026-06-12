---
title: "Y is my ATI driver not working ? Help !"
date: 2008-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by tarekeldeeb on 2008-01-28
Hello all ..

I have been working with Ubuntu since several months now .. cube desktop worked .. and all effect were cool ..
I had previously installed the driver from the restricted list (ATI Radion express series)
But when i type: glxinfo , i find that the direct rendering: No, although the vendor string was : ATI

I was satisfied .. until i was blocked when i tried transgaming !

I had to install the ATI distributed driver ..

I downloaded it .. installed the driver .. typed: aticonfig --initial .. and rebooted ...

but the driver does not work .. and now i cant start the desktop effects .. and the vendor string became: MESA !

I repeated the scenario using the howto provided here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

as well as the envy tool:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Under Applications menu, i find the item "ATI catalyst control center" .. but it says that there is no installed driver!

Something is blocking me ..!!

I also tried to remove/re-install the restricted ubuntu driver .. with no success !!

Please help .. i cannot figure out the problem :confused:

Thanks in advance,
Tarek

---

### Post by Kilz on 2008-01-28
[Have a look here, this howto is real good.]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually")

---

### Post by tarekeldeeb on 2008-01-28
> **Kilz said:**
> [Have a look here, this howto is real good.]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually")

I followed the steps u gave ..

downloaded and installed ..

```

sudo dpkg -i xorg-driver-fglrx_8.452.1-1*.deb fglrx-kernel-source_8.452.1-1*.deb fglrx-amdcccle_8.452.1-1*.deb
Selecting previously deselected package xorg-driver-fglrx.
(Reading database ... 116821 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.452.1-1_amd64.deb) ...
Selecting previously deselected package fglrx-kernel-source.
Unpacking fglrx-kernel-source (from fglrx-kernel-source_8.452.1-1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.452.1-1_amd64.deb) ...
Setting up xorg-driver-fglrx (8.452.1-1) ...

Configuration file `/etc/xdg/compiz/compiz-manager'
 ==> Deleted (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** compiz-manager (Y/I/N/O/D/Z) [default=N] ? 
 * Starting atieventsd                                                   [ OK ] 

Setting up fglrx-kernel-source (8.452.1-1) ...
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.

Setting up fglrx-amdcccle (8.452.1-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

rebooted ..configured ati .. rebooted .. and i got this:
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7276 Release

```

then ..

clear the blacklist pci Ids variable *Recommended*
```

sudo gedit /usr/bin/compiz

# Driver whitelist
WHITELIST="fglrx nvidia intel ati radeon i810"

# blacklist based on the pci ids 
# BLACKLIST_PCIIDS="$T"
BLACKLIST_PCIIDS=""

```


rebooted ..

Now the desktop affects are back ..:)

but .. when i started the system test from the cedega , the session crashed into an orange full screen and i had to hard reset m lappy ..

when i started a simple game (xmoto) it was terribly slow .. the mouse cursor hardly moved !

Even the ATI Catalyst Control Center: complained that the driver is not installed !!

although the fglrxinfo gave good results .. the glxinfo showed direct rendering: no , and showed MESA as well in the vendor string !


Now .. I dont know how to proceed .. there is something still missing .. !

Please help ..

---

### Post by Kilz on 2008-01-28
> **tarekeldeeb said:**
> I followed the steps u gave ..

downloaded and installed ..

```

sudo dpkg -i xorg-driver-fglrx_8.452.1-1*.deb fglrx-kernel-source_8.452.1-1*.deb fglrx-amdcccle_8.452.1-1*.deb
Selecting previously deselected package xorg-driver-fglrx.
(Reading database ... 116821 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.452.1-1_amd64.deb) ...
Selecting previously deselected package fglrx-kernel-source.
Unpacking fglrx-kernel-source (from fglrx-kernel-source_8.452.1-1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.452.1-1_amd64.deb) ...
Setting up xorg-driver-fglrx (8.452.1-1) ...

Configuration file `/etc/xdg/compiz/compiz-manager'
 ==> Deleted (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** compiz-manager (Y/I/N/O/D/Z) [default=N] ? 
 * Starting atieventsd                                                   [ OK ] 

Setting up fglrx-kernel-source (8.452.1-1) ...
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.

Setting up fglrx-amdcccle (8.452.1-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

rebooted ..configured ati .. rebooted .. and i got this:
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7276 Release

```

then ..

clear the blacklist pci Ids variable *Recommended*
```

sudo gedit /usr/bin/compiz

# Driver whitelist
WHITELIST="fglrx nvidia intel ati radeon i810"

# blacklist based on the pci ids 
# BLACKLIST_PCIIDS="$T"
BLACKLIST_PCIIDS=""

```


rebooted ..

Now the desktop affects are back ..:)

but .. when i started the system test from the cedega , the session crashed into an orange full screen and i had to hard reset m lappy ..

when i started a simple game (xmoto) it was terribly slow .. the mouse cursor hardly moved !

Even the ATI Catalyst Control Center: complained that the driver is not installed !!

although the fglrxinfo gave good results .. the glxinfo showed direct rendering: no , and showed MESA as well in the vendor string !


Now .. I dont know how to proceed .. there is something still missing .. !

Please help ..

Games and desktop effects can crash your system. Desktop effects are relitivly new and there are a lot of issues with them still. You might want to report the problem to cedega and compiz so they can fix it.
Odds are it reverted to a state before the driver was installed. Reinstall and turn off effects before playing games, you can always turn them back on.

---

### Post by tarekeldeeb on 2008-02-02
Mmm..

So .. how can I REVERT to ubuntu's restricted -supported- drivers ..??

My computer is too slow .. 

Ok i will abandon games .. but i did not save backups of xorg.conf

When i enable the driver from the restricted manager .. it does not work .!!

Do u have any clue .. ?:confused:

---

### Post by coskierken on 2008-02-02
Just a note:  Is your card supported with the new ATI 8.01 drivers?  If so, and you still have xserver-xgl installed, this is the problem I had.  I was having the same error come up on my system (Core2Duo ATI X1700 Mobility) until through research and trial/error fixed the problem.  My catalyst center works now.  Try doing a complete purge of xserver-xgl.  Do you have Compiz Config Manager installed?  I hope this helps.  The video playback while Compiz is running does not work correctly.  I have not read of any fixes as of yet.  Maybe next release will fix it.  When you installed the new drivers, can you still shutdown and log out without problems?  If you have problems, follow the link below.  :)

[http://www.phoronix.com/forums/showpost.php?p=23097&postcount=23](http://www.phoronix.com/forums/showpost.php?p=23097&postcount=23)

---

### Post by tarekeldeeb on 2008-02-02
> **coskierken said:**
> Just a note:  Is your card supported with the new ATI 8.01 drivers?  If so, and you still have xserver-xgl installed, this is the problem I had.  I was having the same error come up on my system (Core2Duo ATI X1700 Mobility) until through research and trial/error fixed the problem.  My catalyst center works now.  Try doing a complete purge of xserver-xgl.  Do you have Compiz Config Manager installed?  I hope this helps.  The video playback while Compiz is running does not work correctly.  I have not read of any fixes as of yet.  Maybe next release will fix it.  When you installed the new drivers, can you still shutdown and log out without problems?  If you have problems, follow the link below.  :)

[http://www.phoronix.com/forums/showpost.php?p=23097&postcount=23](http://www.phoronix.com/forums/showpost.php?p=23097&postcount=23)

Thanks a TON ..

u r ABSOLUTELY right .. i checked my card .. it is Radeon Xpress 1100 ..  not listed in the supported ati 8.01 driver !!

All this time and i was trying with the WRONG driver ..

I googled .. and did not find my driver .. many ppl complain (from this forum as well) .. 

Now i want to revert to the restricted drivers .. they worked better ..

i had tried to install the 8.01 (my HW not supported) , then i tried to re-enable the restricted .. but they no longer work ..

Can u help ?

---

### Post by Kilz on 2008-02-02
Back in September of last year ATI brought out a driver from a new code base. [Here is the last driver]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.40.4-x86.x86_64.run") from the old code base, Im still using it without problems.[ According to the release notes ]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.40.4.html")for that version your card is supported. Just use the howto I gave you in post 2 and edit the commands to match the 8.40.4 driver version. The bad thing is compiz doesnt work for this version, but cedega will.
Ati releases a new driver about once a month, look for it and a new driver that will support your card. Someone always makes a post here when they are released.[ Or you can go here]("http://ati.amd.com/support/drivers/linux64/previous/linux64-r-8-40-4.html") and click on the rss driver notificatuion about half way down.

---

