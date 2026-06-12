---
title: "lm-sensors problem"
date: 2005-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by minio on 2005-01-01
Hi, I installed lm-sensors (following the HOWTO from this forum), but all I can get from them is the size of my memory bank. I have MSI K8T Neo-fis2r (K8T800 chipset). Have anyone success with lm-sensors on this board (or on any board using 64-bit linux)?

output from "sensros"

eeprom-i2c-0-50
Adapter: SMBus Via Pro adapter at 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       512

output from "lsmod | grep i2c"

i2c_viapro              8076  0
i2c_sensor              3328  2 w83627hf,eeprom
i2c_core               25368  4 i2c_viapro,w83627hf,eeprom,i2c_sensor

---

### Post by ahyden on 2005-01-01
Hi, you need i2c_isa module, try sudo modprobe i2c_isa

If that works you can add it to /etc/modules to automatically load at bootup.

---

### Post by minio on 2005-01-01
It works!  :D  
Thank you

I already have this module in /etc/modules but i've never noticed it's not loaded  :oops:

---

