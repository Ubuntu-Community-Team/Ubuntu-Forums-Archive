---
title: "Linux drivers for Oki C3400N laser printer?"
date: 2007-12-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Axdrenalin on 2007-12-11
Based on my searches in this forum, the last inquiry for OKI laser drivers was sometime late October 2006. I'm relatively new to Ubuntu - been tinkering for a few months, and wanted to load my Oki C3400N printer up. When I bring up the printers under prefs and click "New Printer", Ubuntu goes out and finds my network printer with no problem at all - even lists it as a C3400N at the correct IP address. Trouble is, I see no included driver for that model, nor can I find one on the intarweb. Has anyone developed a compatible driver, or can anyone point me in the right direction to resolve this issue?

Thanks in advance!

Axdrenalin

---

### Post by kuja on 2007-12-12
According to [http://openprinting.org/printer_list.cgi?make=Okidata](http://openprinting.org/printer_list.cgi?make=Okidata), your printer is of no more use to you right now than being a large paperweight. 

Realistically speaking, you're probably better off getting something else than waiting for drivers that may or may not ever come. (And if you do, the approach that I would recommend would be to first lay down some printers within your budget that you think you might be interested in, then cross check each model agains the openprinting.org list - if it's not listed in the left column you probably don't want to go with it.)

Then again, you might want to try using the generic postscript driver first .... Maybe you'll be lucky, maybe that will actually work. Good luck dude.

---

### Post by kleeman on 2007-12-12
One other desperation move is to hunt through the driver disk that came with the printer for a ppd file (i.e. SOMENAME.ppd). It may be in the OS X section. Then copy this to your system and use it as a custom driver (There is an option Install Driver on the dialog after the gnome printer selection (yours was found by this right?)

Might work if you are (very) lucky...

---

### Post by Axdrenalin on 2007-12-12
Thank you all for your responses. I guess I'll have to pull one of my older inkjet printers off the shelf, buy some new cartridges and hook it up exclusively for use with my linux box.

Ax

---

### Post by andypeter on 2008-05-07
Try the Ubuntu instructions on this page:

[http://foo2hiperc.rkkda.com/INSTALL](http://foo2hiperc.rkkda.com/INSTALL)

It works even with color! :)

---

