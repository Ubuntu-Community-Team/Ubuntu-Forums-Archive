---
title: "64 bit users i need your help please!!!"
date: 2006-08-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by codejunkie on 2006-08-06
i just got a new motherboard and processor, i finaly got dapper 32bit and 64bit to install on this motherboard, it's an ecs nforce3-a motherboard and athlon64 3400+ processor but im having the strangest problem with this new system, if i try to copy .gz files to or from my usb harddrive i always get this error when checking the archive
```
gzip: stdin: invalid compressed data--format violated
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
```
this only happens with the .gz archives other archive types like .tar, .rar, .zip, and .bz2 are not affected and it only happens when transfering them via usb2.0 im stumped if any one has any idea on whats causing this please help me[-o<  i've racked my brain on what could be causing this all day.](*,)

---

### Post by codejunkie on 2006-08-06
bump

---

### Post by jamesford on 2006-08-06
cant really help you, but i tried transfering a .gz from usb myself, on 64 bit, and there are no problems here..

---

### Post by John.Michael.Kane on 2006-08-06
codejunkie have you tried to mount the usb drive under 32bit ubuntu? or does these errors happen under both versions?

---

### Post by codejunkie on 2006-08-06
> **SD-Plissken said:**
> codejunkie have you tried to mount the usb drive under 32bit ubuntu? or does these errors happen under both versions?

it happens under both versions

---

### Post by John.Michael.Kane on 2006-08-06
codejunkie you say the errors only happen using usb2.0? can you try transfering them via usb1.1. it's a downgrade in transfer speed,however.It may help.

---

### Post by codejunkie on 2006-08-06
> **SD-Plissken said:**
> codejunkie you say the errors only happen using usb2.0? can you try transfering them via usb1.1. it's a downgrade in transfer speed,however.It may help.
it works fine transfering them via usb1.1 but it's dog slow, all other files seem to transfer correctly under usb2.0 just not .gz archives, im just wondering if this would be a bad motherboard, or the usb2.0 chip set just isn't supported under linux yet?.

---

### Post by John.Michael.Kane on 2006-08-06
codejunkie it might be that the chip's 2.0 code is not well supported though that is guess.however.If 1.1usb works albeit slowly then you may want to stick with that method. I would sugest trying to compile one of the newer kernels. Though this maybe a drastic mesure just to get 2.0 working.

---

### Post by codejunkie on 2006-08-06
> **SD-Plissken said:**
> codejunkie it might be that the chip's 2.0 code is not well supported though that is guess.however.If 1.1usb works albeit slowly then you may want to stick with that method. I would sugest trying to compile one of the newer kernels. Though this maybe a drastic mesure just to get 2.0 working.
i dugg around the forum, and found that if you enable the module ehci-hcd with ```
sudo modprobe -r ehci-hcd
```it will work with usb 2.0 enabled it slows it down greatly i think i'll try compiling the latest kernel to see if this helps any.

---

### Post by codejunkie on 2006-08-06
well i tried the latest kernel and it didn't change a thing.

---

### Post by John.Michael.Kane on 2006-08-06
codejunkie darn sorry to have had you compile all that and it not work. I wonder if you can manualy edit the file that handles the mounting of said devices. i never did this so it's a guess. it just seem odd that it mount's and reads fine under 1.1.

---

### Post by codejunkie on 2006-08-06
> **SD-Plissken said:**
> codejunkie darn sorry to have had you compile all that and it not work. I wonder if you can manualy edit the file that handles the mounting of said devices. i never did this so it's a guess. it just seem odd that it mount's and reads fine under 1.1.

yep it is strange, it mount's and reads files in usb 1.1, it works on all files except large tar.gz archives 100mb+ in usb2.0 mode could a faulty usb 2.0 cable cause something like this? it works good in 1.1 mode and on all other files in 2.0 mode for me to believe something is wrong with the board.

---

### Post by John.Michael.Kane on 2006-08-06
codejunkie last ditch effort would be to try it on a known working machine with 2.0. i'm not to sure about the cable it should be rated for 2.0. that may play a factor if it's not. if you really have to get the files off the drive i would leave it transfering over night.

---

