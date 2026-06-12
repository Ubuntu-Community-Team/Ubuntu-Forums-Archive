---
title: "system repair?"
date: 2008-06-27
forum: x86 64-bit Users
---

### Post by Vercynogetorix on 2008-06-27
im pretty new to linux, althought i did some playing around a while ago, 

i have had quite a problems installing ubuntu, first it claimed broken cd several times, than claimed its oki than other things, long list,

eventually i have installed it from "alternative" cd 

tho i have had some err's while installing, now:

a) how to check what err's i have while running the system (i do have some, just dont know what they are)

b) what can i do to check wheter all system files and such are installed properly, is there a sytem check program of some sort?

or is synaptics/package installer supposed to do that for me?

generally i believe there is something conflicting on line software/hardware but i do not know how to check it, even less fix it...

i have also found some straight occurences in workings of wine, as it is somewhat popular xplatform soft, i wonder wheter these errors would not mean either network/sound card/graph failures, ....
=============================

open to any adivce, please post in if you need hardware info etc... 

(compaq presario v6xxx, i945gm chip, 2gb ram x64 1.60ghz proc)

---

### Post by Sef on 2008-06-27
How do things work when you use the Live CD?

---

### Post by nikgare on 2008-06-28
> tho i have had some err's while installing,

What errors are you getting?

---

### Post by Fir3chi3f on 2008-06-28
Do you know some system specs?

---

### Post by Vercynogetorix on 2008-06-28
now system spec is:

Intel t550 core2duo (whatever the codename is)
2gb ram
intel 945gm/pm chipset (graphic card on board)
intel v100 network card
broadcom wireless b43 card (not native to linux)
===============================================

now i do have some networking err's at log out but im not sure what it is, i dont know how to check it, other than that, some app crashings (random) and when i eject cd's i usually get another kde err....

i run ubuntu 8.4,

and funny enough when i was on live cd it was working perfect, no crashes whatsoever, :/

im not sure what shall i think of it, 

ps. some applications run under wine does not work even tho they get excellent reviews from others using it, and having no problems whatsoever :/

---

### Post by nikgare on 2008-06-28
> i usually get another kde err

Yes, but what errors are you getting?
No-one can start to help you until they know what errors you are getting!

---

### Post by jimei on 2008-06-28
[Dunk SB]("http://www.gucci-sneaker.com/catalog_39.html")
[Air force one]("http://www.gucci-sneaker.com/catalog_42.html")

---

### Post by Vercynogetorix on 2008-06-28
the thing is, i do not know, when kde one will appear again i will note, other than that one of original questions was is there anywhere something like error log, so i can start figuring whats wrong

---

### Post by cariboo on 2008-06-28
You can look two places for errors, /var/log/messages and dmesg, both put out lots of info, I would suggest piping the output to a text file. To do this in a Applications-->Accessories-->Termianl type:

```
cat /var/log/messages > messages.txt
```

and

```
dmesg > dmesg.txt
```

or

System-->Administartion-->System Log

Jim

---

### Post by Vercynogetorix on 2008-06-28
first of commands you gave nme didnt work in terminal, just nothing happened at all, 

as to second im not sure what to look for so i decided to rather copy everything that comes under loose term suspicious to me.

ive found those:

xorg.0.log

Jun 28 04:45:59 ubuntu dhcdbd: Started up.
Jun 28 04:46:23 ubuntu pulseaudio[5961]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jun 28 04:46:23 ubuntu pulseaudio[5961]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jun 28 04:46:23 ubuntu pulseaudio[5961]: alsa-util.c: Cannot find fallback mixer control "Mic".
Jun 28 04:46:36 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun 28 04:47:00 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Jun 28 04:47:00 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.domain_name
Jun 28 04:47:00 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Jun 28 04:47:00 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Jun 28 04:47:00 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
Jun 28 13:41:33 ubuntu dhcdbd: Started up.
Jun 28 13:41:57 ubuntu pulseaudio[5953]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jun 28 13:41:57 ubuntu pulseaudio[5953]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jun 28 13:41:57 ubuntu pulseaudio[5953]: alsa-util.c: Cannot find fallback mixer control "Mic".
Jun 28 13:42:13 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun 28 13:42:32 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Jun 28 13:42:32 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.domain_name
Jun 28 13:42:32 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Jun 28 13:42:32 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Jun 28 13:42:32 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
=======================================================================
=========================================================================
syslog
======
Jun 27 17:13:23 ubuntu pulseaudio[5954]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jun 27 17:13:23 ubuntu pulseaudio[5954]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jun 27 17:13:23 ubuntu pulseaudio[5954]: alsa-util.c: Cannot find fallback mixer control "Mic".
=======================================================================
Jun 26 18:15:55 ubuntu dhcdbd:  dhclient 5762 down (9) but si_code == 0 and releasing==0 !
=======================================================================
Jun 28 05:06:55 ubuntu kernel: [  553.149269] gvfs-fuse-daemo[6021] general protection rip:7f7efdb2b423 rsp:7fff07755040 error:0
Jun 28 05:06:55 ubuntu console-kit-daemon[5419]: WARNING: Unable to activate console: No such device or address 
========================================================================
Jun 28 05:06:56 ubuntu gdm[5645]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jun 28 05:06:56 ubuntu gdm[5645]: WARNING: Request for invalid configuration key xdmcp/Enable=false 
=====================================================================
Jun 28 13:41:32 ubuntu kernel: [    0.000000] No NUMA configuration found
======================================================================
Jun 28 13:41:32 ubuntu kernel: [   29.678353] Failure registering capabilities with primary security module.
=======================================================================
Jun 28 13:41:32 ubuntu kernel: [   30.138534] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
==========================================================================
Jun 28 13:41:32 ubuntu kernel: [   30.411292] system 00:00: iomem range 0xe0000000-0xefffffff could not be reserved
Jun 28 13:41:32 ubuntu kernel: [   30.411300] system 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
Jun 28 13:41:32 ubuntu kernel: [   30.411304] system 00:02: iomem range 0xfed14000-0xfed17fff could not be reserved
Jun 28 13:41:32 ubuntu kernel: [   30.411307] system 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
Jun 28 13:41:32 ubuntu kernel: [   30.411311] system 00:02: iomem range 0xfed19000-0xfed19fff could not be reserved
Jun 28 13:41:32 ubuntu kernel: [   30.411314] system 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
Jun 28 13:41:32 ubuntu kernel: [   30.411318] system 00:02: iomem range 0xfed20000-0xfed3ffff could not be reserved
Jun 28 13:41:32 ubuntu kernel: [   30.411321] system 00:02: iomem range 0xfed40000-0xfed44fff could not be reserved
Jun 28 13:41:32 ubuntu kernel: [   30.411325] system 00:02: iomem range 0xfed45000-0xfed8ffff could not be reserved
Jun 28 13:41:32 ubuntu kernel: [   30.411332] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
=========================================================================
Jun 28 13:41:32 ubuntu kernel: [   33.832095]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
==========================================================================
Jun 28 13:41:32 ubuntu kernel: [   34.358495] PM: Checking swsusp image.
Jun 28 13:41:32 ubuntu kernel: [   34.358687] PM: Resume from disk failed.
==========================================================================
Jun 28 13:41:41 ubuntu audio[5570]: audio.conf: Key file does not have key 'Disable'
Jun 28 13:41:41 ubuntu audio[5570]: audio.conf: Key file does not have group 'A2DP'
=========================================================================
Jun 28 13:42:13 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
======================================================================
Jun 28 13:42:19 ubuntu kernel: [   99.336290] UDF-fs: No VRS found
======================================================================
Jun 28 13:42:30 ubuntu dhclient: wmaster0: unknown hardware address type 801
===================================================================
Jun 28 16:32:58 ubuntu kernel: [ 8322.321210] UDF-fs: No VRS found
===================================================================
Jun 28 19:49:16 ubuntu udevd[2810]: udev_rules_init: could not read '/etc/udev/rules.d/z60_usrp.rules': No such file or directory
===================================================================
Jun 28 22:13:00 ubuntu NetworkManager: <debug> [1214687580.991394] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_label_STARCRAFT'). 
=====================================================================
======================================================================
messages:
---------
Jun 28 19:37:45 ubuntu kernel: [19400.801342] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
Jun 28 19:38:25 ubuntu kernel: [19441.415316] npviewer.bin[13442]: segfault at f5b51030 rip f7945540 rsp ff83d1ec error 4
Jun 28 19:39:10 ubuntu kernel: [19486.149496] npviewer.bin[13504]: segfault at f5ac4030 rip f78b8540 rsp ff8f4b3c error 4
Jun 28 19:39:11 ubuntu kernel: [19487.083139] npviewer.bin[13524]: segfault at f5b76030 rip f796a540 rsp ff91b36c error 4
Jun 28 19:39:12 ubuntu kernel: [19488.056369] npviewer.bin[13544]: segfault at f5adb030 rip f78cf540 rsp ffb1f4cc error 4
Jun 28 19:40:37 ubuntu kernel: [19572.677199] npviewer.bin[13690]: segfault at f5aad030 rip f78a1540 rsp fff0194c error 4
Jun 28 19:40:37 ubuntu kernel: [19572.864813] npviewer.bin[13710]: segfault at f5b70030 rip f7964540 rsp ffd5efac error 4
Jun 28 19:40:59 ubuntu kernel: [19594.891342] npviewer.bin[13772]: segfault at f5b08030 rip f78fc540 rsp ffb8e5dc error 4
Jun 28 19:41:04 ubuntu kernel: [19599.835279] npviewer.bin[13814]: segfault at f5aa4030 rip f7898540 rsp fff611ac error 4
Jun 28 19:41:23 ubuntu kernel: [19619.265906] npviewer.bin[13860]: segfault at f5aeb030 rip f78df540 rsp fff360dc error 4
Jun 28 19:41:32 ubuntu kernel: [19628.061538] npviewer.bin[13900]: segfault at f5b34030 rip f7928540 rsp ffe8402c error 4
Jun 28 19:43:51 ubuntu kernel: [19767.024035] npviewer.bin[14003]: segfault at f5ab5030 rip f78a9540 rsp ffc4ce9c error 4
Jun 28 20:01:31 ubuntu -- MARK --
Jun 28 20:21:31 ubuntu -- MARK --
Jun 28 20:41:31 ubuntu -- MARK --
Jun 28 21:01:31 ubuntu -- MARK --
Jun 28 21:21:31 ubuntu -- MARK --
Jun 28 21:41:31 ubuntu -- MARK --
Jun 28 21:56:16 ubuntu kernel: [27706.068431] npviewer.bin[15079]: segfault at f5b69030 rip f795d540 rsp ffe51ffc error 4
Jun 28 21:56:27 ubuntu kernel: [27717.084224] npviewer.bin[15150]: segfault at f5b21030 rip f7915540 rsp ffc50e9c error 4
Jun 28 21:56:42 ubuntu kernel: [27731.964797] npviewer.bin[15190]: segfault at f5b7e030 rip f7972540 rsp ff926b6c error 4
Jun 28 21:56:53 ubuntu kernel: [27743.052897] npviewer.bin[15230]: segfault at f5b53030 rip f7947540 rsp ffb6fdbc error 4
Jun 28 21:57:44 ubuntu kernel: [27793.947462] npviewer.bin[15273]: segfault at f5b95030 rip f7989540 rsp ffc83ecc error 4
Jun 28 22:10:15 ubuntu kernel: [28544.329563] npviewer.bin[15663]: segfault at f5a9f030 rip f7893540 rsp ff975bbc error 4
===================================================
i have a lot of those kernel debugs there, i wont paste all of them unless you will require me to.
=======================================================================
kern log
=======
a lot of kernel debugs on npviewer 
===================================
Jun 28 04:45:58 ubuntu kernel: [   18.845214] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
======================================================================
Jun 28 04:45:58 ubuntu kernel: [   19.673341] system 00:00: iomem range 0xe0000000-0xefffffff could not be reserved
Jun 28 04:45:58 ubuntu kernel: [   19.673349] system 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
Jun 28 04:45:58 ubuntu kernel: [   19.673353] system 00:02: iomem range 0xfed14000-0xfed17fff could not be reserved
Jun 28 04:45:58 ubuntu kernel: [   19.673357] system 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
Jun 28 04:45:58 ubuntu kernel: [   19.673360] system 00:02: iomem range 0xfed19000-0xfed19fff could not be reserved
Jun 28 04:45:58 ubuntu kernel: [   19.673364] system 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
Jun 28 04:45:58 ubuntu kernel: [   19.673367] system 00:02: iomem range 0xfed20000-0xfed3ffff could not be reserved
Jun 28 04:45:58 ubuntu kernel: [   19.673371] system 00:02: iomem range 0xfed40000-0xfed44fff could not be reserved
Jun 28 04:45:58 ubuntu kernel: [   19.673374] system 00:02: iomem range 0xfed45000-0xfed8ffff could not be reserved
Jun 28 04:45:58 ubuntu kernel: [   19.673382] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
========================================================================
Jun 28 04:45:58 ubuntu kernel: [   20.693267] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
=========================================================================
Jun 28 04:45:58 ubuntu kernel: [   37.915438] agpgart: Detected an Intel 945GM Chipset.
Jun 28 04:45:58 ubuntu kernel: [   37.916525] agpgart: Detected 7932K stolen memory.
Jun 28 04:45:58 ubuntu kernel: [   37.935454] agpgart: AGP aperture is 256M @ 0xc0000000
==========================================================================
======================================================================
daemon log:
========
Jun 28 13:41:32 ubuntu avahi-daemon[5264]: No service file found in /etc/avahi/services.
=========================================================================
auth log:
==========
Jun 28 00:12:12 ubuntu gnome-keyring-daemon[5935]: couldn't read 4 bytes from client: 
=======================================================================


terrible in that situation is fact im kinda newbie to linux so i cant be awfully helpfull :/

---

