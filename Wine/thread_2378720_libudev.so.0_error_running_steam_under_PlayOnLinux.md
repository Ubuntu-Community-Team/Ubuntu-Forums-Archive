---
title: "libudev.so.0 error running steam under PlayOnLinux"
date: 2017-11-26
forum: Wine
---

### Post by lex1000 on 2017-11-26
Hi,

I'm having issues running steam under PlayOnLinux. I am running:
Ubuntu 16.04.3 LTS
PlayOnLinux 4.2.10

I get the following debug output:
> Running wine-2.12-staging Steam.exe (Working directory : /home/lex/.PlayOnLinux/shortcuts)
fixme:winediag:start_process Wine Staging 2.12 is a testing version containing experimental patches.
fixme:winediag:start_process Please mention your exact version when filing bug reports on winehq.org.
err:module:load_builtin_dll failed to load .so lib for builtin L"winebus.sys": libudev.so.0: cannot open shared object file: No such file or directory
err:winedevice:async_create_driver failed to create driver L"WineBus": c0000142
wine: cannot find L"C:\\windows\\system32\\Steam.exe"


I have manually installed the missing package:
> dpkg -i libudev0_175-0ubuntu9_amd64.deb
(I got the deb from [http://mirrors.kernel.org/ubuntu/pool/main/u/udev/libudev0_175-0ubuntu9_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/u/udev/libudev0_175-0ubuntu9_amd64.deb))

And confirmed it unpacked:
> ls -l /lib/x86_64-linux-gnu/libudev.so.0
lrwxrwxrwx 1 root root 17 Apr  5  2012 /lib/x86_64-linux-gnu/libudev.so.0 -> libudev.so.0.13.0

But PlayOnLinux/steam doesn't seem to be able to source it. Any idea what I'm doing wrong?

Thanks
Lex.

---

### Post by Perfect Storm on 2017-11-26
You properly need the 32-bit version of it.

```
sudo apt install libudev1:i386
```

---

### Post by lex1000 on 2017-11-26
Thanks AI, I did try adding it with apt-get before I downloaded the deb. I think this module is no longer available since Ubuntu 14.04, and the all version are 32-bit.

Output from apt install was:

> libudev1:i386 is already the newest version (229-4ubuntu21).

---

