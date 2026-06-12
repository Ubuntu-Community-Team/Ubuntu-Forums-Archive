---
title: "Installing Microsoft.NET Framework 2.0 SP1"
date: 2008-09-18
forum: Wine
---

### Post by raiderleaf on 2008-09-18
I'm trying to install Microsoft.NET Framework 2.0 SP1 in order to play my game online, Secret of the Solstice. How can I achieve this? It keeps saying it fails...

---

### Post by Bakon Jarser on 2008-09-18
[http://appdb.winehq.org/appview.php?iVersionId=3754](http://appdb.winehq.org/appview.php?iVersionId=3754)

---

### Post by raiderleaf on 2008-09-18
Thank you! That worked like a trick! Anyways, I still can't get the internet to work at all though, and the application that uses this Framework can't detect the internet... Any advice would be greatly appreciated!

---

### Post by le_vainqueur on 2008-10-11
How were you able to get the installer to work?  Every version of Windows I tried had an installation failure.  I installed 1.1 without a problem.  The 2.0 installer got through the first few portions of the wizard, but when it got to the "Installing Components" window, no progress was made in the bar, and after sitting there for a bit, it said that the installation failed.  It also gave me the "send message to windows" or whatever dialog box.  Did you have any problems like this?

---

### Post by qwertymn on 2008-10-12
> **raiderleaf said:**
> I'm trying to install Microsoft.NET Framework 2.0 SP1 in order to play my game online, Secret of the Solstice. How can I achieve this? It keeps saying it fails...

.net 2.0 sp1 should install fine in wine-1.6 , after doing
 "winetricks dotnet20 volnum"
Then run the installer for .net 2.0 SP1. If things still fail, try it on a complete new ~/.wine, it should work

---

### Post by le_vainqueur on 2008-10-18
> **qwertymn said:**
> .net 2.0 sp1 should install fine in wine-1.6 , after doing
 "winetricks dotnet20 volnum"
Then run the installer for .net 2.0 SP1. If things still fail, try it on a complete new ~/.wine, it should work

That worked perfectly, thank you.

---

