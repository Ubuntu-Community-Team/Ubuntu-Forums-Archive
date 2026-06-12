---
title: "[SOLVED] Flash problem - yes another one"
date: 2008-08-16
forum: x86 64-bit Users
---

### Post by Plasma_NZ on 2008-08-16
ok all was going fine, the there was some jre java updates..


Well now when i load a flash video - it loads up the flashplayer, does the loading symbol... but doesnt do anything apart from that...

Flash pages work fine... but them videos just dont play/buffer...

tried following kiltz guides... results are the same..


Any ideas.?

```

physics@physics:~$ ls -al /usr/lib/mozilla//plugins/
total 12
drwxr-xr-x 2 physics users 4096 2008-08-16 21:49 .
drwxr-xr-x 4 root    root  4096 2008-02-22 14:58 ..
lrwxrwxrwx 1 root    root    37 2008-08-16 21:49 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
-rwx------ 1 physics users    0 2008-08-16 21:46 libflashplayer.so
lrwxrwxrwx 1 physics users   60 2008-08-16 21:46 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
physics@physics:~$ ls -al /usr/lib/firefox/plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-08-16 21:49 .
drwxr-xr-x 4 root root 4096 2008-08-16 21:49 ..
lrwxrwxrwx 1 root root   37 2008-08-16 21:49 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
physics@physics:~$ uname -a
Linux physics 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux
physics@physics:~$ 
```

---

