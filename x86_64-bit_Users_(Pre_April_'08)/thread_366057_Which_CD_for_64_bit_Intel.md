---
title: "Which CD for 64 bit Intel ?"
date: 2007-02-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by jbt on 2007-02-20
Hi,

Which CD set do I need to install on an Intel DG965SS motherboard with Pentium Core2Duo ?

There only seems to be a choice of regular x86 or AMD 64 bit.

Thanks
JohnT

---

### Post by John.Michael.Kane on 2007-02-20
Your  Core2Duo runs EM64T. with this in mind you can run the 64bit iso's linked below.

Desktop Live CD: This cd will allow you test you setup to make sure all is functioning. as well as allow you to install the os. 
**Link->**[For computers based on the AMD64 or EM64T architecture]("http://releases.ubuntu.com/edgy/ubuntu-6.10-desktop-amd64.iso")

Alternate text mode install CD: Is a direct to hard install.
**Link->**[For computers based on the AMD64 or EM64T]("http://releases.ubuntu.com/edgy/ubuntu-6.10-alternate-amd64.iso")

---

### Post by jbt on 2007-02-21
Thanks.

It would be helpful if this was included in the CD help information.
e.g. "Supports EMT64T, such as the Intel 965 motherboards" (or whatever is correct)

While I am an experienced Linux user, I'm not familiar 64 bit architecture.

I have been trying to get linux installed on this machine for a number of weeks,
and this is the first time it has been referred to as EM64T.


Cheers
JohnT

---

### Post by jbt on 2007-02-21
OK,
I've tried the 64 bit Desktop CD (ubuntu-6.10-desktop-amd64.iso) now.

It does manage to boot the CD, and seems to be able to load linux when I select an option from the main install menu, but busybox dumps me at a shell prompt with the error:

/bin/sh: can't access tty; job control turned off

Should I go to a different forum with this ?

---

### Post by John.Michael.Kane on 2007-02-21
Can we have your full system spec's?

Also a lookup of this error gives many diffrent explaintion,and reasons for it happening.

---

### Post by jbt on 2007-02-21
The details as follows:

Intel Desktop Board DG965SS with Core 2 Duo processor
([http://www.intel.com/products/motherboard/dg965ss/index.htm](http://www.intel.com/products/motherboard/dg965ss/index.htm))

1GB 667MHz DDR2 Non-ECC CL5 DIMM

Seagate 80GB Serial ATA HD

Samsung DVD RW
([http://www.samsungoms-europe.com/samsung.php?section=product&id=Writemaster%20TS-H552B](http://www.samsungoms-europe.com/samsung.php?section=product&id=Writemaster%20TS-H552B))

Thats it - video/network are all on the motherboard

Thanks
JohnT

---

### Post by John.Michael.Kane on 2007-02-21
If you can get a hold of the alternate cd,and try that. it's text mode thus direct to hard drive install. When the disk loads before you hit enter press F4,and select your proper resolution then press enter. 

note you can give the F4 test with the livecd as well to see if the helps with the boot issue.

From looking around the forum there seems to be an issue with some folks hardware running the ubuntu edgy livecd it may or may not be hardware related.

---

### Post by jbt on 2007-02-22
OK, I'll give it a go.

Have to wait a few days, as I've run out of CD's now :-(

Thanks
JohnT

---

