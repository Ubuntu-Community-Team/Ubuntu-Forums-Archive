---
title: "Disable Track Pad Clicking"
date: 2005-10-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Netherfox on 2005-10-22
How do I disable trackpad clicking totally? It's really irritating. Thanks.

---

### Post by AikenDrum on 2005-10-23
Try installing 'powerprefs' with synaptic / apt-get.   (you may need the universe repositories for it)  and then call it from a terminal with 'sudo powerprefs'

This lets you configure all the powerpc options built into the OS - including how the trackpad responds to tap-click, tap-drag etc etc.

Cheers,

---

### Post by skeporang on 2005-10-23
Has anyone had any luck with this? 

No matter which option I select (notap, tap, lock etc.), it makes no difference to the tap-to-click on the touchpad: it still tap-to-clicks...

---

### Post by Netherfox on 2005-10-24
Apparently there is a powerpc-utils package with executables that allow you to set these options individually. The package properties said that there was an executable "trackpad" in directory /sbin...so I went there and tried to set that variable...

```
root@stealth:/sbin# trackpad drag
no trackpad !
root@stealth:/sbin#

```

So now it appears I have no trackpad :rolleyes:

---

### Post by skeporang on 2005-10-25
[QUOTE=Netherfox]Apparently there is a powerpc-utils package with executables that allow you to set these options individually. The package properties said that there was an executable "trackpad" in directory /sbin...so I went there and tried to set that variable...

So now it appears I have no trackpad :rolleyes:[/QUOTE]

Hmm.. same here :???:

---

