---
title: "Problem installing mplayer"
date: 2008-11-02
forum: x86 64-bit Users
---

### Post by jozmak on 2008-11-02
When I try to install mplayer on ibex amd64 by using synaptic, I get the following message. 

mplayer:
 Depends: libfaac0 (>=1.26) but it is not installable
 Depends: libmp3lame0 (>=3.98) but it is not installable
 Depends: libx264-59 (>=1:0.svn20080408) but it is not installable
 Depends: libxvidcore4 (>=1:1.0.0-0.0) but it is not installable
 Depends: mplayer-skins  but it is not installable

Any idea how to proceed_

Thanks,
jmak

---

### Post by sisco311 on 2008-11-02
make sure you have the multiverse repositories enabled.

go to Synaptic -> Settings -> Repositories and check the *Software restricted by copyright or legal issues (multiverse)* box

---

### Post by jozmak on 2008-11-02
Thanks,
Multiverse is enabled, but I've just noticed that the repository is not updating. When update, I get the following:

W: Failed to fetch http:/us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg  Unable to connect to  http:

W: Failed to fetch http:/us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_CA.bz2  Unable to connect to  http:

W: Failed to fetch http:/us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-amd64/Packages.gz  Unable to connect to  http:

W: Failed to fetch http:/us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz  Unable to connect to  http:

E: Some index files failed to download, they have been ignored, or old ones used instead.

It is the first time, I've come across with this kind of error. 

jozmak

---

