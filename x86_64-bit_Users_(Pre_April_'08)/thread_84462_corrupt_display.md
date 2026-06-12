---
title: "corrupt display"
date: 2005-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by tadazmas on 2005-10-31
hi,
my machine
---------------
athlon 64 2800+
abit k8v - x
radeon 9200
ram 512 ddr
hdd smasung 80GB
     wd 20GB
OS ubuntu 5.10 64 bit
-----------------
if enyone can help me...
 i installed breezy badger 5.10 on my computer. And after instaliation it's fails to start. I see corrupt display (like overclocked video card). If i try start X in recovery mode i also saw corrupt display but i heard ubuntu welcome music playing.
 I'm not very experienced user, but i tryed to install ati driver : ati-driver-installer-8.18.8-x86_64.run
 but when i select ubuntu packages reseiv error what failed to built ubuntu packages.
 In some forrums i read what if i have via card, kernel must load via-agp.ko modules, but when i go 
ls /lib64/modules/2.5.12-9-amd64-generic/kernel/drivers/char/agp
 i saw only intel-agp.ko modules.. i'm not sure if it's ok
  same happens when i tryed to instal fedora 4, redht enterprise 4 WS, Desktop...

---

### Post by tadazmas on 2005-11-01
if someone has same problem:
installing ati newest drivers solve this freezing
thanks for nothing :)

---

