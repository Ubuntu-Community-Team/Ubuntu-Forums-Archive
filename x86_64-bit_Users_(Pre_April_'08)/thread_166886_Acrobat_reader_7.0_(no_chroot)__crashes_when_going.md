---
title: "Acrobat reader 7.0 (no chroot)  crashes when going to print"
date: 2006-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by hardhu on 2006-04-27
Hello everybody, I have managed to install Acrobat Reader 7.0 without using the chroot, following the suggestions I have found on a debian mailing list:
[http://lists.debian.org/debian-amd64/2005/05/msg00707.html](http://lists.debian.org/debian-amd64/2005/05/msg00707.html)

To summarize I did these steps:
--
1. Install ia32-libs (if you don't already have it);

2. Install  ia32-libs-gtk (if you don't already have it);

3. Get the acroread debian package from
[ftp://ftp.nerim.net/debian-marillat/pool/main/a/acroread/](ftp://ftp.nerim.net/debian-marillat/pool/main/a/acroread/)
While you are at it, you may also get the extra plugins.

4. Install them it with dpkg -i --force-all. It wont go without force, because it is the wrong architecture.

5. Edit /usr/bin/acroread. Towards the end, there is a line 
  exec "$ACRO_EXEC_CMD" ${1+"$@"}
Add 
      GCONV_PATH=/usr/lib32/gconv LD_PRELOAD=/usr/lib32/libpangohack.so.0.0  GDK_PIXBUF_MODULE_FILE=/etc/gtk-2.0/gdk-pixbuf.loaders32
    at the beginning of this line, before exec. 
  6. Copy /etc/gtk-2.0/gdk-pixbuf.loaders to
/etc/gtk-2.0/gdk-pixbuf.loaders32, and replace all references to
/usr/lib/ with /usr/lib32/:

sed 's:/usr/lib/:/usr/lib32/:' < /etc/gtk-2.0/gdk-pixbuf.loaders >
/etc/gtk-2.0/gdk-pixbuf.loaders32

7. To remove the warning during module loading:

rm /usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/PPKLite.api  

--

Now Acrobat Reader is working, I get only these warnings when I launch it:
--
(acroread:10148): Gdk-WARNING **: locale not supported by Xlib

(acroread:10148): Gdk-WARNING **: cannot set locale modifiers

(acroread:10148): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/immodules/im-xim.so: cannot open shared object file:          No such file or directory

(acroread:10148): Gtk-WARNING **: Loading IM context type 'xim' failed

(acroread:10148): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/immodules/im-xim.so: cannot open shared object file:          No such file or directory

(acroread:10148): Gtk-WARNING **: Loading IM context type 'xim' failed

(acroread:10148): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/immodules/im-xim.so: cannot open shared object file:          No such file or directory

(acroread:10148): Gtk-WARNING **: Loading IM context type 'xim' failed

(acroread:10148): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/immodules/im-xim.so: cannot open shared object file:          No such file or directory

(acroread:10148): Gtk-WARNING **: Loading IM context type 'xim' failed
--

But when I try to print anything, it crashes immediately without giving any explanations.

Has anybody the same setup and can help me?

---

