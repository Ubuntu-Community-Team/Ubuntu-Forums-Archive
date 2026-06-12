---
title: "Package Management Issues"
date: 2005-12-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by donvella on 2005-12-02
Alot of programs in my packagemanager program under "Applications > Add Applications" do not want to install for some odd reason. It issues the following error:
The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preference.

I have these repositories enabled:
CD Ubuntu 5.10 "Breezy Badger" (Binary)
Officially supported 
Restricted copyright

Ubuntu 5.10 "Breezy Badger" (Binary)
Community maintained (Universe)

Ubuntu 5.10 "Breezy Badger" (Binary)
Non-free (Multiverse)

Ubuntu 5.10 "Breezy Badger" (Binary)
Non-free (Multiverse)

Ubuntu 5.10 "Breezy Badger" (Binary)
Non-free (Multiverse)

---

### Post by otey on 2005-12-02
I don't know if it will help. but try to add all the repositories available from the : settings > repositories manager.. works for me

---

### Post by donvella on 2005-12-02
Cheers man, you fixed 90% of my problems. The other 10% includes 64bit drivers, Im going to get the 32bit version of ubuntu, but am wondering a good way to uninstall and reinstall ubuntu without harming my windows partition. would it just be wise to fdisk, delete the partitions, and reinstall?

---

### Post by Pablo_Escobar on 2005-12-02
No need for fdisk if current partitions size are enough for You.
Just pop the 32bit CD, and during install select the partitions that 64 uses as a mount point "/" and select also to format it.

---

