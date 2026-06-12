---
title: "wlan problems Broadcom 802.11b/g"
date: 2008-11-22
forum: x86 64-bit Users
---

### Post by 9170 on 2008-11-22
Hello everyone

I have a HP Compaq 6715b and problems to use the wlan. :confused:
Does anyone have experience with it?

Christian

---

### Post by inobe on 2008-11-22
open terminal and type

```
lspci
```
then hit enter and paste the output on your next post.

you may have to use ndiswrapper to get that card working, we shall see !

note, if you don't get an output with that command

```
sudo lspci
```

---

### Post by buyyourall3 on 2008-11-22
[size=5]there are lots of [/size][**[size=5]chinese mobile phones[/size]**](http://www.buyyourall.com)[size=5] are very cool,such as [/size][**[size=5]spy watch mobile phone[/size]**](http://www.buyyourall.com)[size=5]  , it is a mobile phone and a watch . the picture is below .[/size][[img]http://www.buyyourall.com/syssite/home/shop/1/pictures/newsimg/1226099832.jpg[/img]](http://www.buyyourall.com/1180_007-spy-watch-mobile-phone.html)

---

### Post by 9170 on 2008-11-22
this is what I have got:

> ..........-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
02:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b6)
02:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 02)
10:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)


---

### Post by inobe on 2008-11-22
sorry it took me this long to reply :)

in terminal do

```
sudo iwlist scan
```

also go to System->Adminstration->Hardware Drivers

ndiswrapper should be on your system by default and needs to be enabled !

after the card is enabled' its just the matter of setting up the key or pass phrase among ssid...

that should be all.

please explain in detail on your next post if you encounter any other problems.

---

### Post by 9170 on 2008-11-22
Thank you!

I'm not able to log in at the university's network and I think it will be similar to everyone. The network seems to work but I don't get the login window at Firefox. 
I have talked to the university's  computer support and they said that my computer do not found its network card and can't establish a connection. 
One thing makes it much worse, I get a network but the wrong one. 

Anyway, here come the result of your last request:
> .......-laptop:~$ sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

---

### Post by 9170 on 2008-11-23
…..............by rebooting my system and activating  the wlan in Windows get I this:

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth2      Scan completed :
          Cell 01 - Address: 00:22:B0:47:06:6F
                    ESSID:"kinda"
                    Mode:Managed
                    Frequency=2.417 GHz (Channel 2)
                    Quality:5/5  Signal level:-55 dBm  Noise level:-92 dBm
                    IE: Unknown: DD750050F204104A00011010440001011041000100103B00010310470010F2A03D639AEEEAB77F680022B047066F10210006442D4C696E6B102300074449522D333030102400074449522D3330301042000830303030303030301054000800060050F2040001101100074449522D33303010080002008E
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:17:3F:92:47:8D
                    ESSID:"Zorek"
                    Mode:Managed
                    Frequency=2.412 GHz (Channel 1)
                    Quality:4/5  Signal level:-63 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:1C:F0:6F:9F:42
                    ESSID:"UCH"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:4/5  Signal level:-67 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:1F:C6:81:BF:AE
                    ESSID:"BroInterns"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:4/5  Signal level:-66 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD710050F204104A0001101044000102103B00010310470010000102030405060708090A0B0C0D0EBB102100075765625354415210230007576562535441521024000631323334353610420007303030303030311054000800060050F204000110110009576562535441524150100800020088
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 05 - Address: 00:15:E9:0F:16:AE
                    ESSID:"BadMotherFucker"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-46 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 06 - Address: 00:1F:33:42:F1:F6
                    ESSID:"Isamael"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-58 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s


I have to go this way, rebooting and start the wlan in windows, otherwise will Ubuntu not found the Broadcom card.

---

### Post by 9170 on 2008-11-23
Part II

> 
Cell 07 - Address: 00:17:9A:63:1C:91
                    ESSID:"maerta"
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-64 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 08 - Address: 00:1E:2A:5D:6D:7A
                    ESSID:"Black Book"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:4/5  Signal level:-61 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 09 - Address: 00:18:F8:40:A3:88
                    ESSID:"wilson"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:4/5  Signal level:-66 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

pan0      Interface doesn't support scanning.

---

### Post by 9170 on 2008-11-24
I have found something on a Debian forum. 
You might need this informations 

[http://uruz.org/2008/03/debian-lenny-freebsd-and-my-hp-compaq-6715b/]("http://uruz.org/2008/03/debian-lenny-freebsd-and-my-hp-compaq-6715b/") Ubuntu is still built on Debian 
...........I followed his instruction 
> # xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection



and have got this as answer 


> ........-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
02:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b6)
02:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 02)
10:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)


---

