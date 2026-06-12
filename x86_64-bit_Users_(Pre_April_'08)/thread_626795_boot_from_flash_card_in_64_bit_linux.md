---
title: "boot from flash card in 64 bit linux"
date: 2007-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by troxy18 on 2007-11-29
I have a new Thinkpad T61 with a core 2 duo and a built in SD card slot.  is it possible to install Ubuntu 7.10 to a large capacity flash card and have the operating system boot from that?  The drive is extremely fast when putting stuff on and off of it.  Would it boot and run faster than with a conventional spinning hard drive?

What about battery life?

What changes would I need to make to grub or anything else to get it to work right?

---

### Post by tighem on 2007-11-29
It should be possible if your system can boot off the card. Best bet is to remove the internal hard drive and run the live CD - if it shows up as a disk it should work.

You also might want to check out pendrivelinux.com.

---

### Post by Radon on 2007-11-29
I've installed Linux on Compact Flash cards connected by IDE cable for a silent PC project I once had.  Here's a [Wikipedia image]("http://upload.wikimedia.org/wikipedia/en/f/f7/CompactFlash_IDE_Adaptor.jpeg") of something similar.  CF cards have the ATA controller onboard, unlike SD cards, so YMMV.  Good Luck!

---

### Post by dptxp on 2007-11-30
You have to make sure that write cycles to Flash are not very high, unlike
hard disks, the no. of write cycles a flash can take is much less.

---

### Post by go_beep_yourself on 2007-11-30
You may expierence way too much trouble with 64 bit. In that case, it's best to switch back to 32 bit Ubuntu.

---

### Post by njparton on 2007-11-30
I tried booting from a CF card (using a CF to IDE adapter) with both ubuntu and xubuntu and was seriously underwhelmed by the performance.

It was sooooo slow I resurrected an old ATA66 IDE drive instead.

Booting from flash media is only worth it with a small distro such as DSL, freenas or openfiler.

---

### Post by Radon on 2007-11-30
I had a Sandisk Ultra II CF card that I use in my Canon DSLR.  It's rated speeds are 10MB/s read and 9MB/s write.  It's good enough :)  You can get 20/20 MB/s r/w CF cards at reasonable prices.

---

### Post by njparton on 2007-11-30
The CF card I had was a sandisk ultra III and performance was rubbish, even when I tested openfiler.

I'd really like to get it to work as the hard disk I'm now using to boot is using the remaining space in my case preventing me moving to raid 5.

---

### Post by crjackson on 2007-11-30
> **go_beep_yourself said:**
> You may expierence way too much trouble with 64 bit. In that case, it's best to switch back to 32 bit Ubuntu.

Not that I know anything about this, but I'm wondering why it would be any easier with 32-bit as compared to 64-bit?

---

### Post by dptxp on 2007-12-01
> **crjackson said:**
> Not that I know anything about this, but I'm wondering why it would be any easier with 32-bit as compared to 64-bit?

When you boot from CD or FLASH it is best to use OS like Knoppix that can be loaded to RAM. Booting
can take a bit of time (CD to RAM), but with 1 GB or more RAM Knoppix CD can be loaded.
Running from RAM, the system will run very fast.
I have not checked if Knoppix can be booted from flash and loaded to RAM.
Puppy Linux needs just 128 MB RAM.

---

