---
title: "[SOLVED] EPSON CX9400FAX - Xsane"
date: 2008-07-01
forum: x86 64-bit Users
---

### Post by pm124493 on 2008-07-01
I recently purchased the EPSON CX9400FAX with a laptop. It is an All-in-One type printer, fax, scan and copy device. UBUNTU 8.04 discovered the printer and auto configured with no problems. However; xsane would not detect the scanner function. 

I did some research and found the following needed to be installed before xsane would detect the device.

sudo apt-get install libsane-extras

Once I installed the deb package and re-ran xsane, it auto detected the scanner with no problems.

This is a relative new device and I was impressed that I was able to get it working. Up until today I was only using HP devices, because of their Linux support. It is good to see we have options. Thanks to the CUPS and Xsane developers and hopefully EPSON for their support.

This device was $49 with any PC or laptop purchase. 

Posted in case others purchase this device.

---

