---
title: "Problems with new version py on 8.04"
date: 2008-05-05
forum: Wine
---

### Post by JParkus on 2008-05-05
parkus@ubuntu:~$ cedega
/usr/lib/transgaming_cedega/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
warning: mmap failed on reservation of 00000000 (00110000)

World of Warcraft gives similar errors

---

### Post by sreekarguddeti on 2008-05-25
similar problem while installing aoe 2 using cedega 

error message is

##########
warning: mmap failed on reservation of 00000000 (00110000)
Warning: Language 'en_IN' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09; 
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
##########

I tried changing the Lang environmental variable from en_IN to en_US , but no peace..!!

---

