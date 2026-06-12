---
title: "vmplayer on amd64"
date: 2006-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by tomcoussement on 2006-01-03
Has anyone managed to install an work with vmware player on kubuntu amd64?

I installed it but I get multiple gtk errors when I try to start vmplayer...

I haven't got an answer that helps on the vmware forums 
-> [https://www.vmware.com/community/thread.jspa?messageID=319660&#319660]("https://www.vmware.com/community/thread.jspa?messageID=319660&#319660")

---

### Post by shadwstalkr on 2006-01-13
Have you tried it under Gnome?  It works fine for me under Gnome, but not KDE (both on the same amd64 Ubuntu box).  I haven't had time to try to figure out an answer yet, sorry.

---

### Post by shadwstalkr on 2006-01-16
I got it working under KDE.  Follow the steps in this thread [http://lists.debian.org/debian-amd64/2005/05/msg00707.html]("http://lists.debian.org/debian-amd64/2005/05/msg00707.html")

What I did was write a shell script that sets the environment variables before it launches vmplayer with the vm I always use.

---

### Post by tomcoussement on 2006-01-20
Ok, thx I got it working!

For those who do not want to read the mailinglist, this is what I have done to make it work.

- install ia32-libs and ia32-libs-gtk if you haven't already

- cp /etc/gtk-2.0/gdk-pixbuf.loaders /etc/gtk-2.0/gdk-pixbuf.loaders32

- sed 's:/usr/lib/:/usr/lib32/:' < /etc/gtk-2.0/gdk-pixbuf.loaders > /etc/gtk-2.0/gdk-pixbuf.loaders32 

- insert the following line into /usr/bin/vmplayer before the exec line:
GCONV_PATH=/usr/lib32/gconv LD_PRELOAD=/usr/lib32/libpangohack.so.0.0 GDK_PIXBUF_MODULE_FILE=/etc/gtk-2.0/gdk-pixbuf.loaders32

This is how I got it working (helped me to get acroread working to)

Thx shadwstalkr!!

---

