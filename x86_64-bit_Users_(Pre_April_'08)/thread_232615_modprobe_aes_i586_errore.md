---
title: "modprobe aes_i586 errore"
date: 2006-08-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by cosmoshell on 2006-08-09
#modprobe aes_i586
FATAL: Module aes_i586 not found.

---

### Post by RAOF on 2006-08-09
Why are you trying to modprobe that?  It certainly won't exist here, and probably wouldn't work even if you copyied it from somewhere (i386 module, x86-64 kernel).

---

### Post by cosmoshell on 2006-08-09
im trying to encrypt my file system [https://help.ubuntu.com/community/EncryptedFilesystem](https://help.ubuntu.com/community/EncryptedFilesystem)

---

### Post by RAOF on 2006-08-09
Looks like you should be able to replace "aes_i586" with just "aes".  Try that.

---

