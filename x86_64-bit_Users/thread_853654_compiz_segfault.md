---
title: "compiz segfault?"
date: 2008-07-08
forum: x86 64-bit Users
---

### Post by Dekafox on 2008-07-08
This has happened a few times after a patch a few weeks ago, and usually only after several days uptime.  Usually I only first realize it happened after trying to start WoW under WINE, since the first symptom I've noticed is it being unbearably slow to bring up the program itself(on the order of 5 minutes compared to 10 seconds) and no sound when it does.  After this point terminals won't start normally, I couldn't get Firefox to start, and trying to use alt-F2 to start anything in a console or trying to launch the system monitor freezes the GUI.

I can ctrl-alt-backspace to restart GNOME, but when I login, nothing seems to happen for about 15-30 seconds, and then a little grey square appears in the upper left corner.  I see no text in it, though when I mouse over it I get a text selection icon.

I went back into /var/log/messages after seeing a similar thread about hard lockups, and this is the only thing I saw that looks relevant:

Jul  8 18:01:58 Iacon -- MARK --
Jul  8 18:15:47 Iacon kernel: [389208.345244] compiz.real[6019]: segfault at 12f59 rip 40fee0 rsp 7fff6abf6120 error 4
Jul  8 18:20:42 Iacon kernel: [389342.929202] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul  8 18:20:43 Iacon exiting on signal 15
Jul  8 18:21:47 Iacon syslogd 1.5.0#1ubuntu1: restart.
Jul  8 18:20:40 Iacon kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul  8 18:20:40 Iacon kernel: Loaded 28491 symbols from /boot/System.map-2.6.24-19-generic.
Jul  8 18:20:40 Iacon kernel: Symbols match kernel version 2.6.24.
Jul  8 18:20:40 Iacon kernel: Loaded 33960 symbols from 83 modules.
Jul  8 18:20:40 Iacon kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul  8 18:20:40 Iacon kernel: [    0.000000] Initializing cgroup subsys cpu
Jul  8 18:20:40 Iacon kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Ubuntu 2.6.24-19.34-generic)

The 18:20 line I believe was me restarting the system to get back to a suable OS, though I didn't look at the time.  I was able to get into a failsafe terminal before the restart, but I didn't know what to do to try to get it operational, as I hadn't checked the log at that point.

I'm running the x64 distro, system specs are a AMD X2 4600 AM2 on a Gigabyte GA-M57SLI-S4 motherboard, 4GB RAM, nVidia 8800GT vidcard with GDDR3 memory, though I can't remember the exact amount right now.  I'm only running Compiz at the Normal effects level, no floating cube or anything.

Any suggestions on what to do to stop this from happening?  Or what to do to recover when it happens?

Thanks in advance.

---

### Post by Dekafox on 2008-07-09
I ran dpkg -l | grep compiz and got this:
```

ii  compiz                                     1:0.7.4-0ubuntu7                                   OpenGL window and compositing manager
ii  compiz-core                                1:0.7.4-0ubuntu7                                   OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.7.4-0ubuntu1                                     Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.7.4-0ubuntu5                                     Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.7.4-0ubuntu7                                   OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.7.4-0ubuntu7                                   OpenGL window and compositing manager - plug
ii  compizconfig-backend-gconf                 0.7.4-0ubuntu1                                     Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.7.4-0ubuntu1                                     Settings library for plugins - OpenCompositi

```

and my /etc/apt/sources.list is:
```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://wine.budgetdedicated.com/apt hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"
```

Couple questions:
Would running 'compiz --replace' restart compiz in this situation, either from the alt-F2 run dialog or from a safe mode xterm?

Should I do what was mentioned in this [thread]("http://ge.ubuntuforums.com/showthread.php?p=5098574")? When mine goes down as I said it's not immediate, it usually only happens after a few days at least.

Anyone else have any suggestions or solutions?

---

### Post by Dekafox on 2008-07-15
Okay, I had a console up this time when it happened so I tried a compiz --replace.  It started fine, then seemed to hang on the gtk-windowdecorator I believe it was.  I looked thorugh my messages log this time and didn't see any mention of the segfault, so I did a little digging, and found this in the daemon log:

```
Jul 15 19:05:13 Iacon gdm[5665]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jul 15 19:05:56 Iacon gdm[17111]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jul 15 19:06:14 Iacon gdm[17216]: GLib-CRITICAL: g_key_file_get_string: assertion `key_file != NULL' failed 
Jul 15 19:06:14 Iacon gdm[17216]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed 
Jul 15 19:06:14 Iacon gdm[17264]: Gtk-WARNING: Ignoring the separator setting 
Jul 15 19:07:29 Iacon gdm[17216]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jul 15 19:08:12 Iacon gdm[17343]: GLib-CRITICAL: g_key_file_get_string: assertion `key_file != NULL' failed 
Jul 15 19:08:12 Iacon gdm[17343]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed 
Jul 15 19:08:12 Iacon gdm[17388]: Gtk-WARNING: Ignoring the separator setting 

```

Not sure if those are caused by my ctrl-alt-backspacing or not, adn I see them in the syslog too.

Doesn't ANYONE have any insights? >.< :confused:](*,)](*,)

---

