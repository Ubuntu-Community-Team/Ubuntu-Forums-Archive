---
title: "[SOLVED] 1.1.8 update help on 8.10"
date: 2008-11-15
forum: Wine
---

### Post by javafiend on 2008-11-15
I guess Wine version 1.1.8 has been out for about a week now, yet there hasn't been an update for it in Update Manager.  After I upgraded to 8.10 I added the new third party source for Intrepid Ibex as shown on the Wine download site and deleted the one for Gutsy.

I try to keep Wine as current as possible on the off chance that it may have improvements for EQ2.  So if anyone can help me get it updated or explain WHY it hasn't, I would appreciate it.

Thanks!

---

### Post by k@e on 2008-11-15
Is Wine currently installed on your system? You won't be notified of updates, if it is not installed.

If you still can't get it updated via Update Manager somehow, you still have the possibility to download amd install the latest version manually from this site.
```

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
```

---

### Post by javafiend on 2008-11-15
That's odd, because I have always been notified of updates with Update Manager before I upgraded to 8.10.

---

### Post by OMJD on 2008-11-15
Hi,

Just go to System > Administration > Software Sources > Third Party Software (Tab) > Click "Add" (Button) > Then input:

[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main

Then scan again for updates, and it should give you the option to download the latest version of Wine.

Hope that helps.

- Rich

---

### Post by hikaricore on 2008-11-15
Third party sources are disabled on version upgrades.
Adding them again manually or uncommenting them out in the sources file will resolve this.

---

### Post by javafiend on 2008-11-15
I guess that leads me to another question then.  How do I uncomment or re-enable third party sources?

EDIT::
I figured it out.  Thanks everyone :)

---

