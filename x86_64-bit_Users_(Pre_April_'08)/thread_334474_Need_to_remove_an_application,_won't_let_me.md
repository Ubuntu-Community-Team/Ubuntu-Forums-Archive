---
title: "Need to remove an application, won't let me"
date: 2007-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by jlacroix on 2007-01-09
Hello, I tried to install a 32-bit KDE theme, Polyester. I know now that it is available in Adept. I didn't know that when I tried at first though.

I thought it would be a good idea to use --force-architecture option when installing the locally downloaded package. The installation was successful, but the theme is not in the KDE Control Center.

Defeated, I tried every command you can think of to remove it, (apt-get remove, etc) and it cannot find the application. I installed Synaptic to see if it could find it, and it can't. 

I tried to install the official 64-bit version once I figured out that it was in the repository.

I get this:
```
jeremy@jeremy-desktop:~/Documents/Themes/KDE/Window Borders & Styles$ sudo apt-get install kde-style-polyester
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  kde-style-polyester
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/163kB of archives.
After unpacking 598kB of additional disk space will be used.
(Reading database ... 145815 files and directories currently installed.)
Unpacking kde-style-polyester (from .../kde-style-polyester_0.99+1.0b1-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/kde-style-polyester_0.99+1.0b1-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/kde3/kwin_polyester_config.so', which is also in package polyester
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-style-polyester_0.99+1.0b1-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
UGH! I want this theme darn it. What can I do to purge the original one that I should not have installed in the first place so I can install the one from Adept/Apt?

---

### Post by jlacroix on 2007-01-09
Wow! "sudo dpkg --purge polyester" worked! What a lucky guess. Thanks anyway everyone!

---

