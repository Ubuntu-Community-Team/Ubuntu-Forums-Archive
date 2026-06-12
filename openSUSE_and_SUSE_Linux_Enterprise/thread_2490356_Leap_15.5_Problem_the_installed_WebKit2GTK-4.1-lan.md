---
title: "Leap 15.5: Problem: the installed WebKit2GTK-4.1-lang-2.38.6-150400.4.42.4.noarch req"
date: 2023-08-31
forum: openSUSE and SUSE Linux Enterprise
---

### Post by maketopsite on 2023-08-31
```
zypper patch
Loading repository data...
Reading installed packages...
Patch 'openSUSE-SLE-15.5-2023-3482-1' is optional. Use 'zypper in patch:openSUSE-SLE-15.5-2023-3482' to install it, or '--with-optional' to include all optional patches.
Patch 'openSUSE-SLE-15.5-2023-3413-1' is optional. Use 'zypper in patch:openSUSE-SLE-15.5-2023-3413' to install it, or '--with-optional' to include all optional patches.
Resolving package dependencies...

Problem: the installed WebKit2GTK-4.1-lang-2.38.6-150400.4.42.4.noarch requires 'WebKit2GTK-4.1 = 2.38.6', but this requirement cannot be provided
  not installable providers: libwebkit2gtk-4_1-0-2.38.6-150400.4.39.1.x86_64[repo-oss]
 Solution 1: Following actions will be done:
  deinstallation of WebKit2GTK-4.1-lang-2.38.6-150400.4.42.4.noarch
  deinstallation of WebKit2GTK-4.0-lang-2.38.6-150400.4.42.4.noarch
 Solution 2: do not install patch:openSUSE-SLE-15.5-2023-3419-1.noarch
 Solution 3: break WebKit2GTK-4.1-lang-2.38.6-150400.4.42.4.noarch by ignoring some of its dependencies

Choose from above solutions by number or cancel [1/2/3/c/d/?] (c): 
```

[COLOR=#000000][FONT=Verdana]What is please best solution ?[/FONT][/COLOR]

---

### Post by nerdyanorak on 2023-08-31
Dear maketopsite,

Probably ubuntu forum is the wrong place to ask questions about openSUSE distribution. Nevertheless. I had the same issue on my leap 15.5 install. I opted for Solution 1. This deinstalled the conflicting packages and installed WebKit2GTK-4_0-37-2.40.5-150400.4.45.3, WebKit2GTK-4_1-0-2.40.5-150400.4.45.3 and other dependencies. All seems to work OK.

Best

---

### Post by maketopsite on 2023-09-11
[COLOR=#000000][FONT=Verdana]Thank you this has solved the problem.

(Name of this subforum is [/FONT][/COLOR]
[LIST]
[*][openSUSE and SUSE Linux Enterprise]("https://ubuntuforums.org/forumdisplay.php?f=164")
[/LIST]
[COLOR=#000000][FONT=Verdana]so I suppose question about openSUSE are expected in this subforum)[/FONT][/COLOR]

---

