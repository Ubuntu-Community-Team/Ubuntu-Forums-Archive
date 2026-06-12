---
title: "Powerbook G4 - Stuck at 640x480"
date: 2005-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by cybergypsy on 2005-11-22
Hi All

I have just finished a completely fresh instal of Ubuntu 5.10 on my Apple Powerbook G4 and the display is stuck at 640x480.

I`ve tried using the System , Preferences , Screen Resolution - but only 640x480 is offered.
Had a look in /etc/X11/x.conf and it all looks right with the correct 1152x768 resolution set. The Control , Alt , + and - keys do nothing.

Also had a look at all the other posts here in the forums but haven`t found anything useful.

Its odd as my display was perfect when using Ubuntu 4.10 / XFree86 / radeon.

Anyone got any ideas ?

Thanks
cybergypsy

---

### Post by ssam on 2005-11-22
```
sudo dpkg-reconfigure xserver-xorg
```

might help find the correct resolution.

---

### Post by cybergypsy on 2005-11-22
[QUOTE=ssam]```
sudo dpkg-reconfigure xserver-xorg
```

might help find the correct resolution.[/QUOTE]

Thanks Sam , OK I`ve tried that , It takes me through all the options and interestingly defaults to the correct 1156x768 resolution , I`ve also dropped the colour depth from 24bit to 16 bit , but still only 640x480 is available.

lspci and dmesg reports the ATI card is on pci 0000:00:10.0 , yet I am sure under Ubuntu 4.10 it used to be 0000:0016.0

Odd.

Anyone got Ubuntu 5.10 on a Apple Powerbook G4 667 or any other suggestions ?

cybergypsy

---

### Post by cybergypsy on 2005-11-23
Yippee - got it going.

Added this into the */etc/X11/xorg.conf*

```

Section "Monitor"
        Identifier      "Color LCD"
        HorizSync       30-70
        VertRefresh     50-160
        Option          "DPMS"
        Option          "DDCMode"               "boolean"
        Modeline        "1152x768"              64.995 1152 1213 1349 1472 768 771 777 806 -HSync -VSync
EndSection

```

---

### Post by jlgoolsbee on 2006-02-09
Can somebody detail what cybergypsy added to his xorg.conf?  I am having the exact same issue on a 12" PB G4 1.33 (nvidia), and his fix didn't work for me.

---

### Post by maku-d on 2006-07-13
I just finished installing dapper on my 667 g4 powerbook and had the same problem (resolution of 640 x 480) as mentioned above.  I edited /etc/X11/xorg.conf as described above and it didn't help. I went back though and used the command

# sudo dpkg-reconfigure xserver-xorg

also as described above.  I just followed the prompts mainly using the default entries.  The key change was when it asked for the horizontal sync I changed it to- 30-70 and then next when it asked for the vertical refresh rate I changed it to- 50-160.  Eventually it finished and I went and checked the 'screen resolution' and had the option for 1152 x 768 (the default). I selected it then pressed CTRL + ALT + BACKSPACE to refresh my display and vwalah! it worked!  

Hope this helps any powerbook owners with the same problem ;D

---

