---
title: "IVTV Init Cannot Open Firmware"
date: 2006-05-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by bper on 2006-05-01
OK, here is one for the "if it ain't broke, don't fix it" files. I had ivtv 0.4.3 working reasonably well in Ubuntu 5.10 64-bit, but I had to redo my installation and I installed Ubuntu 6.06 and ivtv 0.4.4. Now, although I've done what I believe to be the right steps, the firmware files are not being seen. Maybe there is a typo? Wrong directory? Any help would be appreciated.

Here is my /usr/lib/hotplug/firmware directory:

drwxr-xr-x 3 root root   4096 2006-04-30 22:35 ..
-r--r--r-- 1 root root  14264 2006-05-01 00:11 v4l-cx25840.fw
-r--r--r-- 1 root root 376836 2006-05-01 00:11 v4l-cx2341-enc.fw
-rw-r--r-- 1 root root 262144 2006-05-01 00:12 v4l-cx2341x-dec.fw
-rw-r--r-- 1 root root 155648 2006-05-01 00:15 v4l-cx2341x-init.mpg
drwxr-xr-x 2 root root   4096 2006-05-01 00:15 .

Here is my ivtv output from dmesg:

[   36.773231] ivtv:  ==================== START INIT IVTV ====================
[   36.773234] ivtv:  version 0.4.4 (tagged release) loading
[   36.773236] ivtv:  Linux version: 2.6.15-21-amd64-generic SMP preempt gcc-4.0[   36.773238] ivtv:  In case of problems please include the debug info between
[   36.773240] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   36.773241] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   36.773289] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[   36.773605] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   36.773610] GSI 20 sharing vector 0x3A and IRQ 20
[   36.773614] ACPI: PCI Interrupt 0000:05:06.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 58
[   36.773621] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   36.918235] tveeprom: ivtv version
[   36.918238] tveeprom: Hauppauge: model = 26582, rev = F0B2, serial# = 9344611[   36.918241] tveeprom: tuner = <unknown> (idx = 112, type = 4)
[   36.918244] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[   36.918246] tveeprom: audio processor = CX25843 (type = 25)
[   36.918248] tveeprom: decoder processor = CX25843 (type = 1e)
[   36.918250] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[   36.943644] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[   36.943649] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[   37.115874] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   37.115878] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 225
[   37.116034] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   37.133564] parport: PnPBIOS parport detected.
[   37.133611] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   37.147808] Real Time Clock Driver v1.12
[   37.200381] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   37.307391] input: PC Speaker as /class/input/input2
[   37.345184] nvidia: module license 'NVIDIA' taints kernel.
[   37.348630] ts: Compaq touchscreen protocol output
[   37.435313] intel8x0_measure_ac97_clock: measured 50720 usecs
[   37.435316] intel8x0: clocking to 46818
[   37.461482] cx25840 2-0044: unable to open firmware v4l-cx25840.fw
[   37.508209] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[   37.525435] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   37.532058] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[   38.182458] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[   38.182461] ivtv0: did you put the firmware in the hotplug firmware directory?
[   38.182464] ivtv0 warning: failed loading encoder firmware
[   38.182466] ivtv0 warning: Error loading firmware -3!
[   38.182468] ivtv0: Error -3 initializing firmware.
[   38.184580] ivtv0: Error -12 on initialization
[   38.184587] ivtv: probe of 0000:05:06.0 failed with error -12
[   38.185137] ivtv:  ====================  END INIT IVTV  ====================

---

### Post by kooldeep on 2006-05-01
I put mine in /lib/firmware/<kernal version>/ and it worked for me.

Something to do with hotplug on dapper I think.

---

### Post by bper on 2006-05-01
Thanks for the tip, kooldeep. I'll give it a shot later and let you know.

Is there a place where we can submit issues to the dapper developers? Or do you think that they are already aware of this?

---

### Post by bper on 2006-05-01
Tried your suggestion, kooldeep. No change.

---

### Post by Trevor2004 on 2006-05-06
[QUOTE=kooldeep]I put mine in /lib/firmware/<kernal version>/ and it worked for me.

Something to do with hotplug on dapper I think.[/QUOTE]

i had the same issue, but that fixed it.  thanks

---

### Post by Eduardo! on 2006-05-06
anyone got a mirror or can upload their firmware they're using? trying to rebuild a mythtv box and the download site has been down for days. =/

---

### Post by bper on 2006-05-11
Kooldeep, your suggestion does work. I think I tried this at a time when my kernel was updated by dapper update. I had to rebuild ivtv to get it to work again. When I tried your suggestion, it worked fine. 

Thanks a lot.

---

### Post by dlai on 2006-05-15
hey everybody i just wanted to let you know since you are probably ivtv-users... If you don't want to use mythtv, it is now possible to view tv with [xawtv]("http://ubuntuforums.org/showthread.php?t=170884")

---

