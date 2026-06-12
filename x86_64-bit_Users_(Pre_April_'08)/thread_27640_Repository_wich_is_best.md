---
title: "Repository wich is best??"
date: 2005-04-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by jaquesdp on 2005-04-17
Hi there..

I need to get win32 codecs to play wmv files through mplayer. i tried to add the hoary backports but seems like the links are broken.

Can anyone copy paste there sources list? that works nicely this is currently mine..

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse
# deb-src [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) hoary universe


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security  main universe multiverse restricted

Thankyou in advance for help here....

---

### Post by lukem on 2005-04-17
Try this:

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

have fun
luke

---

### Post by negatory on 2005-04-17
Remember that the win32codecs aren't available to amd64....
Don't know if there is a way with a chroot....

Pedro Carrico

---

### Post by floogy on 2005-04-25
[QUOTE=lukem]Try this:

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

have fun
luke[/QUOTE]

Hello,

Does this work on a ubuntu Horay amd64 installation? 
I'm just wondering if there is something like [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) [COLOR=Red]amd64[/COLOR] hoary-extras main universe multiverse restricted ?

regards

floogy

---

