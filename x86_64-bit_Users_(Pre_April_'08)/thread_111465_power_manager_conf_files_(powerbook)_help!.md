---
title: "power manager conf files (powerbook) help!"
date: 2006-01-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by shawn12345 on 2006-01-02
I'm looking for a place to run a command upon closing the lid, and a command 
upon opening the lid (aka going in and out of sleep). Sleep works fine, but I want to 
put my firewire drives to spin down when i close the lid, and wake them up when i open it.

/sbin/scsi-spin -d /dev/sda
/sbin/scsi-spin -u /dev/sda

aparently by reading the gnome faq, they didn't implement sleeping of drives for various reasons: [http://www.gnome.org/projects/gnome-power-manager/faq.html#whynobattery](http://www.gnome.org/projects/gnome-power-manager/faq.html#whynobattery)

reasons sound valid....but its not very useful for firewire drives.

on OSX when you sleep your powerbook your firewire drives spin down also. This can be duplicated with the scsitools scsi-spin command, but i dont know what file(s) to put pre and post commands.


thanks,
shawn

---

### Post by callipeo on 2006-01-03
If you have pbbuttonsd installed, you can put this script in /etc/power/scripts.d/:

------------------------------------------------------------------------------------------------------------
#!/bin/sh

# source configuration
. pmcs-config

case "$1" in
suspend)
  /sbin/scsi-spin -d /dev/sda
;;
resume)
  /sbin/scsi-spin -u /dev/sda
;;
esac
--------------------------------------------------------------------------------------------------------

and then create a link from it in /etc/power/event.d/. File /etc/power/scripts.d/skeleton contains a template for this kind of script.

---

### Post by shawn12345 on 2006-01-04
Thanks! I will try that...just what i was looking for.

-shawn

---

