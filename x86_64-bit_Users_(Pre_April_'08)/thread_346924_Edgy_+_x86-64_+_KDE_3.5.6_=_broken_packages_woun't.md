---
title: "Edgy + x86-64 + KDE 3.5.6 = broken packages woun't install"
date: 2007-01-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Xemanth on 2007-01-26
I installed few mins ago Ubuntu Edgy Server x86-64 to my Acer Aspire 5024wlmi laptop.
I did these: [http://kubuntu.org/announcements/kde-356.php](http://kubuntu.org/announcements/kde-356.php)

And hit 'sudo apt-get update && sudo apt-get install kde-core' and upgrade failed in the start to depency problems....

"kde-core can't be installed because it needs kdebase but it woun't be installed"
If I try to install pure kde, it fails again to even more depency errors.

Well I kinda solved that problem... Removed all KDE 3.5.6 stuff from sources.list and then installed kde-core, now apt-get installs 3.5.5 packages.

Does anybody else have this same problem?

---

### Post by koshcu on 2007-01-27
Do the update again. I just tried it and it works now but it did not last night.

---

### Post by kuja on 2007-01-28
I solved the problem with a hammer on Friday morning. The way I did so was to do "sudo aptitude install ....(and I listed every package that still needed upgrading here)"

Not pretty, but it got me on 3.5.6.

---

