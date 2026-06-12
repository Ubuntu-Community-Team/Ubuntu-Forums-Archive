---
title: "HP LJ3600 not printing (OK in 32 bit)"
date: 2007-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by kwacka on 2007-08-26
Feisty 7.04 (all updates) HP laserjet 3600, recognised by printer wizard, appears to be set up, jjob appears but is stopped by CUPS (I assume).

Works fine using 32bit LiveCD .

error.log has following:

CUPS-Add-Modify-Printer: Unauthorized

followed by several lines:

E [26/Aug/2007:20:28:25 +0300] cupsdAuthorize: Local authentication certificate not found!

(obviously time is different in each line.

I had tried logging on as root and installing printer, but same error.

Any suggestions, please?

---

### Post by John.Michael.Kane on 2007-08-26
> **kwacka said:**
> Feisty 7.04 (all updates) HP laserjet 3600, recognised by printer wizard, appears to be set up, jjob appears but is stopped by CUPS (I assume).

Works fine using 32bit LiveCD .

error.log has following:

CUPS-Add-Modify-Printer: Unauthorized

followed by several lines:

E [26/Aug/2007:20:28:25 +0300] cupsdAuthorize: Local authentication certificate not found!

(obviously time is different in each line.

I had tried logging on as root and installing printer, but same error.

Any suggestions, please?

Are you using the hpijs driver ?

Also looking over the info for that printer working it seems using the pxljr driver is recommended. you may want to try installing that driver.

---

### Post by kwacka on 2007-08-27
> **SD-Plissken said:**
> Are you using the hpijs driver ?

Also looking over the info for that printer working it seems using the pxljr driver is recommended. you may want to try installing that driver.

Confirm working fine with pxljr driver.

many thanks for assistance.

---

