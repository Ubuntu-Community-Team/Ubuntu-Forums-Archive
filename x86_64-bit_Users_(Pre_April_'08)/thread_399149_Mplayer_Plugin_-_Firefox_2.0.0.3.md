---
title: "Mplayer Plugin - Firefox 2.0.0.3"
date: 2007-04-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by madman91 on 2007-04-01
Hey guys,
I am running Firefox 2.0.0.3 with 64bit dapper. 

I installed the java,flash, and mplayer plugins with this script. [http://www.ubuntuforums.org/showpost.php?p=1174435&postcount=1](http://www.ubuntuforums.org/showpost.php?p=1174435&postcount=1)

And I installed all the codecs I could find into all the dirs i could think of..

And when I launch firefox, no videos will play. The mplayer plugin will not even show up. Yet it is shown as installed in about:plugins ... as v3.2.5..


Any ideas?


Thanks,
MaDman

---

### Post by Kilz on 2007-04-01
> **madman91 said:**
> Hey guys,
I am running Firefox 2.0.0.3 with 64bit dapper. 

I installed the java,flash, and mplayer plugins with this script. [http://www.ubuntuforums.org/showpost.php?p=1174435&postcount=1](http://www.ubuntuforums.org/showpost.php?p=1174435&postcount=1)

And I installed all the codecs I could find into all the dirs i could think of..

And when I launch firefox, no videos will play. The mplayer plugin will not even show up. Yet it is shown as installed in about:plugins ... as v3.2.5..


Any ideas?


Thanks,
MaDman

What version number of the script did you install? Also please click on Help, then About Mozilla Firefox , at the bottom will be a section starting with Mozilla/5.0 . Copy the section and paste it into a reply here.

---

### Post by madman91 on 2007-04-02
I used script version 0.7.1 ..

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.3) Gecko/20070309 Firefox/2.0.0.3

---

### Post by Kilz on 2007-04-02
What sites have you tried to view video's on and what format were they?
Also please open a terminal, type in ```
ls -al /usr/lib32/firefox32/plugins
``` and copy/paste the results into a reply here.

---

### Post by madman91 on 2007-04-02
> **Kilz said:**
> What sites have you tried to view video's on and what format were they?
Also please open a terminal, type in ```
ls -al /usr/lib32/firefox32/plugins
``` and copy/paste the results into a reply here.

total 8260
drwxr-xr-x 2 greg greg     4096 2007-03-30 17:53 .
drwxr-xr-x 4 greg greg     4096 2007-03-30 16:07 ..
-r--r--r-- 1  500 users     856 2006-12-15 15:51 flashplayer.xpt
-rwxr-xr-x 1  500 users 7040080 2006-12-15 15:51 libflashplayer.so
lrwxrwxrwx 1 root root       62 2007-03-30 17:53 libjavaplugin_oji.so -> /usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavaplugin_oji.so
-rw-r--r-- 1 greg greg    92448 2006-09-19 08:39 libnpp.so
-rwxr-xr-x 1 greg greg    19496 2006-09-09 21:41 libnullplugin.so
-rw-r--r-- 1 root root   244412 2007-03-30 17:53 mplayerplug-in-gmp.so
-rw-r--r-- 1 root root      981 2007-03-30 17:53 mplayerplug-in-gmp.xpt
-rw-r--r-- 1 root root   244540 2007-03-30 17:53 mplayerplug-in-qt.so
-rw-r--r-- 1 root root      981 2007-03-30 17:53 mplayerplug-in-qt.xpt
-rw-r--r-- 1 root root   244572 2007-03-30 17:53 mplayerplug-in-rm.so
-rw-r--r-- 1 root root      981 2007-03-30 17:53 mplayerplug-in-rm.xpt
-rw-r--r-- 1 root root   245660 2007-03-30 17:53 mplayerplug-in.so
-rw-r--r-- 1 root root   244860 2007-03-30 17:53 mplayerplug-in-wmp.so
-rw-r--r-- 1 root root      981 2007-03-30 17:53 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 root root      981 2007-03-30 17:53 mplayerplug-in.xpt


I visited [www.apple.com/trailers](www.apple.com/trailers) .. That is in the quicktime format... I also tried some BBC videos.. Should those mplayer plugins be owned by me instead of root ?


Thanks


UPDATE::::

I ran chown -hR greg /usr/lib32/firefox32/plugins

here is the updated ls -al /usr/lib32/firefox32/plugins
total 8260
drwxrwxrwx 2 greg greg     4096 2007-03-30 17:53 .
drwxr-xr-x 4 greg greg     4096 2007-03-30 16:07 ..
-r--r--r-- 1 greg users     856 2006-12-15 15:51 flashplayer.xpt
-rwxr-xr-x 1 greg users 7040080 2006-12-15 15:51 libflashplayer.so
lrwxrwxrwx 1 greg root       62 2007-03-30 17:53 libjavaplugin_oji.so -> /usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavaplugin_oji.so
-rw-r--r-- 1 greg greg    92448 2006-09-19 08:39 libnpp.so
-rwxr-xr-x 1 greg greg    19496 2006-09-09 21:41 libnullplugin.so
-rw-r--r-- 1 greg root   244412 2007-03-30 17:53 mplayerplug-in-gmp.so
-rw-r--r-- 1 greg root      981 2007-03-30 17:53 mplayerplug-in-gmp.xpt
-rw-r--r-- 1 greg root   244540 2007-03-30 17:53 mplayerplug-in-qt.so
-rw-r--r-- 1 greg root      981 2007-03-30 17:53 mplayerplug-in-qt.xpt
-rw-r--r-- 1 greg root   244572 2007-03-30 17:53 mplayerplug-in-rm.so
-rw-r--r-- 1 greg root      981 2007-03-30 17:53 mplayerplug-in-rm.xpt
-rw-r--r-- 1 greg root   245660 2007-03-30 17:53 mplayerplug-in.so
-rw-r--r-- 1 greg root   244860 2007-03-30 17:53 mplayerplug-in-wmp.so
-rw-r--r-- 1 greg root      981 2007-03-30 17:53 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 greg root      981 2007-03-30 17:53 mplayerplug-in.xpt

---

### Post by Kilz on 2007-04-02
I think you have the right idea on the fix. But the command of 

```
sudo chown -hR greg:users /usr/lib32/firefox32/plugins
```

should do a better job as the files are still part of the root group.

---

### Post by madman91 on 2007-04-03
> **Kilz said:**
> I think you have the right idea on the fix. But the command of 

```
sudo chown -hR greg:users /usr/lib32/firefox32/plugins
```

should do a better job as the files are still part of the root group.


greg@greg-ubuntu:~$ ls -al /usr/lib32/firefox32/plugins
total 8260
drwxrwxrwx 2 greg users    4096 2007-03-30 17:53 .
drwxr-xr-x 4 greg greg     4096 2007-03-30 16:07 ..
-r--r--r-- 1 greg users     856 2006-12-15 15:51 flashplayer.xpt
-rwxr-xr-x 1 greg users 7040080 2006-12-15 15:51 libflashplayer.so
lrwxrwxrwx 1 greg users      62 2007-03-30 17:53 libjavaplugin_oji.so -> /usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavaplugin_oji.so
-rw-r--r-- 1 greg users   92448 2006-09-19 08:39 libnpp.so
-rwxr-xr-x 1 greg users   19496 2006-09-09 21:41 libnullplugin.so
-rw-r--r-- 1 greg users  244412 2007-03-30 17:53 mplayerplug-in-gmp.so
-rw-r--r-- 1 greg users     981 2007-03-30 17:53 mplayerplug-in-gmp.xpt
-rw-r--r-- 1 greg users  244540 2007-03-30 17:53 mplayerplug-in-qt.so
-rw-r--r-- 1 greg users     981 2007-03-30 17:53 mplayerplug-in-qt.xpt
-rw-r--r-- 1 greg users  244572 2007-03-30 17:53 mplayerplug-in-rm.so
-rw-r--r-- 1 greg users     981 2007-03-30 17:53 mplayerplug-in-rm.xpt
-rw-r--r-- 1 greg users  245660 2007-03-30 17:53 mplayerplug-in.so
-rw-r--r-- 1 greg users  244860 2007-03-30 17:53 mplayerplug-in-wmp.so
-rw-r--r-- 1 greg users     981 2007-03-30 17:53 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 greg users     981 2007-03-30 17:53 mplayerplug-in.xpt


I did the sudo chown and thats the output of ls .. However, I still cannot view trailers, video streams, etc..:(

---

### Post by madman91 on 2007-04-05
So.. Any ideas?

---

### Post by Kilz on 2007-04-06
> **madman91 said:**
> So.. Any ideas?

Sure, try this one

```
ls -al /usr/bin/mplayer64
```
and this
```
ls -al /usr/bin/mplayer
```

---

### Post by madman91 on 2007-04-06
```
ls -al /usr/bin/mplayer64
```

greg@greg-ubuntu:~$ ls -al /usr/bin/mplayer64
-rwxr-xr-x 1 root root 7240800 2006-05-15 16:42 /usr/bin/mplayer64

```
ls -al /usr/bin/mplayer
```

greg@greg-ubuntu:~$ ls -al /usr/bin/mplayer
-rwxr-xr-x 1 root root 7251160 2006-06-04 15:31 /usr/bin/mplayer

---

### Post by Kilz on 2007-04-06
> **madman91 said:**
> ```
ls -al /usr/bin/mplayer64
```

greg@greg-ubuntu:~$ ls -al /usr/bin/mplayer64
-rwxr-xr-x 1 root root 7240800 2006-05-15 16:42 /usr/bin/mplayer64

```
ls -al /usr/bin/mplayer
```

greg@greg-ubuntu:~$ ls -al /usr/bin/mplayer
-rwxr-xr-x 1 root root 7251160 2006-06-04 15:31 /usr/bin/mplayer

Well, it should work, it looks like you have the player and the plugins. Everything is setup like I think it should be. Lets try this from a different direction. Close all browsers. Open a terminal, type in firefox32, firefox will start. [Go to this page]("http://www.apple.com/trailers/magnolia/thehost/trailer/"), see if the trailer works. If it doesnt, copy whats in the terminal to a post here.

---

### Post by madman91 on 2007-04-07
> **Kilz said:**
> Well, it should work, it looks like you have the player and the plugins. Everything is setup like I think it should be. Lets try this from a different direction. Close all browsers. Open a terminal, type in firefox32, firefox will start. [Go to this page]("http://www.apple.com/trailers/magnolia/thehost/trailer/"), see if the trailer works. If it doesnt, copy whats in the terminal to a post here.

```

greg@greg-ubuntu:~$ firefox32
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
esd: no process killed
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
/home/greg/.gtkrc-2.0:2: Unable to find include file: ".gtkrc-2.0-scrollbar_cog"
LoadPlugin: failed to initialize shared library /home/greg/.mozilla/plugins/mpla yerplug-in-qt.so [/home/greg/.mozilla/plugins/mplayerplug-in-qt.so: cannot open shared object file: No such file or directory]

```

UPDATE:::
Here is another sites error

```

LoadPlugin: failed to initialize shared library /home/greg/.mozilla/plugins/mplayerplug-in-wmp.so [/home/greg/.mozilla/plugins/mplayerplug-in-wmp.so: cannot open shared object file: No such file or directory]

```

Yes!!! Finally an error that can help us :) .

Oh yeah.. and here is the ls of that directory.

```

greg@greg-ubuntu:~/.mozilla/plugins$ ls -al /home/greg/.mozilla/plugins/
total 8084
drwxr-xr-x 2 greg root    4096 2006-12-18 20:13 .
drwxrwx--- 5 greg greg    4096 2006-12-16 15:32 ..
-rw-r--r-- 1 greg root 6904912 2006-12-16 15:28 libflashplayer.so
lrwxrwxrwx 1 greg greg      58 2006-12-18 20:13 libjavaplugin_oji.so -> /usr/java/jre1.5.0_10/plugin/i386/ns7/libjavaplugin_oji.so
-rw-r--r-- 1 greg root  261056 2006-12-17 14:14 mplayerplug-in-gmp.so
-rw-r--r-- 1 greg root     981 2006-12-17 14:14 mplayerplug-in-gmp.xpt
-rw-r--r-- 1 greg root  261056 2006-12-17 14:14 mplayerplug-in-qt.so
-rw-r--r-- 1 greg root     981 2006-12-17 14:14 mplayerplug-in-qt.xpt
-rw-r--r-- 1 greg root  261056 2006-12-17 14:14 mplayerplug-in-rm.so
-rw-r--r-- 1 greg root     981 2006-12-17 14:14 mplayerplug-in-rm.xpt
-rw-r--r-- 1 greg root  261696 2006-12-17 14:14 mplayerplug-in.so
-rw-r--r-- 1 greg root  261056 2006-12-17 14:14 mplayerplug-in-wmp.so
-rw-r--r-- 1 greg root     981 2006-12-17 14:14 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 greg root     981 2006-12-17 14:14 mplayerplug-in.xpt

```

---

### Post by FuturePilot on 2007-04-07
....

---

### Post by Kilz on 2007-04-07
> **madman91 said:**
> ```

greg@greg-ubuntu:~$ firefox32
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
esd: no process killed
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be pr eloaded: ignored.
/home/greg/.gtkrc-2.0:2: Unable to find include file: ".gtkrc-2.0-scrollbar_cog"
LoadPlugin: failed to initialize shared library /home/greg/.mozilla/plugins/mpla yerplug-in-qt.so [/home/greg/.mozilla/plugins/mplayerplug-in-qt.so: cannot open shared object file: No such file or directory]

```

UPDATE:::
Here is another sites error

```

LoadPlugin: failed to initialize shared library /home/greg/.mozilla/plugins/mplayerplug-in-wmp.so [/home/greg/.mozilla/plugins/mplayerplug-in-wmp.so: cannot open shared object file: No such file or directory]

```

Yes!!! Finally an error that can help us :) .

Oh yeah.. and here is the ls of that directory.

```

greg@greg-ubuntu:~/.mozilla/plugins$ ls -al /home/greg/.mozilla/plugins/
total 8084
drwxr-xr-x 2 greg root    4096 2006-12-18 20:13 .
drwxrwx--- 5 greg greg    4096 2006-12-16 15:32 ..
-rw-r--r-- 1 greg root 6904912 2006-12-16 15:28 libflashplayer.so
lrwxrwxrwx 1 greg greg      58 2006-12-18 20:13 libjavaplugin_oji.so -> /usr/java/jre1.5.0_10/plugin/i386/ns7/libjavaplugin_oji.so
-rw-r--r-- 1 greg root  261056 2006-12-17 14:14 mplayerplug-in-gmp.so
-rw-r--r-- 1 greg root     981 2006-12-17 14:14 mplayerplug-in-gmp.xpt
-rw-r--r-- 1 greg root  261056 2006-12-17 14:14 mplayerplug-in-qt.so
-rw-r--r-- 1 greg root     981 2006-12-17 14:14 mplayerplug-in-qt.xpt
-rw-r--r-- 1 greg root  261056 2006-12-17 14:14 mplayerplug-in-rm.so
-rw-r--r-- 1 greg root     981 2006-12-17 14:14 mplayerplug-in-rm.xpt
-rw-r--r-- 1 greg root  261696 2006-12-17 14:14 mplayerplug-in.so
-rw-r--r-- 1 greg root  261056 2006-12-17 14:14 mplayerplug-in-wmp.so
-rw-r--r-- 1 greg root     981 2006-12-17 14:14 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 greg root     981 2006-12-17 14:14 mplayerplug-in.xpt

```

Ignore the libproangohack errors. But I do not have the mplayer plugins installed in my .mozilla folder. If you want to have them there you may need to chown them to greg:users and not root. Otherwise remove them so the ones in /usr/lib32/firefox32/plugins are used.

---

### Post by madman91 on 2007-04-07
> **Kilz said:**
> Ignore the libproangohack errors. But I do not have the mplayer plugins installed in my .mozilla folder. If you want to have them there you may need to chown them to greg:users and not root. Otherwise remove them so the ones in /usr/lib32/firefox32/plugins are used.

I removed the ones from my .mozilla folder...When I visit a video stream (like apple trailers) no errors are thrown, but firefox says it does not have the plugins it needs. Same goes for any other stream I visit.

So I went to about:plugins .. and now all of them .. or almost all of them are gone.. Maybe firefox isnt looking at the /usr/lib32/firefox32/plugins folder...

---

### Post by madman91 on 2007-04-07
So..

After removing them, I copied the ones from /usr/lib32..... over and chown'ed them to greg:users ... I whipped open firefox .. and voila! It works.. but is it possible now to get firefox to look at the ones in /usr/lib32... ?


Thanks for all the help!!

---

### Post by Kilz on 2007-04-07
We can try, Id like to see how the firefox32 directory is setup please post the results of

```
ls -al /usr/local/firefox32
```

---

### Post by madman91 on 2007-04-07
> **Kilz said:**
> We can try, Id like to see how the firefox32 directory is setup please post the results of

```
ls -al /usr/local/firefox32
```

greg@greg-ubuntu:~$ ls -al /usr/local/firefox32/
total 20432
drwxr-xr-x 13 root root     4096 2007-03-30 16:08 .
drwxr-xr-x 10 root root     4096 2006-12-16 15:08 ..
-rw-r--r--  1 greg greg        0 2007-03-09 20:42 .autoreg
-rw-r--r--  1 greg greg      232 2007-03-09 20:42 browserconfig.properties
drwxr-xr-x  3 greg greg     4096 2007-03-30 16:08 chrome
drwxr-xr-x  2 greg greg     4096 2007-03-30 16:08 components
drwxr-xr-x  5 greg greg     4096 2006-10-11 01:57 defaults
drwxr-xr-x  2 greg greg     4096 2007-03-30 16:08 dictionaries
drwxr-xr-x  5 greg greg     4096 2007-02-18 13:23 extensions
-rwxr-xr-x  1 greg greg     5247 2007-03-09 20:43 firefox
-rwxr-xr-x  1 greg greg 10534772 2007-03-09 20:43 firefox-bin
drwxr-xr-x  2 greg greg     4096 2007-03-30 16:08 greprefs
drwxr-xr-x  2 greg greg     4096 2007-03-30 16:08 icons
-rw-r--r--  1 root root  6904912 2006-12-16 15:25 libflashplayer.so
-rw-r--r--  1 greg greg      476 2007-03-09 20:43 libfreebl3.chk
-rwxr-xr-x  1 greg greg   231468 2007-03-09 20:43 libfreebl3.so
-rwxr-xr-x  1 greg greg   627004 2007-03-09 20:43 libmozjs.so
-rwxr-xr-x  1 greg greg   176716 2007-03-09 20:43 libnspr4.so
-rwxr-xr-x  1 greg greg   430608 2007-03-09 20:43 libnss3.so
-rwxr-xr-x  1 greg greg   260832 2007-03-09 20:43 libnssckbi.so
-rwxr-xr-x  1 greg greg    15304 2007-03-09 20:43 libplc4.so
-rwxr-xr-x  1 greg greg     8240 2007-03-09 20:43 libplds4.so
-rwxr-xr-x  1 greg greg   138316 2007-03-09 20:43 libsmime3.so
-rw-r--r--  1 greg greg      476 2007-03-09 20:43 libsoftokn3.chk
-rwxr-xr-x  1 greg greg   309624 2007-03-09 20:43 libsoftokn3.so
-rwxr-xr-x  1 greg greg   155560 2007-03-09 20:43 libssl3.so
-rwxr-xr-x  1 greg greg    94924 2007-03-09 20:43 libxpcom_compat.so
-rwxr-xr-x  1 greg greg   698672 2007-03-09 20:43 libxpcom_core.so
-rwxr-xr-x  1 greg greg     9240 2007-03-09 20:43 libxpcom.so
-rwxr-xr-x  1 greg greg     8284 2007-03-09 20:43 libxpistub.so
-rwxr-xr-x  1 greg greg    10336 2007-03-09 20:43 mozilla-xremote-client
-rw-r--r--  1 greg greg      112 2007-03-09 20:42 old-homepage-default.properties
drwxr-xr-x  2 greg greg     4096 2007-01-17 17:04 plugins
-rw-r--r--  1 greg greg      177 2007-03-09 20:43 readme.txt
-rwxr-xr-x  1 greg greg     2257 2007-03-09 20:42 removed-files
drwxr-xr-x  6 greg greg     4096 2007-03-30 16:08 res
-rwxr-xr-x  1 greg greg    10492 2007-03-09 20:43 run-mozilla.sh
drwxr-xr-x  2 greg greg     4096 2007-03-30 16:08 searchplugins
-rwxr-xr-x  1 greg greg    67496 2007-03-09 20:43 updater
-rw-r--r--  1 greg greg      145 2007-03-09 20:42 updater.ini
drwxr-xr-x  3 root root     4096 2006-12-16 15:26 updates
-rwxr-xr-x  1 greg greg    21368 2007-03-09 20:43 xpicleanup



Thanks again for all the help

---

### Post by Kilz on 2007-04-07
> **madman91 said:**
> greg@greg-ubuntu:~$ ls -al /usr/local/firefox32/
total 20432
drwxr-xr-x 13 root root     4096 2007-03-30 16:08 .
drwxr-xr-x 10 root root     4096 2006-12-16 15:08 ..
-rw-r--r--  1 greg greg        0 2007-03-09 20:42 .autoreg
-rw-r--r--  1 greg greg      232 2007-03-09 20:42 browserconfig.properties
drwxr-xr-x  3 greg greg     4096 2007-03-30 16:08 chrome
drwxr-xr-x  2 greg greg     4096 2007-03-30 16:08 components
drwxr-xr-x  5 greg greg     4096 2006-10-11 01:57 defaults
drwxr-xr-x  2 greg greg     4096 2007-03-30 16:08 dictionaries
drwxr-xr-x  5 greg greg     4096 2007-02-18 13:23 extensions
-rwxr-xr-x  1 greg greg     5247 2007-03-09 20:43 firefox
-rwxr-xr-x  1 greg greg 10534772 2007-03-09 20:43 firefox-bin
drwxr-xr-x  2 greg greg     4096 2007-03-30 16:08 greprefs
drwxr-xr-x  2 greg greg     4096 2007-03-30 16:08 icons
-rw-r--r--  1 root root  6904912 2006-12-16 15:25 libflashplayer.so
-rw-r--r--  1 greg greg      476 2007-03-09 20:43 libfreebl3.chk
-rwxr-xr-x  1 greg greg   231468 2007-03-09 20:43 libfreebl3.so
-rwxr-xr-x  1 greg greg   627004 2007-03-09 20:43 libmozjs.so
-rwxr-xr-x  1 greg greg   176716 2007-03-09 20:43 libnspr4.so
-rwxr-xr-x  1 greg greg   430608 2007-03-09 20:43 libnss3.so
-rwxr-xr-x  1 greg greg   260832 2007-03-09 20:43 libnssckbi.so
-rwxr-xr-x  1 greg greg    15304 2007-03-09 20:43 libplc4.so
-rwxr-xr-x  1 greg greg     8240 2007-03-09 20:43 libplds4.so
-rwxr-xr-x  1 greg greg   138316 2007-03-09 20:43 libsmime3.so
-rw-r--r--  1 greg greg      476 2007-03-09 20:43 libsoftokn3.chk
-rwxr-xr-x  1 greg greg   309624 2007-03-09 20:43 libsoftokn3.so
-rwxr-xr-x  1 greg greg   155560 2007-03-09 20:43 libssl3.so
-rwxr-xr-x  1 greg greg    94924 2007-03-09 20:43 libxpcom_compat.so
-rwxr-xr-x  1 greg greg   698672 2007-03-09 20:43 libxpcom_core.so
-rwxr-xr-x  1 greg greg     9240 2007-03-09 20:43 libxpcom.so
-rwxr-xr-x  1 greg greg     8284 2007-03-09 20:43 libxpistub.so
-rwxr-xr-x  1 greg greg    10336 2007-03-09 20:43 mozilla-xremote-client
-rw-r--r--  1 greg greg      112 2007-03-09 20:42 old-homepage-default.properties
drwxr-xr-x  2 greg greg     4096 2007-01-17 17:04 plugins
-rw-r--r--  1 greg greg      177 2007-03-09 20:43 readme.txt
-rwxr-xr-x  1 greg greg     2257 2007-03-09 20:42 removed-files
drwxr-xr-x  6 greg greg     4096 2007-03-30 16:08 res
-rwxr-xr-x  1 greg greg    10492 2007-03-09 20:43 run-mozilla.sh
drwxr-xr-x  2 greg greg     4096 2007-03-30 16:08 searchplugins
-rwxr-xr-x  1 greg greg    67496 2007-03-09 20:43 updater
-rw-r--r--  1 greg greg      145 2007-03-09 20:42 updater.ini
drwxr-xr-x  3 root root     4096 2006-12-16 15:26 updates
-rwxr-xr-x  1 greg greg    21368 2007-03-09 20:43 xpicleanup



Thanks again for all the help

Here is the problem
```
drwxr-xr-x 2 greg greg 4096 2007-01-17 17:04 plugins
```
For some reason the plugins folder isnt a symlink of /usr/lib32/firefox32/plugins like it should be. I checked the deb file I created , and its a symlink there. This is easy to fix.

```
sudo rm -rfd /usr/local/firefox32/plugins
sudo ln -s /usr/lib32/firefox32/plugins /usr/local/firefox32
```
This way if you install another browser from my howto they can all use the same plugins.

---

### Post by madman91 on 2007-04-08
Thank you!! 

Everything works just as it should. I can now stop having to boot up my vmware windows to view streams :) . 

Thanks again!

---

