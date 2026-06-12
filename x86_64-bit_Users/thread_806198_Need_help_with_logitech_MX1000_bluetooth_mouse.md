---
title: "Need help with logitech MX1000 bluetooth mouse"
date: 2008-05-24
forum: x86 64-bit Users
---

### Post by chuugokujin on 2008-05-24
Hi,
I'm a noob and I just installed Ubuntu 8.04 64bit version.
My wireless mouse is not working under this version.
I opened the bluetooth manager, and the Bonded Device shows I have my Logitech MX1000 mouse connected. However, the mouse is actually not working. Can anyone help me with it? Thanks

---

### Post by John Jason Jordan on 2008-05-24
> **chuugokujin said:**
> Hi,
I'm a noob and I just installed Ubuntu 8.04 64bit version.
My wireless mouse is not working under this version.
I opened the bluetooth manager, and the Bonded Device shows I have my Logitech MX1000 mouse connected. However, the mouse is actually not working. Can anyone help me with it? Thanks
Here's what I do when my bluetooth mouse suddenly quits on me:

sudo hidd --search
Searching ...
        Connecting to device 00:0F:F6:6C:6C:DB

If that doesn't work, try:
sudo hidd --connect 00:0F:F6:6C:6C:DB

Note the address of the device above is the address of my mouse. Yours will be different.

Another tip is to install Blueman. It may be in Synaptic now. It wasn't when I installed it and I had to go out on the net and find it. Just google on "Blueman" and it should turn up. Once you have the .deb file downloaded open it with gdebi (Applications > Add / Remove).

---

### Post by chuugokujin on 2008-05-25
Thanks a lot, it works just after the command!

---

### Post by no1cares on 2008-05-26
i had the same problem.. started my own posts no one helped... google searched and found this page, sudo hidd --search works. thanks a lot

---

