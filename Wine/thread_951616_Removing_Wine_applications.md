---
title: "Removing Wine applications?"
date: 2008-10-18
forum: Wine
---

### Post by Julian David Pitt on 2008-10-18
Can anyone please tell me how I remove VMWare Server Windows version from my 8.04.1 laptop as whenever I try to use wine it now starts Apache Tomcat. There does not seem to be an uninstall option within Wine itself

---

### Post by komputes on 2008-10-19
Does Applications > Wine > Uninstall Wine Software not work for this particular application? If not you can always do a dirty removal (although the wine registry will probably still have keys matching to the software). By going to /home/$USER/.wine/drive_c/Program Files and deleting the folder although this is not recommended. If you can reproduce not being able to uninstall  VMWare Server Windows edition, I would file a bug against wine.

---

