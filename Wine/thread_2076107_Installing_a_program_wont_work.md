---
title: "Installing a program wont work"
date: 2012-10-25
forum: Wine
---

### Post by StevenHodges92 on 2012-10-25
OKay here are the directions to it

```
**[Tibia on Linux Using Wine without Windows]("http://search.yahoo.com/r/_ylt=A0oG7mKWJolQunAAcSNXNyoA;_ylu=X3oDMTE1ZWQzZTI1BHNlYwNzcgRwb3MDMQRjb2xvA2FjMgR2dGlkA0FDQlkwOF8xMDQ-/SIG=11mv1bnm9/EXP=1351194390/**http%3a//download.tibia.com/wine.pdf")**

Adobe PDF

```

Go down to page 10 where it says "install tibia" and where it says wine tibia*.exe

And this is what I got when I did it

```
steven@ubuntu:~$ wine tibia*.exe
wine: created the configuration directory '/home/steven/.wine'
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
fixme:seh:RtlAddFunctionTable 0x3b6ea0 1 390000: stub
fixme:seh:RtlAddFunctionTable 0x68f5b6a0 1 68f40000: stub
fixme:seh:RtlAddFunctionTable 0x6b431bc0 1 69c40000: stub
fixme:iphlpapi:NotifyAddrChange (Handle 0xdbe2f8, overlapped 0xdbe2c0): stub
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
wine: configuration in '/home/steven/.wine' has been updated.
wine: cannot find L"C:\\windows\\system32\\tibia*.exe"
steven@ubuntu:~$ wine tibia*.exe
wine: cannot find L"C:\\windows\\system32\\tibia*.exe"
steven@ubuntu:~$ cd ~/.wine/drive_c/Program\ Files/Tibia
bash: cd: /home/steven/.wine/drive_c/Program Files/Tibia: No such file or directory
steven@ubuntu:~$ 
```

It says it should pop up to install tibia, but nothing popped up for me.  What do I have to do to get it to work, wine installed version 1.4 fine.

---

### Post by dino99 on 2012-10-25
the only usefull error is :

```
err:mscoree:LoadLibraryShim error reading registry key for installroot
```

which means it cant find a valid .NET installation. So recheck that tibia prog readme (or howto) to know what is needed (either .NET2 or 4) before trying to install tibia.

To get the better chance you should use wine 1.5.15 (from wine-team ppa) and use winetricks to install the required .NET , and finally load tibia. Maybe your should also glance at winehq progs feedback.

---

### Post by StevenHodges92 on 2012-10-25
Well the instructions say to
type in
wine tibia*.exe

so I did and I got

steven@ubuntu:~$ wine tibia*.exe
wine: cannot find L"C:\\windows\\system32\\tibia*.exe"


But the directions also say to

if necessary, add the path to the file that you have
downloaded

how do I do that?

---

### Post by howefield on 2012-10-26
Thread moved to the "*Wine*" forum.

---

