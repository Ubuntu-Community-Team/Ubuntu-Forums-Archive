---
title: "New NVidia driver causes blackout on login"
date: 2009-04-12
forum: x86 64-bit Users
---

### Post by tlxreed on 2009-04-12
Hi all,

I've got an HP dv9000 laptop running Hardy 8.10. I had some problems initially with getting the NVidia driver going but finally got 1.73 installed and all was great. Yesterday I was trying to upgrade to the 1.8 driver in a wireless cafe. I had deactivated the old one, activated the new one, then the network stalled before the upgrade had begun. 

Today I booted up the system and was back in a lower resolution, probably 800x600. I activated the 1.8 driver, installed and rebooted. When I login now the screen is black. I would think it's trying to activate a resolution that this monitor can't handle (native 1440x900).

What can I do to get back into a working resolution or deactivate the driver?

Thanks.

---

### Post by norwoods on 2009-04-12
when you boot up, press the Esc key when grub says Press 'Esc' to enter the menu
then press the down arrow to highlight the menu entry ending with (recovery mode)
press Enter
you should get the Recovery Menu
repeat pressing the down arrow to highlight the menu entry xfix Try to fix the X server
press Enter
reboot

---

