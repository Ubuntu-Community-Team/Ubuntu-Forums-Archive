---
title: "cannot access .ICEauthority: Stale NFS file handle"
date: 2009-01-06
forum: x86 64-bit Users
---

### Post by Richuelo on 2009-01-06
Dear users,

when I am trying to log in I get an error message:

> No write access to /.ICEauthority
> Could not start ksmserver. Check your installation.

The solution that worked for many people but not for me was to write this code:

> sudo chown username .ICEauthority

When I type this line and several variations of it I get the following message:

> chown: cannot access /home/jaime/.ICEauthority: Stale NFS file handle

I am using Kubuntu 8.10 and kde 4.1

I'd appreciate any help concerning this issue.

Best

---

### Post by Ehtetur on 2009-01-06
> **Richuelo said:**
> > chown: cannot access /home/jaime/.ICEauthority: Stale NFS file handle

Stale NFS file handle usually means the network share being referenced is not found.. That is, it's been unmounted; it's been overmounted (is this a word!?) with another share; it's been removed; it can't see the network, etc... It sounds like your home directory is on a network share.

If that's the case, you can boot to recovery mode and modify /etc/fstab with the correct configuration for your NFSserver/home folder location.

---

