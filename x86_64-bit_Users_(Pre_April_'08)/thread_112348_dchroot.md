---
title: "dchroot"
date: 2006-01-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by ricka on 2006-01-04
Hi,

maybe someone could give mesome tips of how to uninstall dchroot + all apps i installed(mplayer xine) without no damage?
last time i deleted /chroot dir it deleted and my home folder aswell:(

thanks

---

### Post by Hallavej on 2006-01-04
[QUOTE=ricka]Hi,

maybe someone could give mesome tips of how to uninstall dchroot + all apps i installed(mplayer xine) without no damage?
last time i deleted /chroot dir it deleted and my home folder aswell:(

thanks[/QUOTE]
Warning I didnt try it myself but.
Did you mount /home into your /chroot? If so, umount it (and every thing else you mounted into the chroot). Then remove /chroot.

---

### Post by ricka on 2006-01-04
thanks, will try that:)

---

### Post by rplantz on 2006-01-04
Looking at /etc/fstab, I see:
```

# for chroot environment
/home /chroot/home none bind 0 0
/tmp /chroot/tmp none bind 0 0
/dev /chroot/dev none bind 0 0
/proc /chroot/proc proc defaults 0 0
/media/cdrom0 /chroot/media/cdrom0 none bind 0 0
/usr/share/fonts /chroot/usr/share/fonts none bind 0 0

```

I don't know a lot about fstab, and I haven't tried this. But perhaps you could delete (or comment out) these entries and reboot your system. If you try this, I would then look in my /chroot/ directory after the reboot to see if these directories exist.

Uh, I did the same thing -- deleted my home. I learned that simplebackup worked very well, at least this one time.  :-)

If you try this, please let us know if it works.

---

### Post by vivedekananda on 2006-01-16
rplantz it works well if you umount the /chroot/xxx directiories,
I only couldn't remove the /chroot/dev directory cause it was 'busy', but after reboot it should be fine

---

