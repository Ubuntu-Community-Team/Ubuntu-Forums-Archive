---
title: "modem question"
date: 2006-02-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by comsec10 on 2006-02-03
Hey there everyone.
Is there a modem that Ubuntu 5.10 Breezy Badger does find and install from installation of the amd64 O/S?

If so, which one?

Any info specific to the question would be greatly appreciated.

Thanks

CS10

---

### Post by towsonu2003 on 2006-02-03
if u are refering to a dial up (56k etc) modem, any modem that is connected tru a serial port is supposed to work in linux without hassle. smartlink softmodems also work nicely in ubuntu but you need driver configuration... and don't know how to find one. 

the modems that work out of the box are also called serial modems or hard modems. the ones that usually dont work or work after a great deal or time or effort (like my modem) are called soft modem or winmodem.

---

### Post by comsec10 on 2006-02-05
Thanks towsonu2003. 
Unfortunately, I am on dial-up as there is no broadband or dsl in my area yet.

I have a smartlink pci modem installed at present but no matter what I try to get it to work doesn't seem to work. I have gone thru linmodems.org for help and information, but that too seems unworkable. I know the modem works thru windows because I am dual booting and I could really use some direction. I am so tired of windows due to the fact that it is unstable and crashes most of the time.
Mobo: Asus VIA K8T800
modem: ALi SmartLink SmartPCI563 vendor: 10b9 device: 545a
kernel: 2.6.12-9-amd64-generic
dist: ubuntu 5.10 Breezy Badger

Thanks in advance for any help you can provide

CS10

---

### Post by towsonu2003 on 2006-02-05
attach your modemdata.txt here (as a file, not as text) and let's see if we can make sense of it.

---

### Post by comsec10 on 2006-02-06
here is the modemdata file. Thanks for the help.

GC10

---

### Post by towsonu2003 on 2006-02-06
> The SmartLink slamr driver supports this modem:
    10b9:545a  ALI545A SL1801
complemented by the SmartLink slmodemd.
which means the slmodem section of the wiki (2nd link in my signature; [https://wiki.ubuntu.com/DialupModemHowto#head-27c1595198125d81eb19201b131a3a91876e1ad4](https://wiki.ubuntu.com/DialupModemHowto#head-27c1595198125d81eb19201b131a3a91876e1ad4) ) should help you wuth this.

---

### Post by comsec10 on 2006-02-06
Thanks,
I'll give it a look and see what can be done.
I also appreciate the help.

I will post the results back here.

---

