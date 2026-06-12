---
title: "Howto: Minicommander gnome-applet"
date: 2008-09-12
forum: x86 64-bit Users
---

### Post by go_beep_yourself on 2008-09-12
After using Fedora x86_64 for a while, I had been using minicommander for a while. Then I used Ubuntu 64-bit and saw that it had no minicommander gnome-applet. I googled and searched the forum and found out that people tried to get it but failed. It's integrated into Gnome, and even the webpage for it says to get a newer gnome because the link to its source alone is not likely to build as Gnome continues to update very often. I saw plenty of people filing bug reports and attempting to get it working but failing. I rebuilt the gnome-applets package with all the ubuntu patches applied, upped the version to 2.22.2-0ubuntu2+mypkg1, so that the package manager won't try to replace them with the same its version. It prefers packages from the repos if they are the same version or older. However this won't prevent you from getting future releases of the package through updates. I've included a few screenshots of minicommander. These are for people using x86_64 bit Ubuntu. If anybody asks for 32 bit packages, then I'll compile those as well. The packages are here. [http://chris1.redirectme.net/~chris/minicommander/]("http://chris1.redirectme.net/~chris/minicommander/")

---

### Post by go_beep_yourself on 2008-09-15
The url should be working again.

---

### Post by Remmelas on 2008-10-31
Can you build 32 bit binaries for me?  It would be much appreciated.

---

### Post by go_beep_yourself on 2008-10-31
You're the second to ask that, so I'll go ahead and start working on it. It looks like I'm going to have to compile my own kernel because the stock Ubuntu kernel won't allow me to compile 32 bit binaries with it's 64 kernel, so give me a little time to do this. Do you want the package made for Ubuntu 8.10 or 8.04? It's going to take me at least a few hours to finish upgrading to 8.10 if you want the packages for that.

---

### Post by go_beep_yourself on 2008-10-31
I doubt I can make anymore 8.04 packages because my computer is almost finished updating to 8.10. Will you have 8.10? Do you want some 8.10 32 bit packages?

---

