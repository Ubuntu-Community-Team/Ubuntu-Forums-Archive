---
title: "cd/dvd rom not responding"
date: 2008-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by sri1833 on 2008-03-08
I migrated from Vista to Fiesty some time ago, but after the install, the cd rom does not respond. 

Any cd/dvd inserted is only recognized as a blank disc. I tried to install another version, thinking there must be something wrong with the driver, but no success. **The cd/dvd rom  just does not respond, even at the booting stage.** Therefore I don't know if the driver is gone, or the device itself has conked.

 I dont intend to hand my laptop to any service centers with their "We dont touch it if it doesn't have vista" rubbish, so please help.   



System specifications:
HP Pavilion dv2415 Notebook PC
1.8 Ghz AMD Turion 64x2 Dual Core Mobile technology TL-56
1024 mb RAM, 160 gb HDD
running on Ubuntu 7.04 fiesty

---

### Post by jan quark on 2008-03-09
can you please post the results of these terminal commands:

```
mount
```
```

cat /etc/fstab

```
```
sudo lshw
```

---

