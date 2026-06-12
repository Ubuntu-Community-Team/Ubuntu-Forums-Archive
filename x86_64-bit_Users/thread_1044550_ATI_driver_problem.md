---
title: "ATI driver problem"
date: 2009-01-19
forum: x86 64-bit Users
---

### Post by Chesnut on 2009-01-19
Hello. I am using Ubuntu 8.10 and have an ATI Radeon 9600 se video card. I recently installed ATI drivers and did "aticonfig --initial -f --input=/etc/X11/xorg.conf --output=/etc/X11/xorg.conf" command.
After reboot, I tried if it works and typed in cosole: fglrxinfo - This is what it gave me as an answer:
```

root@Tarvo-PC:/home/tarvo# fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
```

Any help would be appreciated.

---

### Post by Chesnut on 2009-01-20
Hello. I seem to have fixed the problem. It just started working after 1 more restart.
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.1.8087 Release

```

---

### Post by soxs on 2009-01-20
Did you resatrt your PC after you installed the driver or just restart X

---

### Post by Chesnut on 2009-01-20
I restarted the PC.

---

### Post by soxs on 2009-01-20
So, you got about an real strange error. I'd suggest to give feedback, there is an unofficial bugtracker for fglrx, there should be a link at the bottom of the fglrx dl page at amd.com

---

