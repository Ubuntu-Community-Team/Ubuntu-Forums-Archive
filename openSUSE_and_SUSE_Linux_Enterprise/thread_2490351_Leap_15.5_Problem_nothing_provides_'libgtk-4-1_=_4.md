---
title: "Leap 15.5: Problem: nothing provides 'libgtk-4-1 = 4.6.9' needed by the to be install"
date: 2023-08-31
forum: openSUSE and SUSE Linux Enterprise
---

### Post by maketopsite on 2023-08-31
```
[COLOR=#000000]zypper patch
[/COLOR]Loading repository data...
Reading installed packages...
Resolving package dependencies...

Problem: nothing provides 'libgtk-4-1 = 4.6.9' needed by the to be installed gtk4-branding-openSUSE-15.0-lp155.3.2.2.noarch
 Solution 1: deinstallation of gtk4-branding-openSUSE-15.0-lp155.2.6.noarch
 Solution 2: do not install patch:openSUSE-2023-239-1.noarch
 Solution 3: break gtk4-branding-openSUSE-15.0-lp155.3.2.2.noarch by ignoring some of its dependencies
 [COLOR=#000000]Choose from above solutions by number or cancel [1/2/3/c/d/?] (c):[/COLOR]
```

[COLOR=#000000][FONT=Verdana]What is please best solution ?[/FONT][/COLOR]

---

### Post by Xian on 2023-08-31
Choose solution 2. Let the package versions to catch up.

Normally better to delay the update rather than de-install/break.

---

### Post by maketopsite on 2023-09-11
Done, thank you.

---

