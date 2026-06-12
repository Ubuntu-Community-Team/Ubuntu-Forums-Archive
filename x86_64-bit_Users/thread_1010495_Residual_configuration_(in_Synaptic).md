---
title: "Residual configuration (in Synaptic)"
date: 2008-12-13
forum: x86 64-bit Users
---

### Post by John Jason Jordan on 2008-12-13
In Synaptic (Intrepid x86_64) I have the following packages in "Not installed (residual config)":

linux-backports-modules-2.6.24-18-generic
linux-backports-modules-2.6.24-19-generic
virtualbox-ose-modules-2.6.22-14-generic

The virtualbox package has been there for a long time and I have just ignored it. The backports packages appeared after upgrading Hardy to Intrepid. In all cases I get error messages when I try to do a Complete Removal in order to get rid of them.

I guess I can continue to ignore them, but loose ends bother me. Does anyone know how to get rid of them?

---

### Post by kaibob on 2008-12-13
I had a somewhat similar problem and the solution was to create an empty directory in the lib/modules directory with the same name as the linux module. In your case, the directories would be:

/lib/modules/2.6.24-18-generic
/lib/modules/2.6.24-19-generic
/lib/modules/2.6.22-14-generic

After creating the above directories, try synaptic again.

This is an old problem that I assumed had been taken care of (and perhaps has). Anyway, it only involves creating a few directories and is worth a shot.

---

### Post by John Jason Jordan on 2008-12-14
> **kaibob said:**
> I had a somewhat similar problem and the solution was to create an empty directory in the lib/modules directory with the same name as the linux module. In your case, the directories would be:

/lib/modules/2.6.24-18-generic
/lib/modules/2.6.24-19-generic
/lib/modules/2.6.22-14-generic

After creating the above directories, try synaptic again.

This is an old problem that I assumed had been taken care of (and perhaps has). Anyway, it only involves creating a few directories and is worth a shot.

Thanks. That got rid of the first two. But I still can't get rid of the virtualbox-ose-modules headers. Do you know where I need to create a folder to get rid of that one?

---

### Post by kaibob on 2008-12-14
> **John Jason Jordan said:**
> Thanks. That got rid of the first two. But I still can't get rid of the virtualbox-ose-modules headers. Do you know where I need to create a folder to get rid of that one?
Sorry I don't. 

While searching for an old thread on this topic, I came across the following post, which you may want to have a look at:

[http://ubuntuforums.org/showthread.php?t=783534](http://ubuntuforums.org/showthread.php?t=783534)

---

