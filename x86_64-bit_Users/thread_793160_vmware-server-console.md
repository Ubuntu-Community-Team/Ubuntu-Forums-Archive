---
title: "vmware-server-console"
date: 2008-05-13
forum: x86 64-bit Users
---

### Post by bensode on 2008-05-13
Ugly mess of errors when attempting to start vmware-server-console 1.0.5

I have ia32-libs installed and also running vmware workstation v6.0.3 just fine.  My problem is running the vmware console for my remote vmware servers.  I've tried using getlibs for each of the missing libs and still no go.  I'd really rather not regress back to 7.10 64bit if I can avoid it but that's my only other solution since I can't find anything that will fix this.  Here is what I get when executing vmware-server-console:

bensode@bensode:~$ vmware-server-console
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
/usr/share/themes/Human/gtk-2.0/gtkrc:43: error: unexpected character `@', expected string constant
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7075767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf70758b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf7ef41bd]
#3 /usr/lib/vmware-server-console/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xf7de4969]
#4 /usr/lib/vmware-server-console/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xf7de4f4c]
#5 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c2a180]
#6 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c2ad2c]
#7 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bfac14]
#8 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c0724f]
#9 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bfac14]
#10 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7c06b34]
#11 /usr/lib/vmware-server-console/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7b0b298]
#12 /usr/lib/vmware-server-console/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7b0b586]
#13 /usr/lib/vmware-server-console/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7b0d77e]
#14 /usr/lib/vmware-server-console/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7d20459]
#15 /usr/lib/vmware-server-console/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7d083a1]
#16 /usr/lib/vmware-server-console/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7d08076]
#17 /usr/lib/vmware-server-console/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7d1f6eb]
#18 /usr/lib/vmware-server-console/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xf7d1ed46]
#19 /usr/lib/vmware-server-console/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xf7d1f0b8]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7075767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf707581e]
#2 /usr/lib32/libX11.so.6 [0xf7ef3518]
#3 /usr/lib32/libX11.so.6(XGetVisualInfo+0x26) [0xf7eea0a6]
#4 /usr/lib/vmware-server-console/lib/libXft.so.2/libXft.so.2 [0xf7ddb4dc]
#5 /usr/lib/vmware-server-console/lib/libXft.so.2/libXft.so.2(XftDrawCreate+0x3e) [0xf7ddb6ee]
#6 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c2890e]
#7 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c289a2]
#8 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c2ad75]
#9 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bfac14]
#10 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c0724f]
#11 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bfac14]
#12 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7c06b34]
#13 /usr/lib/vmware-server-console/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7b0b298]
#14 /usr/lib/vmware-server-console/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7b0b586]
#15 /usr/lib/vmware-server-console/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7b0d77e]
#16 /usr/lib/vmware-server-console/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7d20459]
#17 /usr/lib/vmware-server-console/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7d083a1]
#18 /usr/lib/vmware-server-console/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7d08076]
#19 /usr/lib/vmware-server-console/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7d1f6eb]
vmware-server-console: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
bensode@bensode:~$

---

### Post by themtx on 2008-05-13
Check a few of the potential solutions in here:
[http://ubuntuforums.org/showthread.php?t=742714](http://ubuntuforums.org/showthread.php?t=742714)

in particular, this one:
[http://x86virtualization.com/virtualizationnews/howto-run-vmware-server-console-105-in-ubuntu-hardy-804.html](http://x86virtualization.com/virtualizationnews/howto-run-vmware-server-console-105-in-ubuntu-hardy-804.html)

worked fine for me.

---

### Post by bensode on 2008-05-13
Read through both and performed the hacks with no luck.  The only difference I see is the last line of my error looks like this, but everything before it is identical:

vmware-server-console: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

Think I might have to consider a rebuild of 8.04 before reverting back to 7.10.  Getlibs may have actually screwed something up.

---

### Post by ddales on 2008-05-15
[http://ubuntuforums.org/showthread.php?t=742714](http://ubuntuforums.org/showthread.php?t=742714)

Yep, this is the instruction set that I followed to get mine working on a 8.04 64bit machine.  The only thing that isn't correct is the GCC library directory didn't exist.  Mine was named something like x86_??????? so I just created the directory it was looking for and linked it.

Also, there is a patch for the installation or it won't compile.

---

### Post by bensode on 2008-05-20
Nope no dice.  Did a fresh installation on a new 64bit machine and have the same dead spot with the error after following each of the steps.

vmware-server-console: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.


This is JUST for the vmware-server-console on my workstation -- not a vmware-server implementation.  I have no way to manage my vmware-servers and after nearly two weeks of screwing around with it I have no other choice but to dump 8.04 and revert back to 7.10.

---

### Post by Kilz on 2008-05-20
[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934) install the server, it comes with the console.

---

