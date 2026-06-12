---
title: "remote x"
date: 2006-05-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by davidmaxwaterman on 2006-05-24
Hi,

I'm using my Powerbook running Ubuntu, and ssh'd into a box running Fedora on the same lan.

With other machines, I've just been able to 'xhost +' on my local box, and 'setenv DISPLAY ${REMOTEHOST}:0.0' on the remote box and I could then run X applications using my local kvm.

For some reason, this doesn't want to work with Ubuntu (I read that Ubuntu doesn't have any servers on it by default, which would include the X server, I suppose).

How can I fix it?

Max.

---

### Post by ssam on 2006-05-25
i think this issue is that ubuntu's Xserver is configured not to listen to the network by default (a good security idea).

if you aready sshing into the fedora box, then you may aswell use the x forwarding in ssh. log in with
```
ssh -X user@fedorabox
```

then just run the application, and it should display locally. the DISPLAY is set automatically by ssh (it is actually set to something like "localhost:10.0").

you may need xuath installed on the fedora box (i have no idea what package it is in on fedora)

---

### Post by calx on 2006-05-25
This post should clear things up, just got it running on my setup too. 
[http://ubuntuforums.org/showthread.php?t=19166&highlight=xhosts]("http://ubuntuforums.org/showthread.php?t=19166&highlight=xhosts")

[QUOTE=davidmaxwaterman]Hi,

I'm using my Powerbook running Ubuntu, and ssh'd into a box running Fedora on the same lan.

With other machines, I've just been able to 'xhost +' on my local box, and 'setenv DISPLAY ${REMOTEHOST}:0.0' on the remote box and I could then run X applications using my local kvm.

For some reason, this doesn't want to work with Ubuntu (I read that Ubuntu doesn't have any servers on it by default, which would include the X server, I suppose).

How can I fix it?

Max.[/QUOTE]

---

