---
title: "Openoffice cant open"
date: 2008-06-26
forum: x86 64-bit Users
---

### Post by Fir3chi3f on 2008-06-26
Hi all, I'm running 64bit ubuntu 8.04. 

Whenever I attempt to launch openoffice the loading screen will appear and I see the openoffice window then closes right away and gives me this:


```
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7fb182dd097c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7fb182dd0a15]
#2 /usr/lib/libX11.so.6 [0x7fb186a9a323]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x44) [0x7fb186a91d54]
#4 /usr/lib/libgdk-x11-2.0.so.0(gdk_window_new+0x395) [0x7fb18297ac05]
#5 /usr/lib/libgtk-x11-2.0.so.0 [0x7fb17e0094c8]
#6 /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10f) [0x7fb181e0ebcf]
#7 /usr/lib/libgobject-2.0.so.0 [0x7fb181e22386]
#8 /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x875) [0x7fb181e240d5]
#9 /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83) [0x7fb181e24483]
#10 /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0x77) [0x7fb17dffa957]
#11 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7fb17e3b276d]
#12 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7fb17e3b316a]
#13 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7fb17e3b382b]
#14 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7fb17e38bf64]
#15 /usr/lib/openoffice/program/libvcl680lx.so [0x7fb18a3374ed]
#16 /usr/lib/openoffice/program/libvcl680lx.so [0x7fb18a2cc322]
#17 /usr/lib/openoffice/program/libvcl680lx.so(_ZN9TabDialogC2EP6WindowRK5ResId+0x5f) [0x7fb18a3091cf]
#18 /usr/lib/openoffice/program/libsvx680lx.so [0x7fb1771eb084]
#19 /usr/lib/openoffice/program/libsvx680lx.so [0x7fb1773bfdb4]

```

The same problem is with my laptop running the same setup but, I haven't checked if the output is the same; will post back on that.

Any comments questions, are greatly appreciated.

---

### Post by mattman85 on 2008-06-26
I'm having basically the same issue.  I dont get any prompt afterwards, but if I go to a .DOC file, and double-click to open it, the OpenOffice 2.4 logo shows up, as if OOo is loading, but then it goes away, and doesn't open at all.  I'm left having to go to Applications > Office > OOo Word Processor to open up Writer and then click on File > Open..  to actually see anything.  Any ideas?

---

### Post by Fir3chi3f on 2008-06-26
> **mattman85 said:**
> I'm having basically the same issue.  I dont get any prompt afterwards, but if I go to a .DOC file, and double-click to open it, the OpenOffice 2.4 logo shows up, as if OOo is loading, but then it goes away, and doesn't open at all.  I'm left having to go to Applications > Office > OOo Word Processor to open up Writer and then click on File > Open..  to actually see anything.  Any ideas?

The only way I can open any .doc is with ```
sudo openoffice
``` and then file open.

What is the output if you launch it from the term?

---

### Post by oldrocker99 on 2008-06-26
> **Fir3chi3f said:**
> Hi all, I'm running 64bit ubuntu 8.04. 

Whenever I attempt to launch openoffice the loading screen will appear and I see the openoffice window then closes right away and gives me this:


```
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7fb182dd097c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7fb182dd0a15]
#2 /usr/lib/libX11.so.6 [0x7fb186a9a323]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x44) [0x7fb186a91d54]
#4 /usr/lib/libgdk-x11-2.0.so.0(gdk_window_new+0x395) [0x7fb18297ac05]
#5 /usr/lib/libgtk-x11-2.0.so.0 [0x7fb17e0094c8]
#6 /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10f) [0x7fb181e0ebcf]
#7 /usr/lib/libgobject-2.0.so.0 [0x7fb181e22386]
#8 /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x875) [0x7fb181e240d5]
#9 /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83) [0x7fb181e24483]
#10 /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0x77) [0x7fb17dffa957]
#11 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7fb17e3b276d]
#12 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7fb17e3b316a]
#13 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7fb17e3b382b]
#14 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7fb17e38bf64]
#15 /usr/lib/openoffice/program/libvcl680lx.so [0x7fb18a3374ed]
#16 /usr/lib/openoffice/program/libvcl680lx.so [0x7fb18a2cc322]
#17 /usr/lib/openoffice/program/libvcl680lx.so(_ZN9TabDialogC2EP6WindowRK5ResId+0x5f) [0x7fb18a3091cf]
#18 /usr/lib/openoffice/program/libsvx680lx.so [0x7fb1771eb084]
#19 /usr/lib/openoffice/program/libsvx680lx.so [0x7fb1773bfdb4]

```

The same problem is with my laptop running the same setup but, I haven't checked if the output is the same; will post back on that.

Any comments questions, are greatly appreciated.

I had the same problem, and solved it by going into Synaptic and completely removing the program, then going to [www.sun.com](www.sun.com) and downloading the package from them. Even though the package was an .rpm rather than a .deb, it installed and works perfectly.

:guitar:

---

### Post by pixel :-) on 2008-06-26
delete the config folder of openoffice.

If sudo works the explanation would be that simply root uses a different config file.

---

### Post by Fir3chi3f on 2008-06-26
Sry oldrocker99 and pixel :-). Neither of thos worked. 

In synaptic I 'completely removed' and reinstalled everything that said OpenOffice. And it is working again but it looks a little funny. A little silvery from the original look but, oh well thanks for all of you help.

---

### Post by mattman85 on 2008-06-26
> **Fir3chi3f said:**
> The only way I can open any .doc is with ```
sudo openoffice
``` and then file open.

What is the output if you launch it from the term?


It works fine if I open OOo with term.  whats odd is that after I used the term to open OpenOffice, I was able to double-click on a random .DOC file, and it worked fine..

---

