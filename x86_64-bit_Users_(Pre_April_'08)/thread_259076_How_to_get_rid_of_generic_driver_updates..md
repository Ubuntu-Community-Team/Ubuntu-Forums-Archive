---
title: "How to get rid of generic driver updates."
date: 2006-09-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ausus on 2006-09-16
Hi all,

How can I get rid off generic drivers to be downloaded.

See attached *.png picture file.

Code:
[HTML]jochen@ubuntu:~$ uname -r
2.6.15-26-amd64-k8
[/HTML]

I'm not running generic drivers anymore.

Regards

---

### Post by Kilz on 2006-09-16
If you are now running another kernel like k8. Do a search for linux-image in synaptic there will be a generic package without a version. Uninstall it. But only if you are running another kernel.

---

### Post by Ausus on 2006-09-17
Hi Kilz,

Tnx, works like a charm.

Regards:-\"

---

