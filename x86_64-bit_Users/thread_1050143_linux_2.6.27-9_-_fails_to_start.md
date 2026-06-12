---
title: "linux 2.6.27-9 - fails to start"
date: 2009-01-25
forum: x86 64-bit Users
---

### Post by sepia-shots on 2009-01-25
I've had to revert to 2.6.24-14 as the newer kernel(s) fail to load with an error saying that the disk doesn't exist (intramfs image maybe?). Any ideas why this is an how I can move to a later, working, version?

Many thanks for any help

---

### Post by x22 on 2009-01-25
2.6.27... and 2.6.28... name your disk "sda" formerly "hda."
you should make adjustments to your bootloader

---

### Post by huntzire on 2009-01-25
When you compiled your newer kernel, did you make sure it included intramfs support? Id check back in a bout of ripping out all unnecessary stuff out of my kernel I found out for some reason when I Was compiling that it wasn't even checked to begin with and I got similar boot errors.

Let me know when you check your config options for the new kernel =)

---

### Post by sepia-shots on 2009-01-25
> **huntzire said:**
> When you compiled your newer kernel, did you make sure it included intramfs support? Id check back in a bout of ripping out all unnecessary stuff out of my kernel I found out for some reason when I Was compiling that it wasn't even checked to begin with and I got similar boot errors.

Let me know when you check your config options for the new kernel =)

Hi, I didn't compile it, it came down as a standard update.

---

