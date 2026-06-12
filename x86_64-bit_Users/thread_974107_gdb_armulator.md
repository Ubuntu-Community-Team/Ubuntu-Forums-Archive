---
title: "gdb armulator"
date: 2008-11-07
forum: x86 64-bit Users
---

### Post by markxxx on 2008-11-07
Hello,

I'm trying to get gdb armulator to compile. When I type ./configure, I get the following errors:

Configuring for a x86_64-unknown-linux-gnu host.
Invalid configuration `x86_64-unknown-linux-gnu': machine `x86_64-unknown' not recognized
Invalid configuration `x86_64-unknown-linux-gnu': machine `x86_64-unknown' not recognized
Unrecognized host system name x86_64-unknown-linux-gnu.

Thanks, 
Mark

---

### Post by Yellow Pasque on 2008-11-07
It appears this page is applicable to you, right? [http://www.uclinux.org/pub/uClinux/utilities/armulator/](http://www.uclinux.org/pub/uClinux/utilities/armulator/)
It has specific instructions on configuring/building gdb.

---

### Post by markxxx on 2008-11-07
That's the page I was working from.

---

### Post by markxxx on 2008-11-07
I found a page with apparently newer info.

 [http://opensrc.sec.samsung.com/Getting_Familiar_with_uClinuxARM2_6.html](http://opensrc.sec.samsung.com/Getting_Familiar_with_uClinuxARM2_6.html)

I'll try it when I get time. If I can get this working, do you think it would be useful to try to make an apt-get package from it? If so, how would I go about doing that?

---

### Post by markxxx on 2008-11-09
I found a program called Skyeye which has an apt-get package already made, and is based on gdb armulator. It looks like it is significantly more polished than gdb armulator.

---

