---
title: "after reboot, 32bit FireFox forgets about plugins!"
date: 2006-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by LinuxConvertJune2006 on 2006-08-12
I can pretty much re-create this issue. To resolve it in the past, I re-ran Kilz's firefox32 scripts and then in about:plugins the plugins are listed again. The plugins directory has the files in it, I'm not sure why after reboot I need to keep re-running? any thoughts?

---

### Post by Kilz on 2006-08-12
Sounds kind of strange, because the plugins are files. I think wwe need to make sure the files are there on reboot. That and the launcher is in fact running 32bit firefox and not 64bit firefox after reboot.
The script installs a deb. It installs firefox32 to /usr/local/firefox32 the plugins are in /usr/local/firefox32/plugins. On the next reboot make sure the plugins are there, and if so click on the firefox launch sh file in  /usr/local/firefox32.

---

### Post by LinuxConvertJune2006 on 2006-08-13
Hi Kilz thanks for the reply!  I know it sounds weird, ubt after another reboot, I got the same result. So after this reboot, I started up a movie in Mplayer (DVD) then launched FireFox32 and about:plugins show everything as being there, and the plugins work fine. I'll come back to this thread if I keep aving problems, but you're right it should just "work" since the plugin files were there.

FYI I did check to see if the files existed when I last had this issue, and they did, but in about:plugins (verifying I was launcing firefox32) nothing but the JRE appeared.


Here are some screen shots and output of various commands:


```

 which firefox32
/usr/local/bin/firefox32

```

```

ls -lat /usr/local/firefox32/plugins/
total 3388
drwxr-xr-x  2 root users    4096 2006-08-07 17:38 .
lrwxrwxrwx  1 root root       62 2006-08-07 17:38 libjavaplugin_oji.so -> /usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavaplugin_oji.so
-r--r--r--  1 root users     856 2006-08-07 17:31 flashplayer.xpt
-r-xr-xr-x  1 root users 2154768 2006-08-07 17:31 libflashplayer.so
drwxr-xr-x 11 root users    4096 2006-08-07 17:31 ..
-rw-r--r--  1 root users  244412 2006-08-04 19:37 mplayerplug-in-gmp.so
-rw-r--r--  1 root users     981 2006-08-04 19:37 mplayerplug-in-gmp.xpt
-rw-r--r--  1 root users  244540 2006-08-04 19:37 mplayerplug-in-qt.so
-rw-r--r--  1 root users     981 2006-08-04 19:37 mplayerplug-in-qt.xpt
-rw-r--r--  1 root users  244572 2006-08-04 19:37 mplayerplug-in-rm.so
-rw-r--r--  1 root users     981 2006-08-04 19:37 mplayerplug-in-rm.xpt
-rw-r--r--  1 root users  245660 2006-08-04 19:37 mplayerplug-in.so
-rw-r--r--  1 root users  244860 2006-08-04 19:37 mplayerplug-in-wmp.so
-rw-r--r--  1 root users     981 2006-08-04 19:37 mplayerplug-in-wmp.xpt
-rw-r--r--  1 root users     981 2006-08-04 19:37 mplayerplug-in.xpt
-rwxr-xr-x  1 root users   19496 2006-07-28 18:38 libnullplugin.so

```

---

