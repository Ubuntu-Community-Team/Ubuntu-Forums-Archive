---
title: "permanent high sysload when no programs running after update to jaunty 64bit"
date: 2009-07-18
forum: x86 64-bit Users
---

### Post by dschneider on 2009-07-18
Hello Guys,

since I changed my system from 8.04 64bit to 9.04 64 bit, there are som strange problems that I cannot solve. Hopefully someone of you can help me to find out. I don't want to go back to 8.04, because it is like a new installation.

At first, I have two problems:

1.) Heavy Sysload all the time despite the fact that no application is running. Only Ubuntu itself. The CPU Graph is always showing mire than 50% load and the load average in top is always more than 2! I have a 2,4GHz DualCore Processor with 4GB ram.
In the following Example, only Firefox is running:

```

top - 10:24:14 up 46 min,  1 user,  load average: 2.22, 2.51, 2.49
Tasks: 154 total,   6 running, 148 sleeping,   0 stopped,   0 zombie
Cpu(s): 38.0%us, 16.6%sy,  1.3%ni, 43.2%id,  0.7%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   3993288k total,  1987232k used,  2006056k free,   157468k buffers
Swap: 11719408k total,        0k used, 11719408k free,   946892k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4248 root      20   0  299m 107m  16m S    8  2.8   5:34.68 Xorg
 4699 pckid     20   0 22612 2428  848 S    6  0.1   2:11.05 dbus-daemon
 4634 pckid     20   0  170m 8740 6316 S    5  0.2   1:41.47 x-session-manag
 8126 pckid     20   0  652m 200m  28m S    4  5.1   2:06.31 firefox
 4707 pckid     20   0 47652 7512 2388 S    2  0.2   1:16.44 gconfd-2
 8394 pckid     20   0 69472  15m 9600 R    2  0.4   1:02.80 npviewer.bin
 4779 pckid     20   0  248m  26m  11m S    1  0.7   0:31.31 python
 5165 pckid     20   0  227m  16m 9456 S    1  0.4   0:38.69 indicator-apple
 4738 pckid     20   0  223m  15m 8028 R    1  0.4   0:30.89 gnome-settings-
 4806 pckid     20   0  139m  11m 5428 S    1  0.3   0:11.83 trackerd
 5691 pckid     39  19  149m  11m 5424 S    1  0.3   0:12.00 tracker-indexer
14722 pckid     20   0  396m  41m  22m S    1  1.1   0:06.44 konsole
31229 pckid     20   0  208m 7408 5720 R    1  0.2   0:00.02 vino-server
 4196 root      20   0 28484 2064 1784 S    0  0.1   0:00.72 hald-addon-stor
 4746 pckid     20   0  335m  38m  17m S    0  1.0   0:28.10 gnome-panel
 4753 pckid     20   0  234m  17m  11m S    0  0.4   0:08.35 update-notifier
 4794 pckid     20   0  163m 8960 6580 S    0  0.2   0:07.40 tracker-applet
 4816 pckid     20   0  222m  10m 6584 S    0  0.3   0:11.58 gnome-power-man
 5157 pckid     20   0  235m  14m 9.8m S    0  0.4   0:16.41 fast-user-switc

```

I'm wondering about the load average of more permanently more than 2 but no process has more than 10% CPU usage.

I suppose that it is something with the x-server, but I don't know.
Do you have some ideas? I searched all the log-files in /var/log, but found no hints about that.

```

output from lspci:
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
04:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
04:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
04:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)

output of lsusb:
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 04a9:221b Canon, Inc. CanoScan 4200F
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 004: ID 046d:c225 Logitech, Inc.
Bus 005 Device 003: ID 046d:c221 Logitech, Inc. G15 Keyboard / Keyboard
Bus 005 Device 002: ID 046d:c223 Logitech, Inc. G15 Keyboard / USB Hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 09bf:00db Auerswald GmbH & Co. KG COMpact 4410/2206 ISDN ISDN
Bus 004 Device 002: ID 0a81:0205 Chesen Electronics Corp. PS/2 Keyboard+Mouse Adapter
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

content of xorg.conf:
# nvidia Driver Version: 180.44
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009
# nvidia-xconfig: X configuration file generated by nvidia-xconfig             
# nvidia-xconfig:  version 1.0  (buildmeister@builder62)  Tue Mar 24 06:15:32 PST 2009

Section "Monitor"
        Identifier     "Monitor0"
        VendorName     "Unknown" 
        ModelName      "Samsung SyncMaster"
        HorizSync       30.0 - 81.0        
        VertRefresh     56.0 - 75.0        
        Option         "DPMS"              
EndSection                                 

Section "Monitor"
        Identifier     "Monitor1"
        VendorName     "Unknown" 
        ModelName      "Samsung SyncMaster"
        HorizSync       30.0 - 81.0        
        VertRefresh     56.0 - 75.0        
EndSection                                 

Section "Screen"
        Identifier     "Screen0"
        Device         "Device0"
        Monitor        "Monitor0"
        Option         "TwinView" "0"
        Option         "TwinViewXineramaInfoOrder" "CRT-0"
        Option         "metamodes" "CRT-0: nvidia-auto-select +0+0"
        DefaultDepth    24                                         
        SubSection "Display"                                       
                Depth       24                                     
        EndSubSection                                              
EndSection                                                         

Section "Screen"
        Identifier     "Screen1"
        Device         "Device1"
        Monitor        "Monitor1"
        DefaultDepth    24       
        Option         "TwinView" "0"
        Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
        SubSection "Display"                                       
                Depth       24                                     
        EndSubSection                                              
EndSection                                                         

Section "Module"
        Load           "dbe"
        Load           "extmod"
        Load           "type1" 
        Load           "freetype"
        Load    "glx"            
        Disable "dri2"           
EndSection                       

Section "InputDevice"
        Identifier     "Mouse0"
        Driver         "mouse" 
        Option         "Protocol" "auto"
        Option         "Device" "/dev/psaux"
        Option         "Emulate3Buttons" "no"
        Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
        Identifier     "Keyboard0"
        Driver         "kbd"
        # generated from default
EndSection

Section "ServerLayout"
        Identifier     "Layout0"
        Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" RightOf "Screen0"
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
        Identifier     "Device0"
        VendorName     "NVIDIA Corporation"
        BoardName      "GeForce 8600 GT"
        BusID          "PCI:3:0:0"
        Screen          0
        Driver  "nvidia"
EndSection

Section "Device"
        Identifier     "Device1"
        VendorName     "NVIDIA Corporation"
        BoardName      "GeForce 8600 GT"
        BusID          "PCI:3:0:0"
        Screen          1
        Driver  "nvidia"
EndSection

Section "ServerFlags"
        Option         "DontZap" "False"
        Option         "Xinerama" "1"
        # Removed Option "Xinerama" "1"
        # Removed Option "Xinerama" "0"
EndSection

```

2.) I cannot start the root-terminal anymore. Everytime I start it, the login mask is opening, and then absolutely nothing happens!
This issue is not so important because I can use the normal terminal to work with.


So thats all for now. It would be very great, if someone can help me!

Thanks and best Regards
Daniel

---

### Post by cariboo on 2009-07-18
I see you have tracker running, try shutting it down to see if your cpu load goes down.

---

### Post by dschneider on 2009-07-19
Hi Cariboo,

thanks for your hint. But sorry, It didn't change anything!

Any other suggestions?

Regards
Daniel

---

### Post by gila_monster on 2009-07-19
Hi.

I have the same problem. In another thread, someone suggested checking udev as well. But that didn't help me, either. 

When I run GNOME's system monitor, it consistently tells me that my CPU ticks are being used by...the GNOME system monitor!

Currently, I'm debugging a problem between X and my nVidia driver, but I'll get back to the CPU problem when I'm done.

---

### Post by aj_the_first on 2009-07-20
Any solution on this? because I am having the same issue.  It is causing my computer to run rather slowly.  Really disappointing.
Andy yes, it is gnome-system-monitor that is taking up the majority of the cpu load.

I didn't check it before I fixed the xorg bug from ati X1200 cards, but I did modify my xorg file, not sure if that has anything to do with it.

---

### Post by ken78724 on 2009-07-23
hi: Pls spell out high sysload. Would this explain slowness that darkens the monitor? can't visualize what you're actually reporting. maybe it's because I've reversed day for night and slept most of today. my Mirus PC is comparatively limited so I want to clear up sys overloads anyway possible.

---

### Post by Yellow Pasque on 2009-07-23
gnome-system-monitor is known to have issues with consuming CPU cycles itself.

Use htop for a more accurate reading.

---

### Post by dschneider on 2009-08-04
Hello All,

The problem is defnetly not gnome-system-monitor! I tried to stop it and trackerdaemon and beagledaemon and Evolution daemons, but no change. The systemload in top or htop is always 2 and more. The processors are 50% and more busy:
```

top - 09:56:20 up  1:26,  2 users,  load average: 2.57, 2.44, 2.66
Tasks: 151 total,   5 running, 146 sleeping,   0 stopped,   0 zombie
Cpu(s): 37.1%us, 17.9%sy,  0.0%ni, 42.9%id,  0.3%wa,  1.5%hi,  0.3%si,  0.0%st
Mem:   3993288k total,  3007484k used,   985804k free,   283236k buffers
Swap: 11719408k total,        0k used, 11719408k free,  1946152k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4338 root      20   0  294m 112m  16m S   10  2.9   9:47.35 Xorg
 4771 dschneid  20   0 22344 2156  848 S    5  0.1   3:59.47 dbus-daemon
 4706 dschneid  20   0  170m 8748 6320 R    4  0.2   3:05.98 x-session-manag
 4779 dschneid  20   0 48344 7832 2388 S    3  0.2   2:21.93 gconfd-2
27135 dschneid  20   0  405m  41m  22m R    3  1.1   0:08.27 konsole
 4862 dschneid  20   0  211m  18m 9176 S    2  0.5   0:56.76 python
28750 dschneid  20   0 19644 1588 1028 S    2  0.0   0:10.02 htop
 4807 dschneid  20   0  223m  14m 7452 S    1  0.4   0:56.70 gnome-settings-
 4816 dschneid  20   0  337m  39m  17m S    1  1.0   0:51.55 gnome-panel
 5087 dschneid  20   0  229m  18m 9528 S    1  0.5   1:10.08 indicator-apple
 5089 dschneid  20   0  235m  14m 9988 S    1  0.4   0:25.05 fast-user-switc
12973 dschneid  20   0     0    0    0 R    1  0.0   0:00.03 vino-server
 4205 root      20   0 28484 2084 1796 S    1  0.1   0:00.63 hald-addon-inpu
 4814 dschneid  20   0  173m  16m 9.8m S    1  0.4   0:14.90 metacity
 4823 dschneid  20   0  504m  42m  21m S    1  1.1   0:24.68 pidgin
 4864 dschneid  20   0  234m  17m  11m S    1  0.4   0:14.39 update-notifier
28739 dschneid  20   0  303m  21m  12m S    1  0.6   0:06.76 gnome-terminal
 4793 dschneid  20   0 40924 2420 1976 S    0  0.1   0:10.76 gvfsd
 4891 dschneid  20   0  222m  10m 6564 S    0  0.3   0:20.05 gnome-power-man
 5756 dschneid  20   0  169m 9340 6836 S    0  0.2   0:37.58 gnome-screensav
    1 root      20   0  5244 2044  632 S    0  0.1   0:00.82 init

```
```

  1  [|||||||||||||||||||||||||||||||||||||||||||||                      60.4%]     Tasks: 194 total, 3 running
  2  [||||||||||||||||||||||||||||||||||||||                             51.7%]     Load average: 2.17 2.21 2.42 
  Mem[||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||  973/3899MB]     Uptime: 01:39:00
  Swp[                                                               0/11444MB]

  PID USER     PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command
 5089 dschneid  20   0  235M 14880  9988 S  1.0  0.4  0:30.12 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=OAFIID:GNOME_FastUserSwitc
13520 dschneid  20   0 69556 15108  9572 S  1.0  0.4  0:04.06 /usr/lib/nspluginwrapper/i386/linux/npviewer.bin --plugin /usr/lib/flashplugin-installer/libflashplaye
20308 dschneid  20   0  515M 72140 25308 S  1.0  1.8  0:05.16 /usr/lib/thunderbird/thunderbird-bin
 4843 dschneid  20   0  196M 15752  9604 S  1.0  0.4  0:17.92 nm-applet --sm-disable
29333 dschneid  20   0  210M  9144  7076 R  1.0  0.2  0:00.02 /usr/lib/vino/vino-server
 4823 dschneid  20   0  504M 43020 21608 S  0.0  1.1  0:30.74 pidgin --session 1015ea1a787b2eb06c124828550953563700000046510050 --display :0.0
13364 dschneid  20   0  616M  182M 26764 S  0.0  4.7  0:01.06 /usr/lib/firefox-3.0.12/firefox
 4891 dschneid  20   0  222M 10980  6564 S  0.0  0.3  0:25.80 gnome-power-manager
 4814 dschneid  20   0  173M 16932 10080 S  0.0  0.4  0:16.96 metacity --sm-client-id 10f2092bc0a70cca30124376837186845100000049130037
 4864 dschneid  20   0  234M 17728 11508 S  0.0  0.4  0:18.92 update-notifier --sm-config-prefix /update-notifier-vPn9Kp/ --sm-client-id 10dcdb640223f0c45e124928044
 4857 dschneid  20   0  172M 14700  8892 S  0.0  0.4  0:17.14 /usr/lib/notify-osd/notify-osd
 4793 dschneid  20   0 40924  2420  1976 S  0.0  0.1  0:13.00 /usr/lib/gvfs/gvfsd
20312 dschneid  20   0  515M 72140 25308 S  0.0  1.8  0:00.28 /usr/lib/thunderbird/thunderbird-bin
 4286 root      20   0 28484  2068  1784 S  0.0  0.1  0:01.26 hald-addon-storage: polling /dev/sr1 (every 2 sec)
 4205 root      20   0 28484  2084  1796 S  0.0  0.1  0:00.96 hald-addon-input: Listening on /dev/input/event1 /dev/input/event0 /dev/input/event3 /dev/input/event5
 4804 dschneid  20   0  170M  8748  6320 S  0.0  0.2  0:01.90 x-session-manager
 4335 root      20   0  140M  3716  2508 S  0.0  0.1  0:04.24 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
 4287 root      20   0 28484  2064  1784 S  0.0  0.1  0:01.04 hald-addon-storage: polling /dev/sr0 (every 2 sec)
 4818 dschneid  20   0  496M 24028 15872 S  0.0  0.6  0:05.75 nautilus --sm-client-id 1035e10ac8f6dfb741124311237845026400000077070036 --sm-client-state-file /home/
10926 root      20   0 62008  1840  1240 S  0.0  0.0  0:00.02 nmbd -D -s /etc/samba/smb.conf
 4780 dschneid  20   0  299M  6492  4712 S  0.0  0.2  0:26.40 /usr/bin/pulseaudio --start
 4776 dschneid  20   0  299M  6492  4712 S  0.0  0.2  0:13.24 /usr/bin/pulseaudio --start
 5078 dschneid  20   0  245M 17068 10984 S  0.0  0.4  0:00.20 /usr/lib/gnome-applets/gweather-applet-2 --oaf-activate-iid=OAFIID:GNOME_GWeatherApplet_Factory --oaf-
13362 dschneid  20   0  616M  182M 26764 S  0.0  4.7  0:00.10 /usr/lib/firefox-3.0.12/firefox
 2664 messageb  20   0 22152  1668   776 S  0.0  0.0  0:00.20 /bin/dbus-daemon --system
13392 dschneid  20   0  616M  182M 26764 S  0.0  4.7  0:00.02 /usr/lib/firefox-3.0.12/firefox
13455 dschneid  20   0  616M  182M 26764 S  0.0  4.7  0:00.36 /usr/lib/firefox-3.0.12/firefox
 4937 dschneid  20   0  215M 13024  8668 S  0.0  0.3  0:00.24 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior
 2624 syslog    20   0 12376   740   564 S  0.0  0.0  0:00.04 /sbin/syslogd -u syslog
 4430 root      20   0 84484  3080  2084 S  0.0  0.1  0:00.18 /usr/sbin/cupsd
 4109 haldaemo  20   0 36820  5316  3908 S  0.0  0.1  0:00.36 /usr/sbin/hald
    1 root      20   0  5244  2044   632 S  0.0  0.1  0:00.84 /sbin/init
28751 dschneid  20   0  303M 22628 12476 S  0.0  0.6  0:00.00 /usr/bin/gnome-terminal -x htop
28748 dschneid  20   0 14412   784   636 S  0.0  0.0  0:00.00 gnome-pty-helper
27154 dschneid  20   0 21080  3904  1540 S  0.0  0.1  0:00.10 /bin/bash
27153 dschneid  20   0  405M 42800 23564 S  0.0  1.1  0:00.00 konsole
 5193 dschneid  20   0 40928  2476  2064 S  0.0  0.1  0:00.00 /usr/lib/gvfs/gvfsd-burn --spawner :1.5 /org/gtk/gvfs/exec_spaw/1
 5084 dschneid  20   0  422M 53436 20588 S  0.0  1.3  0:04.17 /usr/bin/python /usr/lib/deskbar-applet/deskbar-applet --oaf-activate-iid=OAFIID:Deskbar_Applet_Factor
 5637 dschneid  20   0  422M 53436 20588 S  0.0  1.3  0:00.00 /usr/bin/python /usr/lib/deskbar-applet/deskbar-applet --oaf-activate-iid=OAFIID:Deskbar_Applet_Factor
 5634 dschneid  20   0  422M 53436 20588 S  0.0  1.3  0:00.00 /usr/bin/python /usr/lib/deskbar-applet/deskbar-applet --oaf-activate-iid=OAFIID:Deskbar_Applet_Factor
 5081 dschneid  20   0  331M 19224 11680 S  0.0  0.5  0:00.24 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=
 5776 dschneid  20   0  331M 19224 11680 S  0.0  0.5  0:00.00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=
 4983 dschneid  20   0 54504  3784  2608 S  0.0  0.1  0:00.00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
 4967 dschneid  20   0 45232  2964  2448 S  0.0  0.1  0:00.00 /usr/lib/gvfs/gvfsd-trash --spawner :1.5 /org/gtk/gvfs/exec_spaw/0
 4951 dschneid  20   0 56224  4248  3108 S  0.0  0.1  0:00.00 /usr/lib/gvfs/gvfs-hal-volume-monitor
F1Help  F2Setup F3SearchF4InvertF5Tree  F6SortByF7Nice -F8Nice +F9Kill  F10Quit

 
```
There is a problem with gnome or the x-server or it's configuration!

---

### Post by houdodu on 2009-08-09
exact same problem.

strangely, only effects one of my machines, the desktop.

laptop seems fine.

---

