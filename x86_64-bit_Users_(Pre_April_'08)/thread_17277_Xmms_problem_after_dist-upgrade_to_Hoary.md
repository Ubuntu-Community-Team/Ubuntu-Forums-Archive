---
title: "Xmms problem after dist-upgrade to Hoary"
date: 2005-02-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by arnage on 2005-02-27
I know hoary is unstable and all but surely xmms should work
please help i love xmms, though rythembox is ok in the meantime.

Ive tried re-installing xmms thats work ok but when i try to run xmms
 i get 

libmikmod.so.2: cannot open shared object file: No such file or directory
Inconsistency detected by ld.so: ../sysdeps/generic/dl-tls.c: 72: _dl_next_tls_modid: Assertion `result <= _rtld_local._dl_tls_max_dtv_idx' failed!
 :confused: 

Any help is appreciated thanks.

Its probably something simple, usually is :) but my google searches didn't help any

---

### Post by syltty on 2005-02-27
sudo apt-get install libmikmod2

---

### Post by arnage on 2005-02-27
lovely that fixed it thanks,

---

### Post by cmsj on 2005-03-01
Might want to file that as a bug, xmms should have depended on that package.

---

### Post by Magneto on 2005-03-06
I had to uninstall xmms-mp4 also to get it working after installing libmikmod2 after the error changed to ```
libmp4v2.so.0: cannot open shared object file: No such file or directory
Inconsistency detected by ld.so: ../sysdeps/generic/dl-tls.c: 72: _dl_next_tls_modid: Assertion `result <= _rtld_local._dl_tls_max_dtv_idx' failed!

```

---

