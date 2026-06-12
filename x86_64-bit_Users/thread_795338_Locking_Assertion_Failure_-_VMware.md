---
title: "Locking Assertion Failure - VMware"
date: 2008-05-15
forum: x86 64-bit Users
---

### Post by reagentz on 2008-05-15
I have been running 8.04 amd64 since its release, haven't ran into any major issues that I couldn't find a fix for looking through other threads or websites, etc.

This time I am stumped and the only thing I have seen this "assertion lock failure" topic on was Java, MATLAB, or some other program I do not use.

I am running the latest VMware, I had it installed right after upgrading to 8.04 amd64 version of Ubuntu and have kept it up-to-date. I have not had one issue, this past week I have not ran it, I have installed several updates, and just setup my x*.conf file for dual monitors (twinview for nVidia). Other than editing my conf file to enable twinview that is the only major system change I have made, well other than our latest Ubuntu updates.

Tonight I try to load VMware so I can mess around with something and it would never load, so I tried loading it in terminal just to see what was happening. Now I get this:

```

reagentz@Lost:~$ vmware
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
/home/reagentz/.themes/MinimaLista/gtk-2.0/gtkrc:19: error: unexpected character `@', expected string constant
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf705f767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf705f8b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf7ede1bd]
#3 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xf7dce969]
#4 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xf7dcef4c]
#5 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c14180]
#6 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c14d2c]
#7 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7be4c14]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bf124f]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7be4c14]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7bf0b34]
#11 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7af5298]
#12 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7af5586]
#13 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7af777e]
#14 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7d0a459]
#15 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7cf23a1]
#16 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7cf2076]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7d096eb]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xf7d08d46]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xf7d090b8]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf705f767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf705f81e]
#2 /usr/lib32/libX11.so.6 [0xf7edd518]
#3 /usr/lib32/libX11.so.6(XAddExtension+0x2c) [0xf7ec0c9c]
#4 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xf7dc6ed7]
#5 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7dc58b1]
#6 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7dc5d39]
#7 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xf7dc5ec0]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c129b6]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c14d75]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7be4c14]
#11 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bf124f]
#12 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7be4c14]
#13 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7bf0b34]
#14 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7af5298]
#15 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7af5586]
#16 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7af777e]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7d0a459]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7cf23a1]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7cf2076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
reagentz@Lost:~$

```

I've tried repairing the install by running sudo vmware-config.pl, also uninstalling and reinstalling VMware. Neither has worked?!

Anyone have any suggestions, or have run into the same problem lately?

Thanks in advance!

---

### Post by Kilz on 2008-05-15
It looks like its a long list of error , not just the last one. vmware is a 32bit application did you install ia32-libs? Also for other libraries it asks for that are not in ia32-libs you will need [getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs").

---

### Post by reagentz on 2008-05-15
I've switched to 64bit Virtualbox and it works great, installs using .deb manager no config issues or hoops to jump through. I'm set now thanks guys, on this thread and previous thred.

---

