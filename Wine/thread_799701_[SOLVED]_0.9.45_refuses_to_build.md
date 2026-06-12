---
title: "[SOLVED] 0.9.45 refuses to build"
date: 2008-05-19
forum: Wine
---

### Post by soxs on 2008-05-19
I want to compile wine on 64 bit hardy heron with phenom.patch (Otherwise wine won't work on phenom cpus).
But every time I try to compile it gives me the following error:
```

parse.c: In Funktion »ldap_parse_sort_controlW«:
parse.c:339: Warnung: Implizite Deklaration der Funktion »ldap_parse_sort_control«
parse.c: In Funktion »ldap_parse_vlv_controlW«:
parse.c:420: Warnung: Implizite Deklaration der Funktion »ldap_parse_vlv_control«
gcc-4.2 -m32 -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -g -O2  -o rename.o rename.c
gcc-4.2 -m32 -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -g -O2  -o search.o search.c
gcc-4.2 -m32 -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -g -O2  -o value.o value.c
../../tools/wrc/wrc --nostdinc -I. -I. -I../../include -I../../include  -D__WINESRC__   -fowldap32.res wldap32.rc
../../tools/winegcc/winegcc -B../../tools/winebuild -shared ./wldap32.spec    add.o ber.o bind.o compare.o control.o delete.o dn.o error.o extended.o init.o main.o misc.o modify.o modrdn.o option.o page.o parse.o rename.o search.o value.o     wldap32.res    -o wldap32.dll.so  -luser32 -lkernel32  -lldap_r -llber ../../libs/port/libwine_port.a -L/lib32 -L/usr/lib32 -L/home/soxs/Desktop/wine-0.9.45/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32 
parse.o: In function `ldap_parse_vlv_controlW':
/home/soxs/Desktop/wine-0.9.45/dlls/wldap32/parse.c:420: undefined reference to `ldap_parse_vlv_control'
/home/soxs/Desktop/wine-0.9.45/dlls/wldap32/parse.c:420: undefined reference to `ldap_parse_vlv_control'
parse.o: In function `ldap_parse_sort_controlW':
/home/soxs/Desktop/wine-0.9.45/dlls/wldap32/parse.c:339: undefined reference to `ldap_parse_sort_control'
collect2: ld gave  1 as exit state back
winegcc: gcc-4.2 failed.
make[2]: *** [wldap32.dll.so] Error 2
make[2]: Leaving folder '/home/soxs/Desktop/wine-0.9.45/dlls/wldap32'
make[1]: *** [wldap32] Error 2
make[1]: Leaving folder '/home/soxs/Desktop/wine-0.9.45/dlls'
make: *** [dlls] Error 2
```
Any ideas?

---

### Post by happyhamster on 2008-05-19
Did you compile wine following these instructions:
[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

If so, perhaps compiling with an older gcc version (3.4) might help. (You'll have to install it first.)

---

### Post by soxs on 2008-05-19
I compiled it according to the named howto.

I even tried gcc-3.4 but I get stuck at th very same point. :-(

---

### Post by happyhamster on 2008-05-19
Do you get any warnings or complaints after running:
```
 CC="gcc-4.2 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure -v
```

(don't run "make").

---

### Post by soxs on 2008-05-19
Well I got one missing library (both with gcc-4.2 and 3.4)

```
...
configure: libicu development files not found.
Wine will be built without bidi (Right to Left) support. (gdi32.dll)

Configure finished.  Do 'make depend && make' to compile Wine.
```

I did not take this missing error that serious, I just installe the library and it still persisted..

Edit: I installed libicu-dev and libicu38 via getlibs -p and linked *any* libicu in /usr/lib32/libicu to my compiling directory. -> still the same error as above.

---

### Post by happyhamster on 2008-05-19
You'll likely need the 32 bit version of libicu-dev. I don't really know how to properly install that though.

---

### Post by soxs on 2008-05-19
I allready have it, but ./configure still will not recognize it :-(

---

### Post by happyhamster on 2008-05-19
BTW: gcc seems to abort while building wldap32.dll, while libicu apparently affects gdi32.dll. So perhaps libicu isn't the only problem here.

> **soxs said:**
> [CODE]...
configure: libicu development files not found.
Wine will be built without bidi (Right to Left) support. (gdi32.dll)

> 
winegcc: gcc-4.2 failed.
make[2]: *** [wldap32.dll.so] Error 2
make[2]: Leaving folder '/home/soxs/Desktop/wine-0.9.45/dlls/wldap32'
make[1]: *** [wldap32] Error 2
make[1]: Leaving folder '/home/soxs/Desktop/wine-0.9.45/dlls'
make: *** [dlls] Error 2

---

### Post by Half-Left on 2008-05-19
Try installing ```
libldap2-dev
``` and make clean and run configure again.

---

### Post by happyhamster on 2008-05-19
Ok, I tried compiling wine 0.9.45, and the libicu warning went away after installing lib32icu-dev, and linking the libraries as in the howto:

```

ln -s /usr/lib32/libicudata.so.38.0    `pwd`/lib32/libicudata.so
ln -s /usr/lib32/libicui18n.so.38.0    `pwd`/lib32/libicui18n.so
ln -s /usr/lib32/libicuio.so.38.0      `pwd`/lib32/libicuio.so
ln -s /usr/lib32/libicule.so.38.0      `pwd`/lib32/libicule.so
ln -s /usr/lib32/libiculx.so.38.0      `pwd`/lib32/libiculx.so
ln -s /usr/lib32/libicutu.so.38.0      `pwd`/lib32/libicutu.so
ln -s /usr/lib32/libicuuc.so.38.0      `pwd`/lib32/libicuuc.so

```

But compilation still fails on wldap32.dll.so.

---

### Post by YokoZar on 2008-05-19
It might just be that the 2 year old version of Wine you're attempting to use doesn't build with the newer libraries in Hardy.

---

### Post by Half-Left on 2008-05-19
> **happyhamster said:**
> Ok, I tried compiling wine 0.9.45, and the libicu warning went away after installing lib32icu-dev, and linking the libraries as in the howto:

```

ln -s /usr/lib32/libicudata.so.38.0    `pwd`/lib32/libicudata.so
ln -s /usr/lib32/libicui18n.so.38.0    `pwd`/lib32/libicui18n.so
ln -s /usr/lib32/libicuio.so.38.0      `pwd`/lib32/libicuio.so
ln -s /usr/lib32/libicule.so.38.0      `pwd`/lib32/libicule.so
ln -s /usr/lib32/libiculx.so.38.0      `pwd`/lib32/libiculx.so
ln -s /usr/lib32/libicutu.so.38.0      `pwd`/lib32/libicutu.so
ln -s /usr/lib32/libicuuc.so.38.0      `pwd`/lib32/libicuuc.so

```

But compilation still fails on wldap32.dll.so.

Did you try installing libldap2-dev?

---

### Post by happyhamster on 2008-05-19
> **Half-Left said:**
> Did you try installing libldap2-dev?
It was already installed. Thanks though.

> 
It might just be that the 2 year old version of Wine you're attempting to use doesn't build with the newer libraries in Hardy. 
Is it already that old? First wine version I used was 0.9.41. Time sure flies. :)

---

### Post by happyhamster on 2008-05-19
Ok, I tried something ugly and it compiled.

In a clean source folder, open the file parse.c (in the /dlls/wldap32 folder), and search for line 339 and 420 respectively.

line 339:
> 
ret = ldap_parse_sort_control( ld, controlU, &res, &attrU );
line 420 (this one is spread out over 2 lines):
> 
ret = ldap_parse_vlv_control( ld, controlU, &pos, &count,
                                  (struct berval **)context, errcode );

change both into: 
> 
ret = LDAP_SUCCESS;

- Then continue with the howto (creating symlinks, etc). When done compiling, you can create a .deb file using checkinstall:

sudo apt-get install checkinstall

sudo checkinstall --fstrans=no

- On first sight, it appears to work fine (it runs Tomb Raider Legend for example).

---

### Post by soxs on 2008-05-20
Will try this as soon as possible! You're my star:KS
Note: I allready had installed libldap2-dev since the first attempt to compile failed.
Edit: I can not get the uggly warning about libicu away though linking and having installed the lib32icu-dev package.

Is it possible to compile wine 0.9.45 in a virtual OS (Ubuntu 7.04 or 7.10) and install that just created package under hardy or can I be sure it will not work?

---

### Post by happyhamster on 2008-05-21
> **soxs said:**
> Edit: I can not get the uggly warning about libicu away though linking and having installed the lib32icu-dev package.
I tried to reproduce my previous result on a fresh install, and I ran into the same problem again. I tried to reconstruct what I could have done to get it to work, and I think I figured it out mostly.

- To make the libicu warning go away, install lib32icu-dev, and also run:

sudo apt-get build-dep libicu-dev

- Lib32icu-dev installs its stuff into /emul/ia32-linux/usr/lib/. It has both .so and .a files which are needed. Easy way of running configure is like this:

 CC="gcc-4.2 -m32" LDFLAGS="-L/emul/ia32-linux/usr/lib/ -L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure -v

I attached a log of what I did after hardy's fresh install (it lists the installed packages, etc.). Note that I see more warnings now when running make (make >makelog.txt) compared to the previous install, so perhaps there's still something missing. Wine appears to run ok though)


> 
Is it possible to compile wine 0.9.45 in a virtual OS (Ubuntu 7.04 or 7.10) and install that just created package under hardy or can I be sure it will not work?
I don't know. Running one of the old AMD64 wine debs ([http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)) should give an indication if it could be feasible. And I have no idea how the virtual machine will affect the process.

[edit: typos]

---

### Post by happyhamster on 2008-05-21
BTW, see also this bugreport I just found:
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/218097](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/218097)

So, it seems that, depending on the update-status of your system, the libraries are in /emul/ia32-linux/usr/lib/ or /usr/lib32/

This has gotten way more complicated than I imagined :(

---

### Post by soxs on 2008-05-22
No, line numbers will not change, it just patches dlls/kernel32/cpu.c for phenom support, nothing else.
I am going to try it according to your log..

Note: I can not test how old wine versions work, due to the requirement for patching cpu.c to recognize phenom correctly. That's the only reason I need to compile myself.

EDIT: Compiling according to your log was successfull! Thx a lot!

---

### Post by YokoZar on 2008-05-22
Have you tried the patch against current Wine?  Or does it not apply cleanly?

---

### Post by soxs on 2008-05-22
It is allready included in current wine.
The latest one without the phenom patch was 0.9.58
The bad thing is thath I only need warcraft 3 support, and current versions lack proper acceptex support and the patches ar too wacky to complete a game and hosting is more like russian roulette

```

From ffbc42fdf48160ef5847c3bc5ce7aa6dca17518e Mon Sep 17 00:00:00 2001
From: =?utf-8?q?Alexander=20Nicolaysen=20S=C3=B8rnes?= <alexander@kurt.alexstyrt>
Date: Sun, 30 Mar 2008 00:44:19 +0100
Subject: [PATCH] kernel32: set processorLevel to cpu family

---
 dlls/kernel32/cpu.c |   15 +++------------
 1 files changed, 3 insertions(+), 12 deletions(-)

diff --git a/dlls/kernel32/cpu.c b/dlls/kernel32/cpu.c
index a2ecb34..a49df99 100644
--- a/dlls/kernel32/cpu.c
+++ b/dlls/kernel32/cpu.c
@@ -454,19 +454,10 @@ VOID WINAPI GetSystemInfo(
 				case 5: cachedsi.dwProcessorType = PROCESSOR_INTEL_PENTIUM;
 					cachedsi.wProcessorLevel= 5;
 					break;
-				case 6: cachedsi.dwProcessorType = PROCESSOR_INTEL_PENTIUM;
-					cachedsi.wProcessorLevel= 6;
-					break;
-				case 1: /* two-figure levels */
-                                    if (value[1] == '5')
-                                    {
-                                        cachedsi.dwProcessorType = PROCESSOR_INTEL_PENTIUM;
-                                        cachedsi.wProcessorLevel= 6;
-                                        break;
-                                    }
-                                    /* fall through */
+
 				default:
-					FIXME("unknown cpu family '%s', please report ! (-> setting to 386)\n", value);
+					cachedsi.dwProcessorType = PROCESSOR_INTEL_PENTIUM;
+					cachedsi.wProcessorLevel = atoi(value);
 					break;
 				}
 			}
-- 
1.5.3.7

```

---

### Post by soxs on 2008-06-15
Attached a diff which will change the pending lines happyhamdter mentioned.

---

