---
title: "install windows packages using ubuntu"
date: 2011-08-17
forum: Wine
---

### Post by Martiini on 2011-08-17
I know this is slightly far fetched .. but .. 

is there any way to install windows installer msiexec msi exe packages using ubuntu into windows partition ??
using wine, unpacking, copy/paste, vmware etc

Theres some trouble packages on windows which dont uninstall/reinstall etc
currently only option I have is reinstall windows 

simple extract/copy/paste doesnt seem to work

---

### Post by disabledaccount on 2011-08-17
> **Martiini said:**
> I know this is slightly far fetched .. but .. 

is there any way to install windows installer msiexec msi exe packages using ubuntu into windows partition ??
using wine, unpacking, copy/paste, vmware etc

Theres some trouble packages on windows which dont uninstall/reinstall etc
currently only option I have is reinstall windows 

simple extract/copy/paste doesnt seem to work
Yes & No :)
No, You can't use wine to fix windows installation and no, You cant use vmware either.

Yes, it is possible to fix windows by using copy/paste method *and* external registry editor *or* another working windows, by connecting to damaged system's registry using regedit. Unfortunatelly it needs deep knowledge about registry structure. (btw this method can be used to "reinstall" f.e. huge games in few seconds after reinstalling broken windows)

Solution for future problems: create system partition image before applying a bunch of updates or at least system restore point.

---

### Post by Martiini on 2011-08-17
> **tomazzi said:**
> Yes & No :)
Solution for future problems: create system partition image before applying a bunch of updates or at least system restore point.

ok ..

---

