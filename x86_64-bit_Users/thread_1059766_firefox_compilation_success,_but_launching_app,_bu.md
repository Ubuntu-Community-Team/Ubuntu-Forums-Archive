---
title: "firefox compilation success, but launching app, buffer overflow falls out"
date: 2009-02-04
forum: x86 64-bit Users
---

### Post by seenxu on 2009-02-04
Hello Everyone,

I had just tried to compile firefox 3.0.5 both from stable source
tarball and the source out of cvs.
the compilation success, but when running firefox, always buffer
overflow.


compilation procedure like the following:
* prepare a very basic .mozconfig [1]
* make -f client.mk build
* compile success
* run compiled firefox in the following dir obj-@CONFIG_GUESS@/dist/
bin/firefox
* buffer overflow, output pls check [2]

any ideas how to fix this?

system spec:
* ubuntu 8.10 amd64
* gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12)


[1] .mozconfig
```

mk_add_options MOZ_CO_PROJECT=browser
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/obj-@CONFIG_GUESS@
ac_add_options --enable-application=browser

```
[2] buffer overflow output
```

$ ./obj-x86_64-unknown-linux-gnu/dist/bin/firefox
*** buffer overflow detected ***: ./obj-x86_64-unknown-linux-gnu/dist/
bin/firefox-bin terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7f9b42971877]
/lib/libc.so.6[0x7f9b4296f740]
/lib/libc.so.6[0x7f9b4296fdfb]
./obj-x86_64-unknown-linux-gnu/dist/bin/libxul.so(XRE_GetBinaryPath
+0x4d)[0x7f9b46de29d7]
./obj-x86_64-unknown-linux-gnu/dist/bin/firefox-bin[0x400e9e]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7f9b42890466]
./obj-x86_64-unknown-linux-gnu/dist/bin/firefox-bin[0x400cf9]
======= Memory map: ========
00400000-00402000 r-xp 00000000 08:05 1309888          /opt/
build_mozilla/mozilla/obj-x86_64-unknown-linux-gnu/dist/bin/firefox-
bin
00602000-00603000 r--p 00002000 08:05 1309888          /opt/
build_mozilla/mozilla/obj-x86_64-unknown-linux-gnu/dist/bin/firefox-
bin
00603000-00604000 rw-p 00003000 08:05 1309888          /opt/
build_mozilla/mozilla/obj-x86_64-unknown-linux-gnu/dist/bin/firefox-
bin
7f9b3e700000-7f9b3e800000 rw-p 7f9b3e700000 00:00 0
7f9b3e839000-7f9b3e83e000 r-xp 00000000 08:05 509740   /usr/lib/
libXdmcp.so.6.0.0
7f9b3e83e000-7f9b3ea3d000 ---p 00005000 08:05 509740   /usr/lib/
libXdmcp.so.6.0.0
7f9b3ea3d000-7f9b3ea3e000 rw-p 00004000 08:05 509740   /usr/lib/
libXdmcp.so.6.0.0
7f9b3ea3e000-7f9b3ea40000 r-xp 00000000 08:05 509738   /usr/lib/
libXau.so.6.0.0
7f9b3ea40000-7f9b3ec3f000 ---p 00002000 08:05 509738   /usr/lib/
libXau.so.6.0.0
7f9b3ec3f000-7f9b3ec40000 rw-p 00001000 08:05 509738   /usr/lib/
libXau.so.6.0.0
7f9b3ec40000-7f9b3ec48000 r-xp 00000000 08:05 1816839  /lib/
librt-2.8.90.so
7f9b3ec48000-7f9b3ee47000 ---p 00008000 08:05 1816839  /lib/
librt-2.8.90.so
7f9b3ee47000-7f9b3ee48000 r--p 00007000 08:05 1816839  /lib/
librt-2.8.90.so
7f9b3ee48000-7f9b3ee49000 rw-p 00008000 08:05 1816839  /lib/
librt-2.8.90.so
7f9b3ee49000-7f9b3ee60000 r-xp 00000000 08:05 508816   /usr/lib/
libICE.so.6.3.0
7f9b3ee60000-7f9b3f05f000 ---p 00017000 08:05 508816   /usr/lib/
libICE.so.6.3.0
7f9b3f05f000-7f9b3f061000 rw-p 00016000 08:05 508816   /usr/lib/
libICE.so.6.3.0
7f9b3f061000-7f9b3f064000 rw-p 7f9b3f061000 00:00 0
7f9b3f064000-7f9b3f06c000 r-xp 00000000 08:05 509736   /usr/lib/
libSM.so.6.0.0
7f9b3f06c000-7f9b3f26b000 ---p 00008000 08:05 509736   /usr/lib/
libSM.so.6.0.0
7f9b3f26b000-7f9b3f26c000 r--p 00007000 08:05 509736   /usr/lib/
libSM.so.6.0.0
7f9b3f26c000-7f9b3f26d000 rw-p 00008000 08:05 509736   /usr/lib/
libSM.so.6.0.0
7f9b3f26d000-7f9b3f288000 r-xp 00000000 08:05 507416   /usr/lib/
libxcb.so.1.0.0
7f9b3f288000-7f9b3f487000 ---p 0001b000 08:05 507416   /usr/lib/
libxcb.so.1.0.0
7f9b3f487000-7f9b3f488000 r--p 0001a000 08:05 507416   /usr/lib/
libxcb.so.1.0.0
7f9b3f488000-7f9b3f489000 rw-p 0001b000 08:05 507416   /usr/lib/
libxcb.so.1.0.0
7f9b3f489000-7f9b3f48a000 r-xp 00000000 08:05 507689   /usr/lib/libxcb-
xlib.so.0.0.0
7f9b3f48a000-7f9b3f689000 ---p 00001000 08:05 507689   /usr/lib/libxcb-
xlib.so.0.0.0
7f9b3f689000-7f9b3f68a000 r--p 00000000 08:05 507689   /usr/lib/libxcb-
xlib.so.0.0.0
7f9b3f68a000-7f9b3f68b000 rw-p 00001000 08:05 507689   /usr/lib/libxcb-
xlib.so.0.0.0
7f9b3f68b000-7f9b3f6ba000 r-xp 00000000 08:05 1816961  /lib/libpcre.so.
3.12.1
7f9b3f6ba000-7f9b3f8b9000 ---p 0002f000 08:05 1816961  /lib/libpcre.so.
3.12.1
7f9b3f8b9000-7f9b3f8ba000 r--p 0002e000 08:05 1816961  /lib/libpcre.so.
3.12.1
7f9b3f8ba000-7f9b3f8bb000 rw-p 0002f000 08:05 1816961  /lib/libpcre.so.
3.12.1
7f9b3f8bb000-7f9b3f8d5000 r-xp 00000000 08:05 1390012  /lib/
libselinux.so.1
7f9b3f8d5000-7f9b3fad4000 ---p 0001a000 08:05 1390012  /lib/
libselinux.so.1
7f9b3fad4000-7f9b3fad5000 r--p 00019000 08:05 1390012  /lib/
libselinux.so.1
7f9b3fad5000-7f9b3fad6000 rw-p 0001a000 08:05 1390012  /lib/
libselinux.so.1
7f9b3fad6000-7f9b3fad7000 rw-p 7f9b3fad6000 00:00 0
7f9b3fad7000-7f9b3faff000 r-xp 00000000 08:05 621951   /usr/local/lib/
libpng12.so.0.34.0
7f9b3faff000-7f9b3fcfe000 ---p 00028000 08:05 621951   /usr/local/lib/
libpng12.so.0.34.0
7f9b3fcfe000-7f9b3fcff000 r--p 00027000 08:05 621951   /usr/local/lib/
libpng12.so.0.34.0
7f9b3fcff000-7f9b3fd00000 rw-p 00028000 08:05 621951   /usr/local/lib/
libpng12.so.0.34.0
7f9b3fd00000-7f9b3fd42000 r-xp 00000000 08:05 626257   /usr/local/lib/
libpixman-1.so.0.12.0
7f9b3fd42000-7f9b3ff42000 ---p 00042000 08:05 626257   /usr/local/lib/
libpixman-1.so.0.12.0
7f9b3ff42000-7f9b3ff44000 rw-p 00042000 08:05 626257   /usr/local/lib/
libpixman-1.so.0.12.0
7f9b3ff44000-7f9b3ff4d000 r-xp 00000000 08:05 508851   /usr/lib/
libXcursor.so.1.0.2
7f9b3ff4d000-7f9b4014d000 ---p 00009000 08:05 508851   /usr/lib/
libXcursor.so.1.0.2
7f9b4014d000-7f9b4014e000 rw-p 00009000 08:05 508851   /usr/lib/
libXcursor.so.1.0.2
7f9b4014e000-7f9b40155000 r-xp 00000000 08:05 507384   /usr/lib/
libXrandr.so.2.1.0
7f9b40155000-7f9b40354000 ---p 00007000 08:05 507384   /usr/lib/
libXrandr.so.2.1.0
7f9b40354000-7f9b40355000 r--p 00006000 08:05 507384   /usr/lib/
libXrandr.so.2.1.0
7f9b40355000-7f9b40356000 rw-p 00007000 08:05 507384   /usr/lib/
libXrandr.so.2.1.0
7f9b40356000-7f9b4035f000 r-xp 00000000 08:05 508043   /usr/lib/
libXi.so.6.0.0
7f9b4035f000-7f9b4055f000 ---p 00009000 08:05 508043   /usr/lib/
libXi.so.6.0.0
7f9b4055f000-7f9b40560000 r--p 00009000 08:05 508043   /usr/lib/
libXi.so.6.0.0
7f9b40560000-7f9b40561000 rw-p 0000a000 08:05 508043   /usr/lib/
libXi.so.6.0.0
7f9b40561000-7f9b40563000 r-xp 00000000 08:05 507860   /usr/lib/
libXinerama.so.1.0.0
7f9b40563000-7f9b40762000 ---p 00002000 08:05 507860   /usr/lib/
libXinerama.so.1.0.0
7f9b40762000-7f9b40763000 rw-p 00001000 08:05 507860   /usr/lib/
libXinerama.so.1.0.0
7f9b40763000-7f9b40773000 r-xp 00000000 08:05 507663   /usr/lib/
libXext.so.6.4.0
7f9b40773000-7f9b40973000 ---p 00010000 08:05 507663   /usr/lib/
libXext.so.6.4.0
7f9b40973000-7f9b40975000 rw-p 00010000 08:05 507663   /usr/lib/
libXext.so.6.4.0
7f9b40975000-7f9b4099c000 r-xp 00000000 08:05 508029   /usr/lib/
libexpat.so.1.5.2
7f9b4099c000-7f9b40b9c000 ---p 00027000 08:05 508029   /usr/lib/
libexpat.so.1.5.2
7f9b40b9c000-7f9b40b9e000 r--p 00027000 08:05 508029   /usr/lib/
libexpat.so.1.5.2
7f9b40b9e000-7f9b40b9f000 rw-p 00029000 08:05 508029   /usr/lib/
libexpat.so.1.5.2
7f9b40b9f000-7f9b40ba4000 r-xp 00000000 08:05 508040   /usr/lib/
libXfixes.so.3.1.0
7f9b40ba4000-7f9b40da3000 ---p 00005000 08:05 508040   /usr/lib/
libXfixes.so.3.1.0
7f9b40da3000-7f9b40da4000 rw-p 00004000 08:05 508040   /usr/lib/
libXfixes.so.3.1.0
7f9b40da4000-7f9b40da6000 r-xp 00000000 08:05 509752   /usr/lib/
libXdamage.so.1.1.0
7f9b40da6000-7f9b40fa5000 ---p 000Aborted

```

---

### Post by cariboo on 2009-02-04
Why would you want compile Firefox 3.0.5, when it is available in the repositories? Even if you don't want to use the version from the repositories, there is a binary version that all you have to do is extract it, and it's ready to go. As a matter fo fact if you go [here]("http://www.mozilla.com/en-US/firefox/"), there is a newer version available.

Jim

---

### Post by seenxu on 2009-02-04
Because I want firefox compiled with pgo optimized for my specific machine, and the one in offical repo does not have it. 

Everytime I tried to compile firefox, it fails with buffer overflow, until I striped out all extra compilation options, I thought this failure may be a bug specific only for ubuntu, so I wrote this post and see if someone else is in the same situation with me.

---

