---
title: "[SOLVED] Can't ge t the sound to work. Help!"
date: 2008-10-06
forum: x86 64-bit Users
---

### Post by khelben1979 on 2008-10-06
Hello!

Yesterday I installed Ubuntu 8.04 on an AMD 64 laptop and I can't get the sound to work.

The laptop has inbuilt support for the soundblaster chipset so I tried modprobe sb, but that didn't work out very well..

I need your support.

---

### Post by Yellow Pasque on 2008-10-06
What kind of sound card do you have? (it's probably not a soundblaster, it just supports old programs that need its functions)):
```
sudo update-pciids
lspci
```

---

### Post by khelben1979 on 2008-10-06
nightrazer@Powercore:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

---

### Post by Yellow Pasque on 2008-10-06
You're running very modern hardware, so try upgrading ALSA with this script:
[http://ubuntuforums.org/showpost.php?p=5792918&postcount=104](http://ubuntuforums.org/showpost.php?p=5792918&postcount=104)

Or you could try OSS4:
[http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961)

EDIT: You could also try install Ubuntu 8.10 Intrepid, which has an updated ALSA (among other drivers)

---

### Post by khelben1979 on 2008-10-06
I have tried the script and the problem which arise over here (not the fault of the script) is that I get permission denied.

How do I get super user rights in Ubuntu? It feels like a stupid question, but when I installed Ubuntu 8.0.4 I have only been able to use the su command when I install things from an command prompt or a shell.

The Synaptic package manager is able to install packages which would require super user rights, so from what I understand, the user which were created at the beginning of the installment of this distribution actually has super user rights but it feels buggy here in Ubuntu. Missing packages??

So I'm in a need of further help to get this working.

If it were a Debian system I would probably go to the Alsa homepage and compile every package from scratch, but I'm trying to get used to Ubuntu.

Thanks!

---

### Post by Yellow Pasque on 2008-10-06
> How do I get super user rights in Ubuntu?
```
sudo <command>
```

---

### Post by khelben1979 on 2008-10-07
In Ubuntu I might use the sudo command almost 100 times on one day. I felt that it was easier with Debian.

Does it exist a possibility to actually create a root account on an Ubuntu system?

When I looked at the user list in one of those graphical interfaces I saw root, but was unable to modify it.

---

### Post by Yellow Pasque on 2008-10-08
Use a search engine to look it up.

> There is a very simple terminal command that will set the password for root so that you can log in as root. We are not allowed to tell you this command because it is not officially recommended by the Ubuntu project (forum rules). You can find it easily on other websites with a search.

---

### Post by etdsbastar on 2008-10-08
Hello friend,

I think your sound card hasn't been initialized by ubuntu or the drivers absent. re-install the sound drivers and try rebooting the machine.

Be in touch...

---

### Post by khelben1979 on 2008-10-08
By using the sudo command, the Ubuntu system is working including the sound.

Temüjin: The script worked!

---

### Post by Sef on 2008-10-08
>  Does it exist a possibility to actually create a root account on an Ubuntu system?

Read [RootSudo]("https://help.ubuntu.com/community/RootSudo").

---

