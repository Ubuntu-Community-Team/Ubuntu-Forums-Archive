---
title: "gdm starts before system is completely up (e.g. nfs) -&gt; cannot login"
date: 2006-12-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by suxen on 2006-12-10
Hi all,
we have linux boxes (amd64) with ubuntu 6.10 installed in a heterogenous
network. home directories are exported by an nfs server, which works well with all other machines (mostly digital/dec/compaq/hp-alphas with tru64 5.1B).
On some of the linux machines I experience the strange behaviour, that
after booting, I cannot login via gdm. In particular, after typing my
username, it takes a long time until I am asked for password, about one minute, say. After typing the password it takes again about one minute until the message "wrong password ..." appears and the whole story starts over again.

I went to tty1 via strg-alt-f1 to login as root. however, just after typing 
login: root
a lot of console messages appear, which normally belong to the boot-phase,
see below.

Finally, logged in as root I say
#/etc/init.d/gdm restart,
go back to strg-alt-f7 and login goes smoothly.
Seems to me, gdm starts before the system is completely up, i.e. nis and nfs are up. Anyone any idea?
Thanks in advance.

Here's the complete /var/log/boot file, note the one-minute break between
12:43:44 and 12:44:36, this is just the time I tried to login via gdm.

```
Dec 10 12:43:30 rcS:  * Reading files needed to boot...                  [ ok ] 
Dec 10 12:43:30 rcS: touch: cannot touch `/lib/init/rw/libnss-ldap.bind_policy_s
oft': No such file or directory
Dec 10 12:43:30 rcS:  * Setting preliminary keymap...                    [ ok ] 
Dec 10 12:43:30 rcS:  * Preparing restricted drivers...                  [ ok ] 
Dec 10 12:43:30 rcS:  * Starting basic networking...                     [ ok ] 
Dec 10 12:43:31 rcS:  * Starting kernel event manager...                 [ ok ] 
Dec 10 12:43:37 rcS:  * Loading hardware drivers...                      [ ok ] 
Dec 10 12:43:37 rcS:  * Loading manual drivers...                        [ ok ] 
Dec 10 12:43:38 rcS:  * Mounting local filesystems...                    [ ok ] 
Dec 10 12:43:38 rcS:  * Activating swapfile swap...                      [ ok ] 
Dec 10 12:43:38 rcS:  * Configuring network interfaces...                [ ok ] 
Dec 10 12:43:39 rcS: Starting "Shorewall firewall": done.
Dec 10 12:43:39 rcS:  * Not starting portmap daemon.  Already running.       
                                                                         [ ok ] 
Dec 10 12:43:40 rcS:  * Setting up console font and keymap...            [ ok ] 
Dec 10 12:43:43 rc2:  * Loading ACPI modules...                          [ ok ] 
Dec 10 12:43:43 rc2:  * Starting ACPI services...                        [ ok ] 
Dec 10 12:43:43 rc2:  * Starting system log...                           [ ok ] 
Dec 10 12:43:43 rc2:  * Starting kernel log...                           [ ok ] 
Dec 10 12:43:44 rc2:  * Starting GNOME Display Manager...                [ ok ] 
Dec 10 12:43:44 rc2: Not starting K Display Manager (kdm); it is not the default
 display manager.
Dec 10 12:43:44 rc2: Setting NIS domainname to: xxxxx

```
#############################################
graphical login
#############################################
```

Dec 10 12:44:36 rc2: Starting NIS services: ypbind [binding to YP server ..... d
one] 
Dec 10 12:44:36 rc2:  * Starting Common Unix Printing System: cupsd      [ ok ] 
Dec 10 12:44:37 rc2:  * Starting HP Linux Printing and Imaging System       
                                                                         [ ok ]
Dec 10 12:44:40 rc2:  * Starting PostgreSQL 7.4 database server          [ ok ] 
Dec 10 12:44:40 rc2: Starting atieventsd: done.
Dec 10 12:44:40 rc2:  * Starting system message bus dbus                 [ ok ] 
Dec 10 12:44:42 rc2:  * Starting Hardware abstraction layer hald         [ ok ] 
Dec 10 12:44:43 rc2:  * Starting System Tools Backends system-tools-backends    
                                                                         [ ok ] 
Dec 10 12:44:43 rc2:  * Starting DirMngr dirmngr                         [ ok ] 
Dec 10 12:44:43 rc2:  * Starting mouse interface server: gpm             [ ok ] 
Dec 10 12:44:43 rc2: Starting LAN Information Server: lisa.
Dec 10 12:44:44 rc2:  * Starting Postfix Mail Transport Agent postfix       
                                                                         [ ok ]
Dec 10 12:44:44 rc2:  * Starting powernowd...                            [ ok ] 
Dec 10 12:44:44 rc2:  * Starting OpenBSD Secure Shell server...          [ ok ] 
Dec 10 12:44:45 rc2: Setting up X font server socket directory /tmp/.font-unix..
.done.
Dec 10 12:44:45 rc2: Starting X font server: xfs.
Dec 10 12:44:45 rc2:  * Starting NFS common utilities                    [ ok ] 
Dec 10 12:44:45 rc2:  * Starting Bluetooth services                      [ ok ]
Dec 10 12:44:45 rc2:  * Starting NTP server...                           [ ok ] 
Dec 10 12:44:45 rc2:  * Starting anac(h)ronistic cron: anacron           [ ok ] 
Dec 10 12:44:45 rc2:  * Starting deferred execution scheduler atd        [ ok ] 
Dec 10 12:44:45 rc2:  * Starting periodic command scheduler...           [ ok ] 
Dec 10 12:44:45 rc2:  * Enabling additional executable binary formats binfmt-sup
port                                                                     [ ok ] 
Dec 10 12:44:45 rc2:  * Checking battery state...                        [ ok ] 
Dec 10 12:44:45 rc2:  * Running local boot scripts (/etc/rc.local)              mount: <server:/directory> already mounted on <mountpoint> or busy
Dec 10 12:44:45 rc2: mount: according to mtab, <server:/directory> is mounted on <mountpoint>
Dec 10 12:44:45 rc2:                                                     [fail]
Dec 10 12:44:45 rc2: Not starting X display manager (xdm); it is not the default
 display manager.

```

---

