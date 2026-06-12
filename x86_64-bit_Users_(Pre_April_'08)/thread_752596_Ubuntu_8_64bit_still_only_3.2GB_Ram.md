---
title: "Ubuntu 8 64bit still only 3.2GB Ram"
date: 2008-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by ryank82 on 2008-04-11
So I was running Ubuntu 8.04 with 2GB ram and decided to upgrade to 4GB of ram as It has become so cheap. I like to have several apps and windows open. Anyways all the ram was not being recognized under Ubuntu 32bit so I did a erase and install with the Ubuntu 8.04 64bit version and the same amount of ram is still only showing up. What gives ?  I do have integrated intel graphics "shared memory" but even If I change it it from 8mb-256mb it makes no difference on what shows up in Ubuntu. 3.2GB is still what its showing. My bios reads 4GB and what ram is installed etc..  What is going on ?   Thanks for any help.

---

### Post by fjgaude on 2008-04-11
I don't think I can be of any help, for it seems some what have 4Gs see it all, as I do, and some don't. The common trait is the motherboard... I have a late model Gigabyte. What's yours?

---

### Post by ryank82 on 2008-04-11
> **fjgaude said:**
> I don't think I can be of any help, for it seems some what have 4Gs see it all, as I do, and some don't. The common trait is the motherboard... I have a late model Gigabyte. What's yours?

             To be honest I don't no off hand. Its a stock Dell Vostro 200 Mini "Core2Duo". Only thing I did was delete Windows Vista and install extra memory.   Thanks

---

### Post by Kilz on 2008-04-11
[Please read this link.]("http://ubuntuforums.org/showthread.php?t=746588")

---

### Post by ryank82 on 2008-04-11
> **Kilz said:**
> [Please read this link.]("http://ubuntuforums.org/showthread.php?t=746588")


              Sorry. I will wait till then. :(

---

### Post by Trindol on 2008-04-12
This might not be it, but what bios are you using? Update to the newest.I think the you are affected by the fix in bios 1.0.12.

---

### Post by jespdj on 2008-04-12
This is a common problem. There are a number of possibilities:
[LIST]
[*]**You don't have memory remapping enabled in the BIOS.** Look in the BIOS setup and see if you can enable memory remapping.
[*]**You have a graphics card which uses part of the main memory.** Especially computers with graphics integrated on the motherboard have this: the graphics card doesn't have its own RAM, but uses part of the main memory. You could buy a separate graphics card and disable the onboard graphics in the BIOS.
[*]**Your motherboard or BIOS doesn't properly support 4 GB or more RAM.** See if there's a newer version of the BIOS available and update the BIOS.
[/LIST]

---

### Post by felker2 on 2008-04-12
Please read this thread: [http://ubuntuforums.org/showthread.php?p=4684049](http://ubuntuforums.org/showthread.php?p=4684049)

So:

- uname -a to show the Linux version you're running 
- dmesg: first 15 lines
- BIOS-version
- BIOS memory hoisting / remapping, but probably not needed in a new system like the Vostro

HTH

---

### Post by ryank82 on 2008-04-12
Thanks. I will try all the above to see if anything works.

---

### Post by dcstar on 2008-04-12
> **ryank82 said:**
> Thanks. I will try all the above to see if anything works.

Or do a full BIOS reset to defaults to see if it will remap things to better accommodate the new RAM.

---

### Post by tamoneya on 2008-04-12
im not sure that setting the bios to defaults will help because typically memory remapping is disabled in the bios.

---

### Post by dcstar on 2008-04-12
> **tamoneya said:**
> im not sure that setting the bios to defaults will help because typically memory remapping is disabled in the bios.

Maybe, but possibly some BIOSs won't dynamically adjust their resource mappings when extra memory is installed - doing a reset might changes things (and it comes under the "What have you got to lose" category of things to try in this situation).

---

