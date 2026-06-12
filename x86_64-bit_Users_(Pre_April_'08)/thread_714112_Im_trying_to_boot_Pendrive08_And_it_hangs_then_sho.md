---
title: "Im trying to boot Pendrive08 And it hangs then shows _"
date: 2008-03-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lukasz Tarkowski on 2008-03-03
Dear Support
I am trying to install Pendrive08 on my 4GB Flash drive and whenever I boot I get this _ on top left corner and it doesn't boot
[http://www.pendrivelinux.com/2008/02/18/pendrivelinux-2008-install-from-linux/](http://www.pendrivelinux.com/2008/02/18/pendrivelinux-2008-install-from-linux/)

And yes I can boot from usb :) I got Ubuntu on external hdd

---

### Post by Kilz on 2008-03-03
> **Lukasz Tarkowski said:**
> Dear Support
I am trying to install Pendrive08 on my 4GB Flash drive and whenever I boot I get this _ on top left corner and it doesn't boot
[http://www.pendrivelinux.com/2008/02/18/pendrivelinux-2008-install-from-linux/](http://www.pendrivelinux.com/2008/02/18/pendrivelinux-2008-install-from-linux/)

And yes I can boot from usb :) I got Ubuntu on external hdd

Does it look at the pendrive during boot?

---

### Post by Lukasz Tarkowski on 2008-03-03
It just shows _ blinking and black screen
I think it might be looking
I dunno what I should edit to make it find?

---

### Post by Kilz on 2008-03-03
> **Lukasz Tarkowski said:**
> It just shows _ blinking and black screen
I think it might be looking
I dunno what I should edit to make it find?

Your bios, it must have the capability of looking at the usb drive on boot. 
Im sure your next post would say something like " But I run Ubuntu from a usb drive".
The thing is, it may not be booting from the usb drive but grub on the master boot record of a hard drive pointing to the usb drive. You could do the same thing, but it would only work on machines with grub installed and edited to include the pendrive install.

---

### Post by Lukasz Tarkowski on 2008-03-03
Nevermind the problem is solved
I create partitions For Linux on Windows Xp and then use it in Linux, cause I was doing it incorrectly on linux.  I created fat32 on Windows xp and its fine :)

---

