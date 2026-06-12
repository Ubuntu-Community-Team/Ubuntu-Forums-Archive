---
title: "Hardy hangs on shutdown"
date: 2008-10-25
forum: x86 64-bit Users
---

### Post by mindless1973 on 2008-10-25
Hi,

I recently upgraded from Gutsy to Hardy. In Gutsy, everything worked fine, so I was quite surprised that my PC won't shutdown properly after the upgrade to Hardy.

I use a Asus Pundit-P1 (AMD Athlon single core processor, nVidia chipset incl. graphic). No wireless as this is a desktop PC, ACPI is enabled in the BIOS.

My BIOS is the latest available on the Asus website (however, it is already quite old as Asus seems to stopped providing updates for this specific board).

When I try to shutdown (regardles if I use the GNOME button or the shutdown -h now command), the shutdown process stops after bringing a bunch of debugging information from network manager and finally:

> 
NetworkManager: nm_dbus_signal_device_status_change: assertion `cbdata->data->dbus_connection` failed
[  242.358884]   CIFS VFS: server not responding
[  242.358919]   CIFS VFS: No response for cmd 50 mid 81


at this point it hangs until I press the power-off button for some seconds. 

BTW: When I try to reboot, I experience exactly the same problem.

After some investigations here in the forum, I already did the following things:

added acpi=force to the /boot/grub/menu.lst file
-- no success
added apm poweroff=1 to the /etc/modules file and 
added apm=power_off to the /boot/grub/menu.lst file
-- again no success

What else could I try to make shutdown and reboot work?

Any help appreciated,

bye
me.

---

### Post by mikewhatever on 2008-10-25
I don't know how to fix it, but what if you install wicd instead gnome's nm. Wicd has at least the same functionalities, and during it's installation, gnome's nm gets removed, thus, hopefully, eliminating the source of the problem.
As a backup strategy, it would be a good idea to download network-manager and network-manager-gnome packages locally, so that you might be able to reinstall them easily, should you decide to.
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)
[http://packages.ubuntu.com/hardy/network-manager](http://packages.ubuntu.com/hardy/network-manager)
[http://packages.ubuntu.com/hardy/network-manager-gnome](http://packages.ubuntu.com/hardy/network-manager-gnome)

By the was, why is this in the x64 section?

---

