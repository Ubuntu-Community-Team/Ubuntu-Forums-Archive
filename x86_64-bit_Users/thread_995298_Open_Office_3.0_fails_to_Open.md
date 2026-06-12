---
title: "Open Office 3.0 fails to Open"
date: 2008-11-27
forum: x86 64-bit Users
---

### Post by Sef on 2008-11-27
When opening OOo3, I get this message:  

> OpenOffice 3.0 - Fatal error.

This application cannot be open.   

Any ideas of what has caused this, and what to do?

---

### Post by Porpoise on 2008-11-27
> **Sef said:**
> When opening OOo3, I get this message:  



Any ideas of what has caused this, and what to do?


I haven't even seen the option to install v3.0 yet!?!

---

### Post by Skripka on 2008-11-27
> **Sef said:**
> When opening OOo3, I get this message:  



Any ideas of what has caused this, and what to do?

If you're on Gnome (Ubuntu), using a package called something to the effect of: "OpenOffice-Gnome"-and installed a recent update, odds are you got bit by a bug in the OOo3 packages.  The OOo3 PPA repos have been emptied as a precautionary measure until the bug is resolved-they were hoping for resolution ~12 hours ago or so, and they are still not back up yet.

@Porpoise:

OOo3 is available via .deb package archive on the OOo website.  The PPA archive-which was the easy instsall way got taken down-see above.  OOo3 is NOT in the official Ubuntu repos yet-as it has not been bug-tested against *buntu and it's variants.

---

### Post by Sef on 2008-11-28
> If you're on Gnome (Ubuntu), using a package called something to the effect of: "OpenOffice-Gnome"-and installed a recent update, odds are you got bit by a bug in the OOo3 packages. The OOo3 PPA repos have been emptied as a precautionary measure until the bug is resolved-they were hoping for resolution ~12 hours ago or so, and they are still not back up yet.

I am.   Thank you for the feedback.

---

### Post by Porpoise on 2008-11-28
> **Skripka said:**
> 

@Porpoise:

OOo3 is available via .deb package archive on the OOo website.  The PPA archive-which was the easy instsall way got taken down-see above.  OOo3 is NOT in the official Ubuntu repos yet-as it has not been bug-tested against *buntu and it's variants.

Aah... I see. OK Thanks for the heads-up. I'm quite happy with the current version, so I'll wait for the bug-ironed release.

---

### Post by mormor on 2008-11-29
Any update on this?

---

### Post by Thirtysixway on 2008-12-06
Have they fixed this yet?


edit

Running sudo apt-get remove openoffice.org-gnome fixed the problem on my machine.

---

