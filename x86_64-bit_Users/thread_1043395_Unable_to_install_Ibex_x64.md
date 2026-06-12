---
title: "Unable to install Ibex x64"
date: 2009-01-18
forum: x86 64-bit Users
---

### Post by Ramirez22 on 2009-01-18
Hello all.
First sorry for my english, I'm French and my English level is very poor :(
I try on French forum to have help but nobody has idea. So I try another brain source :) .
I try to install Ibex x64 on my computer but something wrong occurs. I have the first screen (where I can choose langage and other options), but when I launch the LiveCD, an error appear.
More information about my computer:
CPU Intel Core2Duo 6300
Motherboard MSI P965 Neo (chipset P965 with RAID P-ATA disable)
DVD burner Samsung Writemaster SH-S183A (S-ATA)
Hard drive Maxtor & Samsung (nothing special)
Memory 5 Gb (2x512 and 2x2048 ) Corsair Value PC5300
Video card nVidia GeForce 7950GT

More information about the failure:
```

sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbute=DRIVER_SENSE,SUGGEST_ok
sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current]
end_request: I/O error, dev sr0, sector 1431620
Buffer I/O error on device sr0, logical block 357905

```

I don't know if sector and logical block are similar at each time.

If you have any idea, I am interresting. As you can see, I have 5 Gb of memory and I want to use it in totality (I use virtual machine for Windows, 2 partition at each times).

Thanks for help if possible :)

bye.

---

### Post by 73ckn797 on 2009-01-18
Would need to see the output of:
```
sudo lshw -c cpu
```Is it a 64 bit system?

---

### Post by 73ckn797 on 2009-01-18
You want to look for the line that states:
```
width: 32bit
``` or ```
width: 64bit
```

---

### Post by Ramirez22 on 2009-01-18
Hello 73ckn797 and thanks for this quick response.

I type your command on a tereminal and the system return :
```

  *-cpu:0                 
       description: CPU
       product: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
       vendor: Intel Corp.
[...]
       width: 64 bits
       clock: 266MHz
[...]

```
So I suppose my computer is 64 bits capable.

Any idea ?

---

### Post by 73ckn797 on 2009-01-18
> **Ramirez22 said:**
> Hello 73ckn797 and thanks for this quick response.

I type your command on a tereminal and the system return :
```

  *-cpu:0                 
       description: CPU
       product: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
       vendor: Intel Corp.
[...]
       width: 64 bits
       clock: 266MHz
[...]

```So I suppose my computer is 64 bits capable.

Any idea ?

Appears to be 64bit.

Did you check the iso download against the md5sum?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 

What is the name of the iso file you downloaded?

---

### Post by jespdj on 2009-01-18
All Intel Core 2 Duo processors are 64-bit, so this cannot be the problem.

The error sounds like there is something wrong with either the CD, the CD drive or your harddisk.

Check if the CD does not have any defects. Try burning it on a new CD, use a lower burning speed in your CD burning software.

---

### Post by 73ckn797 on 2009-01-18
> **jespdj said:**
> All Intel Core 2 Duo processors are 64-bit, so this cannot be the problem.

The error sounds like there is something wrong with either the CD, the CD drive or your harddisk.

Check if the CD does not have any defects. Try burning it on a new CD, use a lower burning speed in your CD burning software.

I am not familiar that much with Intel so that is my error. Even though my laptop has Intel.

Agreed on the disk issue(s).

---

### Post by Ramirez22 on 2009-01-21
Hello

Sorry for delay, I was out from home during long time.
The downloaded file is ubuntu-8.10-desktop-amd64.iso and I use the "check CD" option at the start menu. I do too a md5sum and that's OK. I download again the file aun burn it at office (different computer). I try to launch Ibex x64 and work fine on the Dell PC of my office. I will try this CD on my own computer after job and repport my experiencce later.

Thanks for the way to explore and for psychologic support :D

Bye

---

### Post by Ramirez22 on 2009-01-21
Unfortunatly, the test fail: same error.
I try all_generic_ide and -irqpoll options but nothing better occurs. I'm affraid that my DVD burner (SATA) is the source of the problem, and I haven't another CD/DVD reader...

:cry:

Bye

---

### Post by Sef on 2009-01-22
Do you have a spare 8 gb usb drive (thumb drive)?  IIt may work with that.

---

### Post by mikespug on 2009-01-22
I would suggest installing using the "[64-bit PC (AMD64) alternate install CD]("http://ubuntu.florianentreprise.com/intrepid/ubuntu-8.10-alternate-amd64.iso")".  It will provide you with the same installation options...minus the GUI interface.  (link is to a local French server)

---

### Post by Ramirez22 on 2009-01-26
Hello 
---> Sef: I have an USB disk, could you explain me how use it to put the install CD content in please ?

--> mikespug: unfortunatly, I already try with the alternate version, but without succes.


Thanks all for help :)

---

### Post by Ramirez22 on 2009-01-29
[humble mode off] I'M THE BEST [humble mode on]

Many thanks to all people who help me !
I can after many long night to install this damned x64 version ;)

In fact, I start with the LiveCD on another computer (at work) and make an usb disk with the Ibex utility. After returning at home, I try with the USB disk and that work perfectly.

All my material was detected... I'm happy :D.
Thanks again for support, everybody help me at his level (I hope you understand, I repeat that my english is not well ...:? )

Bye all

---

### Post by ejprinz on 2009-01-31
I have installed Ubuntu 8.10 on four i386 machines and had a similar error (Buffer I/O error on device sr0, logical block 178898 ) from the CD ROM drives, on every installable CD I tried. I ended up copying the installation CD onto a USB stick (1GB) with a (newer) CD drive which worked better but also has the Buffer I/O errors (in /var/log/kern.log). Surprisingly the CD/DVD ROM's which fail to read the CD's can read a DVD, so I'll try to burn the iso image onto a DVD instead and try that. To install the iso image onto a USB stick, boot into the LiveCD and choose the respective menu item. HTH, Erwin.

---

### Post by shadowhacker on 2009-02-02
I have had this exact problem on several machines with all versions of 8.10. I found that burning the CDs with Disc at Once instead of Track at Once solved it.

---

