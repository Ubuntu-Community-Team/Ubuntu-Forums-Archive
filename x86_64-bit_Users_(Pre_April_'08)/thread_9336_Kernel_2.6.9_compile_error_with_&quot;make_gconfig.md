---
title: "Kernel 2.6.9 compile error with &quot;make gconfig&quot; and &quot;make xconfig&quot;"
date: 2004-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kareema on 2004-12-27
I was not able to compile a new kernel with "make xconfig" or "make gconfig" using the source package "linux-source-2.6.9-10" for Hoary AMD64. All necessary packages for kernel compilation are installed. Here are the errors:

```

root@smartbook:/usr/src/linux # make xconfig
  HOSTCXX scripts/kconfig/qconf.o
  HOSTLD  scripts/kconfig/qconf
/usr/bin/ld: cannot find -lqt
collect2: ld returned 1 exit status
make[1]: *** [scripts/kconfig/qconf] Error 1
make: *** [xconfig] Error 2

``` 

Meanwhile I found a solution to the "make xconfig" problem: See [http://www.fedoraforum.org/forum/showthread.php?p=97712](http://www.fedoraforum.org/forum/showthread.php?p=97712). Since it is a AMD64 related problem I posted it here. Could be interesting for others having this problem. 

For the "make gconfig" problem I didn't find a solution. The errors are:

```

root@smartbook:/usr/src/linux # make gconfig
  HOSTCC  scripts/kconfig/gconf.o
In file included from /usr/include/gtk-2.0/gtk/gtkactiongroup.h:34,
                 from /usr/include/gtk-2.0/gtk/gtk.h:38,
                 from scripts/kconfig/gconf.c:17:
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:53: Warning: function declaration isn't a prototype
scripts/kconfig/images.c:6: Warning: `xpm_load' defined but not used
scripts/kconfig/images.c:36: Warning: `xpm_save' defined but not used
scripts/kconfig/images.c:66: Warning: `xpm_back' defined but not used
scripts/kconfig/images.c:175: Warning: `xpm_symbol_no' defined but not used
scripts/kconfig/images.c:192: Warning: `xpm_symbol_mod' defined but not used
scripts/kconfig/images.c:209: Warning: `xpm_symbol_yes' defined but not used
scripts/kconfig/images.c:226: Warning: `xpm_choice_no' defined but not used
scripts/kconfig/images.c:243: Warning: `xpm_choice_yes' defined but not used
scripts/kconfig/images.c:277: Warning: `xpm_menu_inv' defined but not used
scripts/kconfig/images.c:294: Warning: `xpm_menuback' defined but not used
scripts/kconfig/gconf.c:974: Warning: `renderer_toggled' defined but not used
  HOSTLD  scripts/kconfig/gconf
scripts/kconfig/gconf arch/x86_64/Kconfig

(gconf:9106): Gtk-CRITICAL **: gtk_label_set_use_underline: assertion `GTK_IS_LABEL (label)' failed

(gconf:9106): Gtk-CRITICAL **: gtk_label_set_use_underline: assertion `GTK_IS_LABEL (label)' failed

(gconf:9106): Gtk-CRITICAL **: gtk_label_set_use_underline: assertion `GTK_IS_LABEL (label)' failed

(gconf:9106): Gtk-CRITICAL **: gtk_label_set_use_underline: assertion `GTK_IS_LABEL (label)' failed

(gconf:9106): Gtk-CRITICAL **: gtk_label_set_use_underline: assertion `GTK_IS_LABEL (label)' failed

(gconf:9106): Gtk-CRITICAL **: gtk_label_set_use_underline: assertion `GTK_IS_LABEL (label)' failed

(gconf:9106): Gtk-CRITICAL **: gtk_label_set_use_underline: assertion `GTK_IS_LABEL (label)' failed

(gconf:9106): Gtk-CRITICAL **: gtk_label_set_use_underline: assertion `GTK_IS_LABEL (label)' failed

(gconf:9106): GLib-GObject-WARNING **: gsignal.c:1716: signal `pressed' is invalid for instance `0x5df120'

(gconf:9106): GLib-GObject-WARNING **: gsignal.c:1716: signal `pressed' is invalid for instance `0x5e3190'

(gconf:9106): GLib-GObject-WARNING **: gsignal.c:1716: signal `pressed' is invalid for instance `0x5e2c30'

(gconf:9106): GLib-GObject-WARNING **: gsignal.c:1716: signal `pressed' is invalid for instance `0x5df850'

(gconf:9106): GLib-GObject-WARNING **: gsignal.c:1716: signal `pressed' is invalid for instance `0x5da380'
make[1]: *** [gconfig] Segmentation fault
make: *** [gconfig] Error 2

```

---

### Post by Kareema on 2004-12-28
I submitted a bug report for this problem to bugzilla.ubuntu.com. Here is the answer:

[list=1]
[*]xconfig problem: "You need to install libqt3-dev"
[*]gconfig problem: "This seems like a genuine bug, though.  There was a patch posted some time ago to lkml: [http://seclists.org/lists/linux-kernel/2004/Jan/1100.html](http://seclists.org/lists/linux-kernel/2004/Jan/1100.html) but it doesn't seem to have been merged, and I'm not sure whether it's correct. One of the GTK guys should be able to say."
[/list]

Perhaps here is the right place for further discussion on point one: I don't understand why I have to use "libqt3-dev". I have installed "libqt3-mt-dev", the threaded version of the libraries - why can't I use these?

The post in the fedora forum says: "The problem is that the scripts/kconfig/Makefile looks for libqt-mt.so, finds it, then appends ../lib64 onto the lib path for some reason. Not sure if that's what it is supposed to do on other platforms, but it doesn't work on the Fedora Core 2 64-bit installation."

AFAIK this means that it is a problem with the Makefile and not with using libqt3-dev or libqt3-mt-dev. Or am I wrong?

---

