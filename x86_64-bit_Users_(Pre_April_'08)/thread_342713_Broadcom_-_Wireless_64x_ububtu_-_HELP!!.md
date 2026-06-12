---
title: "Broadcom - Wireless 64x ububtu - HELP!!"
date: 2007-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rorey_breaker on 2007-01-20
Hello, 

I have a acer aspire 5101AWLMI:
AMD 64 2.0GHz.
ATI Radeon Express.
BroadCom 802.11b/g wireless Lan. 

I have installed edgy, and without performing any other operations attempted to install ndiswrapper and use a 64x windows driver. This I attempted by use of a HOW-To from the Ubuntu forums, this ran a script which unzipped and installed ndiswrapper, this it did successfully, when it came to installing the driver returned an error stating incompatible kernal.  After some forum surfing I found listings where a kernel upgrade was indeed successful, I have installed the latest Ubuntu kernel but this simply won't boot, when attempting to boot in recovery mode it stops just after loading the usb stuff.  I still have the previous generic Ubuntu kernel installed and operational.

My aim is to have a 64 bit Linux distribution which is functional and easy to use, preferably a Ubuntu flavor,  I need to have my broadcom wireless working, I am aware that this is supported under 32x but I wish to run a 86x OS. 

Thanks for any help you can give!!

---

### Post by teaker1s on 2007-01-20
follow the link in my signature:D 

secondly if your not happy removing the problem kernel then use synaptic and it will update grub for you provided you completely remove offending kernel and it's accompanying restricted modules

---

### Post by prince_niceguy on 2007-01-20
turn off your wireless using the switch on your computer and then reboot. it should work. i too had acer and was facing the same issue. 

after this is done. compile ndiswrapper rather than installing the .deb as it was not working on my comp. for compiling you will require build-essential package i think.

best of luck!!!

---

### Post by woopud on 2007-01-21
> **Rorey_breaker said:**
> Hello, 

I have a acer aspire 5101AWLMI:
AMD 64 2.0GHz.
ATI Radeon Express.
BroadCom 802.11b/g wireless Lan. 

I have installed edgy, and without performing any other operations attempted to install ndiswrapper and use a 64x windows driver. This I attempted by use of a HOW-To from the Ubuntu forums, this ran a script which unzipped and installed ndiswrapper, this it did successfully, when it came to installing the driver returned an error stating incompatible kernal.  After some forum surfing I found listings where a kernel upgrade was indeed successful, I have installed the latest Ubuntu kernel but this simply won't boot, when attempting to boot in recovery mode it stops just after loading the usb stuff.  I still have the previous generic Ubuntu kernel installed and operational.

My aim is to have a 64 bit Linux distribution which is functional and easy to use, preferably a Ubuntu flavor,  I need to have my broadcom wireless working, I am aware that this is supported under 32x but I wish to run a 86x OS. 

Thanks for any help you can give!!

Using the following link helped me get my broadcom 4306 working in ten minutes on my amd64 laptop running Edgy 64bit.  I too tried the ndiswrapper thing but could not get it to work, the fwcutter method is much easier to install and works !

Bert

---

### Post by methane on 2007-02-02
teaker,
I used the link in your signature, and it worked perfectly on a Dapper build.  Trying to upgrade to Edgy and then follow the instructions resulted in no joy.  I'm pretty sure that I'm able to follow the guide since I tried it once more in Dapper and got it to work again.  So, that's twice it's worked in Dapper, and zero for Edgy.
That guide is great.  Next I'm going to try the fw-cutter method, but that guide is not nearly as good as the like in your sig.  We'll see.

Regards,
Brad

AMD64, HP zv6000, broadcom.

---

