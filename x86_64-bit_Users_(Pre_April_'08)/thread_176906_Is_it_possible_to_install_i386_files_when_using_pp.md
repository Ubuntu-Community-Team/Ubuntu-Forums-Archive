---
title: "Is it possible to install i386 files when using ppc (powerbook g4)"
date: 2006-05-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by kybela on 2006-05-15
I just finished installing ubuntu on my powerbook and am now trying to install my favorite applications.  To install skype i downloaded the debian package..but then received the error message that the package architechture (i386) did not match the system, powepc.  There are more i386 files I'm interested in...is there any way for me to use them?

---

### Post by hentaidan on 2006-05-15
Short answer: no. Long answer is probably no as well :)

You need either PPC packages or source packages.

---

### Post by Ptero-4 on 2006-05-15
for apps (like skype) you may be able to use them with qemu (the binary level emulation mode, not the full blown system emulation one). All you need is to install with the correct --force option of dpkg. For codecs. You can't use qemu at all which means that you'll be able to use loose x86 apps but no x86 libraries or codecs.

---

### Post by kybela on 2006-05-16
Ok thanks for the information guys.

---

