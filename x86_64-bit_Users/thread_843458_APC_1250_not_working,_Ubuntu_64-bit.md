---
title: "APC 1250 not working, Ubuntu 64-bit"
date: 2008-06-28
forum: x86 64-bit Users
---

### Post by rompstar420 on 2008-06-28
I have Ubuntu 8.04 64bit, running dual-AMD64 processors.

I have the APC SmartUPS 1250, I've connected the cables from the UPS to COM1, which is /dev/ttyS0

When I type this command, I get an error:
[B]
kodiak:/etc/apcupsd# apctest

2008-06-28 08:57:26 apctest 3.14.2 (15 September 2007) debian
Checking configuration ...
Attached to driver: apcsmart
sharenet.type = DISABLE
cable.type = CUSTOM_SMART

You are using a SMART cable type, so I'm entering SMART test mode
mode.type = APCSMART_UPS
Setting up the port ...
apctest FATAL ERROR in smartsetup.c at line 171
PANIC! Cannot communicate with UPS via serial port.
Please make sure the port specified on the DEVICE directive is correct,
and that your cable specification on the UPSCABLE directive is correct.
apctest error termination completed
kodiak:/etc/apcupsd# [/B]


Any Idea how to test/fix ?

[B]When I type:

kodiak:/etc/default# apcaccess
FATAL ERROR in apcaccess.c at line 41
tcp_open: cannot connect to server localhost on port 3551.
ERR=Connection refused
kodiak:/etc/default# [/B]

---

### Post by jimei on 2008-06-28
[Dunk SB]("http://www.gucci-sneaker.com/catalog_39.html")
[Air force one]("http://www.gucci-sneaker.com/catalog_42.html")

---

