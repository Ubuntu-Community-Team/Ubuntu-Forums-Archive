---
title: "[SOLVED] Where are the usb devices?"
date: 2008-09-14
forum: x86 64-bit Users
---

### Post by acidblue on 2008-09-14
I'm trying to get a list of my connected usb devics.
By doing this: cat /proc/bus/usb/devices
But that dosn't work, i get the 'no files or directory' message.
Just where are they listed?
Can anyone show me the light?


Basically i'm trying to do this:
[http://letsmakerobots.com/node/663](http://letsmakerobots.com/node/663)

---

### Post by cdtech on 2008-09-14
Try "lsusb", this will list all connected USB devices.....

**Update::.**
I can list mine using "cat /proc/bus/usb/devices"

---

### Post by acidblue on 2008-09-14
Thanks!
Thats just what i needed!

---

