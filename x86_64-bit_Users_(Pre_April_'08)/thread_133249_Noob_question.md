---
title: "Noob question"
date: 2006-02-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by arjunsharma on 2006-02-19
Help! I have the following 3 problems...Thanks:

so I found the command for fglrx-control (fireglcontrolpanel). Now when I try to run it, I get: 
> fireglcontrolpanel: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory

When I tried changing the /etc/ld.so.conf (as per [Can't open ati control panel]("http://ubuntuforums.org/showthread.php?t=75977&highlight=fglrx-control")). I still get the same error message.

When I did "ldd `which fireglcontrolpanel`" I got:
>  linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0x55579000)
        libXmu.so.6 => /usr/lib32/libXmu.so.6 (0x55618000)
        libXt.so.6 => /usr/lib32/libXt.so.6 (0x5562d000)
        libICE.so.6 => /usr/lib32/libICE.so.6 (0x5567b000)
        libSM.so.6 => /usr/lib32/libSM.so.6 (0x55694000)
        libdl.so.2 => /lib32/tls/libdl.so.2 (0x5569b000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0x5569e000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x556ac000)
        libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0x5576c000)
        libexpat.so.0 => not found
        libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0x5579a000)
        libXrender.so.1 => /usr/lib32/libXrender.so.1 (0x5579d000)
        libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0x557a5000)
        libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0x557a9000)
        libXxf86vm.so.1 => not found
        libXft.so.2 => /usr/lib32/libXft.so.2 (0x55813000)
        libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0x55825000)
        libstdc++.so.5 => /usr/lib32/libstdc++.so.5 (0x5582e000)
        libm.so.6 => /lib32/tls/libm.so.6 (0x558e8000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0x5590b000)
        libc.so.6 => /lib32/tls/libc.so.6 (0x55916000)
        libpthread.so.0 => /lib32/tls/libpthread.so.0 (0x55a44000)
        /lib/ld-linux.so.2 (0x55555000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0x55a55000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0x55a58000)
        libz.so.1 => /usr/lib32/libz.so.1 (0x55a5d000)
        libexpat.so.1 => /usr/lib32/libexpat.so.1 (0x55a71000)
        libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0x55a90000)


Note libexpat.so.0 => not found, yet libexpat.so.1 worked, when they are in the same directory. Please advise...

Also:

How do I get my soundcard working? I have a Gateway 7508GX laptop, AMD64 (I can't remember, possibly 3600), and a Conexant AC-Link sound card. I have sound working on my Windows partition, with the Windows drivers in their own folder.

Y tambien:

What should I do to get my wireless working? I thought I had an Intel Prowireless 2200BG wireless card, but when I run lspci it says I have a Broadcom... I thought I had the intel because the 7510 has it... but I guess I was wrong. I don't know which Broadcom I have, how can I find more details? In the list of Gateway products they skip over the 7508GX. (UPDATE: As I wrote this, I thought to search Gateway support for "Broadcom wireless", and found update #9528158 with Broadcom wireless drivers for 7000 series laptops... but under part numbers it doesn't have any parts that correspond to the 7508GX... and when I search support for "7508GX" I get all my other drivers, but no wireless driver...should I just download it, and then use cabextract, and then use ndiswrapper?)

Thanks for the help...

Thanks,

Arjun

---

### Post by SVFUSiON on 2006-02-20
sudo apt-get update
sudo apt-get install libexpat


download the drivers from here

[http://www.lanknights.net/optendo/7510GX/Recovery%20Disk/7510GX%20Wireless%20recovery.zip](http://www.lanknights.net/optendo/7510GX/Recovery%20Disk/7510GX%20Wireless%20recovery.zip)

Those are the drivers right from the recovery disk.

This is what came up when I searched for drivers for your notebook.

then use them using ndiswrapper

---

### Post by arjunsharma on 2006-02-20
The drivers you gave me were the right ones... since I was able to use them to set up my wireless in Windows.... but for some reason I'm having trouble using ndiswrapper.

I did "ndiswrapper -i *filename*"
then when I did "ndiswrapper -l" I got:
> Installed ndis drivers:
bcmwl5  driver present, hardware present

Now what? I tried the strategies of a few sites, none actually configured the wireless properly.


In the repositories I have loaded I don't see libexpat, I only see libexpat1

Any ideas for the conexant question...?

also, related to the libexpat, when I try running X-Plane, I get the same error message, but instead of libexpat.so.0 it says libopenal.so.0

Thanks for the Wireless drivers... it's surprising, since gateway gives Intel drivers for the 7510GX... weird...

Arjun

---

### Post by deathbyswiftwind on 2006-03-03
oh man I have the same card and I was so CONFUSED and PISSED off for a month trying to figure out why I couldnt get this card to work. Every other distro Ive ever tried has just worked but not ubuntu. There is a real simple step around this go to this wonderful howto [http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom) 
this works with both 32bit and 64bit If you need help finding 64bit drivers I have them and know where to get them

---

