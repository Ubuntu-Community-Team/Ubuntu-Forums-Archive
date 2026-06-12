---
title: "Session lasts for less than 10 seconds crash"
date: 2007-10-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by ST.x on 2007-10-04
First I thought compiz fusion was causing the crash(I had everything stable before this), so I removed compiz fusion and I still cant login to the 'last session' or the 'GNOME session'(default) but im now using the failsafe GNOME session. Before I removed compiz fusion the message I got was this:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "seynthan"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/seynthan-lappy:/tmp/.ICE-unix/6486
Checking for Xgl: not present. 
Initializing gnome-mount extension
Detected PCI ID for VGA: 01:00.0 0300: 10de:01d7 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: Checking for Xgl: not present. 
present. 
Checking for Composite extension: Password:
*** glibc detected *** x-session-manager: corrupted double-linked list: 0x0000000000942d00 ***
======= Backtrace: =========
/lib/libc.so.6[0x2aaff7b1cdec]
/lib/libc.so.6(__libc_malloc+0x93)[0x2aaff7b1de23]
/usr/lib/libICE.so.6(IceAcceptConnection+0x58)[0x2aaff49f44a8]
x-session-manager[0x4101bb]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1b4)[0x2aaff762ea14]
/usr/lib/libglib-2.0.so.0[0x2aaff763185d]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0x2aaff7631b6a]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa3)[0x2aaff4f65023]
x-session-manager(main+0x4d4)[0x410d14]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2aaff7ac7b44]
x-session-manager[0x40caf9]
======= Memory map: ========
00400000-00424000 r-xp 00000000 08:08 1733764                            /usr/bin/gnome-session
00624000-00626000 rw-p 00024000 08:08 1733764                            /usr/bin/gnome-session
00626000-009c9000 rw-p 00626000 00:00 0                                  [heap]
40000000-40001000 ---p 40000000 00:00 0 
40001000-40801000 rw-p 40001000 00:00 0 
2aaaaaaaf000-2aaaaaab9000 r--s 00000000 08:08 98194                      /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86-64.cache-2
2aaaaaab9000-2aaaaaabc000 r--s 00000000 08:08 103832                     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86-64.cache-2
2aaaaaabc000-2aaaaaac0000 r--s 00000000 08:08 100605                     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86-64.cache-2
2aaaaaac0000-2aaaaaac2000 r--s 00000000 08:08 103834                     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86-64.cache-2
2aaaaaac2000-2aaaaaacc000 r--s 00000000 08:08 100607                     /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86-64.cache-2
2aaaaaacc000-2aaaaaacd000 r--s 00000000 08:08 100608                     /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86-64.cache-2
2aaaaaacd000-2aaaaaad5000 r--s 00000000 08:08 100656                     /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86-64.cache-2
2aaaaaad5000-2aaaaaada000 r--s 00000000 08:08 103835                     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86-64.cache-2
2aaaaaada000-2aaaaaadc000 r--s 00000000 08:08 100724                     /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86-64.cache-2
2aaaaaadc000-2aaaaaadd000 r--s 00000000 08:08 100725                     /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86-64.cache-2
2aaaaaadd000-2aaaaaae1000 r--s 00000000 08:08 100728                     /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86-64.cache-2
2aaaaaae1000-2aaaaaae4000 r--s 00000000 08:08 100739                     /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86-64.cache-2
2aaaaaae4000-2aaaaaaea000 r--s 00000000 08:08 100740                     /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86-64.cache-2
2aaaaaaea000-2aaaaaaf1000 r--s 00000000 08:08 100741                     /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86-64.cache-2
2aaaaaaf1000-2aaaaaaf2000 r--s 00000000 08:08 100742                     /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86-64.cache-2
2aaaaaaf2000-2aaaaaaf5000 r--s 00000000 08:08 100743                     /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86-64.cache-2
2aaaaaaf5000-2aaaaaaf7000 r--s 00000000 08:08 100744                     /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86-64.cache-2
2aaaaaaf7000-2aaaaaafa000 r--s 00000000 08:08 100745                     /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86-64.cache-2
2aaaaaafa000-2aaaaab01000 r--s 00000000 08:08 103837                     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86-64.cache-2
2aaaaab01000-2aaaaab05000 r--s 00000000 08:08 100747                     /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86-64.cache-2
2aaaaab05000-2aaaaab06000 r--s 00000000 08:08 103838                     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86-64.cache-2
2aaaaab06000-2aaaaab07000 r--s 00000000 08:08 100749                     /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86-64.cache-2
2aaaaab07000-2aaaaab08000 r--s 00000000 08:08 100750                     /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86-64.cache-2
2aaaaab08000-2aaaaab0a000 r--s 00000000 08:08 100751                     /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86-64.cache-2
2aaaaab0a000-2aaaaab0b000 r--s 00000000 08:08 100752                     /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86-64.cache-2
2aaaaab0b000-2aaaaab15000 r--s 00000000 08:08 98209                      /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86-64.cache-2
2aaaaab15000-2aaaaab1a000 r--s 00000000 08:08 98187                      /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
2aaaaab1a000-2aaaaab1e000 r--s 00000000 08:08 99987                      /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86-64.cache-2
2aaaaab1e000-2aaaaab25000 r--s 00000000 08:08 99989                      /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86-64.cache-2
2aaaaab25000-2aaaaab28000 r--s 00000000 08:08 100059                     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86-64.cache-2
2aaaaab28000-2aaaaab2c000 r--s 00000000 08:08 103854                     /var/cache/fontconfig/9caec58b795a0e0785d8ba94b93e4224-x86-64.cache-2
2aaaaab2c000-2aaaaab4b000 r--s 00000000 08:08 98221                      /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86-64.cache-2
2aaaaab4b000-2aaaaab4c000 r--s 00000000 08:08 100061                     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
2aaaaab4c000-2aaaaab54000 r--s 00000000 08:08 100062                     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
2aaaaab54000-2aaaaab5f000 r--s 00000000 08:08 100065                     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
2aaaaab5f000-2aaaaab62000 r--s 00000000 08:08 100067                     /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86-64.cache-2
2aaaaab62000-2aaaaab65000 r--s 00000000 08:08 100068                     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86-64.cache-2
2aaaaab65000-2aaaaab6c000 r--s 00000000 08:08 100069                     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
2aaaaab6c000-2aaaaab6e000 r--s 00000000 08:08 100144                     /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86-64.cache-2
2aaaaab6e000-2aaaaab70000 r--s 00000000 08:08 100276                     /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86-64.cache-2
2aaaaab70000-2aaaaab72000 r--s 00000000 08:08 100277                     /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86-64.cache-2
2aaaaab72000-2aaaaab75000 r--s 00000000 08:08 100278                     /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86-64.cache-2
2aaaaab75000-2aaaaab76000 r--s 00000000 08:08 100280                     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
2aaaaab76000-2aaaaab77000 r--s 00000000 08:08 100281                     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86-64.cache-2
2aaaaab77000-2aaaaab7c000 r--s 00000000 08:08 100315                     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86-64.cache-2
2aaaaab7c000-2aaaaab7d000 r--s 00000000 08:08 100326                     /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86-64.cache-2
2aaaaab7d000-2aaaaab7e000 r--s 00000000 08:08 100337                     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86-64.cache-2
2aaaaab7e000-2aaaaab81000 r--s 00000000 08:08 100343                     /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86-64.cache-2
2aaaaab81000-2aaaaab82000 r--s 00000000 08:08 100348                     /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86-64.cache-2
2aaaaab82000-2aaaaab8a000 r--s 00000000 08:08 98205                      /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
2aaaaab8a000-2aaaaab8d000 r-xp 00000000 08:08 1832568                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
2aaaaab8d000-2aaaaad8c000 ---p 00003000 08:08 1832568                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
2aaaaad8c000-2aaaaad8d000 rw-p 00002000 08:08 1832568                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
2aaaaad8d000-2aaaaae0a000 r--p 00000000 08:08 1916444                    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
2aaaaae1d000-2aaaaae2a000 r-xp 00000000 08:08 2076766                    /lib/libgcc_s.so.1
2aaaaae2a000-2aaaab02a000 ---p 0000d000 08:08 2076766                    /lib/libgcc_s.so.1
2aaaab02a000-2aaaab02b000 rw-p 0000d000 08:08 2076766                    /lib/libgcc_s.so.1
2aaaac000000-2aaaac021000 rw-p 2aaaac000000 00:00 0 
2aaaac021000-2aaab0000000 ---p 2aaaac021000 00:00 0 
2aaff3d03000-2aaff3d20000 r-xp 00000000 08:08 2076839                    /lib/ld-2.6.1.so
2aaff3d20000-2aaff3d23000 rw-p 2aaff3d20000 00:00 0 
2aaff3f1f000-2aaff3f21000 rw-p 0001c000 08:08 2076839                    /lib/ld-2.6.1.so
2aaff3f21000-2aaff3f23000 r-xp 00000000 08:08 1734581                    /usr/lib/libXau.so.6.0.0
2aaff3f23000-2aaff4122000 ---p 00002000 08:08 1734581                    /usr/lib/libXau.so.6.0.0
2aaff4122000-2aaff4123000 rw-p 00001000 08:08 1734581                    /usr/lib/libXau.so.6.0.0
2aaff4123000-2aaff412d000 r-xp 00000000 08:08 1734768                    /usr/lib/libesd.so.0.2.36
2aaff412d000-2aaff432d000 ---p 0000a000 08:08 1734768                    /usr/lib/libesd.so.0.2.36
2aaff432d000-2aaff432e000 rw-p 0000a000 08:08 1734768                    /usr/lib/libesd.so.0.2.36
2aaff432e000-2aaff4344000 r-xp 00000000 08:08 1734892                    /usr/lib/libgnome-desktop-2.so.2.3.5
2aaff4344000-2aaff4544000 ---p 00016000 08:08 1734892                    /usr/lib/libgnome-desktop-2.so.2.3.5
2aaff4544000-2aaff4545000 rw-p 00016000 08:08 1734892                    /usr/lib/libgnome-desktop-2.so.2.3.5
2aaff4545000-2aaff45de000 r-xp 00000000 08:08 1734920                    /usr/lib/libgnomeui-2.so.0.1788.4
2aaff45de000-2aaff47de000 ---p 00099000 08:08 1734920                    /usr/lib/libgnomeui-2.so.0.1788.4
2aaff47de000-2aaff47e4000 rw-p 00099000 08:08 1734920                    /usr/lib/libgnomeui-2.so.0.1788.4
2aaff47e4000-2aaff47e5000 rw-p 2aaff47e4000 00:00 0 
2aaff47e5000-2aaff47ee000 r-xp 00000000 08:08 1734571                    /usr/lib/libSM.so.6.0.0
2aaff47ee000-2aaff49ee000 ---p 00009000 08:08 1734571                    /usr/lib/libSM.so.6.0.0
2aaff49ee000-2aaff49ef000 rw-p 00009000 08:08 1734571                    /usr/lib/libSM.so.6.0.0
2aaff49ef000-2aaff4a06000 r-xp 00000000 08:08 1734553                    /usr/lib/libICE.so.6.3.0
2aaff4a06000-2aaff4c05000 ---p 00017000 08:08 1734553                    /usr/lib/libICE.so.6.3.0
2aaff4c05000-2aaff4c07000 rw-p 00016000 08:08 1734553                    /usr/lib/libICE.so.6.3.0
2aaff4c07000-2aaff4c0a000 rw-p 2aaff4c07000 00:00 0 
2aaff4c0a000-2aaff4c21000 r-xp 00000000 08:08 1734890                    /usr/lib/libgnome-2.so.0.1800.0
2aaff4c21000-2aaff4e20000 ---p 00017000 08:08 1734890                    /usr/lib/libgnome-2.so.0.1800.0
2aaff4e20000-2aaff4e22000 rw-p 00016000 08:08 1734890                    /usr/lib/libgnome-2.so.0.1800.0
2aaff4e22000-2aaff4e23000 rw-p 2aaff4e22000 00:00 0 
2aaff4e23000-2aaff51b2000 r-xp 00000000 08:08 1734989                    /usr/lib/libgtk-x11-2.0.so.0.1000.11
2aaff51b2000-2aaff53b1000 ---p 0038f000 08:08 1734989                    /usr/lib/libgtk-x11-2.0.so.0.1000.11
2aaff53b1000-2aaff53bc000 rw-p 0038e000 08:08 1734989                    /usr/lib/libgtk-x11-2.0.so.0.1000.11
2aaff53bc000-2aaff53be000 rw-p 2aaff53bc000 00:00 0 
2aaff53be000-2aaff5453000 r-xp 00000000 08:08 1734840                    /usr/lib/libgdk-x11-2.0.so.0.1000.11
2aaff5453000-2aaff5652000 ---p 00095000 08:08 1734840                    /usr/lib/libgdk-x11-2.0.so.0.1000.11
2aaff5652000-2aaff5657000 rw-p 00094000 08:08 1734840                    /usr/lib/libgdk-x11-2.0.so.0.1000.11
2aaff5657000-2aaff5675000 r-xp 00000000 08:08 1734652                    /usr/lib/libatk-1.0.so.0.1809.1
2aaff5675000-2aaff5875000 ---p 0001e000 08:08 1734652                    /usr/lib/libatk-1.0.so.0.1809.1
2aaff5875000-2aaff5878000 rw-p 0001e000 08:08 1734652                    /usr/lib/libatk-1.0.so.0.1809.1
2aaff5878000-2aaff5879000 rw-p 2aaff5878000 00:00 0 
2aaff5879000-2aaff5890000 r-xp 00000000 08:08 1734842                    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
2aaff5890000-2aaff5a90000 ---p 00017000 08:08 1734842                    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
2aaff5a90000-2aaff5a91000 rw-p 00017000 08:08 1734842                    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
2aaff5a91000-2aaff5a97000 r-xp 00000000 08:08 1734616                    /usr/lib/libXrandr.so.2.1.0
2aaff5a97000-2aaff5c97000 ---p 00006000 08:08 1734616                    /usr/lib/libXrandr.so.2.1.0
2aaff5c97000-2aaff5c98000 rw-p 00006000 08:08 1734616                    /usr/lib/libXrandr.so.2.1.0
2aaff5c98000-2aaff5cda000 r-xp 00000000 08:08 1735165                    /usr/lib/libpango-1.0.so.0.1600.2
2aaff5cda000-2aaff5eda000 ---p 00042000 08:08 1735165                    /usr/lib/libpango-1.0.so.0.1600.2
2aaff5eda000-2aaff5edd000 rw-p 00042000 08:08 1735165                    /usr/lib/libpango-1.0.so.0.1600.2
2aaff5edd000-2aaff5ede000 rw-p 2aaff5edd000 00:00 0 
2aaff5ede000-2aaff5fe4000 r-xp 00000000 08:08 1734575                    /usr/lib/libX11.so.6.2.0
2aaff5fe4000-2aaff61e4000 ---p 00106000 08:08 1734575                    /usr/lib/libX11.so.6.2.0
2aaff61e4000-2aaff61eb000 rw-p 00106000 08:08 1734575                    /usr/lib/libX11.so.6.2.0
2aaff61eb000-2aaff6250000 r-xp 00000000 08:08 1734677                    /usr/lib/libbonobo-2.so.0.0.0
2aaff6250000-2aaff644f000 ---p 00065000 08:08 1734677                    /usr/lib/libbonobo-2.so.0.0.0
2aaff644f000-2aaff6460000 rw-p 00064000 08:08 1734677                    /usr/lib/libbonobo-2.so.0.0.0
2aaff6460000-2aaff6477000 r-xp 00000000 08:08 1734679                    /usr/lib/libbonobo-activation.so.4.0.0
2aaff6477000-2aaff6677000 ---p 00017000 08:08 1734679                    /usr/lib/libbonobo-activation.so.4.0.0
2aaff6677000-2aaff667b000 rw-p 00017000 08:08 1734679                    /usr/lib/libbonobo-activation.so.4.0.0
2aaff667b000-2aaff667c000 rw-p 2aaff667b000 00:00 0 
2aaff667c000-2aaff66b5000 r-xp 00000000 08:08 1734820                    /usr/lib/libgconf-2.so.4.1.2
2aaff66b5000-2aaff68b4000 ---p 00039000 08:08 1734820                    /usr/lib/libgconf-2.so.4.1.2
2aaff68b4000-2aaff68b9000 rw-p 00038000 08:08 1734820                    /usr/lib/libgconf-2.so.4.1.2
2aaff68b9000-2aaff6915000 r-xp 00000000 08:08 1734563                    /usr/lib/libORBit-2.so.0.1.0
2aaff6915000-2aaff6b14000 ---p 0005c000 08:08 1734563                    /usr/lib/libORBit-2.so.0.1.0
2aaff6b14000-2aaff6b27000 rw-p 0005b000 08:08 1734563                    /usr/lib/libORBit-2.so.0.1.0
2aaff6b27000-2aaff6b28000 r--p 00000000 08:08 1799707                    /usr/lib/locale/en_AU.utf8/LC_IDENTIFICATION
2aaff6b28000-2aaff6b2f000 r--s 00000000 08:08 1766145                    /usr/lib/gconv/gconv-modules.cache
2aaff6b2f000-2aaff6b30000 r--p 00000000 08:08 1799708                    /usr/lib/locale/en_AU.utf8/LC_MEASUREMENT
2aaff6b30000-2aaff6b31000 r--p 00000000 08:08 1799713                    /usr/lib/locale/en_AU.utf8/LC_TELEPHONE
2aaff6b31000-2aaff6b32000 r--p 00000000 08:08 1799704                    /usr/lib/locale/en_AU.utf8/LC_ADDRESS
2aaff6b32000-2aaff6b33000 r--p 00000000 08:08 1799710                    /usr/lib/locale/en_AU.utf8/LC_NAME
2aaff6b33000-2aaff6b34000 r--p 00000000 08:08 1799712                    /usr/lib/locale/en_AU.utf8/LC_PAPER
2aaff6b34000-2aaff6b35000 r--p 00000000 08:08 1799715                    /usr/lib/locale/en_AU.utf8/LC_MESSAGES/SYS_LC_MESSAGES
2aaff6b35000-2aaff6b36000 r--p 00000000 08:08 1799709                    /usr/lib/locale/en_AU.utf8/LC_MONETARY
2aaff6b3a000-2aaff6b50000 r-xp 00000000 08:08 2077034                    /lib/libpthread-2.6.1.so
2aaff6b50000-2aaff6d4f000 ---p 00016000 08:08 2077034                    /lib/libpthread-2.6.1.so
2aaff6d4f000-2aaff6d51000 rw-p 00015000 08:08 2077034                    /lib/libpthread-2.6.1.so
2aaff6d51000-2aaff6d56000 rw-p 2aaff6d51000 00:00 0 
2aaff6d56000-2aaff6d74000 r-xp 00000000 08:08 1734721                    /usr/lib/libdbus-glib-1.so.2.1.0
2aaff6d74000-2aaff6f74000 ---p 0001e000 08:08 1734721                    /usr/lib/libdbus-glib-1.so.2.1.0
2aaff6f74000-2aaff6f76000 rw-p 0001e000 08:08 1734721                    /usr/lib/libdbus-glib-1.so.2.1.0
2aaff6f76000-2aaff6fad000 r-xp 00000000 08:08 1734052                    /usr/lib/libdbus-1.so.3.2.0
2aaff6fad000-2aaff71ac000 ---p 00037000 08:08 1734052                    /usr/lib/libdbus-1.so.3.2.0
2aaff71ac000-2aaff71ae000 rw-p 00036000 08:08 1734052                    /usr/lib/libdbus-1.so.3.2.0
2aaff71ae000-2aaff71ee000 r-xp 00000000 08:08 1734932                    /usr/lib/libgobject-2.0.so.0.1200.11
2aaff71ee000-2aaff73ee000 ---p 00040000 08:08 1734932                    /usr/lib/libgobject-2.0.so.0.1200.11
2aaff73ee000-2aaff73f0000 rw-p 00040000 08:08 1734932                    /usr/lib/libgobject-2.0.so.0.1200.11
2aaff73f0000-2aaff73f1000 rw-p 2aaff73f0000 00:00 0 
2aaff73f1000-2aaff73ff000 r-xp 00000000 08:08 1734894                    /usr/lib/libgnome-keyring.so.0.0.1
2aaff73ff000-2aaff75fe000 ---p 0000e000 08:08 1734894                    /usr/lib/libgnome-keyring.so.0.0.1
2aaff75fe000-2aaff75ff000 rw-p 0000d000 08:08 1734894                    /usr/lib/libgnome-keyring.so.0.0.1
2aaff75ff000-2aaff769f000 r-xp 00000000 08:08 1734878                    /usr/lib/libglib-2.0.so.0.1200.11
2aaff769f000-2aaff789e000 ---p 000a0000 08:08 1734878                    /usr/lib/libglib-2.0.so.0.1200.11
2aaff789e000-2aaff78a0000 rw-p 0009f000 08:08 1734878                    /usr/lib/libglib-2.0.so.0.1200.11
2aaff78a0000-2aaff78a8000 r-xp 00000000 08:08 2077015                    /lib/libwrap.so.0.7.6
2aaff78a8000-2aaff7aa7000 ---p 00008000 08:08 2077015                    /lib/libwrap.so.0.7.6
2aaff7aa7000-2aaff7aa9000 rw-p 00007000 08:08 2077015                    /lib/libwrap.so.0.7.6
2aaff7aa9000-2aaff7aaa000 rw-p 2aaff7aa9000 00:00 0 
2aaff7aaa000-2aaff7bfc000 r-xp 00000000 08:08 2077020                    /lib/libc-2.6.1.so
2aaff7bfc000-2aaff7dfb000 ---p 00152000 08:08 2077020                    /lib/libc-2.6.1.so
2aaff7dfb000-2aaff7dfe000 r--p 00151000 08:08 2077020                    /lib/libc-2.6.1.so
2aaff7dfe000-2aaff7e00000 rw-p 00154000 08:08 2077020                    /lib/libc-2.6.1.so
2aaff7e00000-2aaff7e05000 rw-p 2aaff7e00000 00:00 0 
2aaff7e05000-2aaff7e2a000 r-xp 00000000 08:08 1734658                    /usr/lib/libaudiofile.so.0.0.2
2aaff7e2a000-2aaff8029000 ---p 00025000 08:08 1734658                    /usr/lib/libaudiofile.so.0.0.2
2aaff8029000-2aaff802d000 rw-p 00024000 08:08 1734658                    /usr/lib/libaudiofile.so.0.0.2
2aaff802d000-2aaff80ad000 r-xp 00000000 08:08 2077024                    /lib/libm-2.6.1.so
2aaff80ad000-2aaff82ac000 ---p 00080000 08:08 2077024                    /lib/libm-2.6.1.so
2aaff82ac000-2aaff82ae000 rw-p 0007f000 08:08 2077024                    /lib/libm-2.6.1.so
2aaff82ae000-2aaff82af000 rw-p 2aaff82ae000 00:00 0 
2aaff82af000-2aaff8385000 r-xp 00000000 08:08 1734646                    /usr/lib/libasound.so.2.0.0
2aaff8385000-2aaff8585000 ---p 000d6000 08:08 1734646                    /usr/lib/libasound.so.2.0.0
2aaff8585000-2aaff858d000 rw-p 000d6000 08:08 1734646                    /usr/lib/libasound.so.2.0.0
2aaff858d000-2aaff86c4000 r-xp 00000000 08:08 1735326                    /usr/lib/libxml2.so.2.6.27
2aaff86c4000-2aaff88c4000 ---p 00137000 08:08 1735326                    /usr/lib/libxml2.so.2.6.27
2aaff88c4000-2aaff88cd000 rw-p 00137000 08:08 1735326                    /usr/lib/libxml2.so.2.6.27
2aaff88cd000-2aaff88ce000 rw-p 2aaff88cd000 00:00 0 
2aaff88ce000-2aaff8938000 r-xp 00000000 08:08 1734681                    /usr/lib/libbonoboui-2.so.0.0.0
2aaff8938000-2aaff8b37000 ---p 0006a000 08:08 1734681                    /usr/lib/libbonoboui-2.so.0.0.0
2aaff8b37000-2aaff8b3c000 rw-p 00069000 08:08 1734681                    /usr/lib/libbonoboui-2.so.0.0.0
2aaff8b3c000-2aaff8b3d000 rw-p 2aaff8b3c000 00:00 0 
2aaff8b3d000-2aaff8b6a000 r-xp 00000000 08:08 1734904                    /usr/lib/libgnomecanvas-2.so.0.1400.0
2aaff8b6a000-2aaff8d6a000 ---p 0002d000 08:08 1734904                    /usr/lib/libgnomecanvas-2.so.0.1400.0
2aaff8d6a000-2aaff8d6c000 rw-p 0002d000 08:08 1734904                    /usr/lib/libgnomecanvas-2.so.0.1400.0
2aaff8d6c000-2aaff8d73000 r-xp 00000000 08:08 2076809                    /lib/libpopt.so.0.0.0
2aaff8d73000-2aaff8f73000 ---p 00007000 08:08 2076809                    /lib/libpopt.so.0.0.0
2aaff8f73000-2aaff8f74000 rw-p 00007000 08:08 2076809                    /lib/libpopt.so.0.0.0
2aaff8f74000-2aaff8f89000 r-xp 00000000 08:08 1734644                    /usr/lib/libart_lgpl_2.so.2.3.17
2aaff8f89000-2aaff9088000 ---p 00015000 08:08 1734644                    /usr/lib/libart_lgpl_2.so.2.3.17
2aaff9088000-2aaff908b000 rw-p 00014000 08:08 1734644                    /usr/lib/libart_lgpl_2.so.2.3.17
2aaff908b000-2aaff908c000 rw-p 2aaff908b000 00:00 0 
2aaff908c000-2aaff90ba000 r-xp 00000000 08:08 1735169                    /usr/lib/libpangoft2-1.0.so.0.1600.2
2aaff90ba000-2aaff92b9000 ---p 0002e000 08:08 1735169                    /usr/lib/libpangoft2-1.0.so.0.1600.2
2aaff92b9000-2aaff92ba000 rw-p 0002d000 08:08 1735169                    /usr/lib/libpangoft2-1.0.so.0.1600.2
2aaff92ba000-2aaff92c3000 r-xp 00000000 08:08 1735167                    /usr/lib/libpangocairo-1.0.so.0.1600.2
2aaff92c3000-2aaff94c2000 ---p 00009000 08:08 1735167                    /usr/lib/libpangocairo-1.0.so.0.1600.2
2aaff94c2000-2aaff94c3000 rw-p 00008000 08:08 1735167                    /usr/lib/libpangocairo-1.0.so.0.1600.2
2aaff94c3000-2aaff94ed000 r-xp 00000000 08:08 1734783                    /usr/lib/libfontconfig.so.1.2.0
2aaff94ed000-2aaff96ec000 ---p 0002a000 08:08 1734783                    /usr/lib/libfontconfig.so.1.2.0
2aaff96ec000-2aaff96f7000 rw-p 00029000 08:08 1734783                    /usr/lib/libfontconfig.so.1.2.0
2aaff96f7000-2aaff96f8000 rw-p 2aaff96f7000 00:00 0 
2aaff96f8000-2aaff9708000 r-xp 00000000 08:08 1734596                    /usr/lib/libXext.so.6.4.0
2aaff9708000-2aaff9908000 ---p 00010000 08:08 1734596                    /usr/lib/libXext.so.6.4.0
2aaff9908000-2aaff9909000 rw-p 00010000 08:08 1734596                    /usr/lib/libXext.so.6.4.0
2aaff9909000-2aaff9912000 r-xp 00000000 08:08 1734618                    /usr/lib/libXrender.so.1.3.0
2aaff9912000-2aaff9b11000 ---p 00009000 08:08 1734618                    /usr/lib/libXrender.so.1.3.0
2aaff9b11000-2aaff9b12000 rw-p 00008000 08:08 1734618                    /usr/lib/libXrender.so.1.3.0
2aaff9b12000-2aaff9b14000 r-xp 00000000 08:08 1734606                    /usr/lib/libXinerama.so.1.0.0
2aaff9b14000-2aaff9c13000 ---p 00002000 08:08 1734606                    /usr/lib/libXinerama.so.1.0.0
2aaff9c13000-2aaff9c14000 rw-p 00001000 08:08 1734606                    /usr/lib/libXinerama.so.1.0.0
2aaff9c14000-2aaff9c15000 rw-p 2aaff9c14000 00:00 0 
2aaff9c15000-2aaff9c1d000 r-xp 00000000 08:08 1734604                    /usr/lib/libXi.so.6.0.0
2aaff9c1d000-2aaff9e1d000 ---p 00008000 08:08 1734604                    /usr/lib/libXi.so.6.0.0
2aaff9e1d000-2aaff9e1e000 rw-p 00008000 08:08 1734604                    /usr/lib/libXi.so.6.0.0
2aaff9e1e000-2aaff9e28000 r-xp 00000000 08:08 1734588                    /usr/lib/libXcursor.so.1.0.2
2aaff9e28000-2aaffa027000 ---p 0000a000 08:08 1734588                    /usr/lib/libXcursor.so.1.0.2
2aaffa027000-2aaffa028000 rw-p 00009000 08:08 1734588                    /usr/lib/libXcursor.so.1.0.2
2aaffa028000-2aaffa02d000 r-xp 00000000 08:08 1734598                    /usr/lib/libXfixes.so.3.1.0
2aaffa02d000-2aaffa22c000 ---p 00005000 08:08 1734598                    /usr/lib/libXfixes.so.3.1.0
2aaffa22c000-2aaffa22d000 rw-p 00004000 08:08 1734598                    /usr/lib/libXfixes.so.3.1.0
2aaffa22d000-2aaffa22e000 rw-p 2aaffa22d000 00:00 0 
2aaffa22e000-2aaffa2a2000 r-xp 00000000 08:08 1734685                    /usr/lib/libcairo.so.2.11.1
2aaffa2a2000-2aaffa4a2000 ---p 00074000 08:08 1734685                    /usr/lib/libcairo.so.2.11.1
2aaffa4a2000-2aaffa4a4000 rw-p 00074000 08:08 1734685                    /usr/lib/libcairo.so.2.11.1
2aaffa4a4000-2aaffa506000 r-xp 00000000 08:08 1734922                    /usr/lib/libgnomevfs-2.so.0.1800.1
2aaffa506000-2aaffa706000 ---p 00062000 08:08 1734922                    /usr/lib/libgnomevfs-2.so.0.1800.1
2aaffa706000-2aaffa70b000 rw-p 00062000 08:08 1734922                    /usr/lib/libgnomevfs-2.so.0.1800.1
2aaffa70b000-2aaffa70e000 r-xp 00000000 08:08 1734888                    /usr/lib/libgmodule-2.0.so.0.1200.11
2aaffa70e000-2aaffa90d000 ---p 00003000 08:08 1734888                    /usr/lib/libgmodule-2.0.so.0.1200.11
2aaffa90d000-2aaffa90e000 rw-p 00002000 08:08 1734888                    /usr/lib/libgmodule-2.0.so.0.1200.11
2aaffa90e000-2aaffa90f000 rw-p 2aaffa90e000 00:00 0 
2aaffa90f000-2aaffa911000 r-xp 00000000 08:08 2077023                    /lib/libdl-2.6.1.so
2aaffa911000-2aaffab11000 ---p 00002000 08:08 2077023                    /lib/libdl-2.6.1.so
2aaffab11000-2aaffab13000 rw-p 00002000 08:08 2077023                    /lib/libdl-2.6.1.so
2aaffab13000-2aaffab17000 r-xp 00000000 08:08 1734986                    /usr/lib/libgthread-2.0.so.0.1200.11
2aaffab17000-2aaffad16000 ---p 00004000 08:08 1734986                    /usr/lib/libgthread-2.0.so.0.1200.11
2aaffad16000-2aaffad17000 rw-p 00003000 08:08 1734986                    /usr/lib/libgthread-2.0.so.0.1200.11
2aaffad17000-2aaffad1f000 r-xp 00000000 08:08 2077036                    /lib/librt-2.6.1.so
2aaffad1f000-2aaffaf1e000 ---p 00008000 08:08 2077036                    /lib/librt-2.6.1.so
2aaffaf1e000-2aaffaf20000 rw-p 00007000 08:08 2077036                    /lib/librt-2.6.1.so
2aaffaf20000-2aaffaf21000 rw-p 2aaffaf20000 00:00 0 
2aaffaf21000-2aaffaf2a000 r-xp 00000000 08:08 1735266                    /usr/lib/libstartup-notification-1.so.0.0.0
2aaffaf2a000-2aaffb129000 ---p 00009000 08:08 1735266                    /usr/lib/libstartup-notification-1.so.0.0.0
2aaffb129000-2aaffb12a000 rw-p 00008000 08:08 1735266                    /usr/lib/libstartup-notification-1.so.0.0.0
2aaffb12a000-2aaffb14b000 r-xp 00000000 08:08 1735059                    /usr/lib/libjpeg.so.62.0.0
2aaffb14b000-2aaffb24b000 ---p 00021000 08:08 1735059                    /usr/lib/libjpeg.so.62.0.0
2aaffb24b000-2aaffb24c000 rw-p 00021000 08:08 1735059                    /usr/lib/libjpeg.so.62.0.0
2aaffb24c000-2aaffb24d000 rw-p 2aaffb24c000 00:00 0 
2aaffb24d000-2aaffb252000 r-xp 00000000 08:08 1734592                    /usr/lib/libXdmcp.so.6.0.0
2aaffb252000-2aaffb451000 ---p 00005000 08:08 1734592                    /usr/lib/libXdmcp.so.6.0.0
2aaffb451000-2aaffb452000 rw-p 00004000 08:08 1734592                    /usr/lib/libXdmcp.so.6.0.0
2aaffb452000-2aaffb457000 r-xp 00000000 08:08 1734567                    /usr/lib/libORBitCosNaming-2.so.0.1.0
2aaffb457000-2aaffb657000 ---p 00005000 08:08 1734567                    /usr/lib/libORBitCosNaming-2.so.0.1.0
2aaffb657000-2aaffb659000 rw-p 00005000 08:08 1734567                    /usr/lib/libORBitCosNaming-2.so.0.1.0
2aaffb659000-2aaffb65a000 rw-p 2aaffb659000 00:00 0 
2aaffb65a000-2aaffb670000 r-xp 00000000 08:08 2077026                    /lib/libnsl-2.6.1.so
2aaffb670000-2aaffb86f000 ---p 00016000 08:08 2077026                    /lib/libnsl-2.6.1.so
2aaffb86f000-2aaffb871000 rw-p 00015000 08:08 2077026                    /lib/libnsl-2.6.1.so
2aaffb871000-2aaffb873000 rw-p 2aaffb871000 00:00 0 
2aaffb873000-2aaffb889000 r-xp 00000000 08:08 1735332                    /usr/lib/libz.so.1.2.3
2aaffb889000-2aaffba88000 ---p 00016000 08:08 1735332                    /usr/lib/libz.so.1.2.3
2aaffba88000-2aaffba89000 rw-p 00015000 08:08 1735332                    /usr/lib/libz.so.1.2.3
2aaffba89000-2aaffba8a000 rw-p 2aaffba89000 00:00 0 
2aaffba8a000-2aaffbafe000 r-xp 00000000 08:08 1734709                    /usr/lib/libfreetype.so.6.3.10
2aaffbafe000-2aaffbcfe000 ---p 00074000 08:08 1734709                    /usr/lib/libfreetype.so.6.3.10
2aaffbcfe000-2aaffbd03000 rw-p 00074000 08:08 1734709                    /usr/lib/libfreetype.so.6.3.10
2aaffbd03000-2aaffbd24000 r-xp 00000000 08:08 1734777                    /usr/lib/libexpat.so.1.0.0
2aaffbd24000-2aaffbf23000 ---p 00021000 08:08 1734777                    /usr/lib/libexpat.so.1.0.0
2aaffbf23000-2aaffbf26000 rw-p 00020000 08:08 1734777                    /usr/lib/libexpat.so.1.0.0
2aaffbf26000-2aaffbf27000 rw-p 2aaffbf26000 00:00 0 
2aaffbf27000-2aaffbf4b000 r-xp 00000000 08:08 1734856                    /usr/lib/libpng12.so.0.15.0
2aaffbf4b000-2aaffc14a000 ---p 00024000 08:08 1734856                    /usr/lib/libpng12.so.0.15.0
2aaffc14a000-2aaffc14b000 rw-p 00023000 08:08 1734856                    /usr/lib/libpng12.so.0.15.0
2aaffc14b000-2aaffc1c0000 r-xp 00000000 08:08 1734930                    /usr/lib/libgnutls.so.13.0.9
2aaffc1c0000-2aaffc3bf000 ---p 00075000 08:08 1734930                    /usr/lib/libgnutls.so.13.0.9
2aaffc3bf000-2aaffc3ca000 rw-p 00074000 08:08 1734930                    /usr/lib/libgnutls.so.13.0.9
2aaffc3ca000-2aaffc3cb000 rw-p 2aaffc3ca000 00:00 0 
2aaffc3cb000-2aaffc3ce000 r-xp 00000000 08:08 1734666                    /usr/lib/libavahi-glib.so.1.0.1
2aaffc3ce000-2aaffc5cd000 ---p 00003000 08:08 1734666                    /usr/lib/libavahi-glib.so.1.0.1
2aaffc5cd000-2aaffc5ce000 rw-p 00002000 08:08 1734666                    /usr/lib/libavahi-glib.so.1.0.1
2aaffc5ce000-2aaffc5d9000 r-xp 00000000 08:08 1734662                    /usr/lib/libavahi-common.so.3.4.3
2aaffc5d9000-2aaffc7d9000 ---p 0000b000 08:08 1734662                    /usr/lib/libavahi-common.so.3.4.3
2aaffc7d9000-2aaffc7da000 rw-p 0000b000 08:08 1734662                    /usr/lib/libavahi-common.so.3.4.3
2aaffc7da000-2aaffc7e9000 r-xp 00000000 08:08 1734660                    /usr/lib/libavahi-client.so.3.2.2
2aaffc7e9000-2aaffc9e9000 ---p 0000f000 08:08 1734660                    /usr/lib/libavahi-client.so.3.2.2
2aaffc9e9000-2aaffc9ea000 rw-p 0000f000 08:08 1734660                    /usr/lib/libavahi-client.so.3.2.2
2aaffc9ea000-2aaffc9eb000 rw-p 2aaffc9ea000 00:00 0 
2aaffc9eb000-2aaffc9fd000 r-xp 00000000 08:08 2077035                    /lib/libresolv-2.6.1.so
2aaffc9fd000-2aaffcbfc000 ---p 00012000 08:08 2077035                    /lib/libresolv-2.6.1.so
2aaffcbfc000-2aaffcbfe000 rw-p 00011000 08:08 2077035                    /lib/libresolv-2.6.1.so
2aaffcbfe000-2aaffcc00000 rw-p 2aaffcbfe000 00:00 0 
2aaffcc00000-2aaffcc16000 r-xp 00000000 08:08 2076819                    /lib/libselinux.so.1
2aaffcc16000-2aaffce15000 ---p 00016000 08:08 2076819                    /lib/libselinux.so.1
2aaffce15000-2aaffce17000 rw-p 00015000 08:08 2076819                    /lib/libselinux.so.1
2aaffce17000-2aaffce18000 rw-p 2aaffce17000 00:00 0 
2aaffce18000-2aaffce1a000 r-xp 00000000 08:08 2077039                    /lib/libutil-2.6.1.so
2aaffce1a000-2aaffd019000 ---p 00002000 08:08 2077039                    /lib/libutil-2.6.1.so
2aaffd019000-2aaffd01b000 rw-p 00001000 08:08 2077039                    /lib/libutil-2.6.1.so
2aaffd01b000-2aaffd01c000 rw-p 2aaffd01b000 00:00 0 
2aaffd01c000-2aaffd031000 r-xp 00000000 08:08 1735274                    /usr/lib/libtasn1.so.3.0.6
2aaffd031000-2aaffd231000 ---p 00015000 08:08 1735274                    /usr/lib/libtasn1.so.3.0.6
2aaffd231000-2aaffd232000 rw-p 00015000 08:08 1735274                    /usr/lib/libtasn1.so.3.0.6
2aaffd232000-2aaffd27c000 r-xp 00000000 08:08 1734822                    /usr/lib/libgcrypt.so.11.2.2
2aaffd27c000-2aaffd47c000 ---p 0004a000 08:08 1734822                    /usr/lib/libgcrypt.so.11.2.2
2aaffd47c000-2aaffd47e000 rw-p 0004a000 08:08 1734822                    /usr/lib/libgcrypt.so.11.2.2
2aaffd47e000-2aaffd480000 rw-p 2aaffd47e000 00:00 0 
2aaffd480000-2aaffd483000 r-xp 00000000 08:08 1734934                    /usr/lib/libgpg-error.so.0.3.0
2aaffd483000-2aaffd682000 ---p 00003000 08:08 1734934                    /usr/lib/libgpg-error.so.0.3.0
2aaffd682000-2aaffd683000 rw-p 00002000 08:08 1734934                    /usr/lib/libgpg-error.so.0.3.0
2aaffd683000-2aaffd6be000 r-xp 00000000 08:08 2076820                    /lib/libsepol.so.1
2aaffd6be000-2aaffd8be000 ---p 0003b000 08:08 2076820                    /lib/libsepol.so.1
2aaffd8be000-2aaffd8bf000 rw-p 0003b000 08:08 2076820                    /lib/libsepol.so.1
2aaffd8bf000-2aaffd8cd000 rw-p 2aaffd8bf000 00:00 0 
2aaffd8cd000-2aaffd8d5000 r-xp 00000000 08:08 2077027                    /lib/libnss_compat-2.6.1.so
2aaffd8d5000-2aaffdad4000 ---p 00008000 08:08 2077027                    /lib/libnss_compat-2.6.1.so
2aaffdad4000-2aaffdad6000 rw-p 00007000 08:08 2077027                    /lib/libnss_compat-2.6.1.so
2aaffdad6000-2aaffdae0000 r-xp 00000000 08:08 2077031                    /lib/libnss_nis-2.6.1.so
2aaffdae0000-2aaffdcdf000 ---p 0000a000 08:08 2077031                    /lib/libnss_nis-2.6.1.so
2aaffdcdf000-2aaffdce1000 rw-p 00009000 08:08 2077031                    /lib/libnss_nis-2.6.1.so
2aaffdce1000-2aaffdceb000 r-xp 00000000 08:08 2077029                    /lib/libnss_files-2.6.1.so
2aaffdceb000-2aaffdeea000 ---p 0000a000 08:08 2077029                    /lib/libnss_files-2.6.1.so
2aaffdeea000-2aaffdeec000 rw-p 00009000 08:08 2077029                    /lib/libnss_files-2.6.1.so
2aaffdeec000-2aaffdfc3000 r--p 00000000 08:08 1799705                    /usr/lib/locale/en_AU.utf8/LC_COLLATE
2aaffdfc3000-2aaffdfc4000 r--p 00000000 08:08 1799714                    /usr/lib/locale/en_AU.utf8/LC_TIME
2aaffdfc4000-2aaffdfc5000 r--p 00000000 08:08 1799711                    /usr/lib/locale/en_AU.utf8/LC_NUMERIC
2aaffdfc5000-2aaffe000000 r--p 00000000 08:08 1799706                    /usr/lib/locale/en_AU.utf8/LC_CTYPE
2aaffe000000-2aaffe00f000 r--p 00000000 08:08 2062295                    /usr/share/locale-langpack/en_AU/LC_MESSAGES/gtk20.mo
2aaffe00f000-2aaffe014000 r--p 00000000 08:08 2062294                    /usr/share/locale-langpack/en_AU/LC_MESSAGES/gtk20-properties.mo
2aaffe014000-2aaffe016000 r-xp 00000000 08:08 1900198                    /usr/lib/gconv/ISO8859-1.so
2aaffe016000-2aaffe215000 ---p 00002000 08:08 1900198                    /usr/lib/gconv/ISO8859-1.so
2aaffe215000-2aaffe217000 rw-p 00001000 08:08 1900198                    /usr/lib/gconv/ISO8859-1.so
2aaffe217000-2aaffe21b000 r--p 00000000 08:08 2062280                    /usr/share/locale-langpack/en_AU/LC_MESSAGES/gnome-session-2.0.mo
2aaffe21b000-2aaffe222000 r--p 00000000 08:08 2062305                    /usr/share/locale-langpack/en_AU/LC_MESSAGES/libgnome-2.0.mo
2aaffe222000-2aaffe230000 r-xp 00000000 08:08 1799087                    /usr/lib/gnome-vfs-2.0/modules/libfile.so
2aaffe230000-2aaffe42f000 ---p 0000e000 08:08 1799087                    /usr/lib/gnome-vfs-2.0/modules/libfile.so
2aaffe42f000-2aaffe430000 rw-p 0000d000 08:08 1799087                    /usr/lib/gnome-vfs-2.0/modules/libfile.so
2aaffe430000-2aaffe434000 r-xp 00000000 08:08 2076733                    /lib/libattr.so.1.1.0
2aaffe434000-2aaffe633000 ---p 00004000 08:08 2076733                    /lib/libattr.so.1.1.0
2aaffe633000-2aaffe634000 rw-p 00003000 08:08 2076733                    /lib/libattr.so.1.1.0
2aaffe634000-2aaffe63a000 r-xp 00000000 08:08 2076729                    /lib/libacl.so.1.1.0
2aaffe63a000-2aaffe839000 ---p 00006000 08:08 2076729                    /lib/libacl.so.1.1.0
2aaffe839000-2aaffe83a000 rw-p 00005000 08:08 2076729                    /lib/libacl.so.1.1.0
2aaffe83a000-2aaffe842000 r-xp 00000000 08:08 1734781                    /usr/lib/libfam.so.0.0.0
2aaffe842000-2aaffea41000 ---p 00008000 08:08 1734781                    /usr/lib/libfam.so.0.0.0
2aaffea41000-2aaffea42000 rw-p 00007000 08:08 1734781                    /usr/lib/libfam.so.0.0.0
2aaffea42000-2aaffea44000 r--p 00000000 08:08 2062269                    /usr/share/locale-langpack/en_AU/LC_MESSAGES/gnome-desktop-2.0.mo
2aaffea44000-2aaffea48000 r--p 00000000 08:08 2062264                    /usr/share/locale-langpack/en_AU/LC_MESSAGES/glib20.mo
2aaffea49000-2aaffea4d000 r-xp 00000000 08:08 1799164                    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
2aaffea4d000-2aaffec4d000 ---p 00004000 08:08 1799164                    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
2aaffec4d000-2aaffec4e000 rw-p 00004000 08:08 1799164                    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
2aaffec4e000-2aaffecae000 rw-s 00000000 00:09 655363                     /SYSV00000000 (deleted)
2aaffecae000-2aaffecb7000 r-xp 00000000 08:08 1799138                    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
2aaffecb7000-2aaffeeb7000 ---p 00009000 08:08 1799138                    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
2aaffeeb7000-2aaffeeb8000 rw-p 00009000 08:08 1799138                    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
2aaffeeb8000-2aafff10f000 r--p 00000000 08:08 2015189                    /usr/share/icons/Tango/icon-theme.cache
2aafff10f000-2aafff7b6000 r--p 00000000 08:08 2016282                    /usr/share/icons/gnome/icon-theme.cache
2aafff7b6000-2ab0008a0000 r--p 00000000 08:08 2142141                    /usr/share/icons/crystalsvg/icon-theme.cache
7fffb6d91000-7fffb6da7000 rw-p 7fffb6d91000 00:00 0                      [stack]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vdso]
present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.
present. 
Checking for Xgl: not present. 
Starting emerald

(gnome-cups-icon:6555): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:6553): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-terminal:6573): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(eog:6574): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

```[B]----------------------------------------------------------------------------------------------------------

[/B]Then after removing compiz fusion:

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "seynthan"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/seynthan-lappy:/tmp/.ICE-unix/6377
/home/seynthan/start-compiz: line 2: compiz: command not found
Initializing gnome-mount extension
Password:
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(gnome-cups-icon:6448): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(update-notifier:6447): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gedit:6449): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-terminal:6453): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(eog:6456): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:6446): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

```

When I choose 'last session', it nearly loads up(part of gnomepanel comes) then the screen goes blank and I get sent back to the login screen. When I just launch 'GNOME session'(default) it tries to load the apps/windows I had running before that first crash but without window borders and displays the 'Session lasts for less than 10 seconds ' message etc. I used this method([http://ubuntuforums.org/showthread.php?t=536149](http://ubuntuforums.org/showthread.php?t=536149)) to install compiz fusion. But now im thinking its some weird gnome error I have instead.

thanks :)

---

### Post by ST.x on 2007-10-04
well I fixed it by deleting  ~/.gnome2/session
Hmm.. im confused as to what caused it now. There was a crash before I first got this, so that must have corrupted the sessions file. lol maybe I shouldn't have got rid of compiz fusion lol, oh well ill install it again one day when I start missing the eye candy.

---

