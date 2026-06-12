---
title: "xorg.conf resolution changes not &quot;sticking&quot;"
date: 2007-04-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by sohosources on 2007-04-24
Hi, gang:

I have a fresh install of 7.04 A64. Enabled "restricted driver" for my ATI X850XT PCIe vid card. Restarted X. Rebooted PC.

I edited xorg.conf to add 1280x960 resolution (worked on i386 install), but when I restart X or reboot system, the new resolution isn't available.

Also opened alt-F2 box and ran "glxgears", which ran slowly...

I guess 3D acceleration ISN'T enabled, right?

And what about xorg.conf?

Thanks for your help!

--Kirk in MN

---

### Post by Coucouf on 2007-05-03
Hi there you may have a look at [this page]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") which is a detailed and well explained HOWTO on how installing the ATI binary drivers.

To check that 3D acceleration works correctly, you can type the following command in a terminal :```
glxinfo | grep render
```
If it works, you will get the following answer :```
direct rendering: Yes
```

An alternative is to use the open source 'radeon' driver, which should work better if you want to enable desktop effects, but has lower 3D performance as the ATI binary driver.
To use it, just put 'radeon' as the driver name in your xorg.conf file.
Here is how the graphic card section looks like for my X800XL :
```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "radeon"
        BusID           "PCI:5:0:0"
        Option "GARTSize" "64"
        Option "DRI" "true"
EndSection

```

---

