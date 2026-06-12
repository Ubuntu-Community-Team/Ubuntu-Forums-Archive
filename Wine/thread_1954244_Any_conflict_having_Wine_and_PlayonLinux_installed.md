---
title: "Any conflict having Wine and PlayonLinux installed?"
date: 2012-04-07
forum: Wine
---

### Post by Curtis6767 on 2012-04-07
Seems that when Wine doesn't do the job, then people install PlayonLinux and that often does work.

From what I've read, these two are different versions of the same app, but I could be wrong about that.

I'm on 12.04 LTS Beta and I'm not ready to install either of these at the moment but plan to install Wine once the final 12.04 is released. Will there be any conflict between these two apps if I install both?

Thanks.

---

### Post by forrestcupp on 2012-04-08
There is no conflict. I have both installed. In fact, PlayOnLinux can manage several different versions of Wine at the same time. The way PlayOnLinux works is that it can have several versions of Wine installed, and it will use the best version of Wine for whatever program you're installing. Like for some reason, Microsoft Office 2007 doesn't work as well with Wine 1.4, so PlayOnLinux uses Wine 1.2 to install and run that program, while it might use 1.4 for other things.

You're fine to have both things installed. I'm doing it without any trouble at all. Just know that any apps you install with PlayOnLinux will have a Wineprefix created in the ~/.PlayOnLinux folder instead of the ~/.wine folder.

---

### Post by Curtis6767 on 2012-04-08
Forrest, Thanks

---

### Post by synaptix on 2012-04-08
Also, latest PoL from website will require the wine metapackage (which seems to install latest 1.5.1 development version).

---

