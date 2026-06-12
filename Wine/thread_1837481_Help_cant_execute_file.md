---
title: "Help cant execute file"
date: 2011-09-01
forum: Wine
---

### Post by retro89 on 2011-09-01
I cant execute setup file from cd because it blocks executables.Is there a work around?

---

### Post by papibe on 2011-09-01
Could you show the directory where the setup file is?
```
$ cd /path/to/dir
$ ls -l
```
Regards.

---

### Post by cgroza on 2011-09-01
Is copying the files from the CD to the HDD and making them executable an option?
I think this is a permission issue, so alternatively you could mount the CD drive with the "exec" flag.

---

