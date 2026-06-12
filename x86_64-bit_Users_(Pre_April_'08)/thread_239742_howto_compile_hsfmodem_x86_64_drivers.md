---
title: "howto compile hsfmodem x86_64 drivers?"
date: 2006-08-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by ville123 on 2006-08-19
im having trouble compiling hsfmodem-7.47.00.02x86_64 drivers
after i type "make install" i get errors... has anyone compiled these driver before? i surely need some advice!

---

### Post by Roddles on 2008-01-29
Hi there

Its a pretty simple process, just make sure your build environment is ready by:

sudo apt-get install build-essential

then, simply follow the install instructions that came with the driver.

sudo make install 

I think there is a newer version of the 64 drivers available now, so i would google for the latest version of the Tar file.

hope thiks help

Cheers

Rod.

---

### Post by Roddles on 2008-01-29
Just an update - here's the link to the latest driver to date for 64 bit HSF modem ...

[http://linux.dell.com/files/ubuntu/modem-drivers/hsf/hsfmodem-7.60.00.18x86_64oem.tar.gz](http://linux.dell.com/files/ubuntu/modem-drivers/hsf/hsfmodem-7.60.00.18x86_64oem.tar.gz)

Cheers

Rod.

---

