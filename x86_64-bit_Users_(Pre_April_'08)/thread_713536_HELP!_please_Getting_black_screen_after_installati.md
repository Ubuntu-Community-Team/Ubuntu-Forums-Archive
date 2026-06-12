---
title: "HELP! please Getting black screen after installation of ubuntu NVidia 8800 GTX cards"
date: 2008-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Leviathangod on 2008-03-02
Hello, my computer has four 750GB HDDs and I've been running vista ultimate on one for a long while and tried to install Ubuntu 64bit on the fourth HDD. The installation went pretty easily but when I finally tried to boot, all I get is a black screen. I have tried some solutions from simular threads like making sure it boots with the "vesa" driver and going through configuring xserver and wanted to see if anyone could suggest anything. Here are my computer's video specs.

------------------
System Information
------------------
Time of this report: 3/2/2008, 20:53:48
       Machine name: LEVIATHANGOD
   Operating System: Windows Vista™ Ultimate (6.0, Build 6000) (6000.vista_gdr.071023-1545)
           Language: English (Regional Setting: English)
System Manufacturer: System manufacturer
       System Model: System Product Name
               BIOS: Phoenix - AwardBIOS v6.00PG
          Processor: Intel(R) Core(TM)2 Extreme CPU Q6850  @ 3.00GHz (4 CPUs), ~900MHz
             Memory: 4094MB RAM
          Page File: 1335MB used, 7002MB available
        Windows Dir: C:\Windows
    DirectX Version: DirectX 10
DX Setup Parameters: Not found
     DxDiag Version: 6.00.6000.16386 32bit Unicode
---------------
Display Devices
---------------
        Card name: NVIDIA GeForce 8800 GTX
     Manufacturer: NVIDIA
        Chip type: GeForce 8800 GTX
         DAC type: Integrated RAMDAC
       Device Key: Enum\PCI\VEN_10DE&DEV_0191&SUBSYS_044319F1&REV_A2
   Display Memory: 2523 MB
 Dedicated Memory: 732 MB
    Shared Memory: 1791 MB
     Current Mode: 1280 x 1024 (32 bit) (60Hz)
          Monitor: Generic PnP Monitor
      Driver Name: nvd3dum,nvd3dumx.dll,nvwgf2um,nvwgf2umx.dll

---

### Post by petzworld999 on 2008-03-02
I just helped a friend with this problem.  Here is what you do:

Boot into recovery mode and run the following command: 

```

sudo editor /etc/X11/xorg.conf

```

Then add this right below the line that has the term "VideoRam"

```

Option "NvAGP"  "1"
Option "ConnectedMonitor" "DFP"

```

Then press Control+O and control+x and type

```

sudo reboot

```

Boot into Ubuntu without recovery mode and see what happens.

---

### Post by Leviathangod on 2008-03-02
Thanx for the reply! I tried this and regrettably it didn't work :(    Any other Ideas?:confused:

---

### Post by petzworld999 on 2008-03-02
Try this:

Boot into recovery mode and run the following command: 

```

sudo editor /etc/X11/xorg.conf

```

Delete this line:

```

Option "ConnectedMonitor" "DFP"

```

And edit the lines that look somewhat like this: 
```


Section "Device"
        Identifier      "Nvidia 8800 GTX deal"
        Driver          "drivername (vesa)"
        Busid           "PCI something:something:something"
        Videoram        numberofsomesort
        Option         "NvAGP"      "1"
EndSection


```

to

```


Section "Device"
        Identifier      "Nvidia 8800 GTX deal"
        Driver          "nvidia"
        Busid           "PCI something:something:something"
        Videoram        number
        Option         "NvAGP"      "1"
EndSection


```

and

```

sudo reboot

```

---

### Post by whoop on 2008-03-02
remove "quiet splash" temporarily from you kernel line in menu.lst.
If you boot see if you will eventually get into X (you won't get the fancy splash screen). if you do it's just a resolution problem.
Then restore you're menu.lst and ad a vga mode to the kernel line. 
Here are some values:
```

Colours   640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
--------+--------------------------------------------------------------
 4 bits |    ?       ?     0x302      ?        ?        ?         ?
 8 bits |  0x300   0x301   0x303    0x305    0x161    0x307     0x31C
15 bits |    ?     0x310   0x313    0x316    0x162    0x319     0x31D
16 bits |    ?     0x311   0x314    0x317    0x163    0x31A     0x31E
24 bits |    ?     0x312   0x315    0x318      ?      0x31B     0x31F
32 bits |    ?       ?       ?        ?      0x164      ?

```

I have the same problem with my nvidia card. I just remove "quiet splash" as a default.... I much rather look at technical stuff than a splash screen ;-)

---

### Post by felker2 on 2008-03-03
Are you using Ubuntu 7.10?

If so, have you tried the Alpha 5 of Ubuntu 8.04? Ubuntu 8.04 contatins a new Xserver (I believe Xorg 7.3), which needs much *less* configuration and does more auto-discovery and auto-configuration. So it only has a very small xorg.conf, which avoids the need for editing it. So, that could be the solution for your problem.

See [https://wiki.ubuntu.com/HardyHeron](https://wiki.ubuntu.com/HardyHeron) for the download of an Alpha version of 8.04 Hardy Heron. BTW: don't let the word 'Alpha' scare you; there is no beta, and I've running an Alpha version of 8.04 Hardy Heron for some weeks now. Yes, there are bugs left, but this test will make whether the new Xserver solves your problem.

HTH

---

### Post by Leviathangod on 2008-03-03
Thank you guys for the quick response. I'll try the two solutions posted above and then if that does not work, I'll try the new alpha release. I'll do these things when I get home from work. Thanks again for the quick response.:)

---

### Post by Leviathangod on 2008-03-03
Well, The two code solutions did not work so I'm gonna try the next alpha version of ubuntu.:(:(

---

### Post by Leviathangod on 2008-03-04
I tried installing the liveCD visual install of HardyHeron but once it got to the visual part the screen just went black. I'll be trying the alternate install of HardyHeron when I get back home from work.

---

### Post by Leviathangod on 2008-03-04
Ok, I  thought I'd ask this. This may come off as a stupid question but I'm new to this so please cut me some slack. Is there a way to install drivers in the Ubuntu recovery mode so that it would be able to startup instead of just giving me a black screen?

---

### Post by petzworld999 on 2008-03-06
```

sudo dpkg-reconfigure xserver-xorg

```

Right at the beginning, hit NO for autodetection of video card. Go manual and select 'vesa.'

---

### Post by halln on 2008-03-19
I had this problem before until i I crack it by changing my monitor with a higher resolution than the one I'm using before.  If you can borrow one from somebody you can try it.

---

