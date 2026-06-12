---
title: "ibook sleep working anyone?"
date: 2005-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by zenlunatic on 2005-10-14
Does anyone use an ibook (600mhz 8mb video) and have sleep **and** resume working in Breezy?

---

### Post by Motomouse on 2005-10-14
sleep and resume, sure :) 
(ibook G4 12" 1 GHz) 

but on G3 600 Mhz perhaps no luck yet, sorry :???: 
[https://wiki.ubuntu.com/LaptopTestingTeam/Apple_iBookG3_12in_600Mhz](https://wiki.ubuntu.com/LaptopTestingTeam/Apple_iBookG3_12in_600Mhz)

(perhaps you want to run a test with the live-cd on your ibook, thats the way i used on mine)

---

### Post by Starman on 2005-10-14
Doesn't work for me either.

(iBook G3/500, dual usb)

The fix someone gave me to make it work in hoary doesn't work with breezy...:(

---

### Post by Xumbi on 2005-10-15
This worked for me on my G3 800MHz dual usb iBook:

[http://ubuntuforums.org/showpost.php?p=8682&postcount=2](http://ubuntuforums.org/showpost.php?p=8682&postcount=2)

Just replade /etc/init.d/dbus-1 with /etc/init.d/dbus

---

### Post by Knome_fan on 2005-10-16
There's a hughe bug report about this problem on G3 macs here:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=1940](http://bugzilla.ubuntu.com/show_bug.cgi?id=1940)

Afaik there are two workarounds for this problem right now.
The first is the one Xumbi linked to, which simply makes sure that hal is stoped before the computer sleeps and started again when it wakes up. The problem I had with this is however that some stuff that depends on dbus doesn't work anymore. For example I had the gnome-battery-monitor crash everytime I put my ibook to sleep.

There is however a second workaroun I found while searching the Suse bugzilla.
The problem seems to be that for some reason hal tries to poll the cdrom drive when waking up, doesn't get an answer and then simply hangs. Now the workaround is to simply tell hal not to poll the cdrom.

To do this you'll have to edit /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi

In it you'll find a section starting with ```
<!-- Handle drives with non-partitioned media  -->
    <match key="storage.no_partitions_hint" bool="true">
      <!-- optical drives -->
      <match key="storage.drive_type" string="cdrom">
        <merge key="storage.policy.mount_filesystem" type="string">auto</merge>
```

Now just put a new key telling hal not to probe the cdrom after this:
```
<merge key="storage.media_check_enabled" type="bool">false</merge>
```

Now restart hal and sleep and wake up should be working.

There is however one drawback, automounting of CDs doesn't work anymore. The best workaround for this problem I have found is to put the disk mounter applet on the panel and mount CDs by hand. Not ideal, but it works for me.

---

