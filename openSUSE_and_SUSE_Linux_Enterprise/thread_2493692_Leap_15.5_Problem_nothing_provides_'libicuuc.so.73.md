---
title: "Leap 15.5: Problem: nothing provides 'libicuuc.so.73' needed by the to be installed l"
date: 2023-12-21
forum: openSUSE and SUSE Linux Enterprise
---

### Post by maketopsite on 2023-12-21
```
zypper patch --category security
Loading repository data...
Reading installed packages...
Patch 'openSUSE-SLE-15.5-2023-4954-1' is not in the specified category.
Resolving package dependencies...

Problem: nothing provides 'libicuuc.so.73' needed by the to be installed libQt5Core5-32bit-5.15.8+kde185-150500.4.13.1.x86_64
 Solution 1: Following actions will be done:
  deinstallation of libQt5Core5-32bit-5.15.8+kde185-150500.4.8.1.x86_64
  deinstallation of libQt5DBus5-32bit-5.15.8+kde185-150500.4.8.1.x86_64
  deinstallation of libQt5Network5-32bit-5.15.8+kde185-150500.4.8.1.x86_64
  deinstallation of libQt5Sql5-32bit-5.15.8+kde185-150500.4.8.1.x86_64
  deinstallation of libQt5Test5-32bit-5.15.8+kde185-150500.4.8.1.x86_64
  deinstallation of libQt5Sensors5-32bit-5.15.8+kde0-150500.1.4.x86_64
  deinstallation of libQt5XmlPatterns5-32bit-5.15.8+kde0-150500.1.4.x86_64
 Solution 2: do not install patch:openSUSE-SLE-15.5-2023-4951-1.noarch
 Solution 3: break libQt5Core5-32bit-5.15.8+kde185-150500.4.13.1.x86_64 by ignoring some of its dependencies

Choose from above solutions by number or cancel [1/2/3/c/d/?] (c): 

```

What is please optimal solution ?

---

### Post by Xian on 2023-12-21
Solution 2 is the optimal choice. 
Allow time for the repos to proivde the needed version.

---

### Post by maketopsite on 2023-12-22
> **Xian said:**
> Solution 2 is the optimal choice. 
Allow time for the repos to proivde the needed version.

Thank you.

---

### Post by maketopsite on 2024-01-05
solved by upgrade

---

