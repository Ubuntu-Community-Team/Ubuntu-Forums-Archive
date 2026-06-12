---
title: "Citrix plugin for Firefox 3"
date: 2008-10-02
forum: x86 64-bit Users
---

### Post by mtrainer on 2008-10-02
Hi,

I was using nspluginwrapper to run the citrix ica client in Firefox 2 on 64-bit Kubuntu 7.10 and the ICA plugin appeared and worked fine.  I installed the plugin using the command:

nspluginwrapper -i /usr/lib/ICAClient/npica.so

Since I have upgraded to Kubuntu 8.04 and Firefox 3.0.3 the Citrix plugin fails to appear in about:plugins.  Has anyone got this working or an idea why it doesn't.  The acroread and flash plugins work OK.

Thanks

Murray

---

### Post by Yellow Pasque on 2008-10-02
Hopefully, it's just a matter of symbolic linking. Please post output of:
```
ls -la /usr/lib/firefox/plugins
ls -la /usr/lib/firefox-addons/plugins
nspluginwrapper -l
```

---

### Post by mtrainer on 2008-10-03
> **Temüjin said:**
> Hopefully, it's just a matter of symbolic linking. Please post output of:
```
ls -la /usr/lib/firefox/plugins
ls -la /usr/lib/firefox-addons/plugins
nspluginwrapper -l
```

# ls -la /usr/lib/firefox/plugins
total 48
drwxr-xr-x 2 root root  4096 2008-09-26 17:07 .
drwxr-xr-x 4 root root    83 2008-09-03 15:45 ..
lrwxrwxrwx 1 root root    37 2008-09-26 17:07 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root    57 2008-09-03 14:12 gcjwebplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so
lrwxrwxrwx 1 root root    43 2008-09-01 11:16 mplayerplug-in-dvx.so -> ../../mozilla/plugins/mplayerplug-in-dvx.so
lrwxrwxrwx 1 root root    44 2008-09-01 11:16 mplayerplug-in-dvx.xpt -> ../../mozilla/plugins/mplayerplug-in-dvx.xpt
lrwxrwxrwx 1 root root    42 2008-09-01 11:16 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root    43 2008-09-01 11:16 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root    42 2008-09-01 11:16 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root    43 2008-09-01 11:16 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root    39 2008-09-01 11:16 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root    43 2008-09-01 11:16 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root    44 2008-09-01 11:16 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root    40 2008-09-01 11:16 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
lrwxrwxrwx 1 root root    26 2008-09-26 11:36 nppdf.so -> /var/lib/acroread/nppdf.so
lrwxrwxrwx 1 root root    51 2008-09-25 14:01 npwrapper.nppdf.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.nppdf.so
-rwxrwxrwx 1 root root 41672 2008-08-05 15:19 nsdejavu.so
# ls -la /usr/lib/firefox-addons/plugins
total 0
drwxr-xr-x 2 root root  6 2008-07-29 05:52 .
drwxr-xr-x 5 root root 57 2008-09-03 15:46 ..
# nspluginwrapper -l
/usr/lib/mozilla/plugins/npwrapper.nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 1.0.0
/usr/lib/mozilla/plugins/nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 0.9.91.5
/usr/lib/mozilla/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib64/mozilla/plugins/npwrapper.nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 1.0.0
/usr/lib64/mozilla/plugins/nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 0.9.91.5
/usr/lib64/mozilla/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib/firefox/plugins/npwrapper.nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 1.0.0
/usr/lib/firefox/plugins/nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 0.9.91.5
/usr/lib/firefox/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib64/firefox/plugins/npwrapper.nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 1.0.0
/usr/lib64/firefox/plugins/nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 0.9.91.5
/usr/lib64/firefox/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
#

---

### Post by mtrainer on 2008-10-03
> **mtrainer said:**
> # ls -la /usr/lib/firefox/plugins
total 48
drwxr-xr-x 2 root root  4096 2008-09-26 17:07 .
drwxr-xr-x 4 root root    83 2008-09-03 15:45 ..
lrwxrwxrwx 1 root root    37 2008-09-26 17:07 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root    57 2008-09-03 14:12 gcjwebplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so
lrwxrwxrwx 1 root root    43 2008-09-01 11:16 mplayerplug-in-dvx.so -> ../../mozilla/plugins/mplayerplug-in-dvx.so
lrwxrwxrwx 1 root root    44 2008-09-01 11:16 mplayerplug-in-dvx.xpt -> ../../mozilla/plugins/mplayerplug-in-dvx.xpt
lrwxrwxrwx 1 root root    42 2008-09-01 11:16 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root    43 2008-09-01 11:16 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root    42 2008-09-01 11:16 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root    43 2008-09-01 11:16 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root    39 2008-09-01 11:16 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root    43 2008-09-01 11:16 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root    44 2008-09-01 11:16 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root    40 2008-09-01 11:16 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
lrwxrwxrwx 1 root root    26 2008-09-26 11:36 nppdf.so -> /var/lib/acroread/nppdf.so
lrwxrwxrwx 1 root root    51 2008-09-25 14:01 npwrapper.nppdf.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.nppdf.so
-rwxrwxrwx 1 root root 41672 2008-08-05 15:19 nsdejavu.so
# ls -la /usr/lib/firefox-addons/plugins
total 0
drwxr-xr-x 2 root root  6 2008-07-29 05:52 .
drwxr-xr-x 5 root root 57 2008-09-03 15:46 ..
# nspluginwrapper -l
/usr/lib/mozilla/plugins/npwrapper.nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 1.0.0
/usr/lib/mozilla/plugins/nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 0.9.91.5
/usr/lib/mozilla/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib64/mozilla/plugins/npwrapper.nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 1.0.0
/usr/lib64/mozilla/plugins/nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 0.9.91.5
/usr/lib64/mozilla/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib/firefox/plugins/npwrapper.nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 1.0.0
/usr/lib/firefox/plugins/nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 0.9.91.5
/usr/lib/firefox/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib64/firefox/plugins/npwrapper.nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 1.0.0
/usr/lib64/firefox/plugins/nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 0.9.91.5
/usr/lib64/firefox/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
#

Sorry, I didn't have the ica plugin installed using nspluginwrapper.  The correct output is below:

root@newkubuntu64-xen:~# nspluginwrapper -l
/usr/lib/mozilla/plugins/npwrapper.nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 1.0.0
/usr/lib/mozilla/plugins/nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 0.9.91.5
/usr/lib/mozilla/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib/mozilla/plugins/npwrapper.npica.so
  Original plugin: /usr/lib/ICAClient/npica.so
  Wrapper version string: 0.9.91.5
/usr/lib64/mozilla/plugins/npwrapper.nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 1.0.0
/usr/lib64/mozilla/plugins/nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 0.9.91.5
/usr/lib64/mozilla/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib64/mozilla/plugins/npwrapper.npica.so
  Original plugin: /usr/lib/ICAClient/npica.so
  Wrapper version string: 0.9.91.5
/usr/lib/firefox/plugins/npwrapper.nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 1.0.0
/usr/lib/firefox/plugins/nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 0.9.91.5
/usr/lib/firefox/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib/firefox/plugins/npwrapper.npica.so
  Original plugin: /usr/lib/ICAClient/npica.so
  Wrapper version string: 0.9.91.5
/usr/lib64/firefox/plugins/npwrapper.nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 1.0.0
/usr/lib64/firefox/plugins/nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 0.9.91.5
/usr/lib64/firefox/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib64/firefox/plugins/npwrapper.npica.so
  Original plugin: /usr/lib/ICAClient/npica.so
  Wrapper version string: 0.9.91.5

---

### Post by mtrainer on 2008-10-03
> **mtrainer said:**
> # ls -la /usr/lib/firefox/plugins
total 48
drwxr-xr-x 2 root root  4096 2008-09-26 17:07 .
drwxr-xr-x 4 root root    83 2008-09-03 15:45 ..
lrwxrwxrwx 1 root root    37 2008-09-26 17:07 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root    57 2008-09-03 14:12 gcjwebplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so
lrwxrwxrwx 1 root root    43 2008-09-01 11:16 mplayerplug-in-dvx.so -> ../../mozilla/plugins/mplayerplug-in-dvx.so
lrwxrwxrwx 1 root root    44 2008-09-01 11:16 mplayerplug-in-dvx.xpt -> ../../mozilla/plugins/mplayerplug-in-dvx.xpt
lrwxrwxrwx 1 root root    42 2008-09-01 11:16 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root    43 2008-09-01 11:16 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root    42 2008-09-01 11:16 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root    43 2008-09-01 11:16 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root    39 2008-09-01 11:16 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root    43 2008-09-01 11:16 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root    44 2008-09-01 11:16 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root    40 2008-09-01 11:16 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
lrwxrwxrwx 1 root root    26 2008-09-26 11:36 nppdf.so -> /var/lib/acroread/nppdf.so
lrwxrwxrwx 1 root root    51 2008-09-25 14:01 npwrapper.nppdf.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.nppdf.so
-rwxrwxrwx 1 root root 41672 2008-08-05 15:19 nsdejavu.so
# ls -la /usr/lib/firefox-addons/plugins
total 0
drwxr-xr-x 2 root root  6 2008-07-29 05:52 .
drwxr-xr-x 5 root root 57 2008-09-03 15:46 ..
# nspluginwrapper -l
/usr/lib/mozilla/plugins/npwrapper.nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 1.0.0
/usr/lib/mozilla/plugins/nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 0.9.91.5
/usr/lib/mozilla/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib64/mozilla/plugins/npwrapper.nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 1.0.0
/usr/lib64/mozilla/plugins/nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 0.9.91.5
/usr/lib64/mozilla/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib/firefox/plugins/npwrapper.nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 1.0.0
/usr/lib/firefox/plugins/nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 0.9.91.5
/usr/lib/firefox/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib64/firefox/plugins/npwrapper.nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 1.0.0
/usr/lib64/firefox/plugins/nppdf.so
  Original plugin: /usr/lib32/Adobe/Reader8/Browser/intellinux/nppdf.so
  Wrapper version string: 0.9.91.5
/usr/lib64/firefox/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
#

The list of plugins now includes the ica one.

# ls -la /usr/lib/firefox/plugins
total 48
drwxr-xr-x 2 root root  4096 2008-10-03 12:15 .
drwxr-xr-x 4 root root    83 2008-09-03 15:45 ..
lrwxrwxrwx 1 root root    37 2008-09-26 17:07 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root    57 2008-09-03 14:12 gcjwebplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so
lrwxrwxrwx 1 root root    43 2008-09-01 11:16 mplayerplug-in-dvx.so -> ../../mozilla/plugins/mplayerplug-in-dvx.so
lrwxrwxrwx 1 root root    44 2008-09-01 11:16 mplayerplug-in-dvx.xpt -> ../../mozilla/plugins/mplayerplug-in-dvx.xpt
lrwxrwxrwx 1 root root    42 2008-09-01 11:16 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root    43 2008-09-01 11:16 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root    42 2008-09-01 11:16 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root    43 2008-09-01 11:16 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root    39 2008-09-01 11:16 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root    43 2008-09-01 11:16 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root    44 2008-09-01 11:16 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root    40 2008-09-01 11:16 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
lrwxrwxrwx 1 root root    26 2008-09-26 11:36 nppdf.so -> /var/lib/acroread/nppdf.so
lrwxrwxrwx 1 root root    51 2008-10-03 12:15 npwrapper.npica.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.npica.so
lrwxrwxrwx 1 root root    51 2008-09-25 14:01 npwrapper.nppdf.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.nppdf.so
-rwxrwxrwx 1 root root 41672 2008-08-05 15:19 nsdejavu.so

---

### Post by mtrainer on 2008-10-05
> **mtrainer said:**
> The list of plugins now includes the ica one.

# ls -la /usr/lib/firefox/plugins
total 48
drwxr-xr-x 2 root root  4096 2008-10-03 12:15 .
drwxr-xr-x 4 root root    83 2008-09-03 15:45 ..
lrwxrwxrwx 1 root root    37 2008-09-26 17:07 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root    57 2008-09-03 14:12 gcjwebplugin.so -> /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so
lrwxrwxrwx 1 root root    43 2008-09-01 11:16 mplayerplug-in-dvx.so -> ../../mozilla/plugins/mplayerplug-in-dvx.so
lrwxrwxrwx 1 root root    44 2008-09-01 11:16 mplayerplug-in-dvx.xpt -> ../../mozilla/plugins/mplayerplug-in-dvx.xpt
lrwxrwxrwx 1 root root    42 2008-09-01 11:16 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root    43 2008-09-01 11:16 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root    42 2008-09-01 11:16 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root    43 2008-09-01 11:16 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root    39 2008-09-01 11:16 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root    43 2008-09-01 11:16 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root    44 2008-09-01 11:16 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root    40 2008-09-01 11:16 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
lrwxrwxrwx 1 root root    26 2008-09-26 11:36 nppdf.so -> /var/lib/acroread/nppdf.so
lrwxrwxrwx 1 root root    51 2008-10-03 12:15 npwrapper.npica.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.npica.so
lrwxrwxrwx 1 root root    51 2008-09-25 14:01 npwrapper.nppdf.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.nppdf.so
-rwxrwxrwx 1 root root 41672 2008-08-05 15:19 nsdejavu.so

Note that despite the above, the plugin doesn't appear in the about:plugins list in Firefox.

---

