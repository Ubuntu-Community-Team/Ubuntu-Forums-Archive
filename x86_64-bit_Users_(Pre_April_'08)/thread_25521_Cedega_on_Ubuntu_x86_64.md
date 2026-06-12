---
title: "Cedega on Ubuntu x86_64?"
date: 2005-04-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by KroniX on 2005-04-10
When trying to install Point2Play/Cedega I get this error:

```
package architecture (i386) does not match system (amd64)
```

On SuSe x86_64, the rpm i386 worked fine on the amd64 arch.

help!

---

### Post by Muchacho_Gasolino on 2005-04-10
sudo dpkg -install --force-architecture /path/to/file

also read [this](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#UPDATED_AMD64_pure64_w.2F32bit_libs_and_NO_32bit_chroot)

---

### Post by monchichi on 2005-04-12
try [these](http://ubuntuforums.org/archive/index.php/t-16143.html) scripts.. worked perfectly for me, but support Cedega 4.2 only... hopefully he'll update them for 4.3 soon?

---

