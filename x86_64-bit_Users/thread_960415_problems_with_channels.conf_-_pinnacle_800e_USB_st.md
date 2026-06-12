---
title: "problems with channels.conf - pinnacle 800e USB stick"
date: 2008-10-27
forum: x86 64-bit Users
---

### Post by sandyeggoboy on 2008-10-27
Hello,

i am running the new 8.10 on my HP Pavilion DV9623cl laptop, and i have a pinnacle HD TV USB stick model 800e that i want to use. So far i have been successful at getting the system to know its there, and all the software works, but i am stuck at getting the channels.conf file created. i used a utility called w_scan and it gives the following:

deric@barney:~$ w_scan >> ~/channels.conf
w_scan version 20080105
Info: using DVB adapter auto detection.
Info: unable to open frontend /dev/dvb/adapter1/frontend0'
Info: unable to open frontend /dev/dvb/adapter2/frontend0'
Info: unable to open frontend /dev/dvb/adapter3/frontend0'
main:2401: FATAL: ***** NO USEABLE DVB CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.

 
when i run dmesg it returns:

[72237.117049] usb 3-5: new high speed USB device using ehci_hcd and address 4
[72237.269525] usb 3-5: configuration #1 chosen from 1 choice
[72237.270696] em28xx new video device (2304:0227): interface 0, class 255
[72237.270706] em28xx Doesn't have usb audio class
[72237.270708] em28xx #0: Alternate settings: 8
[72237.270710] em28xx #0: Alternate setting 0, max size= 0
[72237.270713] em28xx #0: Alternate setting 1, max size= 0
[72237.270715] em28xx #0: Alternate setting 2, max size= 1448
[72237.270717] em28xx #0: Alternate setting 3, max size= 2048
[72237.270719] em28xx #0: Alternate setting 4, max size= 2304
[72237.270721] em28xx #0: Alternate setting 5, max size= 2580
[72237.270723] em28xx #0: Alternate setting 6, max size= 2892
[72237.270725] em28xx #0: Alternate setting 7, max size= 3072
[72237.279350] em28xx #0: chip ID is em2882/em2883
[72237.448893] tuner' 4-0061: chip found @ 0xc2 (em28xx #0)
[72237.485518] em28xx #0: i2c eeprom 00: 1a eb 67 95 04 23 27 02 d0 12 5c 03 8e 16 a4 1c
[72237.485534] em28xx #0: i2c eeprom 10: 6a 24 27 57 46 07 01 00 00 00 00 00 00 00 00 00
[72237.485545] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 02 00 b8 00 00 00 5b 1c 00 00
[72237.485555] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 00 00 00 00 00 00
[72237.485565] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[72237.485574] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[72237.485584] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 24 03 50 00 69 00
[72237.485594] em28xx #0: i2c eeprom 70: 6e 00 6e 00 61 00 63 00 6c 00 65 00 20 00 53 00
[72237.485604] em28xx #0: i2c eeprom 80: 79 00 73 00 74 00 65 00 6d 00 73 00 00 00 16 03
[72237.485613] em28xx #0: i2c eeprom 90: 50 00 43 00 54 00 56 00 20 00 38 00 30 00 30 00
[72237.485623] em28xx #0: i2c eeprom a0: 65 00 00 00 1c 03 30 00 37 00 30 00 38 00 30 00
[72237.485633] em28xx #0: i2c eeprom b0: 31 00 30 00 36 00 39 00 30 00 33 00 39 00 00 00
[72237.485643] em28xx #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[72237.485653] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[72237.485662] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[72237.485672] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[72237.485683] EEPROM ID= 0x9567eb1a, hash = 0xe4e5adbf
[72237.485685] Vendor/Product ID= 2304:0227
[72237.485687] AC97 audio (5 sample rates)
[72237.485688] 500mA max power
[72237.485690] Table at 0x27, strings=0x168e, 0x1ca4, 0x246a
[72237.505514] xc2028 4-0061: creating new instance
[72237.505524] xc2028 4-0061: type set to XCeive xc2028/xc3028 tuner
[72237.507097] firmware: requesting xc3028-v27.fw
[72237.598174] xc2028 4-0061: Error: firmware xc3028-v27.fw not found.
[72237.693395] tvp5150 4-005c: tvp5150am1 detected.
[72237.854019] em28xx #0: V4L2 device registered as /dev/video1 and /dev/vbi0
[72237.855399] em28xx-audio.c: probing for em28x1 non standard usbaudio
[72237.855406] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger
[72237.918594] xc2028 4-0061: attaching existing instance
[72237.918603] xc2028 4-0061: type set to XCeive xc2028/xc3028 tuner
[72237.918605] em28xx #0/2: xc3028 attached
[72237.920921] DVB: registering new adapter (em28xx #0)
[72237.921731] DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[72237.923351] Successfully loaded em28xx-dvb
[72237.923359] em28xx #0: Found Pinnacle PCTV HD Pro Stick
[72239.022270] tvp5150 4-005c: tvp5150am1 detected.
[72240.533270] tvp5150 4-005c: tvp5150am1 detected.
[72240.774395] tvp5150 4-005c: tvp5150am1 detected.
[72241.074270] tvp5150 4-005c: tvp5150am1 detected.

Does anyone have an idea what i may be doing wrong?

Thanks.

Deric Stowell

---

### Post by kayalemao on 2008-11-16
Hi,

I have the same problem. Can anybody help us
Here my files

w_scan:
w_scan version 20080105
Info: using DVB adapter auto detection.
Info: unable to open frontend /dev/dvb/adapter1/frontend0'
Info: unable to open frontend /dev/dvb/adapter2/frontend0'
Info: unable to open frontend /dev/dvb/adapter3/frontend0'
main:2401: FATAL: ***** NO USEABLE DVB CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.

lspci:
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
00:07.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 20)
00:0a.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0c.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0c.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0c.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0c.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:0d.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

lspci-v:
00:0d.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
	Subsystem: Technotrend Systemtechnik GmbH Device 0003
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at dffff800 (32-bit, non-prefetchable) [size=512]
	Kernel driver in use: dvb
	Kernel modules: dvb-ttpci, snd-aw2

dmesg:
[   33.920278] DVB: registering new adapter (Technotrend/Hauppauge WinTV Nexus-S rev2.X)
[   33.957319] adapter has MAC addr = 00:d0:5c:20:94:c0
[   34.258823] dvb-ttpci: gpioirq unknown type=0 len=0
[   34.284210] dvb-ttpci: info @ card 0: firm f0240009, rtsl b0250018, vid 71010068, app 80002622
[   34.284221] dvb-ttpci: firmware @ card 0 supports CI link layer interface
[   34.336231] dvb-ttpci: Crystal audio DAC @ card 0 detected
[   34.341570] saa7146_vv: saa7146 (0): registered device video1 [v4l2]
[   34.342053] saa7146_vv: saa7146 (0): registered device vbi0 [v4l2]
[   34.768285] DVB: registering frontend 0 (ST STV0299 DVB-S)...
[   34.769913] input: DVB on-card IR receiver as /devices/pci0000:00/0000:00:0d.0/input/input7
[   34.770881] dvb-ttpci: found av7110-0.

---

### Post by _gpf_ on 2008-12-24
Try explicitly specifying the adapter you want w_scan to use.  I have this USB HDTV stick on 8.10 as well, and this worked for me:

```
w_scan -a /dev/dvb/adapter0 -X > channels.conf
```

Hope that helps!

---

