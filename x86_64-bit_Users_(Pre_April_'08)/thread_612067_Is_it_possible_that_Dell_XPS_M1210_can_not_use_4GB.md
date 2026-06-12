---
title: "Is it possible that Dell XPS M1210 can not use 4GB of RAM?"
date: 2007-11-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by strahl on 2007-11-13
Hi everyone :)

I need your help. I am simply not able to access the full 4GB of RAM on my M1210. The BIOS recognizes 4GB but also warns me that only 3.4GB will be available.

I understand that this is due to the PCI memory mapped into the working memory downwards from the 4 GB address.

I goggled a lot but only found users with the same problem and no one reporting to be successful. One guy even reported that the BIOS / mainboard is the limiting factor and it is not possible at all.

Also memtest86 from the Live CD tests only 3.4GB. And also the Dell Diagnostic CD is testing only up to CFA93000h = 3,482,071,584 bytes

I did also try the server kernel without success.

And compiling my own kernel didn't help either. As I couldn't find the CONFIG_HIGHMEM setting using "make menuconfig" I guess that this is not necessary anymore for kernel 2.6 and a Core2 Duo?

Any memory expanding insights are welcome :)

:) stefan

---

### Post by Bokonon on 2007-11-13
Sounds right.   I think there has been some discussion of the limitation at notebook forums.  Even though it is pretty cheap now, I decided to skip on that upgrade.

Here is a link to the [Dell Section]("http://www.notebookforums.com/forum71.html")

---

### Post by tighem on 2007-11-13
Not  sure on that particular model, but there are numerous chipsets that do indeed limit the memory available.

Not sure why you'd put a 64-bit processor in a machine and then hamper it that way, but that does appear to be the way it is.

---

