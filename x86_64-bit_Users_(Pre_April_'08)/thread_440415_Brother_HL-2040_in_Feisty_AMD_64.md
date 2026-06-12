---
title: "Brother HL-2040 in Feisty AMD 64"
date: 2007-05-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by MicahCarrick on 2007-05-11
I just bought a Brother HL-2040 Laser printer. It detects the printer fine and using the "HL-2060" dirver it prints but clips a bit at the top. When I try to use the correct driver "HL2040 for CUPS" as discussed in the thread: [HOWTO: Set up your Brother 2030/70 Laser printer - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=123539") nothing happens. The print job gets to the queue but never gets to the printer (the light never blinks).

Anybody know why the right driver isn't working?

---

### Post by gerkin on 2007-07-06
Hi 

I have  a HL-2040 which works fine on the 32 bit version of Feisty (also Dapper-Edgy), running on AMD 64 hardware

some options are:

1. just use the HL-2060 driver and change to 600dpi etc.

2. check out the brother site and instructions:

here - [http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html)

            [http://solutions.brother.com/linux/sol/printer/linux/printsetlpr.html](http://solutions.brother.com/linux/sol/printer/linux/printsetlpr.html)

            [http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install5.html](http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install5.html)

more info here -    [http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-2040](http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-2040)

or you can download and install a HL2040 .ppd file from here:   [http://www.profv.de/brother/](http://www.profv.de/brother/)

....which is what I did, and it worked well but you have to change the first line (for Ubuntu) to:

code:   "cd /usr/share/ppd/openprinting/Brother/"

code:   "sudo wget -c http://www.profv.de/brother/Brother-HL-2040-hl1250.ppd"

hope this helps

---

### Post by gerkin on 2007-07-06
sorry duplicated my post :-)

---

