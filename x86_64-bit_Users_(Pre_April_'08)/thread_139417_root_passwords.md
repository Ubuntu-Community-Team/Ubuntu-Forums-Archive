---
title: "root passwords"
date: 2006-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by hakito on 2006-03-04
Hi,
I just reset the root password (trough "linux single" variation for grub)  I can change to root on terminals, but any GUI asking for root password says it's wrong, so what should I do to reset any other root password?

Also, once the above is solved, I guess I can update to 5.10 and also install KDE (Kubuntu?) trough software updates, right?

Thanks in advance.

PS  I posted here because of the plataform (Ubuntu 5.04 on AMD64), but is this the right place to post this, or did I missed the right one?

---

### Post by stuporglue on 2006-03-04
>  I just reset the root password (trough "linux single" variation for grub) I can change to root on terminals, but any GUI asking for root password says it's wrong, so what should I do to reset any other root password?


You didn't need to set a root password since Ubuntu uses sudo for everything. 

The GUI programs that run as super-admin are usually launched by gksudo which wants 1) you to be in the sudo-doers group, and 2) you to use your own password. 

In the GUI login boxes, try the password your user (non-root) uses. 

> Also, once the above is solved, I guess I can update to 5.10 and also install KDE (Kubuntu?) trough software updates, right?

Yes. You'll need to add Breezy (5.10) repositories to Synaptic (The package manager) and then you can upgrade to 5.10. To install Kubuntu, search for kubuntu-desktop in Synaptic and install that.

---

### Post by hakito on 2006-03-04
[QUOTE=stuporglue]In the GUI login boxes, try the password your user (non-root) uses.
[/QUOTE]The sad part is... I already knew it, but I forgot about it.

[QUOTE=stuporglue]Yes. You'll need to add Breezy (5.10) repositories to Synaptic (The package manager) and then you can upgrade to 5.10.
[/QUOTE]Thanks, I'll check which repositories and how to add them.

[QUOTE=stuporglue]To install Kubuntu, search for kubuntu-desktop in Synaptic and install that.
[/QUOTE]I'm already on that.

Thanks for your complete and really quick answer.

That reminds me, the last time I used Ubuntu I installed mysql 4.x, but everytime I tried to connect to a remote server (using tunnels on a different port) it always connected to the local server, any ideas about this?  I recall having checked anythig I read about the config files, but still nothing worked.

---

