---
title: "[SOLVED] OOPS!  Deleted files."
date: 2008-09-12
forum: x86 64-bit Users
---

### Post by C. Wizard on 2008-09-12
Hello,
First, I'm running Kubuntu 8.04, amd_64.

I was looking at some recent upgradeable files using Apt-get and one of them was a GNOME app for writing HTML. As I'm using KDE
and not about to write HTML, I looked at the details and told apt-get to remove the file.

Good thing I didn't look away from the computer as it informed me it was deleting 348 files. I quickly stopped it, but not before doing some damage to the desktop.
Several apps were remove from the menu, including apt-get, but I've found it still will run from the command line.
Is there any command I can run that will re-install the deleted files?  They are there, a long list of them, and apt-get tells me to use the "autoremove" switch to deleted them, but I'm not about to do that. :)
Any help would be greatly appreicated!
Many Thanks.

---

### Post by go_beep_yourself on 2008-09-12
[PHP]sudo apt-get install kubuntu-desktop[/PHP]

That's a meta package that will get all the packages that make up a default Kubuntu desktop. Then search through your /var/log/dpkg.log for packages you installed.

[PHP]grep -v "status" /var/log/dpkg.log | grep "install\|upgrade"[/PHP]

---

### Post by C. Wizard on 2008-09-12
That was a great help.
Thanks!
:)

---

