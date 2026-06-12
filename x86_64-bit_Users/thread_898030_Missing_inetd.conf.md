---
title: "Missing inetd.conf"
date: 2008-08-22
forum: x86 64-bit Users
---

### Post by -gs- on 2008-08-22
Hi, I have been trying to install VMWare Server, and when configuring the port for remote console connections [902] it states that I'm missing inetd/xinetd or the .conf file of either. I looked in my synaptic package manager and it says that I have update-inetd, but I'm missing inetd.conf in my etc file. I don't have xinetd or xinetd.conf.

How can I get inetd.conf?

---

### Post by -gs- on 2008-08-22
Nevermind, I fixed that by installing it in Konsole rather than Console. 

Now I have a new problem, though. This time running VMWare. This is what I get:


> Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
/usr/share/themes/Human/gtk-2.0/gtkrc:43: error: unexpected character `@', expected string constant
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7073767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf70738b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf7ef21bd]
#3 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xf7de2969]
#4 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xf7de2f4c]
#5 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c28180]
#6 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c28d2c]
#7 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bf8c14]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c0524f]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bf8c14]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7c04b34]
#11 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7b09298]
#12 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7b09586]
#13 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7b0b77e]
#14 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7d1e459]
#15 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7d063a1]
#16 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7d06076]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7d1d6eb]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xf7d1cd46]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xf7d1d0b8]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7073767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf707381e]
#2 /usr/lib32/libX11.so.6 [0xf7ef1518]
#3 /usr/lib32/libX11.so.6(XAddExtension+0x2c) [0xf7ed4c9c]
#4 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xf7ddaed7]
#5 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7dd98b1]
#6 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7dd9d39]
#7 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xf7dd9ec0]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c269b6]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c28d75]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bf8c14]
#11 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7c0524f]
#12 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bf8c14]
#13 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7c04b34]
#14 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7b09298]
#15 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7b09586]
#16 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7b0b77e]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7d1e459]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7d063a1]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7d06076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

---

### Post by Ehtetur on 2008-08-22
You're on the right track... default Hardy's doesn't have the file /etc/inetd.conf...
You'll need to create & configure your own inetd.conf with this command:
> sudo update-inetd

---

### Post by -gs- on 2008-08-22
See second post. Thanks for the input, tho

---

### Post by Ehtetur on 2008-08-22
good deal but damn, your problems come and go so fast :twisted:

Have a look at [bodhi.zazen]("http://ubuntuforums.org/showpost.php?p=4868919&postcount=1")'s vmware server howto...
Its got all the steps for installing vmware server on ubuntu...

---

