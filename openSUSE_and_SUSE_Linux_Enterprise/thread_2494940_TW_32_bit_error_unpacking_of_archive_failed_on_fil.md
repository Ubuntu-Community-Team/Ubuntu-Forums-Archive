---
title: "TW 32 bit: error: unpacking of archive failed on file /etc/ssl/engdef.d;65bb5a57: cpi"
date: 2024-02-01
forum: openSUSE and SUSE Linux Enterprise
---

### Post by maketopsite on 2024-02-01
```

zypper dup
...
(1093/1859) Installation of : openssl-3-3.1.4-2.1.noarch ........ [done]
error: unpacking of archive failed on file /etc/ssl/engdef.d;65bb5a57: cpio: File from package already exists as a directory in system
error: openssl-3-3.1.4-3.1.i586: install failed
error: openssl-3-3.1.4-2.1.i586: erase skipped
(1094/1859) Installation of : openssl-3-3.1.4-3.1.i586 ........ [error]
Installation of openssl-3-3.1.4-3.1.i586 failed :
error in update Subprocess failed. Error: RPM failed: Command exited with status 1.
Abort, retry, ignore ? [a/r/i] (a): r
error: unpacking of archive failed on file /etc/ssl/engdef.d;65bb5bdc: cpio: File from package already exists as a directory in system
error: openssl-3-3.1.4-3.1.i586: install failed
error: openssl-3-3.1.4-2.1.i586: erase skipped
(1094/1859) Installation of : openssl-3-3.1.4-3.1.i586 ........ [error]
Installation of openssl-3-3.1.4-3.1.i586 failed :
error in update Subprocess failed. Error: RPM failed: Command exited with status 1.
Abort, retry, ignore ? [a/r/i] (a): 

```

Any idea please ?

---

### Post by maketopsite on 2024-02-04
solved after choosing *[FONT=courier new]ignore[/FONT]* and re-run

```
zypper dup
```

---

