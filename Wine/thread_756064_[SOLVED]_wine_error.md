---
title: "[SOLVED] wine error"
date: 2008-04-15
forum: Wine
---

### Post by Rytron on 2008-04-15
Hi,
I get this error when I try to start a windows application in wine:

```
wine dsCrypt_1.10.exe 
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
err:wineboot:main Cannot set the dir to L"c:\\windows" (2)
```

The dsCrypt_1.10.exe application did work before.

Also I installed automatix, perhaps this caused trouble with my wine installation?

---

### Post by beefcurry on 2008-04-15
try 

```
wineprefixcreate
```

---

### Post by Rytron on 2008-04-15
> **beefcurry said:**
> try 

```
wineprefixcreate
```

I got this:

```
:~$ wineprefixcreate
mkdir: cannot create directory `/home/myname/.wine/dosdevices/c:/windows': Permission denied
```

I also tried wine prefixcreate

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/raymond', starting in the Windows directory.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\prefixcreate.exe": Module not found
myname@Tron:~$ err:wineboot:main Cannot set the dir to L"c:\\windows" (2)

---

### Post by Rytron on 2008-06-09
I installed a new wine and now there are no problems.

---

