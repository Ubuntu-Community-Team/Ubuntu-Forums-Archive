---
title: "convert dmg to iso"
date: 2007-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Digitallysick on 2007-10-23
how do i convert a dmg to an iso that my mac will read? i hear that acetoneiso can do this, but its not 64bit, anyone have a program or way to do it?

---

### Post by bonestonne on 2007-10-23
.dmg is a standard Mac file format. double click in apple and it will auto-mount/open.

you cannot convert .dmg to .iso in order to mount in another OS though.

64bit Mac is not very widely used, so of course you might not have 64bit...thats reserved for Apple Servers, Mac Pros and MacBook Pros.

---

### Post by Digitallysick on 2007-10-23
i want to convert a dmn to an iso to boot on my powerbook. , i think i can burn it as UDF?

---

### Post by bonestonne on 2007-10-23
i don't think you can burn it like that, but if you open/uncompress it in apple, you may find the .iso....or, the .dmg could uncompress to an ISO...but there's no converting a .dmg file. it just doesn't work like that.

---

### Post by Digitallysick on 2007-10-23
im going to try this in wine, i know windows has apps to convert dmg to iso

[http://vu1tur.eu.org/tools/](http://vu1tur.eu.org/tools/)


or maybe transfer the dmg to the mac, and convert it to iso, transfer it back to linux and burn the iso (alot of work huh)

Open Disk Utility, convert the DMG file to a CD/DVD Master (it'll have the extention .cdr), change the extention to .iso, transfer it over to your PC



this all stems from the fact my powerbook g4 that was supposed to come with a dual layer burner , infact, it does not grr

---

### Post by bulletxt on 2007-10-24
download this file on linux:
[http://vu1tur.eu.org/tools/download.pl?dmg2img.tar.gz](http://vu1tur.eu.org/tools/download.pl?dmg2img.tar.gz)

extract, enter the dir and type: 

make
sudo make install


now type:

dmg2img -i image.img -o newimage.img

now you can mount it from root:
modprobe hfsplus
mount -t hfsplus -o loop newimage.img /folder_you_want

I'm not sure if you can burn directly the newimage.img, but at least you can mount it and get the files you need.
please note that AcetoneISO2 1.95 beta 1 will do all this for you in a nice graphical set but it's not for 64-bit. you must compile dmg2img and run make install to make AcetoneISO2 be compatible with 64-bit
cheers!

---

