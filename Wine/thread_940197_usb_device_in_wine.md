---
title: "usb device in wine"
date: 2008-10-06
forum: Wine
---

### Post by henning_1966 on 2008-10-06
Ok I have a prototype of a product that was designed to work in windows and the program runs fine in wine other than is is not finding it when plugged in to the usb port. I know that it uses a Fdti chip and have installed the drivers from there page. Oh by the way this uses a  FT232 USB-Serial port to a usb. I can see it when I check the dmesg and here is the last lines of that showing it connected.
[296736.196551] ftdi_sio 2-2:1.0: FTDI USB Serial Device converter detected
[296736.196576] /build/buildd/linux-2.6.24/drivers/usb/serial/ftdi_sio.c: Detected FT232RL
[296736.196666] usb 2-2: FTDI USB Serial Device converter now attached to ttyUSB0


 I just want this to connect to usb and be recognized by its windows program in wine
.

---

### Post by henning_1966 on 2008-10-07
ok well after some digging I have figured out I need to use d2xx dll instead of  ttyUSB0 how do I get it to do that

---

### Post by gatopeich on 2008-10-26
Hi, I kind of ported D2XX driver to Wine. Check it out here: [http://gatopeichs.pbwiki.com/#USBD2XXdriverforWine](http://gatopeichs.pbwiki.com/#USBD2XXdriverforWine)

---

