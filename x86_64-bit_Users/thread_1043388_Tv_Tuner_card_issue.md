---
title: "Tv Tuner card issue"
date: 2009-01-18
forum: x86 64-bit Users
---

### Post by rhonaldmoses on 2009-01-18
Hi,

I bought a new PC - HP Pavillion Elite PC m9373.me-a days back which comes with TV tuner card and other stuffs to watch TV directly from the PC with the cable inserted.

It came with Windows Vista which I wiped out completely since I prefer Gnu/Linux [openSUSE in my laptop and Ubuntu in desktop].

I use 64-bit Ubuntu 8.10 on my desktop.

The problem is that I am not able to setup tvtime or mythTV successfully.

I get Cannot Open Capture Device /dev/video0 in tvtime and no response from mythTV.

The **lspci** command returns the following output.

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
05:00.0 VGA compatible controller: nVidia Corporation Device 0601 (rev a2)


Though I use Gnu/Linux for a year, I have very less clue about deep technical informations.

I believe Conexant Systems, Inc. **CX23885 PCI Video and Audio Decoder** is the card by the output.

But there is no /dev/video0 or anything close to that in /dev

This link: [http://www.mythtv.org/wiki/Tuner_Card](http://www.mythtv.org/wiki/Tuner_Card) says that my card CX23885 is supported under Gnu/Linux and works with MythTV. [it says all cards of CX2388x are supported]

The command: "**lsmod | grep tv**" gives me the below output.

tveeprom               23428  1 cx23885
i2c_core               36128  7 tda18271,tda8290,tda10048,cx23885,v4l2_common,tveeprom,nvidia

Now, what am i really missing here? please lemme know in very novice terms.

Thanks in advance, Rhonald

---

### Post by rhonaldmoses on 2009-01-18
also, dmesg give me the below output.

[   12.652752] cx23885 driver version 0.0.1 loaded
[   12.652807] cx23885 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.652958] CORE cx23885[0]: subsystem: 0070:71d3, board: Hauppauge WinTV-HVR1200 [card=7,autodetected]
[   12.708180] cx23885[0]: i2c bus 0 registered
[   12.708200] cx23885[0]: i2c bus 1 registered
[   12.708213] cx23885[0]: i2c bus 2 registered
[   12.734754] tveeprom 0-0050: Hauppauge model 71949, rev H2E9, serial# 5020405
[   12.734757] tveeprom 0-0050: MAC address is 00-0D-FE-4C-9A-F5
[   12.734759] tveeprom 0-0050: tuner model is Philips 18271_8295 (idx 149, type 54)
[   12.734761] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[   12.734763] tveeprom 0-0050: audio processor is CX23885 (idx 39)
[   12.734764] tveeprom 0-0050: decoder processor is CX23885 (idx 33)
[   12.734766] tveeprom 0-0050: has no radio
[   12.734767] cx23885[0]: hauppauge eeprom: model=71949
[   12.734770] cx23885[0]: cx23885 based dvb card

***Well, that's part of my output.***

---

### Post by tazthecat on 2009-04-12
I have the exact same problem, no /dev/video0.

I also have a HP pavillion elite

I hope some one can help me.

---

### Post by jaxson on 2009-04-16
I have a Leadtek WinFast PxDVR320 TV Card with the cx23885 chipset. I found that I couldn't get it going with mythtv or others that rely on the /dev/video0 or such. Try me-tv. It looks for the card accurately without looking for the device.
Also you may want to try the below link although it's for my card:
[http://tsihtd.wordpress.com/2008/10/26/leadtek-winfast-pxdvr3200h-tv-tuner/](http://tsihtd.wordpress.com/2008/10/26/leadtek-winfast-pxdvr3200h-tv-tuner/)

Try me-tv first though since the module drivers are getting standard with later releases.

---

