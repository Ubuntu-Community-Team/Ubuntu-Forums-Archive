---
title: "Having issues with startupmanager and splashy"
date: 2009-02-17
forum: x86 64-bit Users
---

### Post by The MAX on 2009-02-17
So I'm trying to install a custom boot loader theme of some sort, but I ran into the problem of the startupmanager not allowing me to check that box.

When I try to add an image to enable this function SUM just crashes.
Also it will not allow me to preview the splashy theme.

heres the output.
```
hughie@The-Flash:~$ sudo startupmanager
/usr/share/startupmanager/gtk_frontend.py:159: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.glade_xml = gtk.glade.XML(GLADE_FILE, None ,APP_NAME)
Grub2 not detected
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Grub Legacy detected
Usplash not detected
Splashy detected
Splashy ERROR: Couldn't splashy_start_splashy(). Error -2
#^ this is the error I get from trying to preview#

#and this is where it crashes#

Segmentation fault

hughie@The-Flash:~$ 

```

If anyone knows what I'm doing wrong I'd greatly appreciate it. thanks.

---

