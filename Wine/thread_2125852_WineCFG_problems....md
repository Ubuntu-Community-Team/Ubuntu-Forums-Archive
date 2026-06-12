---
title: "WineCFG problems..."
date: 2013-03-15
forum: Wine
---

### Post by DoctorVell on 2013-03-15
I recently downloaded PlayOnLinux AND Wine (do I need both?) on my Ubuntu 12.10 system and I did the following and you can see the results.  I am trying to get iTunes version 10 to work.  I do have VirtualBox but I don't like to use it as it is super slow.  I want to be able to access my iTunes account without going on an IBM PC Compat or a Mac (which I do NOT have).  

doctorvell@DoctorVell:~$ winecfg
wine: created the configuration directory '/home/doctorvell/.wine'
fixme:storage:create_storagefile Storage share mode not implemented.
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
fixme:seh:RtlAddFunctionTable 0x61e45620 1 61e40000: stub
fixme:seh:RtlAddFunctionTable 0x61776ba0 1 61700000: stub
fixme:seh:RtlAddFunctionTable 0x64f69540 1 64f40000: stub
fixme:seh:RtlAddFunctionTable 0x622c6620 1 622c0000: stub
fixme:seh:RtlAddFunctionTable 0x6ce47620 1 6ce40000: stub
fixme:seh:RtlAddFunctionTable 0x682d4b20 1 682c0000: stub
fixme:seh:RtlAddFunctionTable 0x638d1dc0 1 63800000: stub
fixme:seh:RtlAddFunctionTable 0x6e6ea0 1 6c0000: stub
fixme:seh:RtlAddFunctionTable 0x68f5b6a0 1 68f40000: stub
fixme:seh:RtlAddFunctionTable 0x6b431bc0 1 69c40000: stub
fixme:iphlpapi:NotifyAddrChange (Handle 0xece2f8, overlapped 0xece2c0): stub
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:storage:create_storagefile Storage share mode not implemented.
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
fixme:iphlpapi:NotifyAddrChange (Handle 0xe9e8cc, overlapped 0xe9e8b0): stub
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
wine: configuration in '/home/doctorvell/.wine' has been updated.
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory

---

