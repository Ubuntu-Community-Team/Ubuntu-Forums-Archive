---
title: "Wine installs fine but always stuck for any wine* commands"
date: 2008-06-14
forum: Wine
---

### Post by bosjee on 2008-06-14
At first I installed wine from the repository in Feisty, and when I type "winecfg", it freezes my terminal (just the terminal, not totally freezes the whole computer and requires a reboot like I have seen people reporting in this forum). It says:
wine: created the configuration directory '/home/myname/.wine'
then do "ps" in other terminal I see that:
/usr/bin/../lib/../bin/wine-pthread winecfg.exe
/usr/bin/../lib/../bin/wine-pthread rundll32.exe setupapi.dll,InstallHinfSection DefaultInstall 128 wine.inf
And I can't kill those processes.

The yesterday I upgraded to Gutsy and install 0.9.46. Nothing change! I was still stuck when issuing any "wine*" command. I removed all the ~/.wine* stuffs and tried many times, but still can't get it to work! Man, I was really mad!

Today I was determined to get it to work by using the latest version by compiling from the source myself -- yes, the latest version 1.0rX from git. I compiled with no error, install with no error but when I removed all the "~/.wine" directories and run "winecfg" again, I was very disappointed to see that I got stuck at the same place! It show just "created configuration directory" and nothing else. Same couple of process just sits there, no error message, nothing. Nothing change!

Believe me, I tried hard to get it to work. But I'm running out of ideas to try. I think I'm missing some fundamental stuffs here. Any suggestion would be appreciated.

My hardware spec:
CPU: C2D E6400
MB: EVGA nForce 680i LT (using onboard sound)
Graphic: GeForce 7950 PCIe using the envy driver
Other: LSI MegaRAID 4 port SATA, ATI HDTV Wonder

lspci:
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GT] (rev a1)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:09.0 RAID bus controller: LSI Logic / Symbios Logic MegaRAID (rev 01)
02:0a.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:0a.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
02:0a.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)

---

### Post by bosjee on 2008-06-16
Sorry to reply to my own post. Any suggestion at all? Anybody?

The problem right now is that I don't see any error messages and I don't know where it got stuck. 

I tried:
$ gdb winecfg
GNU gdb 6.6-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
"/usr/local/bin/winecfg": not in executable format: File format not recognized
(gdb) 

Why is "winecfg" not in executable format? Any programmers out there?

Thanks.

---

### Post by cogadh on 2008-06-16
Completely remove all versions of Wine you have installed. For those installed from the repositories, use "sudo apt-get remove --purge wine", then delete the .wine directory.

Now, a couple of questions:
You have a 64-bit processor, are you using the 64-bit version of Ubuntu?
If so, are you using the 64-bit version of Wine?
If you are using the 64-bit version of each, have you installed the 32-bit support libraries (ia32libs)?
When you compiled it yourself, did you follow the instructions [here](http://wiki.winehq.org/WineOn64bit)?

---

### Post by bosjee on 2008-06-16
cogadh, I did completely remove all the previous version of wine with exact same command and deleted all the ".wine" and ".wine-xxxxxx" directories. In fact, I did it many times.

Although I have a 64 bit processor, I'm only running only the 32 bit version of Ubuntu.

$ uname -a
Linux bonfante 2.6.22-14-386 #1 Tue Feb 12 07:12:19 UTC 2008 i686 GNU/Linux

All I did for compile is:
$ ./configure && make depend && make
$ sudo make install
Everything goes smoothly, no error or what so ever. I did fixed some warning message during configure by installing some *-dev packages.

---

