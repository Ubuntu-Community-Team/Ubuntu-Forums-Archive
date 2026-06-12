---
title: "iscan crashes when I try to scan - very confused"
date: 2008-09-01
forum: x86 64-bit Users
---

### Post by x20mar on 2008-09-01
Hi,

I'm having some problems using iscan on ubuntu 64-bit. When I try to scan an image with it, I get thrown the following errors
```
*** glibc detected *** iscan: double free or corruption (fasttop): 0x082b3d48 ***
======= Backtrace: =========
/lib32/libc.so.6[0xf7723615]
/lib32/libc.so.6(cfree+0x90)[0xf7727080]
iscan(_ZN5iscan9imgstream11find_dlopenEPKc+0x25d)[0x806cba1]
iscan(_ZN5iscan9imgstream6dlopenEPKc+0xf7)[0x806d975]
iscan(_ZN5iscan9pngstream9is_usableEv+0x54)[0x806e9a4]
iscan(_ZN13file_selector21add_dialog_extensionsEv+0x2dc)[0x80575a4]
iscan(_ZN13file_selector13create_windowEP10_GtkWindowP10_GtkWidgetb+0xa8)[0x8057bc8]
iscan(_ZN12view_manager12do_scan_fileEP15_scan_parameterP13file_selectorb+0x2f6)[0x806b5be]
iscan(_ZN12view_manager10start_scanEv+0xc4)[0x806b6cc]
iscan[0x805bb73]
/usr/lib32/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x4f)[0xf7a09a4f]
/usr/lib32/libgobject-2.0.so.0(g_closure_invoke+0x129)[0xf79fc759]
/usr/lib32/libgobject-2.0.so.0[0xf7a10d1d]
/usr/lib32/libgobject-2.0.so.0(g_signal_emit_valist+0x8c6)[0xf7a12916]
/usr/lib32/libgobject-2.0.so.0(g_signal_emit+0x29)[0xf7a12c59]
/usr/lib32/libgtk-x11-2.0.so.0(gtk_button_clicked+0x8a)[0xf7ba701a]
/usr/lib32/libgtk-x11-2.0.so.0[0xf7ba8b7e]
/usr/lib32/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x4f)[0xf7a09a4f]
/usr/lib32/libgobject-2.0.so.0[0xf79fb079]
/usr/lib32/libgobject-2.0.so.0(g_closure_invoke+0x129)[0xf79fc759]
/usr/lib32/libgobject-2.0.so.0[0xf7a10975]
/usr/lib32/libgobject-2.0.so.0(g_signal_emit_valist+0x8c6)[0xf7a12916]
/usr/lib32/libgobject-2.0.so.0(g_signal_emit+0x29)[0xf7a12c59]
/usr/lib32/libgtk-x11-2.0.so.0(gtk_button_released+0x8a)[0xf7ba70aa]
/usr/lib32/libgtk-x11-2.0.so.0[0xf7ba70d1]
/usr/lib32/libgtk-x11-2.0.so.0[0xf7c808d4]
/usr/lib32/libgobject-2.0.so.0[0xf79fb079]
/usr/lib32/libgobject-2.0.so.0(g_closure_invoke+0x129)[0xf79fc759]
/usr/lib32/libgobject-2.0.so.0[0xf7a10ea0]
/usr/lib32/libgobject-2.0.so.0(g_signal_emit_valist+0x5fe)[0xf7a1264e]
/usr/lib32/libgobject-2.0.so.0(g_signal_emit+0x29)[0xf7a12c59]
/usr/lib32/libgtk-x11-2.0.so.0[0xf7d9f667]
/usr/lib32/libgtk-x11-2.0.so.0(gtk_propagate_event+0xc1)[0xf7c79b21]
/usr/lib32/libgtk-x11-2.0.so.0(gtk_main_do_event+0x2b8)[0xf7c7ad88]
/usr/lib32/libgdk-x11-2.0.so.0[0xf7af3a9a]
/usr/lib32/libglib-2.0.so.0(g_main_context_dispatch+0x178)[0xf796fbf8]
/usr/lib32/libglib-2.0.so.0[0xf7972e5e]
/usr/lib32/libglib-2.0.so.0(g_main_loop_run+0x1e7)[0xf79731e7]
/usr/lib32/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xf7c7b264]
iscan(_ZN12view_manager4mainEv+0xb)[0x8068b21]
iscan(main+0x8f)[0x805ba13]
/lib32/libc.so.6(__libc_start_main+0xe0)[0xf76cd450]
iscan(__gxx_personality_v0+0x141)[0x8055e31]
======= Memory map: ========
08048000-08089000 r-xp 00000000 08:05 84866                              /usr/bin/iscan
08089000-0808d000 rw-p 00041000 08:05 84866                              /usr/bin/iscan
0808d000-08363000 rw-p 0808d000 00:00 0                                  [heap]
f6000000-f6021000 rw-p f6000000 00:00 0 
f6021000-f6100000 ---p f6021000 00:00 0 
f61ea000-f61eb000 ---p f61ea000 00:00 0 
f61eb000-f69eb000 rw-p f61eb000 00:00 0 
f6be3000-f6c43000 rw-s 00000000 00:09 3604520                            /SYSV00000000 (deleted)
f6c43000-f6d4b000 rw-p f6c43000 00:00 0 
f6d4b000-f6dab000 rw-s 00000000 00:09 3571743                            /SYSV00000000 (deleted)
f6dab000-f6db1000 r-xp 00000000 08:05 303311                             /usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
f6db1000-f6db2000 rw-p 00005000 08:05 303311                             /usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
f6db2000-f6eb6000 rw-p f6db2000 00:00 0 
f6eb6000-f6f47000 r--p 00000000 08:05 174067                             /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
f6f47000-f6f49000 r-xp 00000000 08:05 377312                             /usr/lib32/pango/1.6.0/modules/pango-basic-fc.so
f6f49000-f6f4a000 rw-p 00001000 08:05 377312                             /usr/lib32/pango/1.6.0/modules/pango-basic-fc.so
f6f4a000-f6f50000 r--s 00000000 08:05 795519                             /home/omar/.fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
f6f50000-f6f53000 r--s 00000000 08:05 795518                             /home/omar/.fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
f6f53000-f6f54000 r--s 00000000 08:05 795517                             /home/omar/.fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
f6f54000-f6f58000 r--s 00000000 08:05 796149                             /home/omar/.fontconfig/926e794c3d5e5dffcaf2fa83ef8d36c2-x86.cache-2
f6f58000-f6f59000 r--s 00000000 08:05 795516                             /home/omar/.fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
f6f59000-f6f5c000 r--s 00000000 08:05 795515                             /home/omar/.fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
f6f5c000-f6f63000 r--s 00000000 08:05 795514                             /home/omar/.fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
f6f63000-f6f66000 r--s 00000000 08:05 795513                             /home/omar/.fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
f6f66000-f6f6e000 r--s 00000000 08:05 795512                             /home/Aborted

```

Could someone please explain these errors to me, and advice me on how to fix it.

Many Thanks

---

### Post by tienhn on 2008-09-27
I also got that error message. My guess is because the iscan is 32 bit app.

I finnaly gave up and use native Windows scanning app inside a VirtualBox engine. It gives you much more capability anyway.

---

