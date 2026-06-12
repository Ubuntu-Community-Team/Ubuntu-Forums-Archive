---
title: "Gamepad hates jscalibrator, wine, ePSXe, Jaunty, and the World."
date: 2009-08-25
forum: x86 64-bit Users
---

### Post by vanwaros on 2009-08-25
I'm attempting to get a gamepad to work in Jaunty, but things just haven't been working out for me. I've attempted to use jscalibrator, but if I try hitting a button or moving a stick nothing updates in the program's preview. I suspect jscalibrator is able to see the device since the window's title clearly says the name of my gamepad. By default, it is looking at /dev/input/js0. I've made an attempt to calibrate the device, but have not saved any changes since nothing started working.

[IMG]http://i32.tinypic.com/5eweg1.png[/IMG]

I only attempted to use jscalibrator when a program I was using through Wine (ePSXe) wasn't able to map buttons to the gamepad. Typically, the user would click a button to use on the dialog, then hit a button on the gamepad to match the two up; instead the game immediately attaches J1_UP to it. It's like some phantom device is rapidly pressing that button.
[B]
[IMG]http://i31.tinypic.com/qx1bhf.png[/IMG]

[/B]Any suggestions on what I should do from here? I've already tried several gamepads without success. I've also done some searching through these forums and elsewhere, but I've come up with nothing. Any advice would be appreciated.[B]

uname -a:[/B]
Linux winterfell 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

**dmesg:**
[ 1954.744012] usb 3-1: new low speed USB device using uhci_hcd and address 3
[ 1954.921091] usb 3-1: configuration #1 chosen from 1 choice
[ 1954.946079] input: Gamtec.,Ltd SmartJoy PLUS Adapter as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input8
[ 1954.972198] generic-usb 0003:0925:0005.0005: input,hidraw3: USB HID v1.00 Joystick [Gamtec.,Ltd SmartJoy PLUS Adapter] on usb-0000:00:1a.0-1/input0
[B]
lsusb: [note: the gamepad adapter is "Lakeview Research"][/B]
Bus 002 Device 002: ID 03f0:4007 Hewlett-Packard [ed- CD/DVD Drive]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 045e:0047 Microsoft Corp. IntelliMouse Explorer 3.0
Bus 007 Device 002: ID 045e:00dd Microsoft Corp. [ed- Keyboard]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 090c:6000 Feiya Technology Corp. [ed- USB drive]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0925:0005 Lakeview Research [ed- Smartjoy Adapter]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**Miscellaneous hints:**
-This adapter worked fine under Dapper on an older computer.
-I am attempting to use this adapter through Wine (1.1.28) in ePSXe (1.7.0). I have no other noticible issues with wine or ePSXe.
-Changing gamepads (to a 360 gamepad, or to yet another gamepad) does not change the odd behavior of both ePSXe or jscalibrator.

---

### Post by vanwaros on 2009-08-25
What a mess to fix. I'd originally thought the key listed at [http://wiki.winehq.org/UsefulRegistryKeys ]("http://wiki.winehq.org/UsefulRegistryKeys")meant the name and value of the key, but it turns out the entire thing is just the name of the key (with a blank value).:KS

Successful key listed below, in case anyone runs into the same problem:
```
[HKEY_CURRENT_USER\Software\Wine\DirectInput] 
""Gamtec.,Ltd SmartJoy PLUS Adapter"="X,Y,Rz,Slider1,POV1""=""
```I'm going to have to play with the x,y,rz,slider1,pov1, but for now things work well. Oddly enough, the PS2 gamepad only works in analog mode.

Also, jscalibrator was useless in this case.

---

