---
title: "Losing sound after playing flash videos"
date: 2009-02-17
forum: x86 64-bit Users
---

### Post by theanswriz42 on 2009-02-17
It's not very consistent, but I'm losing sound after playing various flash sites, ie. youtube.
```

steve@ganymede:~$ dpkg -l | grep -i firefox
ii  firefox                                    3.0.6+nobinonly-0ubuntu0.8.10.1         meta package for the popular mozilla web bro
ii  firefox-3.0                                3.0.6+nobinonly-0ubuntu0.8.10.1         safe and easy web browser from Mozilla
ii  firefox-3.0-branding                       3.0.6+nobinonly-0ubuntu0.8.10.1         Package that ships the firefox branding
ii  firefox-3.0-gnome-support                  3.0.6+nobinonly-0ubuntu0.8.10.1         Support for Gnome in Mozilla Firefox
ii  firefox-gnome-support                      3.0.6+nobinonly-0ubuntu0.8.10.1         meta package pointing to the latest gnome-su
ii  ia32-lib-firefox                           0.1                                     Libraries and other files to help 32bit Fire
ii  ubufox                                     0.6-0ubuntu1.8.10.1                     Ubuntu Firefox specific configuration default
```
```
steve@ganymede:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GT/GTO] (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
05:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
05:01.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 05)

```

I'm sure it's an issue with pulseaudio but I haven't yet found a solution that seems to be effective. Anyone have any suggestions? This is in 8.10 btw.

Cheers

---

### Post by 0br0k3n0 on 2009-02-17
have you tried restarting because tis happened to me and i did it twice and it worked

---

### Post by theanswriz42 on 2009-02-17
> **0br0k3n0 said:**
> have you tried restarting because tis happened to me and i did it twice and it worked

Yeah, it works fine after I restart, but there has to be a proper solution to prevent such issues. 

Cheers

---

### Post by theanswriz42 on 2009-02-18
to the top

---

### Post by crjackson on 2009-02-18
It happens to me too after playing several music videos (10-15).

---

### Post by theanswriz42 on 2009-02-18
> **crjackson said:**
> It happens to me too after playing several music videos (10-15).

I wonder what's causing it.

---

### Post by matmat07 on 2009-02-18
Same here, but I do not need to restart everything. I just have to close firefox, wait for it to completely exit, then restart the application which I want to ear the sound. I got told it came from pulseaudio, but I did what the pulseaudio guide told and it still happens

---

### Post by theanswriz42 on 2009-02-19
> **matmat07 said:**
> Same here, but I do not need to restart everything. I just have to close firefox, wait for it to completely exit, then restart the application which I want to ear the sound. I got told it came from pulseaudio, but I did what the pulseaudio guide told and it still happens

Yeah, it seems like Pulseaudio is buggy, at best.

---

### Post by theanswriz42 on 2009-02-26
ttt

---

