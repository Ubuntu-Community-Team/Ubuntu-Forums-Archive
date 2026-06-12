---
title: "Rpm.tar.gz Tar.gz"
date: 2006-01-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by masingerz on 2006-01-18
Dear Forum:

I am doing an experiment in which I'm trying to install Ubuntu 64bits on an HP Proliant server DL385. I think breezy will work, but there are some HP tools for other linux distros in rpm.tar.gz and tar.gz: I need the HP tools to work on this system: Please advice: is there a way to run rpm.tar.gz and tar.gz in Ubuntu?

-masingerz

---

### Post by LordBug on 2006-01-19
RPM is meant more for Redhat, though there should be a tool to install them anyway (I don't know the name of it).  Might have to do some changes to make those work correctly.

.tar.gz = .tgz = Tarred and Gzip'd.  tar -vxzf (filename) will de-compress them.

---

### Post by dsierpin on 2006-01-20
alien will convert .rpm to .deb  

You should be able to get it with apt-get or synaptic

Good luck!

---

