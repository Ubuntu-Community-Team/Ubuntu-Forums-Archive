---
title: "&quot;Share&quot; tab not working"
date: 2008-12-01
forum: x86 64-bit Users
---

### Post by Tilex on 2008-12-01
Hi all,

I recently re-installed Kubuntu 8.10 64-bit on a Core2 machine, and it works great!

I noticed, however, that when I want to configure the "Sharing" attribute of a folder (right-click->propertoes->Share), I click on "Configure File Sharing", I am prompted to enter my root password, and nothing.

Is there a known bug for this?

Thanks!

---

### Post by soxs on 2008-12-01
Did you want to share it via nfs or smaba (with windows and/or linux)?
Both require additional install cadidates:
samba:
```
sudo apt-get install samba
```nfs is for more advanced users... so ask me if it'that what you want, but the Nautilus tab usually references to smb.

For smaba to work properly, you may have to reboot.

---

### Post by PS5000 on 2008-12-01
SOXS,

Thanks for the suggestion, but is's still a no-go.  I installed samaba, and restarted, but am experiencing the same issue.  Did you make any progress Tilex?

---

### Post by Tilex on 2008-12-02
> Did you make any progress Tilex?

No PS5000, no progress.  I had samba installed but it was not working.  

I'm having huge stability problems; i'm so disappointed with KDE 4.1, I can't believe the community have let it out without giving the opportunity to not install it on a fresh install.

My Samba home network does not work anymore (even if I manually edit the smb.conf file it does not work), my system will freeze from time to time, the "restart" does not work only shutdowns, crossoffice installs all crashes even though they did not before...and the list goes on.

I updated my other system today and it went blank after I rebooted.  Way to go.

---

