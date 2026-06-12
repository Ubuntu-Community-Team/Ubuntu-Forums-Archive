---
title: "nomachine nxserver/nxnode vulnerable on amd64"
date: 2008-05-14
forum: x86 64-bit Users
---

### Post by freelsjd on 2008-05-14
After I installed the new openssh security updates to 1:4.7p1-8ubuntu1.1, it became necessary to regenerate the public keys from nomachine's nxnode.  Unfortunately, the keys remain shown as vulnerable (compromised) no matter what I do for the amd64 version of Ubuntu.  For the 32-bit Ubuntu, 32-bit Debian, and 64-bit Debian amd64, the keys are OK.  I will cross post this to the security forum.

---

### Post by Nampla on 2008-05-14
i just installed the update on all my systems (all 64bit ubuntu) and had one small problem.  I had to go to the target machine and edit the /usr/NX/home/nx/.ssh/known_hosts on the target machine and remove the keys.  Then i was able to connect.

---

