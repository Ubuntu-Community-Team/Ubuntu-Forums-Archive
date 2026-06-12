---
title: "TW: Problem: the to be installed python310-ipyparallel-8.6.1-1.4.noarch requires 'pyt"
date: 2023-09-18
forum: openSUSE and SUSE Linux Enterprise
---

### Post by maketopsite on 2023-09-18
```
# zypper dup
2 Problems:
Problem: problem with the installed libvo-amrwbenc0-0.1.3-1.77.x86_64
Problem: the to be installed python310-ipyparallel-8.6.1-1.4.noarch requires 'python310-jupyter-client < 8', but this requirement cannot be provided


Problem: problem with the installed libvo-amrwbenc0-0.1.3-1.77.x86_64
 Solution 1: install libvo-amrwbenc0-0.1.3+5-1.2.x86_64 from vendor openSUSE
  replacing libvo-amrwbenc0-0.1.3-1.77.x86_64 from vendor http://packman.links2linux.de
 Solution 2: keep obsolete libvo-amrwbenc0-0.1.3-1.77.x86_64


Choose from above solutions by number or skip, retry or cancel [1/2/s/r/c/d/?] (c): 1
Applying solution 1


Problem: the to be installed python310-ipyparallel-8.6.1-1.4.noarch requires 'python310-jupyter-client < 8', but this requirement cannot be provided
  deleted providers: python310-jupyter-client-7.4.9-1.2.noarch
not installable providers: python310-jupyter-client7-7.4.9-2.3.noarch[download.opensuse.org-oss]
                   python310-jupyter-client7-7.4.9-2.3.noarch[openSUSE-20220310-0]
 Solution 1: deinstallation of python310-ipyparallel-8.4.1-2.3.noarch
 Solution 2: deinstallation of python310-jupyter-client-7.4.9-1.2.noarch
 Solution 3: keep obsolete python310-ipyparallel-8.4.1-2.3.noarch
 Solution 4: keep obsolete python310-jupyter-client-7.4.9-1.2.noarch
 Solution 5: break python310-ipyparallel-8.6.1-1.4.noarch by ignoring some of its dependencies


Choose from above solutions by number or skip, retry or cancel [1/2/3/4/5/s/r/c/d/?] (c):
```

What is please best solution ?

---

### Post by Xian on 2023-09-19
This:

Solution 2: keep obsolete libvo-amrwbenc0-0.1.3-1.77.x86_64

---

### Post by maketopsite on 2023-09-21
> **Xian said:**
> This:

Solution 2: keep obsolete libvo-amrwbenc0-0.1.3-1.77.x86_64

Thank you, problem with [FONT=courier new]python310-jupyter-client[/FONT] was solved by
```
zypper rm jupyter-jupyter-client
```

---

