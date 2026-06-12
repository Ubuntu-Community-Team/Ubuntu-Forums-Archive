---
title: "using portato (Gtk)"
date: 2008-01-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by papaw on 2008-01-18
im very new to linux i am running a dual boot with sabayon 1.1 pro 64-bit and window vista ultimate 64-bit i have portato as my install package when i try  to install nero 3 Linux or beryl it tells me they are masked dont understand term is it like a hidden file here is what comes upon both thx in advance for ant help be gentle im new to linux but love it so far


pawpaw@localhost ~ $ su
Password:
localhost pawpaw # emerge =kuroo-0.81_rc1
Calculating dependencies /
!!! All ebuilds that could satisfy "=kuroo-0.81_rc1" have been masked.
!!! One of the following masked packages is required to complete your request:
- app-portage/kuroo-0.81_rc1 (masked by: ~amd64 keyword)

For more information, see MASKED PACKAGES section in the emerge man page or
refer to the Gentoo Handbook.

localhost pawpaw # emerge -av nero

These are the packages that would be merged, in order:

Calculating dependencies... done!
[ebuild  N    ] app-cdr/nero-3.0.1.3  USE="-doc" 17,224 kB

Total: 1 package (1 new), Size of downloads: 17,224 kB

Would you like to merge these packages? [Yes/No] y
>>> Verifying ebuild Manifests...

>>> Emerging (1 of 1) app-cdr/nero-3.0.1.3 to /
>>> Downloading 'ftp://ftp6.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm'
--00:39:09--  [ftp://ftp6.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm](ftp://ftp6.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm)
           => `/usr/portage/distfiles/nerolinux-3.0.1.3-x86_64.rpm'
Resolving ftp6.use.nero.com... failed: Name or service not known.
>>> Downloading 'http://ftp5.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm'
--00:39:15--  [http://ftp5.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm](http://ftp5.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm)
           => `/usr/portage/distfiles/nerolinux-3.0.1.3-x86_64.rpm'
Resolving ftp5.use.nero.com... failed: Name or service not known.
>>> Downloading 'http://ftp4.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm'
--00:39:15--  [http://ftp4.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm](http://ftp4.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm)
           => `/usr/portage/distfiles/nerolinux-3.0.1.3-x86_64.rpm'
Resolving ftp4.use.nero.com... failed: Name or service not known.
>>> Downloading 'ftp://ftp3.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm'
--00:39:15--  [ftp://ftp3.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm](ftp://ftp3.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm)
           => `/usr/portage/distfiles/nerolinux-3.0.1.3-x86_64.rpm'
Resolving ftp3.use.nero.com... failed: Name or service not known.
>>> Downloading 'ftp://ftp4.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm'
--00:39:15--  [ftp://ftp4.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm](ftp://ftp4.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm)
           => `/usr/portage/distfiles/nerolinux-3.0.1.3-x86_64.rpm'
Resolving ftp4.use.nero.com... failed: Name or service not known.
>>> Downloading 'http://ftp6.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm'
--00:39:16--  [http://ftp6.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm](http://ftp6.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm)
           => `/usr/portage/distfiles/nerolinux-3.0.1.3-x86_64.rpm'
Resolving ftp6.use.nero.com... failed: Name or service not known.
>>> Downloading 'ftp://ftp5.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm'
--00:39:16--  [ftp://ftp5.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm](ftp://ftp5.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm)
           => `/usr/portage/distfiles/nerolinux-3.0.1.3-x86_64.rpm'
Resolving ftp5.use.nero.com... failed: Name or service not known.
>>> Downloading 'http://ftp3.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm'
--00:39:16--  [http://ftp3.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm](http://ftp3.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm)
           => `/usr/portage/distfiles/nerolinux-3.0.1.3-x86_64.rpm'
Resolving ftp3.use.nero.com... failed: Name or service not known.
!!! Couldn't download 'nerolinux-3.0.1.3-x86_64.rpm'. Aborting.

---

### Post by Kilz on 2008-01-18
It looks like you are trying to install it to sabayon, not Ubuntu. But the reason it isnt installing is because it cant download the package [ftp://ftp6.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm ](ftp://ftp6.use.nero.com/software/NeroLINUX/nerolinux-3.0.1.3-x86_64.rpm ). The url is bad.

---

