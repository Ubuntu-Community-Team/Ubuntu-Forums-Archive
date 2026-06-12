---
title: "bonfire"
date: 2006-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by davmor2 on 2006-06-01
has anyone been able to install Bonfire on their system.

---

### Post by JoWilly on 2006-06-02
[QUOTE=davmor2]has anyone been able to install Bonfire on their system.[/QUOTE]

Nope, does not build here on 64bit.

---

### Post by Rouquier on 2006-06-13
Hi
I'm bonfire developper. Could you tell me more about the issues you ran into when you tried to install/build? bonfire.

---

### Post by ato on 2006-06-13
Hi Rouquier,
when i try to compile bonfire i've got the following error:

```
Requested 'gnome-vfs-2.0 >= 2.14.2' but version of gnome-vfs is 2.14.1
```

there's a workaround you know?

Thanks

---

### Post by davmor2 on 2006-06-14
I can't remember off hand When I get home tonight I will try to install again and see what it say,  the giest I think is though that it can't find any libraries. GTK etc.

---

### Post by davmor2 on 2006-06-14
here's the last few line of output from ./configure

checking for ANSI C header files... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for BONFIRE... configure: error: Package requirements (        glib-2.0 >= 2.6.0                       gdk-2.0 >= 2.6.0             gtk+-2.0 >= 2.6.0                       libgnome-2.0 >= 2.10.0          libgnomeui-2.0 >= 2.10.0            gnome-vfs-2.0 >= 2.14.0          gnome-vfs-module-2.0    gstreamer-0.10 >= 0.10.6        gstreamer-plugins-base-0.10 >= 0.10.0        hal >= 0.5      dbus-1 >= 0.30  dbus-glib-1 >= 0.30     libnautilus-burn >= 2.14.0      libxml-2.0 >= 2.6.0) were not met:

No package 'gdk-2.0' found
No package 'gtk+-2.0' found
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'gnome-vfs-2.0' found
No package 'gnome-vfs-module-2.0' found
No package 'gstreamer-plugins-base-0.10' found
No package 'hal' found
No package 'dbus-1' found
No package 'dbus-glib-1' found
No package 'libnautilus-burn' found

I don't know what to do about changing the lib file or anything.

---

### Post by ato on 2006-06-14
davmor2 you must install all dev packages of that libs.

---

### Post by davmor2 on 2006-06-14
Thanks a pain in the butt finding everything but it is up and running out of curiosity though I see there are loads of options like libnotify and stuff at the end how do I go about enabling them please.:D

---

### Post by henriquemaia on 2006-06-14
[quote=davmor2]Thanks a pain in the butt finding everything but it is up and running out of curiosity though I see there are loads of options like libnotify and stuff at the end how do I go about enabling them please.:D[/quote]

[Corbelius]("http://ubuntuforums.org/member.php?u=32301") has set up an unofficial Dapper repository with severall packages including bonfire.

Read more on this here:

[http://ubuntuforums.org/showpost.php?p=1134877&postcount=1](http://ubuntuforums.org/showpost.php?p=1134877&postcount=1)

---

### Post by xplode_me on 2006-06-15
[QUOTE=ato]Hi Rouquier,
when i try to compile bonfire i've got the following error:

```
Requested 'gnome-vfs-2.0 >= 2.14.2' but version of gnome-vfs is 2.14.1
```

there's a workaround you know?

Thanks[/QUOTE]


I'm having this problem too :(
Anyone knows how to deal with it?

---

### Post by JoWilly on 2006-06-15
[quote=xplode_me]I'm having this problem too :(
Anyone knows how to deal with it?[/quote]

Yes, install the binary from the corbelius repo, its the latest version :D

---

### Post by xplode_me on 2006-06-15
i'm on ~x86 :(
just saw that error and replied too, but i have no x64 machine

---

### Post by Tao on 2006-06-16
3 ways for gnome-vfs :
- download the 2.14.2 version at [http://ftp.gnome.org/pub/GNOME/platform/2.14/2.14.2/sources/](http://ftp.gnome.org/pub/GNOME/platform/2.14/2.14.2/sources/) then compile it and install it.
- edit the ./configure script to change the minimal version of gnome-vfs from 2.14.2 to 2.14.2. This solution is at your own risks, but I think it works if you don't use vfs.
- wait for an upgrade of gnome-vfs in repo.

---

### Post by Rouquier on 2006-06-20
Your solutions are the right ones.

For the impatient the best is the second option. The only risk is if you try to burn over a network (and in particular samba). Gnome-vfs-2.14.1 will mess up almost immediatly. That's why I bumped up the requirements to 2.14.2.

---

### Post by kaktusztea on 2006-06-20
Add this line to /etc/apt/sources.list:
```
deb http://hu.archive.ubuntu.com/ubuntu dapper-updates main restricted
```

---

