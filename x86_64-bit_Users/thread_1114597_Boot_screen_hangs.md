---
title: "Boot screen hangs"
date: 2009-04-02
forum: x86 64-bit Users
---

### Post by Zekes on 2009-04-02
During boot up ubuntu hangs indefinitely unless I hold down a key. Although it is not a big deal it is bothersome. 

I'm running a AMD64 bit HP Pavilion DV6000 laptop with intrepid  
I ran log errors and it gave me the following.

zeke@zeke-laptop:~$ sudo tail -n100 /var/log/messages
Apr  2 20:05:13 zeke-laptop kernel: [  259.110162] sdhci: Copyright(c) Pierre Ossman
Apr  2 20:05:13 zeke-laptop kernel: [  259.211363] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Apr  2 20:05:13 zeke-laptop kernel: [  259.233052] ACPI: Power Button (FF) [PWRF]
Apr  2 20:05:13 zeke-laptop kernel: [  259.233197] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
Apr  2 20:05:13 zeke-laptop kernel: [  259.265035] ACPI: Sleep Button (CM) [SLPB]
Apr  2 20:05:13 zeke-laptop kernel: [  259.265187] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
Apr  2 20:05:13 zeke-laptop kernel: [  259.266427] ACPI: Lid Switch [LID]
Apr  2 20:05:13 zeke-laptop kernel: [  259.266582] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
Apr  2 20:05:13 zeke-laptop kernel: [  259.297048] ACPI: Power Button (CM) [PWRB]
Apr  2 20:05:13 zeke-laptop kernel: [  259.299092] ACPI: AC Adapter [ACAD] (on-line)
Apr  2 20:05:13 zeke-laptop kernel: [  259.299232] ACPI: WMI: Mapper loaded
Apr  2 20:05:13 zeke-laptop kernel: [  259.299460] sdhci-pci 0000:02:05.1: SDHCI controller found [1180:0822] (rev 22)
Apr  2 20:05:13 zeke-laptop kernel: [  259.299900] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
Apr  2 20:05:13 zeke-laptop kernel: [  259.299913] sdhci-pci 0000:02:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
Apr  2 20:05:13 zeke-laptop kernel: [  259.312676] mmc0: SDHCI controller on PCI [0000:02:05.1] using PIO
Apr  2 20:05:13 zeke-laptop kernel: [  259.367540] ricoh-mmc: Ricoh MMC Controller disabling driver
Apr  2 20:05:13 zeke-laptop kernel: [  259.367544] ricoh-mmc: Copyright(c) Philip Langdale
Apr  2 20:05:13 zeke-laptop kernel: [  259.367587] ricoh-mmc: Ricoh MMC controller found at 0000:02:05.2 [1180:0843] (rev 12)
Apr  2 20:05:13 zeke-laptop kernel: [  259.367602] ricoh-mmc: Controller is now disabled.
Apr  2 20:05:13 zeke-laptop kernel: [  259.877301] Linux video capture interface: v2.00
Apr  2 20:05:13 zeke-laptop kernel: [  259.926203] ACPI: Battery Slot [BAT0] (battery present)
Apr  2 20:05:13 zeke-laptop kernel: [  259.931827] acpi device:25: registered as cooling_device2
Apr  2 20:05:13 zeke-laptop kernel: [  259.932077] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:23/input/input6
Apr  2 20:05:13 zeke-laptop kernel: [  259.953028] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
Apr  2 20:05:13 zeke-laptop kernel: [  260.006549] uvcvideo: Found UVC 1.00 device HP Webcam (0408:030c)
Apr  2 20:05:13 zeke-laptop kernel: [  260.008252] input: HP Webcam as /devices/pci0000:00/0000:00:04.1/usb4/4-2/4-2:1.0/input/input7
Apr  2 20:05:13 zeke-laptop kernel: [  260.008290] usbcore: registered new interface driver uvcvideo
Apr  2 20:05:13 zeke-laptop kernel: [  260.008305] USB Video Class driver (v0.1.0)
Apr  2 20:05:13 zeke-laptop kernel: [  260.075993] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  2 20:05:13 zeke-laptop kernel: [  260.183955] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  2 20:05:13 zeke-laptop kernel: [  260.365976] nvidia: module license 'NVIDIA' taints kernel.
Apr  2 20:05:13 zeke-laptop kernel: [  260.367736] Symbol init_mm is marked as UNUSED, however this module is using it.
Apr  2 20:05:13 zeke-laptop kernel: [  260.367739] This symbol will go away in the future.
Apr  2 20:05:13 zeke-laptop kernel: [  260.367741] Please evalute if this is the right api to use and if it really is, submit a report the linux kernel mailinglist together with submitting your code for inclusion.
Apr  2 20:05:13 zeke-laptop kernel: [  260.623248] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
Apr  2 20:05:13 zeke-laptop kernel: [  260.623262] nvidia 0000:00:12.0: PCI INT A -> Link[LGPU] -> GSI 16 (level, low) -> IRQ 16
Apr  2 20:05:13 zeke-laptop kernel: [  260.623595] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.12  Thu Jul 17 18:10:24 PDT 2008
Apr  2 20:05:13 zeke-laptop kernel: [  260.695893] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
Apr  2 20:05:13 zeke-laptop kernel: [  260.695908] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
Apr  2 20:05:13 zeke-laptop kernel: [  260.736309] input: PC Speaker as /devices/platform/pcspkr/input/input8
Apr  2 20:05:13 zeke-laptop kernel: [  260.854508] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
Apr  2 20:05:13 zeke-laptop kernel: [  260.854522] wl 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
Apr  2 20:05:13 zeke-laptop kernel: [  260.888430] eth1: Broadcom BCM4328 802.11 Wireless Controller 5.10.27.12
Apr  2 20:05:13 zeke-laptop kernel: [  261.614039] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0xa00000
Apr  2 20:05:13 zeke-laptop kernel: [  261.695538] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
Apr  2 20:05:13 zeke-laptop kernel: [  262.456203] lp: driver loaded but no devices found
Apr  2 20:05:13 zeke-laptop kernel: [  262.696984] Adding 6385796k swap on /dev/sda5.  Priority:-1 extents:1 across:6385796k
Apr  2 20:05:13 zeke-laptop kernel: [  263.248319] EXT3 FS on sda1, internal journal
Apr  2 20:05:13 zeke-laptop kernel: [  264.218510] type=1505 audit(1238727910.959:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4293
Apr  2 20:05:13 zeke-laptop kernel: [  264.385058] type=1505 audit(1238727911.127:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4298
Apr  2 20:05:13 zeke-laptop kernel: [  264.385309] type=1505 audit(1238727911.127:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4298
Apr  2 20:05:13 zeke-laptop kernel: [  264.545458] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr  2 20:05:13 zeke-laptop kernel: [  265.562862] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-64 processors (2 cpu cores) (version 2.20.00)
Apr  2 20:05:13 zeke-laptop kernel: [  265.562941] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x12
Apr  2 20:05:13 zeke-laptop kernel: [  265.562945] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x13
Apr  2 20:05:13 zeke-laptop kernel: [  265.562947] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x14
Apr  2 20:05:13 zeke-laptop kernel: [  265.562949] powernow-k8:    3 : fid 0x8 (1600 MHz), vid 0x15
Apr  2 20:05:13 zeke-laptop kernel: [  265.562951] powernow-k8:    4 : fid 0x0 (800 MHz), vid 0x1e
Apr  2 20:05:13 zeke-laptop kernel: [  266.429416] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Apr  2 20:05:13 zeke-laptop kernel: [  266.617861] ppdev: user-space parallel port driver
Apr  2 20:05:17 zeke-laptop kernel: [  270.793884] VBoxDrv: dbg - g_abExecMemory=ffffffffa0d05fe0
Apr  2 20:05:17 zeke-laptop kernel: [  270.793927] vboxdrv: fAsync=1 offMin=0xea373 offMax=0xea373
Apr  2 20:05:17 zeke-laptop kernel: [  270.797217] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
Apr  2 20:05:17 zeke-laptop kernel: [  271.023590] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa0ea3e20
Apr  2 20:05:22 zeke-laptop kernel: [  275.489620] eth0: no link during initialization.
Apr  2 20:05:22 zeke-laptop kernel: [  276.127067] Bluetooth: Core ver 2.13
Apr  2 20:05:22 zeke-laptop kernel: [  276.128380] NET: Registered protocol family 31
Apr  2 20:05:22 zeke-laptop kernel: [  276.128389] Bluetooth: HCI device and connection manager initialized
Apr  2 20:05:22 zeke-laptop kernel: [  276.128400] Bluetooth: HCI socket layer initialized
Apr  2 20:05:22 zeke-laptop kernel: [  276.196530] Bluetooth: L2CAP ver 2.11
Apr  2 20:05:22 zeke-laptop kernel: [  276.196545] Bluetooth: L2CAP socket layer initialized
Apr  2 20:05:22 zeke-laptop kernel: [  276.236345] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr  2 20:05:22 zeke-laptop kernel: [  276.236367] Bluetooth: BNEP filters: protocol multicast
Apr  2 20:05:23 zeke-laptop kernel: [  276.304718] Bluetooth: RFCOMM socket layer initialized
Apr  2 20:05:23 zeke-laptop kernel: [  276.305618] Bluetooth: RFCOMM TTY layer initialized
Apr  2 20:05:23 zeke-laptop kernel: [  276.305630] Bluetooth: RFCOMM ver 1.10
Apr  2 20:05:23 zeke-laptop kernel: [  276.361421] Bridge firewalling registered
Apr  2 20:05:23 zeke-laptop kernel: [  276.409818] Bluetooth: SCO (Voice Link) ver 0.6
Apr  2 20:05:23 zeke-laptop kernel: [  276.409835] Bluetooth: SCO socket layer initialized
Apr  2 20:05:24 zeke-laptop kernel: [  277.865334] NET: Registered protocol family 17
Apr  2 20:05:42 zeke-laptop pulseaudio[5928]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr  2 20:05:42 zeke-laptop pulseaudio[5930]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr  2 20:05:42 zeke-laptop pulseaudio[5930]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr  2 20:05:42 zeke-laptop pulseaudio[5930]: alsa-util.c: Cannot find fallback mixer control "Mic".
Apr  2 20:05:43 zeke-laptop kernel: [  297.003192] NET: Registered protocol family 10
Apr  2 20:05:43 zeke-laptop kernel: [  297.006769] lo: Disabled Privacy Extensions
Apr  2 20:05:43 zeke-laptop kernel: [  297.009499] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  2 20:05:48 zeke-laptop pulseaudio[5930]: sap.c: sendmsg() failed: Invalid argument
Apr  2 20:06:23 zeke-laptop last message repeated 7 times
Apr  2 20:06:48 zeke-laptop last message repeated 5 times
Apr  2 20:06:50 zeke-laptop kernel: [  363.913981] eth0: link up.
Apr  2 20:06:50 zeke-laptop kernel: [  363.915464] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr  2 20:06:53 zeke-laptop pulseaudio[5930]: sap.c: sendmsg() failed: Invalid argument
Apr  2 20:07:28 zeke-laptop last message repeated 7 times
Apr  2 20:08:33 zeke-laptop last message repeated 13 times
Apr  2 20:09:38 zeke-laptop last message repeated 13 times
Apr  2 20:10:38 zeke-laptop last message repeated 12 times
Apr  2 20:11:38 zeke-laptop last message repeated 12 times
Apr  2 20:12:39 zeke-laptop last message repeated 12 times
Apr  2 20:13:39 zeke-laptop last message repeated 12 times
zeke@zeke-laptop:~$ 

Any help would be appreciated Thanks 
Zeke

---

### Post by lensman3 on 2009-04-03
This probably won't work, but in the BIOS turn off your sound.  Then try a reboot and see if will get by the hang up.  If it does and gets to the log in screens, then see what lspci show for a sound card and see if you can manually load the sound drivers using modprobe.

The trick for this to work is if the BIOS reports to the loading drivers that there is NO sound card.  Some OS's and drivers can ignore the BIOS.

Hope this helps.

---

### Post by Zekes on 2009-04-15
Unfortunately this didn't work for me. Any other solutions. I've researched this topic extensively and it seems to be a problem with all intrepid amd64 machines.

---

### Post by ericwait on 2009-05-28
I had the same problems with 8.10 and now 9.04.  Here is what I did as a work around:

Edit your /boot/grub/menu.lst

Go all the way down the doc and edit your first "kernel" line so the end looks like this 

```
 ro quiet splash acpi=noirq
```

This should appear right after root=UUID=[long number]

This at lest allowed my laptop to start up without pressing the cntl key.

I don't know how much you paid attention, but I found before this fix, my laptop would start just fine if it was pluged in prior or during the boot process.

Hope that does the trick for you too.  Now just to get the sleep mode working.

E

---

