---
title: "failed to reserve range 00000000-60000000"
date: 2008-07-08
forum: Wine
---

### Post by stevew328 on 2008-07-08
Anytime I start up Wine (even if it's just winecfg) I get a bunch of this:

preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

This happens regardless of what directory I attempt to start Wine from.  Is this a config issue that I overlooked?

Just fyi, I installed the latest (I would assume) version from winehq.com but still get the error:

stevew@stevew-ubuntu:~$ wine --version
preloader: Warning: failed to reserve range 00000000-60000000
wine-0.9.59


**FIXED IT - Apparently the 'click here to install Wine' in the installation instructions on [www.winehq.com](www.winehq.com) install the older version.  Conchises sticky post actually got me upgraded to the latest error free:

stevew@stevew-ubuntu:~$ wine --version
wine-1.1.0
stevew@stevew-ubuntu:~$

---

