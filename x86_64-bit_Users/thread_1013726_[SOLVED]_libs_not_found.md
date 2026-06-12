---
title: "[SOLVED] libs not found"
date: 2008-12-17
forum: x86 64-bit Users
---

### Post by any.linux12 on 2008-12-17
As you can see here there are some files that can't be found, and I realy need those files to install a business software.
> 
$ ldd psregsvr 
	linux-gate.so.1 =>  (0xffffe000)
	libpscore.so.3 => not found
	libpscl.so.3 => not found
	libuuid.so.1 => not found
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7f50000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf7f4c000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7e59000)
	libm.so.6 => /lib32/libm.so.6 (0xf7e34000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7e28000)
	libc.so.6 => /lib32/libc.so.6 (0xf7cd9000)
	/lib/ld-linux.so.2 (0xf7f74000)


Please help

---

### Post by jespdj on 2008-12-17
Use [http://packages.ubuntu.com/](http://packages.ubuntu.com/) - scroll down to "Search the contents of packages" to find out in which packages those missing libraries are.

---

### Post by any.linux12 on 2008-12-17
i found the solution in other thread. thanks anyway

---

