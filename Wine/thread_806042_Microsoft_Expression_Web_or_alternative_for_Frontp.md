---
title: "Microsoft Expression Web or alternative for Frontpage Server Extensions"
date: 2008-05-24
forum: Wine
---

### Post by mainstreetexile on 2008-05-24
Does anyone have any advice on installing Expression Web or access FPSE sites directly in linux?

I need to support some older sites for work that are unfortunately only accessible via Frontpage Server Extensions.  I have a copy of Expression Web, but I can't find any information on getting it to install with Wine and trying to run the setup.exe on the cd fails with:

"Setup cannot continue because a required file is either corrupted or not available. Run setup again from the original source disc or download location."

I tried poking through the cd for msi files and tried installing them with msiexec too, but no luck.

Alternatively, is there any other way to access Frontpage Server Extension / fpse / fpe sites from Linux?  I can't find any information on this anywhere.  A KDE KIO slave would be great, but I'm not holding my breath. :)

---

### Post by mainstreetexile on 2008-05-27
nobody? bueller? bueller?

---

### Post by johnycage on 2009-05-12
I'm looking for this answer as well... :?

---

### Post by asdfoo on 2009-05-12
I would suggest looking at developing using native free alternatives to frontpage.

---

### Post by xpakratx on 2009-06-28
I know redhat used to have a package for FrontPage extensions.  I just started Ubuntu yesterday, but what I do is Use frontpage to edit then use win SCP to SSh it my ubuntu box.

---

### Post by blood$ on 2009-07-15
this is my problem too.

---

### Post by Tibuda on 2009-07-15
See [http://support.microsoft.com/kb/202198/en-us/](http://support.microsoft.com/kb/202198/en-us/)
It looks like you need to patch Apache. It does not look safe for me.

---

