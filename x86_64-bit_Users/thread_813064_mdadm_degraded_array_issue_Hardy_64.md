---
title: "mdadm degraded array issue Hardy 64"
date: 2008-05-30
forum: x86 64-bit Users
---

### Post by ASULutzy on 2008-05-30
Hey all, I recently had a disk fail in my software RAID 1. I can still boot to Windows, but if I choose to boot into Ubuntu it falls back to a busybox prompt. I've tried changing the root= from the current UUID to /dev/md0 with the same results.

I have a live-usb and am able to boot off that, but am not really 100% sure what I should actually do to enable Ubuntu to boot the degraded array until I can buy another hdd to replace and rebuild the array.

I tried mdadm --assemble /dev/md0 /dev/sdc1 and it said that /dev/sdc1 didn't have a valid superblock?

when I do cat /proc/partitions I see /dev/sdc1 but /dev/md0 isn't there. That's also why it falls to busybox, says /dev/md0 doesn't exist.

When I boot from live-usb I can see /dev/md0; it's a degraded array.

Please help, the last couple of days of only having Windows on my desktop (thank god for my Ubuntu laptop) have been a real torture.

Thanks so much!

edit: I could have sworn that I had this problem solved before, because when I initially built the RAID array I had to boot from degraded... Let me try and dig up my old post and maybe that will have the answer for me.

---

