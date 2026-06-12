---
title: "Epson 4490 Photo scanner in AMD64"
date: 2008-05-23
forum: x86 64-bit Users
---

### Post by rocketship on 2008-05-23
I finally got my Epson Perfection 4490 Photo scanner working in AMDx64, here's how:

Download the latest RPMS from Avasys:
[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do ]("http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do")

You should have two RPMs - one called iscan_2.10.0-2_i386.rpm (or later version), and the other iscan-plugin-gt-x750_1.0.0-2_i386.rpm.

In the download folder execute:
```
sudo alien -k iscan_2.10.0-2_i386.rpm
sudo alien -k iscan-plugin-gt-x750_1.0.0-2_i386.rpm
```

You should now have two .deb files.

Now:
```
sudo dpkg -i --force-architecture iscan_2.10.0-2_i386.deb
sudo dpkg -i --force-architecture iscan-plugin-gt-x750_1.0.0-2_i386.deb
```

You should now be able to run:
```
iscan
```

This SHOULD open up the Iscan scanning window.

Addendum:  What I really wanted was to get Vuescan working on AMDx64.  On 32-bit Ubuntu, I used to have to run ```
scanimage -T
``` before ```
vuescan
``` to get the system to see the scanner.  Scanimage no longer works, but I have to start up Iscan to get Vuescan to work.  Anybody run into this and found an easy workaround?

Best,
RS

---

### Post by Rhubarb on 2008-05-23
Does this work with XSane as well?
As this tutorial should work with the Epson V200 scanners from this thread:
[http://ubuntuforums.org/showthread.php?t=627650&page=5](http://ubuntuforums.org/showthread.php?t=627650&page=5)

---

### Post by rocketship on 2008-05-23
Mmmm... no, it doesn't seem to.  For some reason (maybe its the 32bit-64bit divide?) all the sane (xsane, scanimage) don't seem to work.  You might need to install 32-bit libsane?

RS

---

### Post by Rhubarb on 2008-05-23
Thanks anyway, the closest solution is to follow this post:
[http://ubuntuforums.org/showpost.php?p=4926086&postcount=44](http://ubuntuforums.org/showpost.php?p=4926086&postcount=44)

I do wish Epson would support the sane project directly / release GPLed source / release 64bit binaries.

---

### Post by rocketship on 2008-05-23
Absolutely - release the source would be best.  It looks like the contracted their Linux drivers out to another company (Avasys)...

---

### Post by bertwagner on 2008-06-08
I also have an EPSON Perfection 4490 Photo and tried following the above steps to get it recognized but with no luck.  When downloading the RPMs I could not find any files named:

> **rocketship said:**
> iscan_2.10.0-2_i386.rpm (or later version), and the other iscan-plugin-gt-x750_1.0.0-2_i386.rpm.

The closest I was able to get were iscan-2.10.0-1.c2.i386.rpm and iscan-plugin-gt-x750-1.0.0-1.c2.i386.rpm .  i then tried to execute the following code on the files:

> **rocketship said:**
> 
In the download folder execute:```
sudo alien -k iscan_2.10.0-2_i386.rpm
sudo alien -k iscan-plugin-gt-x750_1.0.0-2_i386.rpm
```

but all I received were a a slew of errors:

```
 sudo alien -k iscan-2.10.0-1.c2.i386.rpm 
Warning: Skipping conversion of scripts in package iscan: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
parsechangelog/debian: warning:     debian/changelog(l7): badly formatted heading line
LINE: - create udev rules from hotplug usermap using custom utility
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/iscan
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: failure: no dependency information found for /usr/lib32/libsane.so.1 (used by debian/iscan/usr/bin/iscan).
dh_shlibdeps: command returned error code 512
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
parsechangelog/debian: warning:     debian/changelog(l7): badly formatted heading line
LINE: - create udev rules from hotplug usermap using custom utility
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: iscan-2.10.0: No such file or directory

```

and ```
sudo alien -k iscan-plugin-gt-x750-1.0.0-1.c2.i386.rpm 
Warning: Skipping conversion of scripts in package iscan-plugin-gt-x750: postrm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
parsechangelog/debian: warning:     debian/changelog(l7): badly formatted heading line
LINE: - package the backend interpreter plugins in their own RPMs
parsechangelog/debian: warning:     debian/changelog(l8): found change data where expected next heading or eof
LINE:   - added support for build on architectures other than IA32
parsechangelog/debian: warning:     debian/changelog(l9): found eof where expected more change data or trailer
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/iscan-plugin-gt-x750
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
parsechangelog/debian: warning:     debian/changelog(l7): badly formatted heading line
LINE: - package the backend interpreter plugins in their own RPMs
parsechangelog/debian: warning:     debian/changelog(l8): found change data where expected next heading or eof
LINE:   - added support for build on architectures other than IA32
parsechangelog/debian: warning:     debian/changelog(l9): found eof where expected more change data or trailer
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: iscan-plugin-gt-x750-1.0.0: No such file or directory

```

Am I overseeing something in not being able to find the correct RPMs or in my attempt to convert to deb files?  Any help would be greatly appreciated, thanks.

---

### Post by crgutierrez on 2008-06-09
No Luck with Epson V350

> crgutierrez@crgutierrez-desktop:~$ sudo dpkg -i --force-all '/home/crgutierrez/Desktop/scanner/iscan_2.3.0-2_i386.deb' 
[sudo] password for crgutierrez: 
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 170279 files and directories currently installed.)
Preparing to replace iscan 2.3.0-2 (using .../scanner/iscan_2.3.0-2_i386.deb) ...
Unpacking replacement iscan ...
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/man/man5/sane-epkowa.5.gz', which is also in package libsane-extras
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/sane/libsane-epkowa.la', which is also in package libsane-extras
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib/sane/libsane-epkowa.so.1', which is also in package libsane-extras
Setting up iscan (2.3.0-2) ...

crgutierrez@crgutierrez-desktop:~$ sudo dpkg -i --force-all '/home/crgutierrez/Desktop/scanner/iscan-plugin-gt-f700_2.0.0-1_i386.deb' 
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 170279 files and directories currently installed.)
Preparing to replace iscan-plugin-gt-f700 2.0.0-1 (using .../iscan-plugin-gt-f700_2.0.0-1_i386.deb) ...
Unpacking replacement iscan-plugin-gt-f700 ...
Setting up iscan-plugin-gt-f700 (2.0.0-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
crgutierrez@crgutierrez-desktop:~$ getlibs /usr/bin/iscan
This application isn't missing any dependencies
crgutierrez@crgutierrez-desktop:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
crgutierrez@crgutierrez-desktop:~$ iscan
scanimage -T

crgutierrez@crgutierrez-desktop:~$ scanimage -T
scanimage: no SANE devices found
crgutierrez@crgutierrez-desktop:~$ iscan
crgutierrez@crgutierrez-desktop:~$ sudo gedit /etc/sane.d/dll.conf
crgutierrez@crgutierrez-desktop:~$ xsane
crgutierrez@crgutierrez-desktop:~$ iscan
*** glibc detected *** iscan: double free or corruption (fasttop): 0x0828f800 ***
======= Backtrace: =========
/lib32/libc.so.6[0xf7705615]
/lib32/libc.so.6(cfree+0x90)[0xf7709080]
iscan(_ZN5iscan9imgstream11find_dlopenEPKc+0x25d)[0x806caa1]
iscan(_ZN5iscan9imgstream6dlopenEPKc+0xf7)[0x806d875]
iscan(_ZN5iscan9pngstream9is_usableEv+0x54)[0x806e8a4]
iscan(_ZN13file_selector21add_dialog_extensionsEv+0x2dc)[0x8057574]
iscan(_ZN13file_selector13create_windowEP10_GtkWindowP10_GtkWidgetb+0xa8)[0x8057b98]
iscan(_ZN12view_manager12do_scan_fileEP15_scan_parameterP13file_selectorb+0x2f6)[0x806b4b4]
iscan(_ZN12view_manager10start_scanEv+0xc9)[0x806b5c7]
iscan[0x805bb33]
/usr/lib32/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x4f)[0xf7a2da4f]
/usr/lib32/libgobject-2.0.so.0(g_closure_invoke+0x129)[0xf7a20759]
/usr/lib32/libgobject-2.0.so.0[0xf7a34d1d]
/usr/lib32/libgobject-2.0.so.0(g_signal_emit_valist+0x8c6)[0xf7a36916]
/usr/lib32/libgobject-2.0.so.0(g_signal_emit+0x29)[0xf7a36c59]
/usr/lib32/libgtk-x11-2.0.so.0(gtk_button_clicked+0x8a)[0xf7bcc01a]
/usr/lib32/libgtk-x11-2.0.so.0[0xf7bcdb7e]
/usr/lib32/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x4f)[0xf7a2da4f]
/usr/lib32/libgobject-2.0.so.0[0xf7a1f079]
/usr/lib32/libgobject-2.0.so.0(g_closure_invoke+0x129)[0xf7a20759]
/usr/lib32/libgobject-2.0.so.0[0xf7a34975]
/usr/lib32/libgobject-2.0.so.0(g_signal_emit_valist+0x8c6)[0xf7a36916]
/usr/lib32/libgobject-2.0.so.0(g_signal_emit+0x29)[0xf7a36c59]
/usr/lib32/libgtk-x11-2.0.so.0(gtk_button_released+0x8a)[0xf7bcc0aa]
/usr/lib32/libgtk-x11-2.0.so.0[0xf7bcc0d1]
/usr/lib32/libgtk-x11-2.0.so.0[0xf7ca58d4]
/usr/lib32/libgobject-2.0.so.0[0xf7a1f079]
/usr/lib32/libgobject-2.0.so.0(g_closure_invoke+0x129)[0xf7a20759]
/usr/lib32/libgobject-2.0.so.0[0xf7a34ea0]
/usr/lib32/libgobject-2.0.so.0(g_signal_emit_valist+0x5fe)[0xf7a3664e]
/usr/lib32/libgobject-2.0.so.0(g_signal_emit+0x29)[0xf7a36c59]
/usr/lib32/libgtk-x11-2.0.so.0[0xf7dc4667]
/usr/lib32/libgtk-x11-2.0.so.0(gtk_propagate_event+0xc1)[0xf7c9eb21]
/usr/lib32/libgtk-x11-2.0.so.0(gtk_main_do_event+0x2b8)[0xf7c9fd88]
/usr/lib32/libgdk-x11-2.0.so.0[0xf7b17a9a]
/usr/lib32/libglib-2.0.so.0(g_main_context_dispatch+0x178)[0xf7998bf8]
/usr/lib32/libglib-2.0.so.0[0xf799be5e]
/usr/lib32/libglib-2.0.so.0(g_main_loop_run+0x1e7)[0xf799c1e7]
/usr/lib32/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xf7ca0264]
iscan(_ZN12view_manager4mainEv+0xb)[0x80689f1]
iscan(main+0x8f)[0x805b9d3]
/lib32/libc.so.6(__libc_start_main+0xe0)[0xf76af450]
iscan(__gxx_personality_v0+0x14d)[0x8055e01]
======= Memory map: ========
08048000-08089000 r-xp 00000000 08:05 3565639                            /usr/bin/iscan
08089000-0808d000 rw-p 00041000 08:05 3565639                            /usr/bin/iscan
0808d000-08331000 rw-p 0808d000 00:00 0                                  [heap]
f6a00000-f6a21000 rw-p f6a00000 00:00 0 
f6a21000-f6b00000 ---p f6a21000 00:00 0 
f6bc5000-f6c25000 rw-s 00000000 00:09 6127695                            /SYSV00000000 (deleted)
f6c25000-f6d31000 rw-p f6c25000 00:00 0 
f6d31000-f6d91000 rw-s 00000000 00:09 6094923                            /SYSV00000000 (deleted)
f6d91000-f6d97000 r-xp 00000000 08:05 2322007                            /usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
f6d97000-f6d98000 rw-p 00005000 08:05 2322007                            /usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
f6d98000-f6e9c000 rw-p f6d98000 00:00 0 
f6e9c000-f6f2d000 r--p 00000000 08:05 784904                             /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
f6f2d000-f6f2f000 r-xp 00000000 08:05 687305                             /usr/lib32/pango/1.6.0/modules/pango-basic-fc.so
f6f2f000-f6f30000 rw-p 00001000 08:05 687305                             /usr/lib32/pango/1.6.0/modules/pango-basic-fc.so
f6f30000-f6f36000 r--s 00000000 08:05 3287125                            /home/crgutierrez/.fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
f6f36000-f6f39000 r--s 00000000 08:05 3287347                            /home/crgutierrez/.fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
f6f39000-f6f3b000 r--s 00000000 08:05 3288358                            /home/crgutierrez/.fontconfig/d5f1ad098af19748a3db45524937c011-x86.cache-2
f6f3b000-f6f3c000 r--s 00000000 08:05 3287124                            /home/crgutierrez/.fontconfig/e3fa16a14183b06aa45b3e009278fd14-x86.cache-2
f6f3c000-f6f40000 r--s 00000000 08:05 3287123                            /home/crgutierrez/.fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
f6f40000-f6f41000 r--s 00000000 08:05 3287122                            /home/crgutierrez/.fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
f6f41000-f6f42000 r--s 00000000 08:05 3287121                            /home/crgutierrez/.fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
f6f42000-f6f45000 r--s 00000000 08:05 3287111                            /home/crgutierrez/.fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
f6f45000-f6f4c000 r--s 00000000 08:05 3287118                            /home/crgutierrez/.fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
f6f4c000-f6f4f000 r--s 00000000 08:05 3287117                            /home/crgutierrez/.fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
f6f4f000-f6f57000 r--s 00000000 08:05 3287116                            /home/crgutierrez/.fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
f6f57000-f6f5f000 r--s 00000000 08:05 3287115                            /home/crgutierrez/.fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
f6f5f000-f6f60000 r--s 00000000 08:05 3287363                            /home/crgutierrez/.fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
f6f60000-f6f82000 r--s 00000000 08:05 3287114                            /home/crgutierrez/.fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
f6f82000-f6f85000 r--s 00000000 08:05 3287113                            /home/crgutierrez/.fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
f6f85000-f6f8c000 r--s 00000000 08:05 3287112                            /home/crgutierrez/.fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
f6f8c000-f718d000 rw-p f6f8c000 00:00 0 
f718d000-f71c5000 r-xp 00000000 08:05 687293                             /usr/lib/iscan/libesint68.so.2.0.0
f71c5000-f71c6000 rw-p 00038000 08:05 687293                             /usr/lib/iscan/libesint68.so.2.0.0
f71c6000-f71c7000 rw-p f71c6000 00:00 0 
f71c7000-f71e5000 r-xp 00000000 08:05 3581391                            /usr/lib/sane/libsane-epkowa.so.1.0.15
f71e5000-f71eb000 rw-p 0001d000 08:05 3581391                            /usr/lib/sane/libsane-epkowa.so.1.0.15
f71eb000-f71ec000 rw-p f71eb000 00:00 0 
f71ec000-f71f5000 r-xp 00000000 08:05 2779960                            /lib32/libnss_files-2.7.so
f71f5000-f71f7000 rw-p 00008000 08:05 2779960                            /lib32/libnss_files-2.7.so
f71f7000-f71fe000 r-xp 00000000 08:05 2779958                            /lib32/libnss_compat-2.7.so
f71fe000-f7200000 rw-p 00006000 08:05 2779958                            /lib32/libnss_compat-2.7.so
f7201000-f7207000 r--s 00000000 08:05 3287356                            /home/crgutierrez/.fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
f7207000-f7209000 r--s 00000000 08:05 3287107                            /home/crgutierrez/.fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
f7209000-f7214000 r-xp 00000000 08:05 2027669                            /usr/lib32/gtk-2.0/2.10.0/engines/libmist.so
f7214000-f7215000 rw-p 0000a000 08:05 2027669                            /usr/lib32/gtk-2.0/2.10.0/engines/libmist.so
f7215000-f7254000 r--p 00000000 08:05 801270                             /usr/lib/locale/en_US.utf8/LC_CTYPE
f7254000-f7335000 r--p 00000000 08:05 3630155                            /usr/lib/locale/en_US.utf8/LC_COLLATE
f7335000-f7338000 rw-p f7335000 00:00 0 
f7338000-f734c000 r-xp 00000000 08:05 2779965                            /lib32/libpthread-2.7.so
f734c000-f734e000 rw-p 00013000 08:05 2779965                            /lib32/libpthread-2.7.so
f734e000-f7350000 rw-p f734e000 00:00 0 
f7350000-f7354000 r-xp 00000000 08:05 1212607                            /usr/lib32/libXdmcp.so.6.0.0
f7354000-f7355000 rw-p 00003000 08:05 1212607                            /usr/lib32/libXdmcp.so.6.0.0
f7355000-f7357000 r-xp 00000000 08:05 1212600                            /usr/lib32/libXau.so.6.0.0
f7357000-f7358000 rw-p 00001000 08:05 1212600                            /usr/lib32/libXau.so.6.0.0
f7358000-f7359000 rw-p f7358000 00:00 0 


---

### Post by magli on 2008-07-23
Bump.

I am getting the same errors as bertwagner. Trying to install a V350.

---

### Post by x20mar on 2008-08-16
Hi,

Maybe some can help on this one. I'm trying to compile a 64bit deb archive for iscan. Now I am actually getting there but I've seem to hit a point where I'm not sure now how to progress to the next step. Here's the tail end of the make report:

```
/usr/bin/ld: ./.libs/libsane-epkowa-s.a(libsane_epkowa_s_la-epkowa-s.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
./.libs/libsane-epkowa-s.a(libsane_epkowa_s_la-epkowa-s.o): could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [libsane-epkowa.la] Error 1
make[3]: Leaving directory `/usr/local/src/iscan-2.10.0/backend'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/local/src/iscan-2.10.0/backend'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/iscan-2.10.0'
make: *** [all] Error 2

``` 

So yeah I understand the problem is libsane-epkowa-s.a and when it's getting compiled I have to stick on -fPIC at some point.

Suggestions?

Thanks

---

### Post by fuhrysteve on 2008-09-01
Bump. I am also getting the same errors as bertwagner. I'm trying to install a Epson 4490 Photo, but none of the rpm files will convert to deb.

---

### Post by fuhrysteve on 2008-09-07
> **x20mar said:**
> Hi,

Maybe some can help on this one. I'm trying to compile a 64bit deb archive for iscan. Now I am actually getting there but I've seem to hit a point where I'm not sure now how to progress to the next step. 

[...]

So yeah I understand the problem is libsane-epkowa-s.a and when it's getting compiled I have to stick on -fPIC at some point.

I ran into the same error. You need to clear the make stuff, then reconfigure with --with-pic

```
make clean && make distclean
./configure --with-pic
```

---

### Post by Lonthong on 2008-09-07
Try installing these first:
sudo apt-get install debhelper debconf build-essential fakeroot

---

### Post by tienhn on 2008-09-27
My solution for all of my scanning work: I use VirtualBox to install XP and use the scanner software to do my scanning. In the case of Epson scanner, the Windows scanning software is much better than using xscan, that is if you get it to work at all. The native Windows version has great profile for film scanning.

I hope I am not starting any flame here but scanning is one of the weak area in Linux world. I don't think it is the problem with Linux but rather lack of software support from hardware manufacture.

Cheers.

---

### Post by cjcj on 2008-11-11
I just want to thank people for their efforts on this thread and add my name to those looking for an answer.

I would like to get my Stylus Photo RX520 (all in one) scanner working in 64 bit Ubuntu. It worked fine in 32 bit with iscan. Why has Epson abandonned Linux in this way? After buiying the printer/scanner because Epson supported linux with a driver only a couple of years ago I am now disillusioned with their attitude. Surely Epson must be losing friends this way. 

Chris

---

### Post by bernecky on 2008-11-24
I'm also fighting with a 4490 on AMD64. I found this, which let me
build a .deb file properly:

# Edit the Perl module that alien uses when converting to deb-files and replace the line that prints the package architecture with 'amd64':

sudo vi /usr/share/perl5/Alien/Package/Deb.pm

Then replace this:

print OUT "Architecture: ".$this->arch."\n";

with this:

print OUT "Architecture: amd64\n";

Save the changes and exit the file.

Running "sudo alien ..." on the resulting .deb files did result in
a copy of iscan that properly previews images on the scanner!!
So, this is a good step forward (No thanks to Epson nor Avasys).

However, an attempt to ACTUALLY scan something iscan results in this:

** glibc detected *** iscan: double free or corruption (fasttop)

So, I'm stuck again/still.

xsane still can't drive the box, even for a preview. It gives
"Failed to start scanner. Invalid argument."

---

### Post by chicken159 on 2008-11-28
FANTASTIC - I'd got used to things 'just working', until I got a V200 scanner and have spent the last few hours trying to get life into it...turned out the solution was quite simple. Before anyone gets too excited though...I think it only works for me because I have Hamrick Vuescan installed. Basically - I installed **just the plugin**, getting round the architecture as suggested, and Vuescan now detects and works fine with it. Thanks for the tip...


> **bernecky said:**
> I'm also fighting with a 4490 on AMD64. I found this, which let me
build a .deb file properly:

# Edit the Perl module that alien uses when converting to deb-files and replace the line that prints the package architecture with 'amd64':

sudo vi /usr/share/perl5/Alien/Package/Deb.pm

Then replace this:

print OUT "Architecture: ".$this->arch."\n";

with this:

print OUT "Architecture: amd64\n";

Save the changes and exit the file.

Running "sudo alien ..." on the resulting .deb files did result in
a copy of iscan that properly previews images on the scanner!!
So, this is a good step forward (No thanks to Epson nor Avasys).

However, an attempt to ACTUALLY scan something iscan results in this:

** glibc detected *** iscan: double free or corruption (fasttop)

So, I'm stuck again/still.

xsane still can't drive the box, even for a preview. It gives
"Failed to start scanner. Invalid argument."

---

### Post by vhozard on 2008-12-11
To fix the [COLOR="DarkRed"]*** glibc detected *** iscan: double free or corruption[/COLOR] problem, just type:
```
export MALLOC_CHECK_=0
```
And then:
```
iscan
```

Greets Vhozard,

---

### Post by vgrisham on 2008-12-20
Man, this scanner thing really stinks. This is the ONLY thing I haven't been able to resolve permanently on Ubuntu. I have an Epson Perfection (HA!) 2580 flatbed scanner. It has worked at times, and in fact worked in Gutsy and Hardy, but I'm now on Intrepid (64 bit) and it ain't workin'.

I've tried building the iscan backend from source, but it fails during make install. I just tried the alien thing, and I've installed my two debs without errors, but when I try to launch iscan I get the error: "iscan: error while loading shared libraries: libjpeg.so.62: cannot open shared object file: No such file or directory"

Does anyone know what to make of that error?

---

### Post by dryder on 2009-02-17
Does anybody know if this thread helps at all? (too technical for me):

[COLOR="RoyalBlue"][http://ubuntuforums.org/showpost.php?p=2849759&postcount=1]("http://ubuntuforums.org/showpost.php?p=2849759&postcount=1")[/COLOR]

David

---

### Post by Darkk on 2009-03-01
Would have been nice if Epson release their source code of both the driver and software so we can compile it to work properly in 64bit.

Having this mixture of 32bit libraries in 64bit isn't really a good thing.  But I guess it's kinda a workaround at the moment.

---

### Post by dryder on 2009-03-01
Does that mean you think it would work?

Has anybody got it working n AMD64?

David:(

Yes - I agree it would be nice if they won't develop a 64bit driver then let the community do it .... in fact, it would be good business sense. Perhaps they don't mind losing sales.

---

### Post by julian.coccia on 2009-03-04
Just in case anyone is experiencing a 2400dpi limitation on the V350 Photo (I think it also happens with the V100), there is a workaround.

[http://juliancoccia.posterous.com/removing-2400dpi-limitation-fo](http://juliancoccia.posterous.com/removing-2400dpi-limitation-fo)

Pasting it all here:

I have recently realized that the Linux driver for the Epson Perfection V350 has an imposed limitation of 2400dpi, while the scanner is capable of doing 4800dpi under Windows.
 
Apparently, this scanner requires a binary plugin which returns a maximum scanner resolution to the scanning problem. Fortunately, the scanner program is distributed under GPL and the code is made available here: [http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)
 
After a quick look at the code, I realized the "iscan" scanning program was limiting the resolution settings to whatever the proprietary plugin was returning as max_resolution. However, if you remove this limitation and tell it to scan at 4800, it will do it. 
 
As a result of that, I now have 4800dpi support under Linux. If you are interested, download the source and replace the frontend/pisa_main_window.cc file with the one I include here before building. If you are lazy, instead, simply install the binary version of the scanner and plugins and replace the /usr/bin/iscan file with the one I include here.
 
Modified iscan source and binary:
[http://julian.coccia.com/stuff/iscan-4800dpi.zip](http://julian.coccia.com/stuff/iscan-4800dpi.zip)

---

### Post by Toadlips on 2009-03-14
Dryder and others,

I've been trying all week to get my Epson Perfection 4490 Photo working in Ubuntu 8.10 AMD64 (x64), and I was just about to ride the great donkey into the pit of despair, as nothing would work!

Well, just as I was literally about to wipe out my installation and start over with 32 bit, I went to [www.avasys.jp](www.avasys.jp) to make sure I had the latest packages, but thinking I'd be stuck with 32 bit RPMs.

Lo and behold the AMD64 version is NOW AVAILABLE, in .deb form no less!!  I couldn't believe it -- truly a miracle.  I swear it was not there the day before.

I had to download the amd64 version of the libltdl3 library from [http://packages.ubuntu.com/hardy/libltdl3]("http://packages.ubuntu.com/hardy/libltdl3") to get it to install and had to remove a couple of packages (libsane-extras and my 2 previously botched iscan packages), but I didn't even break a sweat!

After that, I rocked the GIMP with a couple of scans through Xsane.  Batch scan is working great!

What a great day!
Toadlips

---

### Post by vgrisham on 2009-03-14
Nice! 

Now if they'd only publish one for my "Perfection" 2580.

---

### Post by fuhrysteve on 2009-03-14
Anyone else getting "Could not send command to scanner. Check the scanner's status"? I tried going through the steps specified in the manual, but here's what i came up with:

```
steve@dickens:~$ sane-find-scanner | grep 0x04b8
found USB scanner (vendor=0x04b8 [EPSON], product=0x0119 [EPSON Scanner]) at libusb:005:002

steve@dickens:~$ sudo chmod 0666 /proc/bus/usb/005/002
chmod: cannot access `/proc/bus/usb/005/002': No such file or directory

steve@dickens:~$ ls -l /proc/bus/usb/
total 0
```

edit: the message comes when trying to load iscan

---

### Post by dryder on 2009-03-14
Toadlips,

How did you get rid of previously botched installs of iscan?

after  a cl -uninstall (it's not is synaptic) I still have files & folders. Did you search for them manually?

David

---

### Post by dryder on 2009-03-14
Hi,

I assume you downloaded the debs instead of converting the rpm as with i386?

Well, I downloaded the debs and they wouldn't install (gdedi). So I deleted all files and folders I could find with Search that contained 'iscan', as I felt it was reasonable to assume that they could only have come from my botched attempts at installing the i386 drivers.

But now xsane is broken and will not open the preview scanning window. I use xsane on an HP multi-purpose scanner in hardy amd64.

How can do I completely remove and reinstall xsane, please, so I get it back to the stage after installation?

David

---

### Post by Toadlips on 2009-03-15
Hi Dryder,

Please bear in mind that I'm a noob at this, so use any advice from me at your own risk! :)

I went to the terminal and did a ```
dpkg -l iscan*
``` and I saw the two iscans I had originally installed -- the plugin and the plain old iscan.  Then, I used ```
dpkg -r
``` with the names found in the list to uninstall the 2 iscan packages.  I did the same dpkg removal process with libsane-extras.  You may need to force a removal from dpkg (check the options under ```
dpkg --help
``` since you already deleted the directories.  I don't know whether deleting the directories releases the conflict earmarks in the package manager, so that might be what your problem is.

Other than that, I did have to install the libltdl3 package prior to installing.

xsane is handled in the Synaptic Package Manager, so you should be able to go to the Synaptic gui and mark it for reinstallation and apply.

Were you getting dependency errors from gdedi?

Good luck!!
Toadlips

---

### Post by Toadlips on 2009-03-15
Hi fuhrysteve,

I tried those same steps, listing the contents of the proc/bus/usb/xxx/xxx directory, and nothing shows up under it, just like yours.  However, the scanner is working, so maybe that's not an issue?

Hope that helps...somewhat!
Toadlips

---

### Post by fuhrysteve on 2009-03-15
How did you get it working though? I feel like it's a permissions problem w/ the usb stuff, but I'm not sure. xsane's saying no devices found, I get that error with iscan, scanimage -L is saying No scanners were identified...

Am I missing something?

---

### Post by Toadlips on 2009-03-15
Hi fuhrysteve,

Is your current user in the scanner group?  I don't know much about it, but that was something I came across in my original search, so I did add myself to it.

I couldn't get System->Administration->Users and Groups->Manage Groups to work, but maybe you can.

Otherwise, try: ```
sudo adduser USER scanner
```

Or maybe gpasswd to add the user to the group?  I can't remember the group ID, but I don't know if that matters.

Strangely, I can't seem to remove myself from the group to test out if that would cause a problem!

Hope that helps!
Toadlips

---

### Post by dryder on 2009-03-15
Toadlips

Thanks for your replies.

Did you install both libltdl3_1.5.26-1ubuntu1_amd64.deb and iscan-plugin-gt-x750_2.1.0-4_amd64.deb?

If so, presumably in that order?

Where did you find out about needing iscan_2.18.0-2_amd64.deb?

David

---

### Post by fuhrysteve on 2009-03-15
AH! I figured out my problem! I just didn't install the iscan-plugin package, since the stupid pdf didn't even mention it. I installed the iscan-plugin package (64-bit) and everything works fine.

Thanks for the help Toadlips!

---

### Post by Toadlips on 2009-03-15
Hi fuhrysteve,

The funny thing is that I didn't see that pdf document until AFTER I had already installed the scanner and had it working, but I had already tried everything I could find in the forums (chroot, conf entries, etc.).

To answer Dryder's question:

I installed:

1) libltdl3_1.5.26-1ubuntu1_amd64.deb
2) iscan_2.18.0-2_amd64.deb
3) iscan-plugin-gt-x750_2.1.0-4_amd64.deb

I'm 90% sure it was in that order because one of those iscan packages had a dependency of "iscan", and I'm pretty sure it was the plugin that required the straight iscan package to be installed first.

After that, everything just worked, iscan and xsane both.

Please let me know if you need any more details and I will do what I can!  I know how frustrating this can be and how satisfying it is when it all works!  :)

Good luck!
Toadlips

---

### Post by dryder on 2009-03-15
Thank you Toadlips - it works!

What confused me was the documentation not mentioning the plugins package.


:D

---

### Post by Toadlips on 2009-03-15
Awesome!!!!

I think we've learned a lesson today -- only turn to the documentation as a last resort!!!  :)

Enjoy!
Toadlips

---

### Post by dryder on 2009-03-17
Toadlips

Where did you find out about needing libltdl3_1.5.26-1ubuntu1_amd64.deb?

I can't find reference to it anywhere. Thanks

David

---

### Post by jgull8502 on 2009-03-22
Hopefully this is an acceptable place to post about my problem: I seem to be having issues getting VueScan to recognize my 4490. 

I've installed the iscan and iscan plugin as well as libltd3. Everything installed fine. Iscan works properly and will successfully scan. However, when opening VueScan I get the following error:[INDENT] VueScan found an Epson Perfection 4490, but no Epson software for this scanner was found on your system. Try downloading a driver for this scanner from [www.avasys.jp/english]("http://www.avasys.jp/english"). See the VueScan Release Notes for more information.

[/INDENT]As far as I know, I have the 32bit compatibility libraries installed. 

I looked at the VueScan Release notes and found the following:[INDENT]  If you're using the Epson Perfection 4490 (GT-X750), make sure you have /usr/lib/libesint54.so from the [Epson AVASYS SANE distribution]("http://www.avasys.jp/english/linux_e/dl_scan.html"). You also need to set up the environment variable SANEI_EPKOWA_FIRMWAREFILE to point to the firmware file esfw54.bin. For newer versions of iscan, set up ISCAN_FW_DIR instead.
  You need to make sure all of the /dev/sg* devices are read/write   accessible.  To see what scanners are available, type "cat /proc/scsi/scsi".
[/INDENT]I noticed that libesint54.so was in /usr/lib/iscan/ instead of in /usr/lib/ so I tried making a symbolic link, but that didn't work. I also tried setting both variables using "env ISCAN_FW_DIR=path/to/esfw54.bin" and that also did not work. I did "cat /proc/scsi/scsi" and no scanners come up, only my DVD drive and HDD.


Any ideas on what do do next?[FONT=Comic Sans MS, Arial]
[/FONT]

---

### Post by fuhrysteve on 2009-03-29
Anyone else getting this warning on apt-get update w/ Jaunty (64-bit)?

```
W: Ignoring Provides line with DepCompareOp for package iscan-interpreter
W: You may want to run apt-get update to correct these problems
```

Didn't have this warning under Intrepid.. Everything works fine of course, but warning messages are lame.

---

### Post by rbmorse on 2009-03-30
> **jgull8502 said:**
> Hopefully this is an acceptable place to post about my problem: I seem to be having issues getting VueScan to recognize my 4490. 

I've installed the iscan and iscan plugin as well as libltd3. Everything installed fine. Iscan works properly and will successfully scan. However, when opening VueScan I get the following error:[INDENT] VueScan found an Epson Perfection 4490, but no Epson software for this scanner was found on your system. Try downloading a driver for this scanner from [www.avasys.jp/english]("http://www.avasys.jp/english"). See the VueScan Release Notes for more information.

[/INDENT]As far as I know, I have the 32bit compatibility libraries installed. 

I looked at the VueScan Release notes and found the following:[INDENT]  If you're using the Epson Perfection 4490 (GT-X750), make sure you have /usr/lib/libesint54.so from the [Epson AVASYS SANE distribution]("http://www.avasys.jp/english/linux_e/dl_scan.html"). You also need to set up the environment variable SANEI_EPKOWA_FIRMWAREFILE to point to the firmware file esfw54.bin. For newer versions of iscan, set up ISCAN_FW_DIR instead.
  You need to make sure all of the /dev/sg* devices are read/write   accessible.  To see what scanners are available, type "cat /proc/scsi/scsi".
[/INDENT]I noticed that libesint54.so was in /usr/lib/iscan/ instead of in /usr/lib/ so I tried making a symbolic link, but that didn't work. I also tried setting both variables using "env ISCAN_FW_DIR=path/to/esfw54.bin" and that also did not work. I did "cat /proc/scsi/scsi" and no scanners come up, only my DVD drive and HDD.


Any ideas on what do do next?[FONT=Comic Sans MS, Arial]
[/FONT]
Jgull, VueScan can't use a 64-bit driver plugin. Hamrick mentions this in reference to the 64-bit Windows installation, but the Linux version has the same problem.  

Having said that, I use Vuescan with my 4490 on 64-bit Ubuntu without problem.  Right now I have this in the 9.04 beta. I don't know if it works for 8.10 because people keep screwing with UDEV and the way it detects devices.  If you have 8.10 and this does not work let me know as I have a UDEV rule statement that might help. 

Note that it uses the ***32-bit 4490/GT-750 plugin***. All other files required are from the 64-bit repositories.

Before you try this you should remove any existing iscan and gt-750 plugin files that may be present.  If you can't unisntall, it may be sufficient to simply remove the folders /usr/share/iscan and /usr/lib/iscan and their contents and any links you may have installed that point to those directories, and any file with the name iscan in you /home directory (check for hidden files too). 

Use the user and group administration utility (system > administration > Users and Groups) to add your user ID to the group "scanner". Log out/log in or reboot to make the change effective. 

Install or verify the following packages are installed:

    sane
    xsane
    libsane
    libsane-extras
    xsane-common
    sane-utils

Download the 32-bit GT750 plugin .deb package (GT750 is the international model number for the unit sold as the 4490 in certain countries) from the Avasys site. The 32-bit driver is correct as VueScan cannot use the 64-bit driver. You do not need the iscan package. The Avasys site is at: 

[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)

Make the desktop (or directory in which you saved the plugin) the current directory and install the .deb package from a terminal with the command:

sudo dpkg -i --force-architecture iscan-plugin<tab><enter>

Download and unpack the latest VueScan package for Ubuntu from [www.hamick.com]("http://www.hamick.com"). 

Move the entire VueScan folder to ~/home.   

Build the launcher in the graphics group menu using system > preferences > main menu from the upper panel.  A suitable scanner icon is located at /usr/share/icons/gnome/scalable/devices/scanner.svg.  Otherwise you can launch vuescan from the terminal. 

Installation complete.

---

### Post by fuhrysteve on 2009-03-30
I exchanged emails with Alesh Slovak from Avasys regarding this warning I'm getting on Jaunty when i use apt-get:

```
W: Ignoring Provides line with DepCompareOp for package iscan-interpreter
W: You may want to run apt-get update to correct these problems
```

He said it looks like a problem with their packaging that they're going to try and correct in the next release. It does not, however, seem to cause any problems whatsoever.

---

### Post by margolism on 2009-04-01
My first posting on the ubuntu forums...

Here's a simple solution I just came up with, and I am far from being a Ubuntu or linux expert.  Note that I have an Epson V500 scanner, but I imagine this works for all Epson scanners with drivers on the Avasys website.  I am running Ubuntu 8.10 64-bit version, and I have an Epson V500 scanner.  

My issue was that I wanted to be able to run VueScan, iscan, and gscan2pdf.  The other solutions I have seen let me either run VueScan (which requires 32 bit scanner libraries) OR software that requires the 64 bit scanner libraries, but not both.  This simple solution lets me use my scanner with all scanning apps, regardless of which libraries it needs.   

First, I installed the AMD64 bit versions of iscan and iscan-plugin, which I got from the Avasys website.  No force architecture stuff needed, since these are built for the 64bit platform. 

I also downloaded (but did not install) the 32 bit version of the iscan-plugin from the Avaya website.  (iscan-plugin-whatever-i386.deb) 

Don't install the 32 bit version DEB using the package manager.  Instead, open this as an archive , go to data.tar.gz, and go to the /usr/lib/iscan folder. 

Extract the file libesint7C.so.2.0.1 (might have a different name if using a different scanner, I don't know.)  This is the 32bit file that VueScan needs to run.  You don't need anything else from this package. 

I renamed this file driver32 and copied it to the /usr/lib/iscan directory.

I then went to the /usr/lib/iscan directory and made a copy of the 64 bit version of libesint7C.so.2.0.1 already there, from when I installed the 64 bit iscan-plugin DEB package.  I called this file driver64

So now I have driver32 (the 32 bit scanner libraries VueScan requires), and driver64 (the 64 bit version all the other scanner apps I use require.)

Basically, I wrote a super simple bash script that copies driver32 to libesint7C.so.2.0.1 when you run VueScan, and restores the 64bit version once you quit VueScan.  Here it is:

rm /usr/lib/iscan/libesint7C.so.2.0.1
cp /usr/lib/iscan/driver32 /usr/lib/iscan/libesint7C.so.2.0.1
/usr/VueScan/vuescan
rm /usr/lib/iscan/libesint7C.so.2.0.1
cp /usr/lib/iscan/driver64 /usr/lib/iscan/libesint7C.so.2.0.1

I called this script vuescan.sh, and I simply run this script to run VueScan.  

If there are any other scanning apps that can only work with the 32 bit libraries, I would assume this approach would work for them too.

Note that I had to change the permissions of the /usr/lib/iscan directory, but other than that, it's working great!

Hope this is helpful to someone!

Cheers,



Mark

---

### Post by Naegling23 on 2009-04-29
Im getting the following error when trying to install:

(Reading database ... 102095 files and directories currently installed.)
Unpacking iscan (from .../iscan_2.19.0-4_amd64.deb) ...
/var/lib/dpkg/tmp.ci/preinst: 29: Bad substitution
dpkg: error processing /home/glaurung/Desktop/iscan_2.19.0-4_amd64.deb (--install):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /home/glaurung/Desktop/iscan_2.19.0-4_amd64.deb

any idea what is going on?

---

### Post by fuhrysteve on 2009-04-29
> **Naegling23 said:**
> Im getting the following error when trying to install:

(Reading database ... 102095 files and directories currently installed.)
Unpacking iscan (from .../iscan_2.19.0-4_amd64.deb) ...
/var/lib/dpkg/tmp.ci/preinst: 29: Bad substitution
dpkg: error processing /home/glaurung/Desktop/iscan_2.19.0-4_amd64.deb (--install):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /home/glaurung/Desktop/iscan_2.19.0-4_amd64.deb

any idea what is going on?

you may want to take a look at this:
[http://ubuntuforums.org/showthread.php?t=1000341&page=2](http://ubuntuforums.org/showthread.php?t=1000341&page=2)

looks like someone had a similar error and solved it by using an older version... are you on jaunty yet, or is this with gutsy? (I assume you are sure you are using a 64bit installation too..)

---

### Post by Naegling23 on 2009-04-30
thanks, the old drivers did install, I had to remove libsane-extras as it was conflicting, but everything went fine.  Scanner is working

Glad to have it back, This broke at some point during my intrepid install, of course, everything broke, so I reformatted and am in the process of rebuilding my system.  Glad to have my scanner back!!

---

### Post by klemi on 2009-05-18
Do I understand as right, the Jaunty Jackalope 64 bit with vuescan and Epson printer functions?

Thanks

Klemi

---

### Post by myoldhouse on 2009-08-13
Mark, this is a great idea. I also have an Epson 4490, Ubuntu 9.04 AMD64 install and wasn't able to get VueScan to work (iScan and XSane worked fine). Your script to exchange the 64 bit library file libesintXX.so.2.0.1, where 'XX' is 54 for the 4490 scanner, for the 32 bit one, run VueScan and then restore the 64 bit library after VueScan closes works perfectly. Thanks for such a great tip!

---

### Post by klemi on 2009-08-20
Hello Mark,

I still have 2 small questions to Vuescan:

1.) How have you installed for more than one user Vuescan?

2.) Can you explain to me more exactly how have you integrated the Script "vuescan.sh" into Ubuntu? How have you made this?

Thank you

Klemi

---

