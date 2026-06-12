---
title: "USB : differences between 32 and 64 bits ?"
date: 2007-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by rralijaona on 2007-02-07
Hello,

I'm using Ubuntu, and I've noticed that USB doens't behave the same way, if I launch it on a 32bit system (Intel P4), or on an AMD64.

Here are some tests I've done :
I've got several computers : 
- Intel P2 laptop
- Intel P4 Desktop computer
- AMD64 desktop computer
- another AMD64 desktop computer

I've booted each computer from a Daper 32bit Live CD, and installed the same programs on each of them.
Then, I launch a program which communicates with an USB instrument device.

On 32bit systems, everything work correctly ; I can communicate with my device : I can send command, and get an answer.

On AMD64, I cannot communicate, I cannot write anything to device.


All these tests have been launched exactly in the same conditions (same CD, and same programs), so I don't understand why it doesn't work on AMD64, even if I used a 32 bit based system.


Is there any known issue about USB on AMD64 systems?



Thank you in advance for all helps.

---

### Post by koshari on 2007-02-07
i doubt it will be a usb problem, more like the driver for your usb device, its possable that no one has written a 64 bit one yet, 

do you care to elaberate as what the music device is?

---

### Post by rralijaona on 2007-02-07
> **koshari said:**
> the driver for your usb device, its possable that no one has written a 64 bit one yet

Since I'm runing a 32bit Daper version of Ubuntu, I just need a 32bit driver, isn't it?


> **koshari said:**
> do you care to elaberate as what the music device is?
In fact, it's not a music device... but a digital scope. 
And I use the *usb_bulk_write* function (in [libusb]("http://libusb.sourceforge.net/")) to write to the scope.


I've read that a 64bit system is fully compatible with 32bit programs, if a 32bit kernel is installed on it.
I've booted my AMD64 from a Dapper, and Edgy live CD (both 32bit kernel).
But I didn't succeed to make a program (that works correctly on a 32bit system) work on them.

Is there any real compatiblility? or is it only marketing stuff?

---

### Post by rralijaona on 2007-02-09
I've launched more tests on other computers, and found out that the difference 32 / 64 bit was not the real cause of my problem ; the program refused to work on a 32bit computer.

The reason seems to be that the scope works correctly on some USB controllers, and doesn't work with others.


If you can help, have any idea about how to resolve this problem, how to make any communication work, on any USB controllers, you can get more details in [_this other post_]("http://ubuntuforums.org/showthread.php?p=2129116").

---

