---
title: "mount flash drive"
date: 2007-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by kiev on 2007-05-27
In the amd64 version of kUbuntu - flash drive mount by default with option "nosync", and I am necessary with option "flush": where it to correct?  where is a configuration file? 
Thank you for an answer.

---

### Post by david_2001 on 2007-05-27
> **kiev said:**
> In the amd64 version of kUbuntu - flash drive mount by default with option "nosync", and I am necessary with option "flush": where it to correct?  where is a configuration file? 
Thank you for an answer.
This is not a good idea!  Take a look at [http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html](http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html).  I copied the URL from /etc/hal/fdi/policy/preferences.fdi, where the necessary change could be made if really desired.  In the meantime, just remembering to unmount the flash drive before removing it is all that is necessary.

---

### Post by kiev on 2007-05-27
"Sync option destroys flash" - I know it, However is necessary my option "flush" - is it closes flash drive after upload each file, instead of the each block as "sync", option flush is specially developed for flash drive. And with an option "nosync" - sometimes flash drive hangs.

---

### Post by david_2001 on 2007-05-28
> **kiev said:**
> "Sync option destroys flash" - I know it, However is necessary my option "flush" - is it closes flash drive after upload each file, instead of the each block as "sync", option flush is specially developed for flash drive. And with an option "nosync" - sometimes flash drive hangs.

Oops.  Ok, I'm no expert on hal so although the following works it is not sophisticated and I won't give a guarantee against undesired side-effects:

[LIST=1]
[*]Edit */usr/share/hal/fdi/policy/10osvendor/20-storage-methods.fdi*, go to line 179 and add the following (highlighted in bold):
> 
      <!-- allow these mount options for vfat -->
      <match key="volume.fstype" string="vfat">
        <match key="/org/freedesktop/Hal/devices/computer:system.kernel.name" string="Linux">
         ** <append key="volume.mount.valid_options" type="strlist">flush</append>**
          <append key="volume.mount.valid_options" type="strlist">utf8</append>

[*]EDIT: I originally wrote "Start gconf-editor, go to */system/storage/default_options/vfat* and add flush to the mount_options key." but now I notice that you're using kubuntu and I haven't got the slightest clue how to change default mount options in KDE!  Sometimes I just start things that I cannot finish.  Gah! :-(
[*]Reboot.
[*]Plug the flash drive in and check the mount options listed in /etc/mtab.
[/LIST]

---

### Post by kiev on 2007-05-28
Thank you!!! I edit /usr/share/hal/fdi/policy/10osvendor/20-storage-methods.fdi and now all works correctly! 
It is necessary to be sent in bugtrack amd64 version kubuntu, (in i386/686 version kubuntu it is so already done by default).

---

### Post by david_2001 on 2007-05-28
> **kiev said:**
> Thank you!!! I edit /usr/share/hal/fdi/policy/10osvendor/20-storage-methods.fdi and now all works correctly! 
It is necessary to be sent in bugtrack amd64 version kubuntu, (in i386/686 version kubuntu it is so already done by default).
Gosh, it's good to hear that it worked! :-)  (I was expecting something different!)

---

### Post by gsiliceo on 2008-01-01
SO, flush option will give me the same behavior as sync(instant file copying and not caching) but without damaging my flash drives?

---

