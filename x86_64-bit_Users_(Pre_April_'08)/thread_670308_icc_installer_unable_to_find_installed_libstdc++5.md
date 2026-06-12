---
title: "icc installer unable to find installed libstdc++5"
date: 2008-01-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by kfstephensii on 2008-01-17
I just changed my system over from RHEL4 to Ubuntu7.10. I'm trying to install the Intel c++ compiler. But it fails, complaining that libstdc++.so.5 cannot be opened. Here is the output from the installer:

    Testing Intel(R) C/C++ compilers installed in /opt/intel/cce/10.1.008 ... 
    ERROR: Output file /tmp/install_cc.sh6408/test_cc.6408 not found
    cat: /tmp/install_cc.sh6408/test_cc.6408.output: No such file or directory
    Problems with C compiler: Output not equal to <Hello, World!  C>
    ----------------------------------------------------
    Contents of /tmp/install_cc.sh6408/test_cc.6408.log:
    Intel(R) C Compiler for applications running on Intel(R) 64, Version 10.1    Build  
    20070913 Package ID: l_cc_p_10.1.008
    Copyright (C) 1985-2007 Intel Corporation.  All rights reserved.
    FOR NON-COMMERCIAL USE ONLY

    /opt/intel/cce/10.1.008/bin/mcpcom: error while loading shared libraries: 
    libstdc++.so.5: cannot open shared object file: No such file or directory
    compilation aborted for /tmp/install_cc.sh6408/test_cc.6408.c (code 127)
    Problems with C compiler: <>!=<Hello, World!  C>

However, I do have libstdc++.so.5 installed. Here is the result of "ll /usr/lib/libstdc++*":
  lrwxrwxrwx 1 root root      18 2008-01-17 09:12 /usr/lib/libstdc++.so.5 -> libstdc++.so.5.0.7
  -rw-r--r-- 1 root root  829360 2007-07-29 15:36 /usr/lib/libstdc++.so.5.0.7
  lrwxrwxrwx 1 root root      18 2008-01-16 08:36 /usr/lib/libstdc++.so.6 -> libstdc++.so.6.0.9
  -rw-r--r-- 1 root root 1014808 2007-09-28 19:51 /usr/lib/libstdc++.so.6.0.9

Any suggestions?

I got the installation to work on my ia32 ubuntu running in VirtualBox on my XP laptop. I know there are typically issues with amd64 but I'm confused here.

Thanks.

---

### Post by Kilz on 2008-01-17
The problem is that the compiler is most likely 32bit, it needs the 32bit version of that library. You might want to install ia32-libs to see if the 32bit libstdc++5 is included. If not [getlibs ]("http://ubuntuforums.org/showthread.php?t=474790")can help install 32bit libraries in the correct location so they do not overwrite 64bit libraries.

---

