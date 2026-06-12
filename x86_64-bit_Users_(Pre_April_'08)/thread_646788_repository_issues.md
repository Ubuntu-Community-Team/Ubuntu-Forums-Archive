---
title: "repository issues"
date: 2007-12-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ryan450 on 2007-12-21
hey guys, I've been using the 64 bit version of ubuntu for a long time with minimal problems. But now for some reason not all the repositories are working, and this is causing a major problem for me as now I can't download needed libraries for my programs,

Here's the error.

```
http://archive.ubuntu.com/ubuntu/dists/gutsy/Release: Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release: Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release: Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)

```

I've no idea how to fix this, if anyone can shed some light on this I'd much appreciate it.

---

### Post by mouseboyx on 2007-12-21
Try running ```
sudo apt-get update
``` and see if it makes a difference.

---

