---
title: "E: spampd: post-installation script code error 4"
date: 2006-12-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by gostview on 2006-12-13
Hi all, I've got a problem with spamd.
I've installed it first, then tried to unistall with synaptic, but it return to me this error: 
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please help me, I try everything to remove this program from my ubuntu 6.10.

Thanx for all advise.

---

### Post by gostview on 2006-12-13
> **gostview said:**
> Hi all, I've got a problem with spamd.
I've installed it first, then tried to unistall with synaptic, but it return to me this error: 
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please help me, I try everything to remove this program from my ubuntu 6.10.

Thanx for all advise.

Try solution.

Replace in /etc/init.d/spampd
#!/bin/bash -e
 
instead of:
#!/bin/sh -e

done, it works.

Byez:D

---

### Post by carla on 2007-01-22
> **gostview said:**
> Try solution.

Replace in /etc/init.d/spampd
#!/bin/bash -e
 
instead of:
#!/bin/sh -e

done, it works.

Absolutely! This has been driving me nuts. *Thank you*--spampd go bye-bye properly. ):P

---

### Post by eudemus on 2007-05-14
Following another thread, I'd just deleted my /etc/init.d/spampd
.... in an attempt to solve the very same problem!

What should it have had in it? Any chance of the contents from someone?
Thanks

Eudemus

---

