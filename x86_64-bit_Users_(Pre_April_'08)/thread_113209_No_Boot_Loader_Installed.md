---
title: "No Boot Loader Installed"
date: 2006-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by CountChocula on 2006-01-05
Hi I am new to linux so please pardon my ignorance if this does not make sense.

Im doing an install on a beige g3 and I get to where it says "no boot loader installed you will need to boot manually with the /boot/vmilinux kernal on part
/dev/hda6 and root=/dev/hda6 passed as kernal argument"....So....I know im supposed to copy my boot to the hfs system folder..... so this is the command lines I have written and then I get this error (see below) device or resource busy? does anybody know what I should do....

here is what i typed.-

cd /target
mkdir hfs
mount /dev/hda6 hfs -t hfs

this is the message I get-

mount:mounting /dev/hda6 on /target/hfs failed: device or resource busy.

I get the same message for hfs and for hfs plus

---

### Post by jdp on 2006-01-07
Have you checked some of the 5.10 update info I give in my [How-To on AppleFritter](http://www.applefritter.com/node/8936)?  Which version of Ubuntu are you installing?

---

### Post by CountChocula on 2006-01-07
im trying your site now....I think it will help...I will keep you posted...thanks a tonne man....

---

