---
title: "VMMON mismatch in VMWare"
date: 2005-12-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by andrewsawyer on 2005-12-29
Hiya,

I am getting the following error in VMware Workstation:

> Version mismatch with vmmon
module: expecting 137.0, got 122.0.
You have an incorrect version of the
'vmmon' kernel module.
Try reinstalling VMware Workstation.

Followed by:

> Failed to initalize
monitor device.

Followed by:

> Unable to change virtual
machine power state:
Cannot find a valid peer
process to connect to.

Followed by:

> Failed to reply to
the dialog: Pipe:
Read failed

When trying to start either an existing or new virtual machine.

I have run sudo ./vmware-config.pl from /usr/lib, and the following is the output:

```
andrew@elisha:/usr/bin$ sudo ./vmware-config.pl
Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel?
[/lib64/modules/2.6.12-10-amd64-generic/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Unknown VMware Workstation 5.5.0 build 18463 detected. Building for TOT.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib64/modules/2.6.12-10-amd64-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-amd64-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-ffreestanding" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/compat.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-amd64-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes]

Extracting the sources of the vmnet module.

Building the vmnet module.

Unknown VMware Workstation 5.5.0 build 18463 detected. Building for TOT.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib64/modules/2.6.12-10-amd64-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-amd64-generic'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_linux.x86_64.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-amd64-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

The configuration of VMware Workstation 5.5.0 build-18463 for Linux for this
running kernel completed successfully.

You can now run VMware Workstation by invoking the following command:
"/usr/bin/vmware".

Enjoy,

--the VMware team

```

I still however get the same error next time around.

I am also only able to run VMware Workstation from root (sudo) as it makes the preferences file in my home directory a root only file.

And finally, I get a whole load of errors when I do run the program (in the command box before the actual program loads up).  These are shown below on the next replay - too long for one post:

see below post.

I would really appreciate some help on getting this rectified - even if it mean uninstalling and reinstalling VMware Workstation - I'm not 100% on how to uninstall.

Many thanks in advance.

Andy

---

### Post by andrewsawyer on 2005-12-29
```
andrew@elisha:/usr/bin$ sudo vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib32/libcairo.so.2)
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed

(vmware:16978): GdkPixbuf-WARNING **: Couldn't convert text chunk value to UTF-8.

(vmware:16978): GdkPixbuf-CRITICAL **: file ../../gtk+-2.4.14/gdk-pixbuf/gdk-pixbuf.c: line 662 (gdk_pixbuf_set_option): assertion `key != NULL' failed
andrew@elisha:/usr/bin$

```

---

### Post by andrewsawyer on 2005-12-30
Please consider this thread closed - I uninstalled and then reinstalled - all is now working.

---

### Post by andrewsawyer on 2005-12-30
Problem - Sorry, not closed!!!

All worked fine, until I ran the update.  This has now sent me back to square one.  It is therefore a fault with the latest upgrade.

Does anyone know how to roll back, or fix the problem?

---

### Post by speeves on 2006-04-19
Check out the newest vmware-any-any-update package at:

[http://ftp.cvut.cz/vmware/](http://ftp.cvut.cz/vmware/)

101 worked for me :)

!nH1m,
speeves

---

