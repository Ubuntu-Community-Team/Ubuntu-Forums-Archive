---
title: "help with uninstall / grub"
date: 2009-11-14
forum: x86 64-bit Users
---

### Post by thaddeusjon on 2009-11-14
I had installed unbuntu  9.1 within my Vista OS ( one of the ways they allow you to do so with Ubuntu ) and had decided I didn't want it on my laptop. I uninstalled the ubuntu but when i restart my laptop, the Grub startup still appears with ubuntu as an OS option. It's not there and I would like to get rid of this happening during start up. I have Vista 64 bit. Any way to get this off my laptop and have Vista boot up as normal? Thank You in advance.

---

### Post by lemming465 on 2009-11-15
Assuming you did a WUBI-style install (ubuntu filesystem stored as an NTFS object, boot manager is windows bootmgr), you can script the removal with Microsoft's command line "bcdedit.exe" tool.  But using a 3rd party tool like [EasyBCD]("http://neosmart.net/dl.php?id=1") will probably be less work.

---

