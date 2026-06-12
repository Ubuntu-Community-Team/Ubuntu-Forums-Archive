---
title: "Applications crash"
date: 2009-08-03
forum: x86 64-bit Users
---

### Post by acsandeep on 2009-08-03
Hi,

Lately i have been experiencing application crashes. Pidgin, Gftp, Filezilla etc crash. For example for pidgin i go to manage accounts ==> add account and it crashes. My ubuntu version is 9.04 Jaunty. Here is the Stack trace from pidgin crash:

*** glibc detected *** pidgin: free(): invalid pointer: 0x0000000002f27180 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f619590dcb8]
/lib/libc.so.6(cfree+0x76)[0x7f6195910276]
/usr/lib/gtk-2.0/2.10.0/engines/libcandido.so(option_menu_get_props+0x78)[0x7f618ee39988]
/usr/lib/gtk-2.0/2.10.0/engines/libcandido.so[0x7f618ee37e8b]
/usr/lib/libgtk-x11-2.0.so.0[0x7f6197479a18]
/usr/lib/libgtk-x11-2.0.so.0[0x7f6197313df8]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xbf)[0x7f61963f31cf]
/usr/lib/libgobject-2.0.so.0[0x7f6196408b1e]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x66d)[0x7f619640a2bd]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f619640a953]
/usr/lib/libgtk-x11-2.0.so.0[0x7f619741c09e]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1c1)[0x7f619728f161]
/usr/lib/libgtk-x11-2.0.so.0[0x7f6197260acb]
/usr/lib/libgtk-x11-2.0.so.0[0x7f619729121f]
/usr/lib/libgtk-x11-2.0.so.0[0x7f6197313df8]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xbf)[0x7f61963f31cf]
/usr/lib/libgobject-2.0.so.0[0x7f6196408b1e]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x66d)[0x7f619640a2bd]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f619640a953]
/usr/lib/libgtk-x11-2.0.so.0[0x7f619741c09e]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1c1)[0x7f619728f161]
/usr/lib/libgtk-x11-2.0.so.0[0x7f6197260acb]
/usr/lib/libgtk-x11-2.0.so.0[0x7f619729121f]
/usr/lib/libgtk-x11-2.0.so.0[0x7f6197313df8]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xbf)[0x7f61963f31cf]
/usr/lib/libgobject-2.0.so.0[0x7f6196408b1e]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x66d)[0x7f619640a2bd]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f619640a953]
/usr/lib/libgtk-x11-2.0.so.0[0x7f619741c09e]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1c1)[0x7f619728f161]
/usr/lib/libgtk-x11-2.0.so.0[0x7f6197260acb]
/usr/lib/libgtk-x11-2.0.so.0[0x7f619729121f]
/usr/lib/libgtk-x11-2.0.so.0[0x7f6197313df8]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xbf)[0x7f61963f31cf]
/usr/lib/libgobject-2.0.so.0[0x7f6196408b1e]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x66d)[0x7f619640a2bd]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f619640a953]
/usr/lib/libgtk-x11-2.0.so.0[0x7f619741c09e]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1c1)[0x7f619728f161]
/usr/lib/libgtk-x11-2.0.so.0[0x7f6197260acb]
/usr/lib/libgtk-x11-2.0.so.0[0x7f619729121f]
/usr/lib/libgtk-x11-2.0.so.0[0x7f6197313df8]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xbf)[0x7f61963f31cf]
/usr/lib/libgobject-2.0.so.0[0x7f6196408b1e]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x66d)[0x7f619640a2bd]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f619640a953]
/usr/lib/libgtk-x11-2.0.so.0[0x7f619741c09e]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1c1)[0x7f619728f161]
/usr/lib/libgtk-x11-2.0.so.0[0x7f6197260acb]
/usr/lib/libgtk-x11-2.0.so.0[0x7f619729121f]
/usr/lib/libgtk-x11-2.0.so.0[0x7f6197313df8]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xbf)[0x7f61963f31cf]
/usr/lib/libgobject-2.0.so.0[0x7f6196408b1e]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x66d)[0x7f619640a2bd]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f619640a953]
/usr/lib/libgtk-x11-2.0.so.0[0x7f619741c09e]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1c1)[0x7f619728f161]
/usr/lib/libgtk-x11-2.0.so.0[0x7f6197260acb]
/usr/lib/libgtk-x11-2.0.so.0[0x7f619729121f]
/usr/lib/libgtk-x11-2.0.so.0[0x7f6197313df8]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xbf)[0x7f61963f31cf]
/usr/lib/libgobject-2.0.so.0[0x7f6196408b1e]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x66d)[0x7f619640a2bd]
======= Memory map: ========
00400000-004d4000 r-xp 00000000 08:15 281075                             /usr/bin/pidgin
006d3000-006d4000 r--p 000d3000 08:15 281075                             /usr/bin/pidgin
006d4000-006d9000 rw-p 000d4000 08:15 281075                             /usr/bin/pidgin
006d9000-006da000 rw-p 006d9000 00:00 0 
02539000-02f33000 rw-p 02539000 00:00 0                                  [heap]
7f6178000000-7f6178021000 rw-p 7f6178000000 00:00 0 
7f6178021000-7f617c000000 ---p 7f6178021000 00:00 0 
7f617c518000-7f617c53a000 r-xp 00000000 08:15 280702                     /usr/lib/libjpeg.so.62.0.0
7f617c53a000-7f617c73a000 ---p 00022000 08:15 280702                     /usr/lib/libjpeg.so.62.0.0
7f617c73a000-7f617c73b000 rw-p 00022000 08:15 280702                     /usr/lib/libjpeg.so.62.0.0
7f617c757000-7f617c75b000 r-xp 00000000 08:15 311406                     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
7f617c75b000-7f617c95b000 ---p 00004000 08:15 311406                     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
7f617c95b000-7f617c95c000 r--p 00004000 08:15 311406                     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
7f617c95c000-7f617c95d000 rw-p 00005000 08:15 311406                     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
7f617c95d000-7f617c9bd000 rw-s 00000000 00:09 1966104                    /SYSV00000000 (deleted)
7f617c9bd000-7f617ca1d000 rw-s 00000000 00:09 1933335                    /SYSV00000000 (deleted)
7f617ca1d000-7f617caa9000 r--p 00000000 08:15 411065                     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
7f617caa9000-7f617cac0000 r--s 00000000 08:15 590514                     /var/lib/aspell/en_GB-ise-wo_accents-only.rws
7f617cac0000-7f617cd48000 r--s 00000000 08:15 590506                     /var/lib/aspell/en-common.rws
7f617cd48000-7f617cd53000 r-xp 00000000 08:15 229383                     /usr/lib/enchant/libenchant_ispell.so
7f617cd53000-7f617cf53000 ---p 0000b000 08:15 229383                     /usr/lib/enchant/libenchant_ispell.so
7f617cf53000-7f617cf54000 r--p 0000b000 08:15 229383                     /usr/lib/enchant/libenchant_ispell.so
7f617cf54000-7f617cf55000 rw-p 0000c000 08:15 229383                     /usr/lib/enchant/libenchant_ispell.so
7f617cf55000-7f617cf57000 r-xp 00000000 08:15 229385                     /usr/lib/enchant/libenchant_zemberek.so
7f617cf57000-7f617d156000 ---p 00002000 08:15 229385                     /usr/lib/enchant/libenchant_zemberek.so
7f617d156000-7f617d157000 r--p 00001000 08:15 229385                     /usr/lib/enchant/libenchant_zemberek.so
7f617d157000-7f617d158000 rw-p 00002000 08:15 229385                     /usr/lib/enchant/libenchant_zemberek.so
7f617d158000-7f617d163000 r-xp 00000000 08:15 229382                     /usr/lib/enchant/libenchant_hspell.so
7f617d163000-7f617d362000 ---p 0000b000 08:15 229382                     /usr/lib/enchant/libenchant_hspell.so
7f617d362000-7f617d363000 r--p 0000a000 08:15 229382                     /usr/lib/enchant/libenchant_hspell.so
7f617d363000-7f617d366000 rw-p 0000b000 08:15 229382                     /usr/lib/enchant/libenchant_hspell.so
7f617d366000-7f617d3a1000 r-xp 00000000 08:15 280659                     /usr/lib/libhunspell-1.2.so.0.0.0
7f617d3a1000-7f617d5a0000 ---p 0003b000 08:15 280659                     /usr/lib/libhunspell-1.2.so.0.0.0
7f617d5a0000-7f617d5a1000 r--p 0003a000 08:15 280659                     /usr/lib/libhunspell-1.2.so.0.0.0
7f617d5a1000-7f617d5a5000 rw-p 0003b000 08:15 280659                     /usr/lib/libhunspell-1.2.so.0.0.0
7f617d5a5000-7f617d5aa000 r-xp 00000000 08:15 229384                     /usr/lib/enchant/libenchant_myspell.so
7f617d5aa000-7f617d7a9000 ---p 00005000 08:15 229384                     /usr/lib/enchant/libenchant_myspell.so
7f617d7a9000-7f617d7aa000 r--p 00004000 08:15 229384                     /usr/lib/enchant/libenchant_myspell.so
7f617d7aa000-7f617d7ab000 rw-p 00005000 08:15 229384                     /usr/lib/enchant/libenchant_myspell.so
7f617d7ab000-7f617d7c1000 r-xp 00000000 08:15 147517                     /lib/libgcc_s.so.1
7f617d7c1000-7f617d9c1000 ---p 00016000 08:15 147517                     /lib/libgcc_s.so.1
7f617d9c1000-7f617d9c2000 r--p 00016000 08:15 147517                     /lib/libgcc_s.so.1
7f617d9c2000-7f617d9c3000 rw-p 00017000 08:15 147517                     /lib/libgcc_s.so.1
7f617d9c3000-7f617dab4000 r-xp 00000000 08:15 280996                     /usr/lib/libstdc++.so.6.0.10
7f617dab4000-7f617dcb4000 ---p 000f1000 08:15 280996                     /usr/lib/libstdc++.so.6.0.10
7f617dcb4000-7f617dcbb000 r--p 000f1000 08:15 280996                     /usr/lib/libstdc++.so.6.0.10
7f617dcbb000-7f617dcbd000 rw-p 000f8000 08:15 280996                     /usr/lib/libstdc++.so.6.0.10
7f617dcbd000-7f617dcd0000 rw-p 7f617dcbd000 00:00 0 
7f617dcd0000-7f617dd7f000 r-xp 00000000 08:15 280187                     /usr/lib/libaspell.so.15.1.4
7f617dd7f000-7f617df7f000 ---p 000af000 08:15 280187                     /usr/Aborted

---

