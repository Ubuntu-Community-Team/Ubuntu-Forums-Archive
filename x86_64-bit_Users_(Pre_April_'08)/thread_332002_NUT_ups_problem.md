---
title: "NUT ups problem"
date: 2007-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by t_ras on 2007-01-05
I have a Gamatronic UPS.
I installed NUT and configured it.
It seemed to work but it was getting wrong status.
I tried to reconnect it after disconnecting the cable and it started (!?!?)
which probably means the driver or tty was wrong.
How can I know which device (tty I guess) is my serial port connected to?

thanks

---

### Post by bronson on 2007-01-05
Because motherboard wiring is so nuts, the only way to know is to send data out each device and then see which port is tickled.  Do you have a modem with status lights or some other device to easily test that your serial port is behaving as it should?

Personally, I loathe serial.  Far too much of my life has been spent trying to figure out XON/XOFF, DCE vs. DTE, etc.  I've thrown away all my breakout boxes and gender benders and D-9 to D-15 to D-25 converters.  Now, when I need to make a serial device work, I just throw that device out and buy a newer USB-based version.  :)

Or, I suppose you could just buy a USB->Serial converter so you can easily check which device corresponds to which port.

---

### Post by t_ras on 2007-01-05
USB-serial converter...sounds like a good idea

> **bronson said:**
> Because motherboard wiring is so nuts, the only way to know is to send data out each device and then see which port is tickled.
How do I do it?

---

### Post by bronson on 2007-01-05
Get a modem, plug it into a port on the back of your motherboard.  Choose a device (i.e. /dev/ttyS0).  Run setserial to set it to the configuration your modem expects, then try talking to the modem.  Move the modem around until you find the port that device ttyS0 responds to.

How to talk to the port?  Usually I just run "echo ATDT > /dev/ttyS0" to write and "cat /dev/ttyS0" to read.  You might find a terminal program like minicom easier to use.

Generally ttyS0 == COM0 etc, so your motherboard manual might tell you how the serial ports arelaid out.  This is not always the case though.

Here's a ton more information:

[http://tldp.org/HOWTO/Serial-HOWTO-4.html#ss4.3](http://tldp.org/HOWTO/Serial-HOWTO-4.html#ss4.3)

Prepare for hurt but I hope you get lucky and get things working early.  Serial communication has never been easy!

---

### Post by t_ras on 2007-01-06
10x

---

