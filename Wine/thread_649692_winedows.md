---
title: "winedows"
date: 2007-12-25
forum: Wine
---

### Post by windows-killer on 2007-12-25
Hi everyone :)
am using wine to run some of my progies and sometimes they dont open, or i get error messages saying files missing from "system 32"

so I was thinning to  copy all my system 32 files into wine, is that a good move?

---

### Post by cogadh on 2007-12-25
Not really. There are some Windows native DLL files that you definitely should not use in Wine. It is best to just copy only those that the application is looking for.

---

