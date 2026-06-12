---
title: "ATI control not working"
date: 2006-07-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by cocteau on 2006-07-30
Hi

I followed <a href="http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually"> this tutorial</a> to set up my Radeon 9600 Mobile, which now works just fine. However the ATI control won't start and I get this error:

fireglcontrolpanel: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

however libGL.so.1 is in /usr/lib, /usr/lib32 and as a symlink in /usr/lib64. Where is the control panel looking for that file?

---

### Post by Kilz on 2006-07-30
> **cocteau said:**
> Hi

I followed <a href="http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually"> this tutorial</a> to set up my Radeon 9600 Mobile, which now works just fine. However the ATI control won't start and I get this error:

fireglcontrolpanel: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

however libGL.so.1 is in /usr/lib, /usr/lib32 and as a symlink in /usr/lib64. Where is the control panel looking for that file?
I had an error when following that howto. The libGL.so.1 was not replaced. You might try deleting the libGL.so.1 files and redoing the howto, it solved my problems.

---

### Post by cocteau on 2006-07-31
> **Kilz said:**
> I had an error when following that howto. The libGL.so.1 was not replaced. You might try deleting the libGL.so.1 files and redoing the howto, it solved my problems.

That didn't work. It get the same error even though that libGL.so.1 was recreated.

---

