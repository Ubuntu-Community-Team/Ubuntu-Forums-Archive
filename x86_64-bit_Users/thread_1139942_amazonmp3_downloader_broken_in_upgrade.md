---
title: "amazonmp3 downloader broken in upgrade?"
date: 2009-04-27
forum: x86 64-bit Users
---

### Post by thedarksavant on 2009-04-27
I upgraded to 9.04 and now my amazonmp3 downloader application will not connect to the download server. It launches but with this output:

```
ccooley@enterprise:~$ amazonmp3 
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so

```

When trying to download songs, it doesn't connect and the status is incomplete. I tried
```
sudo getlibs /usr/bin/amazonmp3
```
again but getlibs claims all the libraries are up to date.

Any ideas?

---

### Post by Slim Odds on 2009-04-27
Well.. for starters... the /usr/lib/... tree is for 64 bit stuff.

32 bit libs go in /usr/lib32/

---

