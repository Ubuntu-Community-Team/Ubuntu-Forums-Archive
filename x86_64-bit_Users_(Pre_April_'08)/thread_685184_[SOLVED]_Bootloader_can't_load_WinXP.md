---
title: "[SOLVED] Bootloader can't load WinXP"
date: 2008-02-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by jomasecu on 2008-02-01
I have had Windows XP Pro on here for quite a while on a SATA drive. Just installed Ubuntu to my Primary Master IDE drive, and Ubunto loads up fine, but if I choose Windows form the bootloader I get "Starting up ..." and it sits there for a couple minutes then reboots. I can get into Windows fine if I go into the BIOS and switch the boot priority, but I'd like to do it with a bootloader, for obvious reasons. Any ideas?

---

### Post by mbrush on 2008-02-01
I believe Windos has to be on the first partition.

So to linux 'sda1' or grub 'hd0,0'

There is a way to trick windows by using grub to swap the names or something

[http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html#SEC21](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html#SEC21)

Windos just assumes you have installed it on the first partition on the first disk i guess.

Good Luck

---

### Post by logos34 on 2008-02-01
mbrush is referring to ['map' commands]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk") in the windows grub entry...if ubuntu didn't add them automatically during install you can't boot windows on a second hard disk.

Post your windows stanza from /boot/grub/menu.lst

---

### Post by jomasecu on 2008-02-02
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```

---

### Post by logos34 on 2008-02-02
Well, it included the map lines, but may be order of the drives has changed (you have at least three I can tell).

Try changing to 

> title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)

If that doesn't work, post your fdisk and map files, and tell me the order in which the drives are listed now in the Bios hard disk boot priority.


[B]sudo fdisk -l

cat /boot/grub/device.map[/B]

---

### Post by jomasecu on 2008-02-02
That did it. Thanks. :)

---

### Post by logos34 on 2008-02-02
ok. Mark as 'solved' in 'thread tools'

---

