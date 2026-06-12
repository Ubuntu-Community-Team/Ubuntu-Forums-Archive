---
title: "Open Office Loading problem Locking assertion failure"
date: 2008-06-21
forum: x86 64-bit Users
---

### Post by pspmasterpro on 2008-06-21
O.K. So I have the AMD 64-bit version of Ubuntu 8.04 when I try to load an Open Office application I see the splash screen and the loading bar and then after, nothing happens so I tried to run it in the terminal and this is what I got.

```

pspmasterpro@pspmasterpro-desktop:~$ openoffice
pspmasterpro@pspmasterpro-desktop:~$ Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7fb94004a97c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7fb94004aa15]
#2 /usr/lib/libX11.so.6 [0x7fb943d14323]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x44) [0x7fb943d0bd54]
#4 /usr/lib/libgdk-x11-2.0.so.0(gdk_window_new+0x395) [0x7fb93fbf4c05]
#5 /usr/lib/libgtk-x11-2.0.so.0 [0x7fb93b2834c8]
#6 /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10f) [0x7fb93f088bcf]
#7 /usr/lib/libgobject-2.0.so.0 [0x7fb93f09c386]
#8 /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x875) [0x7fb93f09e0d5]
#9 /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83) [0x7fb93f09e483]
#10 /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0x77) [0x7fb93b274957]
#11 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7fb93b62c76d]
#12 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7fb93b62d16a]
#13 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7fb93b62d82b]
#14 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7fb93b605f64]
#15 /usr/lib/openoffice/program/libvcl680lx.so [0x7fb9475b14ed]
#16 /usr/lib/openoffice/program/libvcl680lx.so [0x7fb947546322]
#17 /usr/lib/openoffice/program/libvcl680lx.so(_ZN9TabDialogC2EP6WindowRK5ResId+0x5f) [0x7fb9475831cf]
#18 /usr/lib/openoffice/program/libsvx680lx.so [0x7fb93427b084]
#19 /usr/lib/openoffice/program/libsvx680lx.so [0x7fb93444fdb4]

pspmasterpro@pspmasterpro-desktop:~$ 


```

This is displayed in the Terminal right after the splash screen. Any ideas as to what the problem might be? Does it have anything to do with the Compiz affects or the ATI driver?

---

### Post by chewearn on 2008-06-22
It's a high priority bug:
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/185311](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/185311)

There are workarounds from the bug report above; personally, I am able to get it working via the ssh method.

.

---

### Post by pspmasterpro on 2008-06-22
O.K. It seams to work when I type sudo openoffice or if I run it off the root Terminal

---

### Post by kungfupanda on 2008-06-26
> **pspmasterpro said:**
> O.K. It seams to work when I type sudo openoffice or if I run it off the root Terminal

try to type '/usr/lib/openoffice/program/soffice.bin'.

---

