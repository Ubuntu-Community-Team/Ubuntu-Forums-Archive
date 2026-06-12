---
title: "USB HDD wont show in fdisk -l to mount"
date: 2006-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by vikrant_me on 2006-11-20
My External USB HDD having a ntfs file system wont show in fdisk -l (i am looking to mount it) ....What do i do?

---

### Post by apsivam on 2006-11-20
are you using "fdisk -l" or "sudo fdisk -l" ?
is your USB HDD getting detected? to check do the following
remove your USB HDD
type the following in a Terminal Window
$ tail -f /var/log/message
now insert the USB HDD look at the Terminal Window you should see your HDD is getting detected

---

### Post by vikrant_me on 2006-11-20
i did do a sudo fdisk -l

vicky@vicky-desktop:/$ tail -f /var/log/message
tail: cannot open `/var/log/message' for reading: No such file or directory
tail: no files remaining

---

### Post by vikrant_me on 2006-11-20
Maybe this will help, im guessing this is my hdd:

Nov 20 04:56:28 vicky-desktop kernel: [10384.453654] usb 1-3: new full speed USB device using ohci_hcd and address 3
Nov 20 05:04:21 vicky-desktop kernel: [10856.833885] usb 1-3: USB disconnect, address 3

---

### Post by ridgeback on 2006-11-20
i am having the same problem

---

### Post by vikrant_me on 2006-11-20
wel anyone have a solution?

---

