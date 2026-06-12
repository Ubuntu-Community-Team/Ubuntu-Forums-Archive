---
title: "Running Astronomy Apps"
date: 2008-01-17
forum: Wine
---

### Post by Greg Mueller on 2008-01-17
I need to try to find help on this.
I'm trying to run an Astronomy app under Wine. It's called Maxim DL/CCD

The way it's supposed to work is when you plug in your ccd camera the program recognizes it and gives you options for connecting to it. Since this particular camera is USB, Maxim should "sense" that. But it doesn't seem to know when I plug in the camera. 

In XP it makes a kadunk noise and the option appears in the "Connect To" box.

When I plug in the camera under Ubuntu/Wine nothing happens 

I can see the camera in the Device Manager under
82371AB/EB/MB PIIX4 USB

I'm really close to being able to use this app. I think this might be the last hurdle.

---

### Post by hikaricore on 2008-01-17
Are you sure that the device is actually supported by/has drivers for Linux?

Post the output of:

> dmesg

From shortly after plugging in the usb connection.

If the device do not function properly under Linux, then it will not function properly /w WINE.
You should also be aware that WINE may have trouble with USB related software.

---

### Post by Greg Mueller on 2008-01-17
I'm a newbee so I don't know what you mean by "dmesg"
sorry

---

### Post by Greg Mueller on 2008-01-17
Here are some drivers that are from the camera manufacturer.
Are these the right kind to work?

[http://www.fli-cam.com/FLIsupport/java_software.htm](http://www.fli-cam.com/FLIsupport/java_software.htm)

---

