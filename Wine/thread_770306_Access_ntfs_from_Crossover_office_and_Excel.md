---
title: "Access ntfs from Crossover office and Excel"
date: 2008-04-27
forum: Wine
---

### Post by rubakov on 2008-04-27
I get error message "... .xls could not be found. Check the spelling of the file name and verify that the file location is correct" when I'm trying to open xls file from ntfs partition.

There is no problem when I try to open .doc file from ntfs - just .xls
There is no problem too when I try to open .xls file from ext3 partition.

Where can be a problem?
In Crossover?
In ntfs-3g?
In Excel?
somewhere else?

Thanks!

---

### Post by rubakov on 2008-05-11
Problem was solved by reformatting ntfs drive into fat32.

---

