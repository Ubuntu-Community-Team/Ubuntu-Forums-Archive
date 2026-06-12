---
title: "Leap 15.5: Problem: the installed samba-ad-dc-4.17.3+git.290.00f806b25c9-150500.1.20."
date: 2023-09-18
forum: openSUSE and SUSE Linux Enterprise
---

### Post by maketopsite on 2023-09-18
```
# zypper patch
Loading repository data...
Reading installed packages...
Resolving package dependencies...
3 Problems:
Problem: the installed samba-ad-dc-4.17.3+git.290.00f806b25c9-150500.1.20.x86_64 requires 'samba-tool = 4.17.3+git.290.00f806b25c9', but this requirement cannot be provided
Problem: the installed samba-ad-dc-libs-32bit-4.17.3+git.290.00f806b25c9-150500.1.20.x86_64 requires 'libLIBWBCLIENT-OLD-samba4.so(SAMBA_4.17.3_GIT.290.00F806B25C9150500.1.20_SUSE_OS15.0_I386_SAMBA4)', but this requirement cannot be provided
Problem: the installed WebKit2GTK-4.1-lang-2.38.6-150400.4.42.4.noarch requires 'WebKit2GTK-4.1 = 2.38.6', but this requirement cannot be provided


Problem: the installed samba-ad-dc-4.17.3+git.290.00f806b25c9-150500.1.20.x86_64 requires 'samba-tool = 4.17.3+git.290.00f806b25c9', but this requirement cannot be provided
  deleted providers: samba-tool-4.17.3+git.290.00f806b25c9-150500.1.20.x86_64
 Solution 1: Following actions will be done:
  deinstallation of samba-ad-dc-4.17.3+git.290.00f806b25c9-150500.1.20.x86_64
  deinstallation of samba-ad-dc-libs-4.17.3+git.290.00f806b25c9-150500.1.20.x86_64
  deinstallation of samba-dsdb-modules-4.17.3+git.290.00f806b25c9-150500.1.20.x86_64
 Solution 2: do not install patch:openSUSE-SLE-15.5-2023-2929-1.noarch
 Solution 3: break samba-ad-dc-4.17.3+git.290.00f806b25c9-150500.1.20.x86_64 by ignoring some of its dependencies


Choose from above solutions by number or skip, retry or cancel [1/2/3/s/r/c/d/?] (c):
```

[COLOR=#000000]What is please best solution ?[/COLOR]

---

### Post by Xian on 2023-09-19
This:

Solution 2: do not install patch openSUSE-SLE-15.5-2023-2929-1.noarch

---

### Post by maketopsite on 2023-10-02
> **Xian said:**
> This:

Solution 2: do not install patch openSUSE-SLE-15.5-2023-2929-1.noarch

Thank you, removing samba has solved the problem.

---

