---
title: "What the hell is wrong with Firefox on 64bit this last week?!"
date: 2008-12-15
forum: x86 64-bit Users
---

### Post by psypher on 2008-12-15
In the last week my firefox has gone from usable to completely pointless. Constant crashing, freezing (greying out) and I cannot find the cause. At 1st I disabled all my extensions which seems to work for like an hour. Then I uninstalled all of them except VMWare and the Ubuntu ones and that works for 2 hours. Then I tried uninstalling flash, same issues. Install 64bit flash beta, still issues. I find now that it's not even flash sites specifically that crash it. Was just on google reader, opened an article in the reader with just a static image, crash. Re-opened FF and that very same page, no crash. 

So what the hell is going on? Going through bugs is so tedious as there are many many reasons FF has crashed over the years. So if anyone knows why since the beginning of last week firefox has started crashing and if there is a bug report for this specific bug please let me know. All I have done is run updates, no other major system changes.

Thanks


UPDATE!!

Seems  like the problem is not only with firefox but pretty much any browser I install. tried Opera and Epiphany and both have exact same symptoms. Problem is NOT flash but could possibly be java. Something that is common amongst all browsers. Read the rest of the posts to see all that i have tried

Ubuntu x86_64 Intrepid

---

### Post by Ng Oon-Ee on 2008-12-15
Have not had this issue, so can't really help there.

Have you tried creating a new profile? Or complete purge of firefox? The second option should NEVER be necessary, but if you're stumped....

---

### Post by toasty_ghosty on 2008-12-15
You know, I was having problems with Firefox a week or two ago. It would crash if I had a few tabs open and generally appeared slow...I don't know what was causing it but it appears to be better now.

---

### Post by psypher on 2008-12-15
Just crashed again. Started it from cli here's the output:

ruald@cipher:~$ firefox
ICEDTEAPLUGIN_DEBUG = (null)
*** glibc detected *** /usr/lib/firefox-3.0.4/firefox: double free or corruption (!prev): 0x00007f3734168aa0 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f374ceaf938]
/lib/libc.so.6(cfree+0x76)[0x7f374ceb1f86]
/usr/lib/libtalloc.so.1(talloc_free+0x128)[0x7f373a82cb88]
/lib/libnss_wins.so.2[0x7f373ba7ff48]
/usr/lib/libtalloc.so.1(talloc_free+0x232)[0x7f373a82cc92]
/lib/libnss_wins.so.2(alloc_sub_basic+0x8e9)[0x7f373baa7d02]
/lib/libnss_wins.so.2(talloc_sub_basic+0x24)[0x7f373baa826d]
/lib/libnss_wins.so.2[0x7f373b9f7be9]
/lib/libnss_wins.so.2(lp_lockdir+0x1e)[0x7f373b9f8a93]
/lib/libnss_wins.so.2(lock_path+0x9)[0x7f373baa2972]
/lib/libnss_wins.so.2(receive_unexpected+0x2c)[0x7f373ba4d321]
/lib/libnss_wins.so.2(receive_nmb_packet+0x3b)[0x7f373ba4fd2e]
/lib/libnss_wins.so.2(name_query+0x303)[0x7f373ba52530]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname_r+0x2c8)[0x7f373b9f5202]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname2_r+0x2b)[0x7f373b9f5484]
/lib/libc.so.6(gethostbyname2_r+0x199)[0x7f374cf36bf9]
/lib/libc.so.6[0x7f374cf0384c]
/lib/libc.so.6(getaddrinfo+0x1de)[0x7f374cf0596e]
/usr/lib/libnspr4.so.0d(PR_GetAddrInfoByName+0x108)[0x7f374c55d828]
/usr/lib/xulrunner-1.9.0.4/libxul.so[0x7f374b667b82]
/usr/lib/libnspr4.so.0d[0x7f374c569dc3]
/lib/libpthread.so.0[0x7f374db5d3ea]
/lib/libc.so.6(clone+0x6d)[0x7f374cf1cc6d]
======= Memory map: ========
00400000-00408000 r-xp 00000000 08:03 3086745                            /usr/lib/firefox-3.0.4/firefox
00608000-00609000 r--p 00008000 08:03 3086745                            /usr/lib/firefox-3.0.4/firefox
00609000-0060a000 rw-p 00009000 08:03 3086745                            /usr/lib/firefox-3.0.4/firefox
00eb5000-0d7ce000 rw-p 00eb5000 00:00 0                                  [heap]
4065f000-40660000 ---p 4065f000 00:00 0 
40660000-40e60000 rw-p 40660000 00:00 0 
40e60000-40e61000 ---p 40e60000 00:00 0 
40e61000-41661000 rw-p 40e61000 00:00 0 
41661000-41662000 ---p 41661000 00:00 0 
41662000-41e62000 rw-p 41662000 00:00 0 
41e62000-41e63000 ---p 41e62000 00:00 0 
41e63000-42663000 rw-p 41e63000 00:00 0 
42663000-42664000 ---p 42663000 00:00 0 
42664000-42e64000 rw-p 42664000 00:00 0 
42e64000-42e65000 ---p 42e64000 00:00 0 
42e65000-43665000 rw-p 42e65000 00:00 0 
43665000-43666000 ---p 43665000 00:00 0 
43666000-43e66000 rw-p 43666000 00:00 0 
43e66000-43e67000 ---p 43e66000 00:00 0 
43e67000-44667000 rw-p 43e67000 00:00 0 
44e68000-44e69000 ---p 44e68000 00:00 0 
44e69000-45669000 rw-p 44e69000 00:00 0 
46e6c000-46e6d000 ---p 46e6c000 00:00 0 
46e6d000-4766d000 rw-p 46e6d000 00:00 0 
7f372b64f000-7f372b651000 r-xp 00000000 08:03 32666                      /lib/libnss_mdns4.so.2
7f372b651000-7f372b851000 ---p 00002000 08:03 32666                      /lib/libnss_mdns4.so.2
7f372b851000-7f372b852000 rw-p 00002000 08:03 32666                      /lib/libnss_mdns4.so.2
7f372b852000-7f372b856000 r-xp 00000000 08:03 32606                      /lib/libattr.so.1.1.0
7f372b856000-7f372ba55000 ---p 00004000 08:03 32606                      /lib/libattr.so.1.1.0
7f372ba55000-7f372ba57000 rw-p 00003000 08:03 32606                      /lib/libattr.so.1.1.0
7f3733517000-7f373351f000 r-xp 00000000 08:03 922121                     /usr/lib/libfam.so.0.0.0
7f373351f000-7f373371e000 ---p 00008000 08:03 922121                     /usr/lib/libfam.so.0.0.0
7f373371e000-7f373371f000 rw-p 00007000 08:03 922121                     /usr/lib/libfam.so.0.0.0
7f373371f000-7f3733726000 r-xp 00000000 08:03 32600                      /lib/libacl.so.1.1.0
7f3733726000-7f3733925000 ---p 00007000 08:03 32600                      /lib/libacl.so.1.1.0
7f3733925000-7f3733927000 rw-p 00006000 08:03 32600                      /lib/libacl.so.1.1.0
7f3733927000-7f373396d000 r-xp 00000000 08:03 423491                     /usr/lib/mozilla/plugins/mplayerplug-in.so
7f373396d000-7f3733b6d000 ---p 00046000 08:03 423491                     /usr/lib/mozilla/plugins/mplayerplug-in.so
7f3733b6d000-7f3733b6e000 r--p 00046000 08:03 423491                     /usr/lib/mozilla/plugins/mplayerplug-in.so
7f3733b6e000-7f3733b70000 rw-p 00047000 08:03 423491                     /usr/lib/mozilla/plugins/mplayerplug-in.so
7f3733b70000-7f3733bb5000 r-xp 00000000 08:03 423493                     /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so
7f3733bb5000-7f3733db5000 ---p 00045000 08:03 423493                     /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so
7f3733db5000-7f3733db6000 r--p 00045000 08:03 423493                     /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so
7f3733db6000-7f3733db8000 rw-p 00046000 08:03 423493                     /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so
7f3733db8000-7f3733dfd000 r-xp 00000000 08:03 423497                     /usr/lib/mozilla/plugins/mplayerplug-in-rm.so
7f3733dfd000-7f3733ffd000 ---p 00045000 08:03 423497                     /usr/lib/mozilla/plugins/mplayerplug-in-rm.so
7f3733ffd000-7f3733ffe000 r--p 00045000 08:03 423497                     /usr/lib/mozilla/plugins/mplayerplug-in-rm.so
7f3733ffe000-7f3734000000 rw-p 00046000 08:03 423497                     /usr/lib/mozilla/plugins/mplayerplug-in-rm.so
7f3734000000-7f37342f9000 rw-p 7f3734000000 00:00 0 
7f37342f9000-7f3738000000 ---p 7f37342f9000 00:00 0 
7f3738131000-7f3738176000 r-xp 00000000 08:03 423495                     /usr/lib/mozilla/plugins/mplayerplug-in-qt.so
7f3738176000-7f3738376000 ---p 00045000 08:03 423495                     /usr/lib/mozilla/plugins/mplayerplug-in-qt.so
7f3738376000-7f3738377000 r--p 00045000 08:03 423495                     /usr/lib/mozilla/plugins/mplayerplug-in-qt.so
7f3738377000-7f3738379000 rw-p 00046000 08:03 423495                     /usr/lib/mozilla/plugins/mplayerplug-in-qt.so
7f3738379000-7f37383be000 r-xp 00000000 08:03 423499                     /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
7f37383be000-7f37385be000 ---p 00045000 08:03 423499                     /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
7f37385be000-7f37385bf000 r--p 00045000 08:03 423499                     /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
7f37385bf000-7f37385c1000 rw-p 00046000 08:03 423499                     /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
7f37385c1000-7f37385f3000 r-xp 00000000 08:03 277005                     /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so
7f37385f3000-7f37387f2000 ---p 00032000 08:03 277005                     /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so
7f37387f2000-7f37387f4000 r--p 00031000 08:03 277005                     /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so
7f37387f4000-7f37387f5000 rw-p 00033000 08:03 277005                     /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so
7f37387f5000-7f3738807000 r-xp 00000000 08:03 16408                      /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
7f3738807000-7f3738a07000 ---p 00012000 08:03 16408                      /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
7f3738a07000-7f3738a08000 r--p 00012000 08:03 16408                      /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
7f3738a08000-7f3738a09000 rw-p 00013000 08:03 16408                      /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
7f3738a09000-7f3738a19000 r-xp 00000000 08:03 16407                      /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
7f3738a19000-7f3738c19000 ---p 00010000 08:03 16407                      /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
7f3738c19000-7f3738c1a000 r--p 00010000 08:03 16407                      /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
7f3738c1a000-7f3738c1b000 rw-p 00011000 08:03 16407                      /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
7f3738c1b000-7f3738c34000 r-xp 00000000 08:03 16406                      /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
7f3738c34000-7f3738e34000 ---p 00019000 08:03 16406                      /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
7f3738e34000-7f3738e35000 r--p 00019000 08:03 16406                      /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
7f3738e35000-7f3738e36000 rw-p 0001a000 08:03 16406                      /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
7f3738e36000-7f3738e38000 r-xp 00000000 08:03 1156509                    /usr/lib/libtotem-plparser-mini.so.12.0.3
7f3738e38000-7f3739038000 ---p 00002000 08:03 1156509                    /usr/lib/libtotem-plparser-mini.so.12.0.3
7f3739038000-7f3739039000 r--p 00002000 Aborted



totem??

---

### Post by Sef on 2008-12-15
What are your system specs?

---

### Post by psypher on 2008-12-15
Dell M6300, 2.40GHz core2 duo, 3gb RAM, 160GB HDD

---

### Post by philinux on 2008-12-15
Start firefox from cli in safe mode.

firefox -safe-mode

---

### Post by caeroe on 2008-12-15
It's not just one guy, it's many here, if the search results are an indication.

If I want something stable in Flash I generally use Opera now, which seems better for the most part.  Something from Update Manager is to blame.

[http://snapshot.opera.com/unix/10.0-Alpha-1/](http://snapshot.opera.com/unix/10.0-Alpha-1/)

Hulu + Firefox is a death sentence.

---

### Post by psypher on 2008-12-16
tried safe mode, clicked on google reader shortcut, crash. output on cli just says aborted. 

tried new profile, same thing

---

### Post by dcstar on 2008-12-17
> **psypher said:**
> Just crashed again. Started it from cli here's the output:
........
totem??

Does it occur when you go to a specific web site?

---

### Post by psypher on 2008-12-17
no, it happens completely randomly and even sites that it did crash on before doesn't crash it the next time you open it. cannot find a specific reason why, anything seems to crash it.

My other PC at home running intrepid 64 is working fine since I haven't run updates in a while so it must be a bug in some update in the last 2 weeks.

Does anyone know if there is a bug report for this problem which has occurred in the last 2 weeks? I don't really want to know about bugs before that. this is brand new and driving me NUTS!

---

### Post by dcstar on 2008-12-17
> **psypher said:**
> no, it happens completely randomly and even sites that it did crash on before doesn't crash it the next time you open it. cannot find a specific reason why, anything seems to crash it.

My other PC at home running intrepid 64 is working fine since I haven't run updates in a while so it must be a bug in some update in the last 2 weeks.

Does anyone know if there is a bug report for this problem which has occurred in the last 2 weeks? I don't really want to know about bugs before that. this is brand new and driving me NUTS!

Check the kernel you are running and see if you can boot a previous version.

---

### Post by psypher on 2008-12-17
latest kernel: 2.6.27-9-generic
booted up with: 2.6.27-7-generic
Opened FF, went to google reader (i'm using google reader as it's something that i can find many different sites to go to quickly to make it crash), clicked on digg, clicked on article, crash

opened FF again, did exactly the same procedure, crash
opened FF again, did exactly the same procedure, did not crash this time. 
clicked on link to this forum post in my email, crash
opened FF again, clicked on link to this forum post in my email, wrote this post. has not crashed yet

---

### Post by psypher on 2008-12-17
just noticed something on the last crash. as i clicked on an article from slashdot it crashed, loaded FF and the article again and it crashed again. but the article doesn't crash immediately, the text bit of the article shows, and then 3 secs later it crashes. after doing it again, seems 3rd time is lucky to get an article working without a crash, I noticed that after the text bit appeared and 3 secs later it did not crash there was a mini slashdot banner that loaded. Seems like it's banners like that one that is causing the crashes. Now when i think bout it that seems to be the one coincidence amongst all the crashes. Just like to mention again, this is not just happening to google reader, it can happen on any website at any time, and sometimes it works and sometimes it doesn't.

---

### Post by xarte on 2008-12-17
I thought neither firefox nor Adobe Flash supported 64 bit versions?

did you try running it in Safe mode to see if its extensions/addons causing the issues?

---

### Post by psypher on 2008-12-17
as per previous post:

> **psypher said:**
> tried safe mode, clicked on google reader shortcut, crash. output on cli just says aborted. 

tried new profile, same thing


and yes there is 64bit FF and now there is 64bit flash beta. but like i said in previous posts, already tried disabling all of that. Please re-read all the posts before.

just tried re-installing ff. did:

```
sudo apt-get remove --purge firefox firefox-3.0 ubufox firefox-3.0-branding firefox-3.0-gnome-support firefox-gnome-support mozilla-mplayer && sudo apt-get install firefox firefox-3.0 ubufox firefox-3.0-branding firefox-3.0-gnome-support firefox-gnome-support mozilla-mplayer
```

still crashes.

Am I the ONLY person with this problem?

---

### Post by psypher on 2008-12-17
just tried safe mode again, crashes immediatly after clicking google reader shotcut:

firefox -safe-mode                   
*** glibc detected *** /usr/lib/firefox-3.0.4/firefox: double free or corruption (!prev): 0x00007f6e780bb5d0 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f6e8e1f3938]
/lib/libc.so.6(cfree+0x76)[0x7f6e8e1f5f86]
/usr/lib/libtalloc.so.1(talloc_free+0x128)[0x7f6e779c0b88]
/lib/libnss_wins.so.2[0x7f6e7ce15f48]
/usr/lib/libtalloc.so.1(talloc_free+0x232)[0x7f6e779c0c92]
/lib/libnss_wins.so.2(alloc_sub_basic+0x8e9)[0x7f6e7ce3dd02]
/lib/libnss_wins.so.2(talloc_sub_basic+0x24)[0x7f6e7ce3e26d]
/lib/libnss_wins.so.2[0x7f6e7cd8dbe9]
/lib/libnss_wins.so.2(lp_lockdir+0x1e)[0x7f6e7cd8ea93]
/lib/libnss_wins.so.2(lock_path+0x9)[0x7f6e7ce38972]
/lib/libnss_wins.so.2(receive_unexpected+0x2c)[0x7f6e7cde3321]
/lib/libnss_wins.so.2(receive_nmb_packet+0x3b)[0x7f6e7cde5d2e]
/lib/libnss_wins.so.2(name_query+0x303)[0x7f6e7cde8530]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname_r+0x2c8)[0x7f6e7cd8b202]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname2_r+0x2b)[0x7f6e7cd8b484]
/lib/libc.so.6(gethostbyname2_r+0x199)[0x7f6e8e27abf9]
/lib/libc.so.6[0x7f6e8e24784c]
/lib/libc.so.6(getaddrinfo+0x1de)[0x7f6e8e24996e]
/usr/lib/libnspr4.so.0d(PR_GetAddrInfoByName+0x108)[0x7f6e8d8a1828]
/usr/lib/xulrunner-1.9.0.4/libxul.so[0x7f6e8c9abb82]
/usr/lib/libnspr4.so.0d[0x7f6e8d8addc3]
/lib/libpthread.so.0[0x7f6e8eea13ea]
/lib/libc.so.6(clone+0x6d)[0x7f6e8e260c6d]
======= Memory map: ========
00400000-00408000 r-xp 00000000 08:03 1327525                            /usr/lib/firefox-3.0.4/firefox
00608000-00609000 r--p 00008000 08:03 1327525                            /usr/lib/firefox-3.0.4/firefox
00609000-0060a000 rw-p 00009000 08:03 1327525                            /usr/lib/firefox-3.0.4/firefox
01773000-0330b000 rw-p 01773000 00:00 0                                  [heap]
4080d000-4080e000 ---p 4080d000 00:00 0 
4080e000-4100e000 rw-p 4080e000 00:00 0 
412ab000-412ac000 ---p 412ab000 00:00 0 
412ac000-41aac000 rw-p 412ac000 00:00 0 
41ca1000-41ca2000 ---p 41ca1000 00:00 0 
41ca2000-424a2000 rw-p 41ca2000 00:00 0 
424a2000-424a3000 ---p 424a2000 00:00 0 
424a3000-42ca3000 rw-p 424a3000 00:00 0 
42ca3000-42ca4000 ---p 42ca3000 00:00 0 
42ca4000-434a4000 rw-p 42ca4000 00:00 0 
434a4000-434a5000 ---p 434a4000 00:00 0 
434a5000-43ca5000 rw-p 434a5000 00:00 0 
43ca5000-43ca6000 ---p 43ca5000 00:00 0 
43ca6000-444a6000 rw-p 43ca6000 00:00 0 
444a6000-444a7000 ---p 444a6000 00:00 0 
444a7000-44ca7000 rw-p 444a7000 00:00 0 
7f6e76f8d000-7f6e76f91000 r-xp 00000000 08:03 32659                      /lib/libnss_dns-2.8.90.so
7f6e76f91000-7f6e77191000 ---p 00004000 08:03 32659                      /lib/libnss_dns-2.8.90.so
7f6e77191000-7f6e77192000 r--p 00004000 08:03 32659                      /lib/libnss_dns-2.8.90.so
7f6e77192000-7f6e77193000 rw-p 00005000 08:03 32659                      /lib/libnss_dns-2.8.90.so
7f6e77193000-7f6e77195000 r-xp 00000000 08:03 65291                      /usr/lib/gconv/IBM850.so
7f6e77195000-7f6e77394000 ---p 00002000 08:03 65291                      /usr/lib/gconv/IBM850.so
7f6e77394000-7f6e77395000 r--p 00001000 08:03 65291                      /usr/lib/gconv/IBM850.so
7f6e77395000-7f6e77396000 rw-p 00002000 08:03 65291                      /usr/lib/gconv/IBM850.so
7f6e77396000-7f6e77398000 r-xp 00000000 08:03 32646                      /lib/libkeyutils-1.2.so
7f6e77398000-7f6e77597000 ---p 00002000 08:03 32646                      /lib/libkeyutils-1.2.so
7f6e77597000-7f6e77599000 rw-p 00001000 08:03 32646                      /lib/libkeyutils-1.2.so
7f6e77599000-7f6e775a0000 r-xp 00000000 08:03 922450                     /usr/lib/libkrb5support.so.0.1
7f6e775a0000-7f6e7779f000 ---p 00007000 08:03 922450                     /usr/lib/libkrb5support.so.0.1
7f6e7779f000-7f6e777a0000 r--p 00006000 08:03 922450                     /usr/lib/libkrb5support.so.0.1
7f6e777a0000-7f6e777a1000 rw-p 00007000 08:03 922450                     /usr/lib/libkrb5support.so.0.1
7f6e777a1000-7f6e777ba000 r-xp 00000000 08:03 922670                     /usr/lib/libsasl2.so.2.0.22
7f6e777ba000-7f6e779b9000 ---p 00019000 08:03 922670                     /usr/lib/libsasl2.so.2.0.22
7f6e779b9000-7f6e779ba000 r--p 00018000 08:03 922670                     /usr/lib/libsasl2.so.2.0.22
7f6e779ba000-7f6e779bb000 rw-p 00019000 08:03 922670                     /usr/lib/libsasl2.so.2.0.22
7f6e779bb000-7f6e779c3000 r-xp 00000000 08:03 922728                     /usr/lib/libtalloc.so.1.2.0
7f6e779c3000-7f6e77bc2000 ---p 00008000 08:03 922728                     /usr/lib/libtalloc.so.1.2.0
7f6e77bc2000-7f6e77bc3000 r--p 00007000 08:03 922728                     /usr/lib/libtalloc.so.1.2.0
7f6e77bc3000-7f6e77bc4000 rw-p 00008000 08:03 922728                     /usr/lib/libtalloc.so.1.2.0
7f6e77bc4000-7f6e77bcd000 r-xp 00000000 08:03 32624                      /lib/libcrypt-2.8.90.so
7f6e77bcd000-7f6e77dcc000 ---p 00009000 08:03 32624                      /lib/libcrypt-2.8.90.so
7f6e77dcc000-7f6e77dcd000 r--p 00008000 08:03 32624                      /lib/libcrypt-2.8.90.so
7f6e77dcd000-7f6e77dce000 rw-p 00009000 08:03 32624                      /lib/libcrypt-2.8.90.so
7f6e77dce000-7f6e77dfc000 rw-p 7f6e77dce000 00:00 0 
7f6e77dfc000-7f6e77dff000 r-xp 00000000 08:03 32623                      /lib/libcom_err.so.2.1
7f6e77dff000-7f6e77ffe000 ---p 00003000 08:03 32623                      /lib/libcom_err.so.2.1
7f6e77ffe000-7f6e77fff000 r--p 00002000 08:03 32623                      /lib/libcom_err.so.2.1
7f6e77fff000-7f6e78000000 rw-p 00003000 08:03 32623                      /lib/libcom_err.so.2.1
7f6e78000000-7f6e780d7000 rw-p 7f6e78000000 00:00 0 
7f6e780d7000-7f6e7c000000 ---p 7f6e780d7000 00:00 0 
7f6e7c000000-7f6e7c002000 r-xp 00000000 08:03 32667                      /lib/libnss_mdns4_minimal.so.2
7f6e7c002000-7f6e7c201000 ---p 00002000 08:03 32667                      /lib/libnss_mdns4_minimal.so.2
7f6e7c201000-7f6e7c202000 rw-p 00001000 08:03 32667                      /lib/libnss_mdns4_minimal.so.2
7f6e7c202000-7f6e7c225000 r-xp 00000000 08:03 922442                     /usr/lib/libk5crypto.so.3.1
7f6e7c225000-7f6e7c424000 ---p 00023000 08:03 922442                     /usr/lib/libk5crypto.so.3.1
7f6e7c424000-7f6e7c426000 r--p 00022000 08:03 922442                     /usr/lib/libk5crypto.so.3.1
7f6e7c426000-7f6e7c427000 rw-p 00024000 08:03 922442                     /usr/lib/libk5crypto.so.3.1
7f6e7c427000-7f6e7c4bf000 r-xp 00000000 08:03 922448                     /usr/lib/libkrb5.so.3.3
7f6e7c4bf000-7f6e7c6be000 ---p 00098000 08:03 922448                     /usr/lib/libkrb5.so.3.3
7f6e7c6be000-7f6e7c6c1000 r--p 00097000 08:03 922448                     /usr/lib/libkrb5.so.3.3
7f6e7c6c1000-7f6e7c6c2000 rw-p 0009a000 08:03 922448                     /usr/lib/libkrb5.so.3.3
7f6e7c6c2000-7f6e7c6ed000 r-xp 00000000 08:03 922305                     /usr/lib/libgssapi_krb5.so.2.2
7f6e7c6ed000-7f6e7c8ec000 ---p 0002b000 08:03 922305                     /usr/lib/libgssapi_krb5.so.2.2
7f6e7c8ec000-7f6e7c8ed000 r--p 0002a000 08:03 922305                     /usr/lib/libgssapi_krb5.so.2.2
7f6e7c8ed000-7f6e7c8ee000 rw-p 0002b000 08:03 922305                     /usr/lib/libgssapi_krb5.so.2.2
7f6e7c8ee000-7f6e7c8fc000 r-xp 00000000 08:03 922454                     /usr/lib/liblber-2.4.so.2.1.0
7f6e7c8fc000-7f6e7cafb000 ---p 0000e000 08:03 922454                     /usr/lib/liblber-2.4.so.2.1.0
7f6e7cafb000-7f6e7cafc000 r--p 0000d000 08:03 922454                     /usr/lib/liblber-2.4.so.2.1.0
7f6e7cafc000-7f6e7cafd000 rw-p 0000e000 08:03 922454                     /usr/lib/liblber-2.4.so.2.1.0
7f6e7cafd000-7f6e7cb40000 r-xp 00000000 08:03 922459                     /usr/lib/libldap_r-2.4.so.2.1.0
7f6e7cb40000-7f6e7cd3f000 ---p 00043000 08:03 922459                     /usr/lib/libldap_r-2.4.so.2.1.0
7f6e7cd3f000-7f6e7cd40000 r--p 00042000 08:03 922459                     /usr/lib/libldap_r-2.4.so.2.1.0
7f6e7cd40000-7f6e7cd41000 rw-p 00043000 08:03 922459                     /usr/lib/libldap_r-2.4.so.2.1.0
7f6e7cd41000-7f6e7cd44000 rw-p 7f6e7cd41000 00:00 0 
7f6e7cd44000-7f6e7cf1b000 r-xp 00000000 08:03 33585                      /lib/libnss_wins.so.2
7f6e7cf1b000-7f6e7d11b000 ---p 001d7000 08:03 33585                      /lib/libnss_wins.so.2
7f6e7d11b000-7f6e7d122000 r--p 001d7000 08:03 33585                      /lib/libnss_wins.so.2
7f6e7d122000-7f6e7d12a000 rw-p 001de000 08:03 33585                      /lib/libnss_wins.so.2
7f6e7d12a000-7f6e7d22f000 rw-p 7f6e7d12a000 00:00 0 
7f6eAborted

---

### Post by psypher on 2008-12-17
safe mode again, clicked google reader, opened article in new window, crash:

firefox -safe-mode
ICEDTEAPLUGIN_DEBUG = (null)
Aborted


strange how errors are not the same

---

### Post by psypher on 2008-12-17
OK now I'm stumped. Just installed Opera so that i can at least do my work and it crashed as well? pretty much exactly the same as with firefox:


```
:~$ opera 
Aborted
```

What do i look for now??

---

### Post by xarte on 2008-12-17
wonder if this might help at all?

[https://bugs.launchpad.net/ubuntu/+source/opera/+bug/183802](https://bugs.launchpad.net/ubuntu/+source/opera/+bug/183802)

I found this too
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888)

though if in safe mode flash is disabled, that's probably no help. If I read it right its the pulsaudio/flash interaction that's the problem, not pulsaudio on its own.

(not much help I know... bumping the thread if nothing else...)

---

### Post by psypher on 2008-12-17
Just loaded epiphany browser and it crashes too, so it's not FF but something that all browsers interact with.

I had a look at the bugs but it's NOT flash. loading Opera and epiphany and running in safe mode proves that.

i don't even have flashplugin-nonfree installed. I use the 64bit flash plugin that i manually put in the .mozilla/plugins folder

Could it be graphics driver? I'm running the restricted drivers provided by ubuntu for nvidia v 177. Don't remember if there was an upgrade recently.

now I'm really stuck, cannot even use ONE browser!

---

### Post by psypher on 2008-12-17
could it be java? it's common amongst all browsers.

i noticed that even though i run ff in safe mode i can still go to [www.java.com](www.java.com) and it tells me i have java installed.

which packages should i remove to complete remove java for all browsers?

---

### Post by psypher on 2008-12-17
K java is not the problem. i uninstalled every package with the word java in it and still crashes. i'm busy stress testing my PC as per suggestion of a guy on irc. So far no issues but will post what i find

---

### Post by caeroe on 2008-12-17
I just gave up with it.  I have to boot Windows just to watch Hulu now.  I had a good run with Opera, but now it decided to be shaky at best, rarely loading the videos.  I guess I was lucky enough it didn't crash me to death though.

I tried the Flash plugin from Synaptic and the alpha straight from Adobe.  Opera uses the plugin directory from Mozilla, to be sure I was testing the same version on different browsers.

Will Flash ever work in x64?  Stupid crap like this is why I have to forever keep Windows on my drive.

---

### Post by xarte on 2008-12-17
could you just run the 32 bit distro? I'm running the generic on my AMD64 and so far it's running just great - well firefox and flash is anyway, having a few hiccups with a partial upgrade issue but that's unrelated.

Other thing is, you're running Intrepid? Why not upgrade to Hardy?

I've seen a mention of font library issues with Gutsy, don't know if Intrepid had those also. 


Another idea: try installing the 32 bit browser and plugins. Didn't know this could be done but apparently so:

[http://blog.burlyhost.com/tag/64-bit/](http://blog.burlyhost.com/tag/64-bit/)

the comments in the above re Adobe's woeful support for 32 bit linux are rather sad.

I know you said it's not flash doing it, but it's worth a try.

---

### Post by psypher on 2008-12-17
up to 2 weeks ago my 64bit was running fine, my pc has never run so well with ubuntu. So no, i don't really want to switch to 32 bit I want to figure out why this is happening.

ran memtest86, 5 passes no errors
ran stress with -v -c 10 -i 10 -m 10 -d 10 switches, no errors. hardware is not the problem. and the rest of my pc is fine, just browsers


what is common, besides java and flash, to all browsers?

---

### Post by randiroo76073 on 2008-12-17
Sounds like a corrupted file that all 3 browsers access, but which one I'm not smart enough to tell you :(

---

### Post by psypher on 2008-12-18
looks like I'm not the only one: [http://ubuntuforums.org/showthread.php?t=990649&highlight=browser+crash](http://ubuntuforums.org/showthread.php?t=990649&highlight=browser+crash)

A re-install fixed his problem. Not an option in my case. Please any help would be great!!

---

### Post by psypher on 2008-12-18
> **xarte said:**
> could you just run the 32 bit distro? I'm running the generic on my AMD64 and so far it's running just great - well firefox and flash is anyway, having a few hiccups with a partial upgrade issue but that's unrelated.

Other thing is, you're running Intrepid? Why not upgrade to Hardy?

I've seen a mention of font library issues with Gutsy, don't know if Intrepid had those also. 


Another idea: try installing the 32 bit browser and plugins. Didn't know this could be done but apparently so:

[http://blog.burlyhost.com/tag/64-bit/](http://blog.burlyhost.com/tag/64-bit/)

the comments in the above re Adobe's woeful support for 32 bit linux are rather sad.

I know you said it's not flash doing it, but it's worth a try.

btw dude, intrepid is the newer version of ubuntu. it goes gutsy, hardy, intredpid. so no, not going back to hardy as it was the worst ubuntu yet for me

---

### Post by psypher on 2008-12-18
tried disabling compiz, still crashes

---

### Post by phlembob on 2008-12-18
Hi,
I'm running Hardy with AMD 64 bit and I never had any of the problems with the browsers noted with others in the forums. I had noticed with 2 updates memory errors noted at boot-ups.  They have come and gone 2 different updates.

A common point of interest I've noticed is Intrepid with a kernel misfit dealing with several visual problems.  Remember I'm using Hardy not Intrepid.  The Gnome interface within the kernel may not be constant between the programming teams.  This would give us problems with some updates compared with other updates.  The inconsistence problems is pointing to more than one kernel version in the hands of the programmers thinking they all have the same.
:popcorn: Through some popcorn on and keep jammin':guitar:

---

### Post by psypher on 2008-12-18
tried:
sudo aptitude remove ubuntu-restricted-extras flashplugin-nonfree w64codecs w32codecs mplayer mozilla-mplayer mplayer-fonts mplayer-skin-blue xbmc smplayer tovid tovidgui

in case it's some kind of plugin. made no differnce. is there a way to run a full debug on FF. running from the terminal doesn't really output anything. I know I posted some errors before but those are not related. Almost all the time FF crashes all it says is aborted, no errors at all.

---

### Post by psypher on 2008-12-19
Found some bug reports that match my problem. Although the errors aren't exactly the same the symptoms are identical. Really really hope this is just a bug and I don't have to re-install.

[https://bugs.launchpad.net/bugs/291843](https://bugs.launchpad.net/bugs/291843)
and
[https://bugs.launchpad.net/bugs/304882](https://bugs.launchpad.net/bugs/304882)

---

### Post by dBuster on 2008-12-19
Okay am I going to be able to post this...  So far so good..

I too am having the random crashes of FF.  I did notice that it all started yesterday morning after the package manager prompted me to do some update and in which that update included something about firefox.  Wish I could remember what exactly it was but something was updated.  Is there a way to see history of package updates?  Maybe if we looked there it would give us a clue...

This is quite frustrating!  Made it last night about an hour and a half without any crashes and now this morning I am on my 20 something crash already in less than 30 minutes..........

I do believe what ever was updated yesterday morning is the culprit...

---

### Post by dBuster on 2008-12-19
Had to switch to Opera to try and finish this..  Opera wanted to update and I said NO for right now!! 

I pulled up what was updated yesterday and here it is, something in this list is what is causing the issues as prior to that I was rock steady with firefox.

Commit Log for Thu Dec 18 04:35:15 2008


Upgraded the following packages:
firefox (3.0.4+nobinonly-0ubuntu0.8.04.1) to 3.0.5+nobinonly-0ubuntu0.8.04.1
firefox-2 (2.0.0.18+nobinonly-0ubuntu0.8.04.1) to 2.0.0.19+nobinonly1-0ubuntu0.8.04.1
firefox-3.0 (3.0.4+nobinonly-0ubuntu0.8.04.1) to 3.0.5+nobinonly-0ubuntu0.8.04.1
firefox-3.0-gnome-support (3.0.4+nobinonly-0ubuntu0.8.04.1) to 3.0.5+nobinonly-0ubuntu0.8.04.1
firefox-gnome-support (3.0.4+nobinonly-0ubuntu0.8.04.1) to 3.0.5+nobinonly-0ubuntu0.8.04.1
libgadu3 (1:1.7~rc2-2) to 1:1.7~rc2-2ubuntu0.8.04.1
liblcms1 (1.16-7ubuntu1) to 1.16-7ubuntu1.1
login (1:4.0.18.2-1ubuntu2.1) to 1:4.0.18.2-1ubuntu2.2
passwd (1:4.0.18.2-1ubuntu2.1) to 1:4.0.18.2-1ubuntu2.2
xulrunner-1.9 (1.9.0.4+nobinonly-0ubuntu0.8.04.1) to 1.9.0.5+nobinonly-0ubuntu0.8.04.1
xulrunner-1.9-gnome-support (1.9.0.4+nobinonly-0ubuntu0.8.04.1) to 1.9.0.5+nobinonly-0ubuntu0.8.04.1

---

### Post by dBuster on 2008-12-19
Okay, I found this thread [ubuntuforums.org/showthread.php?p=6398633#post6398633]("http://ubuntuforums.org/showthread.php?p=6398633#post6398633")  and gave it a shot.  So far after about 50 minutes I am stable.  No crashes and have even pulled up some flash without an issue.  I however have not closed the terminal window just yet in case FF Acts up..

Just thought to share.  Lets hope this does not return and if it does lets hope a fix is on its way!!!

> **smotsie said:**
> Now that is weird. I did killall firefox then ps -ef | grep firefox and it showed a couple of firefox-bin processes running. I killed them too (killall firefox-bin) and re-installed the Kubuntu version. Icons back to normal and search and address bar working as expected.

When the upgrade occurred it prompted that I would need to restart Firefox, which I did using the normal top-right X to close and then start from K menu. It would seem that didn't purge all processes for the old FF and it was that which caused the instability. Ho hum. At least with Ubuntu I could get another copy of the browser and install in a different way. Try that when Windoze IE upgrade causes a problem! (oh, yeah... install FF on Windoze too!)

So upshot is if you get weirdness, try a cold boot or commands above before anything else.

---

### Post by ellannjohnson on 2008-12-19
> **philinux said:**
> Start firefox from cli in safe mode.

firefox -safe-mode


Hey, thanx. That worked for me. I have been having trouble with FireFox for the last few days. It is kind of a need, because other Kubuntu browsers are not supported by my schools website. And other major sites I must use.

Thanxs, again.

---

### Post by cb34 on 2008-12-20
I'm having the same issues as you psypher man.. truly, truly a huge pain in the azz.

and just like you, i grabbed the newest Opera off their site, Opera crashes also.. sometimes does, sometimes doesn't.. but i'm on the web so much.. basically. it alwayz crashes sooner or later.

im gonna look into pulseaudio/alsa settings.. them maybe try to remove winbind.. then look into this probably: [http://ubuntuforums.org/showthread.php?t=1015598](http://ubuntuforums.org/showthread.php?t=1015598)

i dunno.. frustrated.. and cant get work done in ANY browser..

and my intrepid install is pretty fresh.. i just did it 3-4 dayz ago all new home directory complete new drive/partitions.. and purposely didn't install too much on it yet.. been slowly testin tweakin..
did the reinstall bcuz intrepid crashed too many times back to the login screen, i fiddled with old pulseaudio instructions, and lots of total reboots.. so i installed fresh with fresh home dir thinking the thing rebooted and crashed too many times.. i must have some damaged stuff(old windowz thinkin maybe, i dont even know if linux gets screwed up like that if a crash/reboot happens)

but now.. im reallly annoyed.. new setup.. love ubuntu..linux.. old install i fiddled too much.. made some problems i figure.... now reinstalled all fresh.. and firefox and all web browsers are totally unusable for me.

im off to try "stuff" :p

i feel what you(and others) are goin through man.. big problems..

crash crash crash all day long.. fun fun.. :mad:

i talk too much.. venting i guess. ):P

peaz

---

### Post by kaivalagi on 2008-12-20
I caught this thread late on but here goes...

I had both firefox and thunderbird crashing for no apparent reason after installing winbind for my samba based network drive...took a lot of searching to come to that conclusion.

So, do you have winbind installed? If so try removing it, and take out "wins" from /etc/nsswitch.conf if it's there, and try firefox again.

I have switched to using static IPs throughout the house now, and have updated my /etc/hosts files to cope with the address resolution instead.

It's been several days now since the change, and I have had zero issues with either firefox or thunderbird.

Hope that helps...

---

### Post by cowanh00 on 2008-12-20
This seams to have fixed it for me for now... I wonder how long it'll last..

```
A workaround:

Firefox menu > File > Quit
Then execute in terminal:
sudo killall -9 -r firefox
sudo apt-get purge firefox firefox-3.0 ubufox
sudo apt-get install --reinstall firefox firefox-3.0 firefox-3.0-gnome-support

When it's done, try run firefox
```

Got this [work around]("https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/270303/comments/3") from [here]("https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/270303").

---

### Post by cb34 on 2008-12-20
ok.. changing pulseaudio to alsa or anything else in both SOUND settings and MULTIMEDIA SYSTEMS SELECTOR.. and shutting down pulseaudio daemon..didn't help, same crashing..

tried to purge winbind,.. thought things were working as it didn't crash for all morning... then BAM.. crash.

but this time.. from all the million crashes over the last week or so.. this time.. first time i see in kern.log that libflashplayer.so segfaulted.. (i was watching a flash vid just now when it crashed.)

next thought..
maybe like i read on the forum around here somewhere, maybe when firefoz upgraded last time.. a firefox task was still running in the background not shut down all the way and caused a corruption.. or version difference between some files.. or somethin like that.. who knows.. still fiddling.......

peaz.

---

### Post by cb34 on 2008-12-20
opera just crashed with:

operapluginwrap[7795]: segfault at bfb52000 ip b67a2ec3 sp bfb4e940 error 4 in libflashplayer.so[b668d000+952000]

where to go from here?

would reinstalling firefox even help since it's showing a problem with opera also.

when setting up opera i did point its plugins to the mozilla dir where libflashplayer.so is.

im stumped if reinstalling firefox would do anything? if you know what i mean...

EDIT-> oh by the way, i'm on 32bit Intrepid.

---

### Post by kaivalagi on 2008-12-20
> **cb34 said:**
> opera just crashed with:

operapluginwrap[7795]: segfault at bfb52000 ip b67a2ec3 sp bfb4e940 error 4 in libflashplayer.so[b668d000+952000]

where to go from here?

would reinstalling firefox even help since it's showing a problem with opera also.

when setting up opera i did point its plugins to the mozilla dir where libflashplayer.so is.

im stumped if reinstalling firefox would do anything? if you know what i mean...

EDIT-> oh by the way, i'm on 32bit Intrepid.

It sounds like maybe the winbind removal sorted the main issue out, but you still have another issue with flash...

Might be worth purging and reinstalling firefox and flash support

I am running 64bit with no issues, so can't help with the flash stuff...

---

### Post by cb34 on 2008-12-20
good idea. thanks man! ya.. because from all the crashes, i never got a seg msg about libflashsupport, only now after purging winbind. so maybe this is a second underlying problem.

and just some info about what i did.
(i dont think it has anything to with the problems, just some info.)

when i reinstalled intrepid few dayz ago, and was gonna install flash like normal, the flash in the repos was screwed.. not the garbage ver, the non-free flash, if u dont install from terminal, you dont see this message, but since i installed it from the terminal.. when it looked like it was done installing, it said, flash was not installed in BOLD. something wrong with the package. so i downloaded the newest flash tar.gz off adobe's site and installed it that way with the script provided in the download, and it installed like normal.

so just a thought, i know how i i nstalled flash was proper, but maybe alot of you out there are having problems because they installed flash-non-free from the repo, in a gui, and didn't notice the msg about it not being installed properly. cuz going through a gui install, it goes through with it and doesn't tell you anything about having a problem. FWIW. (<-- now the reason why i ALWAYZ use the cli to install packages.)

i'll be back..LoL :p

---

### Post by cb34 on 2008-12-20
since i mentioned it.. might as well go all the way and show the log, remembered about the var/log/apt dir.. so here goes.. this is the attempt at installing flash-non-free from the repo..
```

Setting up flashplugin-nonfree (10.0.12.36ubuntu1) ...

debconf: unable to initialize frontend: Dialog

debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)

debconf: falling back to frontend: Readline

Downloading...

--2008-12-18 06:11:01--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz

Resolving fpdownload.macromedia.com... 218.61.9.243, 218.61.9.114, 60.217.232.254, ...

Connecting to fpdownload.macromedia.com|218.61.9.243|:80... connected.

HTTP request sent, awaiting response... 200 OK

Length: 3962157 (3.8M) [application/x-gzip]

Saving to: `./install_flash_player_10_linux.tar.gz'



     0K .......... .......... .......... .......... ..........  1% 42.4K 90s

    50K .......... .......... .......... .......... ..........  2% 84.0K 67s

   100K .......... .......... .......... .......... ..........  3%  167K 51s

   150K .......... .......... .......... .......... ..........  5%  160K 44s

   200K .......... .......... .......... .......... ..........  6% 86.2K 43s

   250K .......... .......... .......... .......... ..........  7%  184K 39s

   300K .......... .......... .......... .......... ..........  9%  165K 36s

   350K .......... .......... .......... .......... .......... 10%  167K 33s

   400K .......... .......... .......... .......... .......... 11%  168K 31s

   450K .......... .......... .......... .......... .......... 12%  168K 30s

   500K .......... .......... .......... .......... .......... 14%  137K 29s

   550K .......... .......... .......... .......... .......... 15%  107K 29s

   600K .......... .......... .......... .......... .......... 16%  169K 28s

   650K .......... .......... .......... .......... .......... 18%  164K 27s

   700K .......... .......... .......... .......... .......... 19% 87.5K 27s

   750K .......... .......... .......... .......... .......... 20% 1.45M 25s

   800K .......... .......... .......... .......... .......... 21%  150K 24s

   850K .......... .......... .......... .......... .......... 23%  103K 24s

   900K .......... .......... .......... .......... .......... 24% 80.0K 24s

   950K .......... .......... .......... .......... .......... 25%  159K 24s

  1000K .......... .......... .......... .......... .......... 27%  177K 23s

  1050K .......... .......... .......... .......... .......... 28% 87.8K 23s

  1100K .......... .......... .......... .......... .......... 29% 82.6K 23s

  1150K .......... .......... .......... .......... .......... 31%  172K 22s

  1200K .......... .......... .......... .......... .......... 32% 58.8K 23s

  1250K .......... .......... .......... .......... .......... 33%  166K 22s

  1300K .......... .......... .......... .......... .......... 34% 82.6K 22s

  1350K .......... .......... .......... .......... .......... 36% 52.5K 22s

  1400K .......... .......... .......... .......... .......... 37% 62.9K 23s

  1450K .......... .......... .......... .......... .......... 38% 49.7K 23s

  1500K .......... .......... .......... .......... .......... 40% 66.6K 23s

  1550K .......... .......... .......... .......... .......... 41% 57.4K 23s

  1600K .......... .......... .......... .......... .......... 42% 61.3K 23s

  1650K .......... .......... .......... .......... .......... 43% 68.0K 23s

  1700K .......... .......... .......... .......... .......... 45% 59.4K 22s

  1750K .......... .......... .......... .......... .......... 46% 79.6K 22s

  1800K .......... .......... .......... .......... .......... 47% 63.1K 22s

  1850K .......... .......... .......... .......... .......... 49% 78.5K 21s

  1900K .......... .......... .......... .......... .......... 50% 60.2K 21s

  1950K .......... .......... .......... .......... .......... 51% 80.3K 21s

  2000K .......... .......... .......... .......... .......... 52% 84.0K 20s

  2050K .......... .......... .......... .......... .......... 54% 80.3K 20s

  2100K .......... .......... .......... .......... .......... 55% 59.7K 19s

  2150K .......... .......... .......... .......... .......... 56% 75.2K 19s

  2200K .......... .......... .......... .......... .......... 58% 65.7K 18s

  2250K .......... .......... .......... .......... .......... 59% 79.8K 18s

  2300K .......... .......... .......... .......... .......... 60% 60.3K 17s

  2350K .......... .......... .......... .......... .......... 62% 83.4K 17s

  2400K .......... .......... .......... .......... .......... 63% 76.9K 16s

  2450K .......... .......... .......... .......... .......... 64% 69.5K 16s

  2500K .......... .......... .......... .......... .......... 65% 74.0K 15s

  2550K .......... .......... .......... .......... .......... 67% 77.1K 15s

  2600K .......... .......... .......... .......... .......... 68% 79.3K 14s

  2650K .......... .......... .......... .......... .......... 69% 51.7K 14s

  2700K .......... .......... .......... .......... .......... 71%  109K 13s

  2750K .......... .......... .......... .......... .......... 72% 74.9K 13s

  2800K .......... .......... .......... .......... .......... 73% 85.1K 12s

  2850K .......... .......... .......... .......... .......... 74% 42.4K 12s

  2900K .......... .......... .......... .......... .......... 76%  170K 11s

  2950K .......... .......... .......... .......... .......... 77% 47.3K 10s

  3000K .......... .......... .......... .......... .......... 78% 48.6K 10s

  3050K .......... .......... .......... .......... .......... 80% 49.1K 9s

  3100K .......... .......... .......... .......... .......... 81% 46.6K 9s

  3150K .......... .......... .......... .......... .......... 82% 54.4K 8s

  3200K .......... .......... .......... .......... .......... 83% 41.6K 8s

  3250K .......... .......... .......... .......... .......... 85% 61.1K 7s

  3300K .......... .......... .......... .......... .......... 86% 37.6K 7s

  3350K .......... .......... .......... .......... .......... 87% 46.1K 6s

  3400K .......... .......... .......... .......... .......... 89% 40.1K 6s

  3450K .......... .......... .......... .......... .......... 90% 34.0K 5s

  3500K .......... .......... .......... .......... .......... 91% 42.7K 4s

  3550K .......... .......... .......... .......... .......... 93% 41.4K 4s

  3600K .......... .......... .......... .......... .......... 94% 28.8K 3s

  3650K .......... .......... .......... .......... .......... 95% 25.4K 2s

  3700K .......... .......... .......... .......... .......... 96% 30.4K 2s

  3750K .......... .......... .......... .......... .......... 98% 35.4K 1s

  3800K .......... .......... .......... .......... .......... 99% 75.5K 0s

  3850K .......... .........                                  100% 68.9K=57s



2008-12-18 06:11:59 (67.4 KB/s) - `./install_flash_player_10_linux.tar.gz' saved [3962157/3962157]



Download done.

md5sum mismatch install_flash_player_10_linux.tar.gz

The Flash plugin is NOT installed.

```

so i did what it said and downloaded the tar.gz package off their site and installed it without a problem, and that is what im using now.

when i reinstall i will try to use the non-free repo version again, because i just noticed, the repo ver is now updated from 12.36 to 15.3(what im using now). noticed when i tried to install from the repo.. it was at ver 12.36.... aaaanywayz.. :D

---

### Post by cb34 on 2008-12-21
so i removed the libflashplayer.so plugin file/dir..(and xpti.dat so it re-reads the plugins installed), still crashed, opera also.. then i purged firefox like it says in post#40 and reinstalled, same crashing with no flash installed.. random crashing, but somewhat predictable.

so now i'm gonna try to force the old version of firefox in synaptic... see what that does, if anything.....

---

### Post by cb34 on 2008-12-21
i wonder if these crashing problems has something to do with the issues im having with a million ipv6 msg's being sent to my syslog, showing that the module keeps trying to connect,. even when using firefox with ipv6 disabled from about:config directly.

ipv6 syslog msg issue:
[http://ubuntuforums.org/showthread.php?t=1017014](http://ubuntuforums.org/showthread.php?t=1017014)

just thinking out loud on the screen trying to get to the bottom of this..

---

### Post by cb34 on 2008-12-21
i think im on to something, i have had no crashes since about writing the last post.. so like 4hrs now of constant browsing and video watching/streaming, not with flash, didn't install flash yet and dont want to until i get things stable.. just some wmv streaming vids that ALWAYS were crashing before in opera or firefox, and no crashes yet using opera.

in synaptic i forced the previous ver of xulrunner 1.9 and xulrunner-gnome-support packages, which was kinda tricky, deleted firefox all the way and with xulrunner forced to previous ver, and firefox not installed. im not getting any crashes in opera were it was crashing before constantly.. but im still testing and have ideas were to go from here, just an update. :D

its something to do with xulrunner.. and now im thinkin the next thing to try is to install firefox again with a forced previous version, since with an older xulrunner it wont let me install the current firefox.

the reason i even thought of xulrunner, is because either last update, or a few ago, i remember seeing xulrunner, and before i hit update, i did apt-cache show to investigate what it was since im fairly new to the unix/linux world.. so the xulrunner packages were in my head, and they even say something about sharing configs across browsers, and that is whats goin on, not just firefox, but opera also crashing.. so im thinkiin theres a problem with either xulrunner, or firefox's integration with the new xulrunner..i think. :p

but i can now browse in opera with no crashes... so far.
now to get firefox working.. if it's possible.

p.s. and to get media playback in opera with no mozilla installed in case you want to use opera but need media playback.. if you install for example mozilla-mplayer package it will want to auto install firefox again(or do all this before you deal with xulrunner and deleting firefox, so you can grab the .so plugin files first and wont have to nuke firefox, reinstall, then nuke again), so do it, let it install firefox, then go to /usr/lib/mozilla/plugins and move all the .so mplayer files to usr/lib/opera/plugins then delete/purge firefox.... for now ya know, in case you want to use opera till things get sorted and realize streaming online media doesn't work and sends you to MS's site.. opera can use mplayer mozilla plugin with no firefox installed on the system.. i tested just now vlc plugin, totem plugin, and xine plugin in opera, and only the mplayer plugin actually works half descent.

peace.
sorry for writing so much in so many posts in here, and im on 32 bit intrepid.. hahaha.. just real thorough and i dont give up. (never give up! never surrender! haha) dont mean to spam this thread or anything..:D

---

### Post by cb34 on 2008-12-21
'bout 4 hrs later, still usin opera, watchin vids like mad, has not crashed once. and just a thought im having, and wanna help anyone else out there, i also uninstalled some sun java packages that were installed auto from some other package, cant remember where it came from this second.. but could that have also maybe been a conflict with java and sun java files freakin out on eachother.. i dunno.. just some ideaz for ya'll.. i still did not install flash or firefox for the meantime just to kinda stress test my opera setup.. another little while.. if still no crashing with 30 tabs open, and 4 streaming vids goin all at once, like i have it goin now in the background, i'll move on to installing a downgraded ver of firefox maybe after i actually sleep.. the sun is up, and im still on the computer.. HAHAHA
oh, and i also have pulseaudio disabled at startup using sysvconfig, and have set SOUND and MULTIMEDIA SELECTOR to oss.. for now while testing.. but for some reason still have pulseaudio daemon running at startup.. so i killed pulseaudio -D also at the begining of this whole test, and also made sure all media players im using to stream with are set to oss, and not alsa or pulse.. just for now. :D
hmmm.. maybe next i'll try to install flash on opera while still not installing firefox, and see if any problems show up.

SPAM :p

---

### Post by VastOne on 2008-12-22
> **psypher said:**
> Dell M6300, 2.40GHz core2 duo, 3gb RAM, 160GB HDD

Psypher,

Caught this thread late and have read through it all...wanted to tell you of an issue I had with the latest update of FF on the same day that yours started.

i too am running 64 bit

FF was so erratic it made no sense. Every mouse move caused it to jump to a different tab or close it. Cut Copy and paste happened with a mind of their own...

After an hour it was driving me insane...

I then noticed that my son had plugged in a flash drive into a different USB 2.0 port than what we normally do.

I took that out and the issue was gone....

I do not know if this relates to anything you went through, but I thought I would throw it out there...

---

### Post by cb34 on 2008-12-22
whats up. :D i got my system back to super stable status.. running firefox with pulseaudio all normal again hooked up.

i have xulrunner-1.9 and xulrunner-1.9-gnome-support locked on the previous 1.9.0.3 version, then totally purged firefox including the .mozilla dir, and any plugin etc. files in /usr/lib/mozilla... then because getting all the firefox packages forced to the previous version was a real pain in the butt, i investigated and figured out to modify(or create) the /etc/apt/preferences file to force apt-get to install the previous version 3.0.3 instead of 3.0.5 current.

to force apt-get to install the previous version of firefox i created:
/etc/apt/preferences file. (i read this: man apt_preferences)

the file looks like this:
```

# force firefox 3.0.3 version instead of 3.0.5 to fix crashing.
#
Package: firefox firefox-3.0 firefox-gnome-support firefox-3.0-gnome-support firefox-3.0-branding
Pin: version 3.0.3*
Pin-Priority: 1001


```

so all day and night, pure videoa, super stressing everything with a million tabs and firefox processes and vids.. it is super stable now. i dont know about any security updated the new ver of firefox had in it, but egh, who carez.. running perfect now. in all browsers. :D:D

done

p.s. flash is also installed now and working well.. using the tar.gz from adobe's site.

p.s.#2 LoL if it helps somehow anyone out there, when reinstalling firefox, i did not install ubufox, so i dont have ubufox package installed right now and the system is stable, dont know if that makes any difference, but might as well tell the while story right. :D
```

sudo apt-get install --no-install-recommends firefox firefox-3.0 firefox-gnome-support firefox-3.0-gnome-support firefox-3.0-branding

```

---

### Post by slideking on 2008-12-22
> **cb34 said:**
> whats up. :D i got my system back to super stable status.. running firefox with pulseaudio all normal again hooked up.

i have xulrunner-1.9 and xulrunner-1.9-gnome-support locked on the previous 1.9.0.3 version, then totally purged firefox including the .mozilla dir, and any plugin etc. files in /usr/lib/mozilla... then because getting all the firefox packages forced to the previous version was a real pain in the butt, i investigated and figured out to modify(or create) the /etc/apt/preferences file to force apt-get to install the previous version 3.0.3 instead of 3.0.5 current.

to force apt-get to install the previous version of firefox i created:
/etc/apt/preferences file. (i read this: man apt_preferences)

the file looks like this:
```

# force firefox 3.0.3 version instead of 3.0.5 to fix crashing.
#
Package: firefox firefox-3.0 firefox-gnome-support firefox-3.0-gnome-support firefox-3.0-branding
Pin: version 3.0.3*
Pin-Priority: 1001


```

so all day and night, pure videoa, super stressing everything with a million tabs and firefox processes and vids.. it is super stable now. i dont know about any security updated the new ver of firefox had in it, but egh, who carez.. running perfect now. in all browsers. :D:D

done

p.s. flash is also installed now and working well.. using the tar.gz from adobe's site.

p.s.#2 LoL if it helps somehow anyone out there, when reinstalling firefox, i did not install ubufox, so i dont have ubufox package installed right now and the system is stable, dont know if that makes any difference, but might as well tell the while story right. :D
```

sudo apt-get install --no-install-recommends firefox firefox-3.0 firefox-gnome-support firefox-3.0-gnome-support firefox-3.0-branding

```


I think i'm gonna follow you cause for now i have a useless firefox.:p

I'm gonna make one step at a time as i'm not a linux expert.8-[

---

### Post by alvaromat on 2008-12-30
My problem come from an incompatibility between wins server due to samba. If had to edit /etc/nsswitch.conf host line and put wins at the end of the line

FROM:

hosts:          files [COLOR="Red"]wins[/COLOR] mdns4_minimal [NOTFOUND=return] dns mdns4

TO
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 wins

Now it works great

Hope it helps

---

### Post by kaivalagi on 2008-12-30
@alvaromat

The documentation said that wins should come before dns entries in nsswitch.conf, so I just removed it altogether to fix previous issues with firefox and thunderbird

With wins at the end of the line do you still have good name resolution for machines on the LAN?

I might well re-instate winbind like you have done...

---

### Post by cb34 on 2009-01-08
i hope this helps:

[http://ubuntuforums.org/showthread.php?t=1034369](http://ubuntuforums.org/showthread.php?t=1034369)

---

### Post by Yfrwlf on 2009-01-08
```
ICEDTEAPLUGIN_DEBUG = (null)
Illegal instruction
```

Getting that whenever I visit [http://www.theregister.co.uk/](http://www.theregister.co.uk/) for example.

Disabling Javascript fixes the problem.  Tried downloading Java from their site but the install apparently didn't work since the "Java Test" still says I have an older version installed and to upgrade.  Removing all the Java packages I can still leaves the IcedTea Firefox plugin in there, and it always is set to enable by default.

Someone seriously needs to destroy and recreate Linux package management...hate DEB package vs. plain script package battles that are totally unaware of each other.

---

### Post by stillboy on 2009-02-26
> **alvaromat said:**
> My problem come from an incompatibility between wins server due to samba. If had to edit /etc/nsswitch.conf host line and put wins at the end of the line

FROM:

hosts:          files [COLOR="Red"]wins[/COLOR] mdns4_minimal [NOTFOUND=return] dns mdns4

TO
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 wins

Now it works great

Hope it helps

**This worked for me**, well - moving the wins to the end of the line. I noticed that all of my crashes so far included something somewhere that pointed to the libnss when running from the command line i got this:
```

*** glibc detected *** /usr/lib/firefox-3.0.6/firefox: double free or corruption (fasttop): 0xad9f6bd0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d9d454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7d9f4b6]
/usr/lib/libtalloc.so.1(talloc_free+0x153)[0xb200b503]
/lib/libnss_wins.so.2[0xaec06289

```

Also, it looks like I was getting this in my kern.log, which seems to have been at different times that ff crashed

```

Feb 25 22:16:48 evildead kernel: [69613.156368] crashreporter[19479]: segfault at b7102030 ip b7102030 sp bfce35cc error 4 in libnss_files-2.8.90.so[b714b000+a000]
```

In any case, the above edit seems to have worked.

---

### Post by rbfthomas on 2009-03-04
Thanks so much, cb34!  I was experiencing unbelievable instability not only with Firefox but with other internet utilities - Thunderbird, evolution, even epiphany!  My browser wouldn't stay open for more than 5 minutes, if that.  I thought it was flash, so I disabled that.  I thought it might be Java/JavaScript, so I disabled that.  I uninstalled and reinstalled everything several times, and  my reward was more instability.  But your fix  of rolling back to FF 3.0.3 seems to have fixed things - I've even got flash up now.  

Appreciate the work you put into research, and your generosity in posting your results!:KS

---

### Post by rbfthomas on 2009-03-05
I wonder if the issues reporting in [this]("http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9128986&source=NLT_AM") article have anything to do with it...

---

### Post by jwilley44 on 2009-03-11
I have had similar problems. I tried the advice on this thread [http://ubuntuforums.org/showthread.php?t=249218](http://ubuntuforums.org/showthread.php?t=249218) but it did not work. It seems to be a problem with the Ipv6. What is this and how can I fix it?

---

### Post by kaivalagi on 2009-03-12
> **jwilley44 said:**
> I have had similar problems. I tried the advice on this thread [http://ubuntuforums.org/showthread.php?t=249218](http://ubuntuforums.org/showthread.php?t=249218) but it did not work. It seems to be a problem with the Ipv6. What is this and how can I fix it?

Ipv6 is the next gen internet protocol, and isn't really necessary yet...ipv4 is the default right now.

How to fix it, no idea....

Post the full error

---

### Post by stchman on 2009-03-12
> **psypher said:**
> In the last week my firefox has gone from usable to completely pointless. Constant crashing, freezing (greying out) and I cannot find the cause. At 1st I disabled all my extensions which seems to work for like an hour. Then I uninstalled all of them except VMWare and the Ubuntu ones and that works for 2 hours. Then I tried uninstalling flash, same issues. Install 64bit flash beta, still issues. I find now that it's not even flash sites specifically that crash it. Was just on google reader, opened an article in the reader with just a static image, crash. Re-opened FF and that very same page, no crash. 

So what the hell is going on? Going through bugs is so tedious as there are many many reasons FF has crashed over the years. So if anyone knows why since the beginning of last week firefox has started crashing and if there is a bug report for this specific bug please let me know. All I have done is run updates, no other major system changes.

Thanks


UPDATE!!

Seems  like the problem is not only with firefox but pretty much any browser I install. tried Opera and Epiphany and both have exact same symptoms. Problem is NOT flash but could possibly be java. Something that is common amongst all browsers. Read the rest of the posts to see all that i have tried

Ubuntu x86_64 Intrepid

I run Firefox on (5) different machines (3) of them 64 bit.  The latest Firefox in the repos 3.0.7 runs absolutely fine.

I installed the Flash 10 plugin into the ~/.mozilla/plugins folder and Flash 10 works fabulously.

Now I read VMWare.  Are you ruinning Firefox in another OS using VMWare?

---

### Post by dlstyley on 2009-04-02
Anyone truly solve this?  I've been pulling my hair out thinking that I had a hardware problem.  Been having random crashes in Firefox and segfaults reported in the log.  Even my USB mouse was acting crazy.

I finally decided I had a bad motherboard and bought new MB, RAM, and Proc, moving from AMD to Intel (both 64bit procs).  Just got system put together and booted up and much to my dismay, Firefox is still taking a dump on me regularly.  

AGGGGHHHHHH!!!!!

Here is what Firefox pukes out:  

```
ICEDTEAPLUGIN_DEBUG = (null)
*** glibc detected *** /usr/lib/firefox-3.0.8/firefox: malloc(): memory corruption: 0x00007f4d006cb0f0 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f4d11d5fe1f]
/lib/libc.so.6(__libc_malloc+0x98)[0x7f4d11d61658]
/usr/lib/libtalloc.so.1(talloc_strdup+0xab)[0x7f4cfab885bb]
/lib/libnss_wins.so.2[0x7f4cfbdff8c0]
/lib/libnss_wins.so.2(lock_path+0x14)[0x7f4cfbdff97d]
/lib/libnss_wins.so.2(receive_unexpected+0x2c)[0x7f4cfbdaa321]
/lib/libnss_wins.so.2(receive_nmb_packet+0x3b)[0x7f4cfbdacd2e]
/lib/libnss_wins.so.2(name_query+0x303)[0x7f4cfbdaf530]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname_r+0x2c8)[0x7f4cfbd52202]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname2_r+0x2b)[0x7f4cfbd52484]
/lib/libc.so.6(gethostbyname2_r+0x199)[0x7f4d11de3bf9]
/lib/libc.so.6[0x7f4d11db085c]
/lib/libc.so.6(getaddrinfo+0x1de)[0x7f4d11db297e]
/usr/lib/libnspr4.so.0d(PR_GetAddrInfoByName+0x108)[0x7f4d1140a828]
/usr/lib/xulrunner-1.9.0.8/libxul.so[0x7f4d1051016a]
/usr/lib/libnspr4.so.0d[0x7f4d11416dc3]
/lib/libpthread.so.0[0x7f4d12a0a3ea]
/lib/libc.so.6(clone+0x6d)[0x7f4d11dc9cbd]
======= Memory map: ========
00400000-00408000 r-xp 00000000 08:01 6865907                            /usr/lib/firefox-3.0.8/firefox
00608000-00609000 r--p 00008000 08:01 6865907                            /usr/lib/firefox-3.0.8/firefox
00609000-0060a000 rw-p 00009000 08:01 6865907                            /usr/lib/firefox-3.0.8/firefox
018f0000-02df9000 rw-p 018f0000 00:00 0                                  [heap]
40a73000-40a74000 ---p 40a73000 00:00 0 
40a74000-41274000 rw-p 40a74000 00:00 0 
41962000-41963000 ---p 41962000 00:00 0 
41963000-42163000 rw-p 41963000 00:00 0 
42163000-42164000 ---p 42163000 00:00 0 
42164000-42964000 rw-p 42164000 00:00 0 
42964000-42965000 ---p 42964000 00:00 0 
42965000-43165000 rw-p 42965000 00:00 0 
43165000-43166000 ---p 43165000 00:00 0 
43166000-43966000 rw-p 43166000 00:00 0 
43966000-43967000 ---p 43966000 00:00 0 
43967000-44167000 rw-p 43967000 00:00 0 
44167000-44168000 ---p 44167000 00:00 0 
44168000-44968000 rw-p 44168000 00:00 0 
44968000-44969000 ---p 44968000 00:00 0 
44969000-45169000 rw-p 44969000 00:00 0 
45169000-4516a000 ---p 45169000 00:00 0 
4516a000-4596a000 rw-p 4516a000 00:00 0 
4596a000-4596b000 ---p 4596a000 00:00 0 
4596b000-4616b000 rw-p 4596b000 00:00 0 
4616b000-4616c000 ---p 4616b000 00:00 0 
4616c000-4696c000 rw-p 4616c000 00:00 0 
4696c000-4696d000 ---p 4696c000 00:00 0 
4696d000-4716d000 rw-p 4696d000 00:00 0 
4716d000-4716e000 ---p 4716d000 00:00 0 
4716e000-4796e000 rw-p 4716e000 00:00 0 
7f4cf1c28000-7f4cf1c66000 rw-s 00000000 00:09 1081362                    /SYSV00000000 (deleted)
7f4cf1c66000-7f4cf1cac000 r--p 00000000 08:01 5292129                    /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf
7f4cf1cac000-7f4cf1e0f000 r-xp 00000000 08:01 6324775                    /usr/lib/libcrypto.so.0.9.8
7f4cf1e0f000-7f4cf200e000 ---p 00163000 08:01 6324775                    /usr/lib/libcrypto.so.0.9.8
7f4cf200e000-7f4cf201b000 r--p 00162000 08:01 6324775                    /usr/lib/libcrypto.so.0.9.8
7f4cf201b000-7f4cf2031000 rw-p 0016f000 08:01 6324775                    /usr/lib/libcrypto.so.0.9.8
7f4cf2031000-7f4cf2035000 rw-p 7f4cf2031000 00:00 0 
7f4cf2035000-7f4cf207e000 r-xp 00000000 08:01 6324970                    /usr/lib/libssl.so.0.9.8
7f4cf207e000-7f4cf227e000 ---p 00049000 08:01 6324970                    /usr/lib/libssl.so.0.9.8
7f4cf227e000-7f4cf227f000 r--p 00049000 08:01 6324970                    /usr/lib/libssl.so.0.9.8
7f4cf227f000-7f4cf2284000 rw-p 0004a000 08:01 6324970                    /usr/lib/libssl.so.0.9.8
7f4cf2284000-7f4cf22b5000 r-xp 00000000 08:01 6324303                    /usr/lib/libidn.so.11.5.37
7f4cf22b5000-7f4cf24b5000 ---p 00031000 08:01 6324303                    /usr/lib/libidn.so.11.5.37
7f4cf24b5000-7f4cf24b6000 r--p 00031000 08:01 6324303                    /usr/lib/libidn.so.11.5.37
7f4cf24b6000-7f4cf24b7000 rw-p 00032000 08:01 6324303                    /usr/lib/libidn.so.11.5.3^C
```

I am on Intrepid 64-bit, all latest updates.  I've tried both Flash 9 and Flash 10 (alpha).  Firefox seems especially twitchy on sites with lots of flash/javascript (Youtube is almost instant death), but sometimes other sites trigger it.  

I'm no longer getting segfaults in teh error log, so that's good.  I am also using a different mouse (I think my old mouse really was hosed).

---

### Post by dlstyley on 2009-04-02
I can't belive it.... after all this it looks like it was java.  I uninstalled it and installed the new beta version for 64-bit and it works.  I guess it was a good excuse for an upgrade.  Oh well.

---

### Post by dlstyley on 2009-04-07
Nevermind...  this intermittent problem is really annoying.  Any suggestions?  Seems there are lots of different threads related to instability of firefox on 64bit.  I can't seem to find anything definitive though.  

```
*** glibc detected *** /usr/lib/firefox-3.0.8/firefox: double free or corruption (!prev): 0x00000000036ac870 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f65fab2ba58]
/lib/libc.so.6(cfree+0x76)[0x7f65fab2e0a6]
/usr/lib/libtalloc.so.1(talloc_free+0x128)[0x7f65e4a66b88]
/lib/libnss_wins.so.2(alloc_sub_basic+0x8e9)[0x7f65e5ce1d02]
/lib/libnss_wins.so.2(talloc_sub_basic+0x24)[0x7f65e5ce226d]
/lib/libnss_wins.so.2[0x7f65e5c31be9]
/lib/libnss_wins.so.2(lp_lockdir+0x1e)[0x7f65e5c32a93]
/lib/libnss_wins.so.2(lock_path+0x9)[0x7f65e5cdc972]
/lib/libnss_wins.so.2(receive_unexpected+0x2c)[0x7f65e5c87321]
/lib/libnss_wins.so.2(receive_nmb_packet+0x3b)[0x7f65e5c89d2e]
/lib/libnss_wins.so.2(name_query+0x303)[0x7f65e5c8c530]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname_r+0x2c8)[0x7f65e5c2f202]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname2_r+0x2b)[0x7f65e5c2f484]
/lib/libc.so.6(gethostbyname2_r+0x199)[0x7f65fabb2bf9]
/lib/libc.so.6[0x7f65fab7f85c]
/lib/libc.so.6(getaddrinfo+0x1de)[0x7f65fab8197e]
/usr/lib/libnspr4.so.0d(PR_GetAddrInfoByName+0x108)[0x7f65fa1d9828]
/usr/lib/xulrunner-1.9.0.8/libxul.so[0x7f65f92df16a]
/usr/lib/libnspr4.so.0d[0x7f65fa1e5dc3]
/lib/libpthread.so.0[0x7f65fb7d93ea]
/lib/libc.so.6(clone+0x6d)[0x7f65fab98cbd]
```

---

### Post by BFG on 2009-04-08
> **dlstyley said:**
> I can't belive it.... after all this it looks like it was java.  I uninstalled it and installed the new beta version for 64-bit and it works.  I guess it was a good excuse for an upgrade.  Oh well.

Java 64 runs, but, the Java plugin does not work with firefox 64.  You can install firefox 32 on ubuntu 64, that apparently is a sound workaround.  I haven;t tried it.

Or, disable the 64 plugin and use iced-tea plugin instead.  Not perfect, but it stopped a lot of crashes for me.

---

### Post by VastOne on 2009-04-19
> **psypher said:**
> as per previous post:




and yes there is 64bit FF and now there is 64bit flash beta. but like i said in previous posts, already tried disabling all of that. Please re-read all the posts before.

just tried re-installing ff. did:

```
sudo apt-get remove --purge firefox firefox-3.0 ubufox firefox-3.0-branding firefox-3.0-gnome-support firefox-gnome-support mozilla-mplayer && sudo apt-get install firefox firefox-3.0 ubufox firefox-3.0-branding firefox-3.0-gnome-support firefox-gnome-support mozilla-mplayer
```

still crashes.

Am I the ONLY person with this problem?


No...Still having this same issue several months later

---

### Post by stanca on 2009-04-26
Add flashblock and fasterfox.
About ipv6 just type about:config in firefox,filter:ipv6,double-click network.dns,disable ipv6 to set the value to true.:popcorn:

---

### Post by Dr Mac 24 on 2009-04-29
I've had similar problems with Intrepid (ADM64 version) with Firefox (FF) crashing all the time. It started a week ago or so after installing updates. I've now sorted it using Cowanh's solution ie

> **cowanh00 said:**
> This seams to have fixed it for me for now... I wonder how long it'll last..

```
A workaround:

Firefox menu > File > Quit
Then execute in terminal:
1  sudo killall -9 -r firefox
2  sudo apt-get purge firefox firefox-3.0 ubufox
3  sudo apt-get install --reinstall firefox firefox-3.0 firefox-3.0-gnome-support

When it's done, try run firefox
```



This may help others. Terminal instruction 1 didn't work so I uninstalled Firefox via Synaptic. Then implemented instructions 2 & 3. Firefox now works fine. So far at least, a couple of hours, time will tell how good this fix is. My terminal dump is as follows:

ddddd@CCCCCC:~$ sudo killall -9 -r firefox
[sudo] password for daniel: 
firefox: no process killed. 

Here I used Synaptic to unintall Firefox ie 6 programmes. Firefox desktop icon disappeared.

ddddd@CCCCCC:~$ sudo apt-get purge firefox firefox-3.0 ubufox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firefox is not installed, so not removed
Package firefox-3.0 is not installed, so not removed
Package ubufox is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ddddd@CCCCCC:~$ sudo apt-get install --reinstall firefox firefox-3.0 firefox-3.0-gnome-support
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  firefox-3.0-branding ubufox
Suggested packages:
  latex-xft-fonts
The following NEW packages will be installed
  firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support ubufox
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1318kB of archives.
After this operation, 4592kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package firefox-3.0-branding.
(Reading database ... 118219 files and directories currently installed.)
Unpacking firefox-3.0-branding (from .../firefox-3.0-branding_3.0.9+nobinonly-0ubuntu0.8.10.1_amd64.deb) ...
Selecting previously deselected package firefox-3.0.
Unpacking firefox-3.0 (from .../firefox-3.0_3.0.9+nobinonly-0ubuntu0.8.10.1_amd64.deb) ...
Selecting previously deselected package firefox.
Unpacking firefox (from .../firefox_3.0.9+nobinonly-0ubuntu0.8.10.1_all.deb) ...
Selecting previously deselected package firefox-3.0-gnome-support.
Unpacking firefox-3.0-gnome-support (from .../firefox-3.0-gnome-support_3.0.9+nobinonly-0ubuntu0.8.10.1_amd64.deb) ...
Selecting previously deselected package ubufox.
Unpacking ubufox (from .../ubufox_0.6-0ubuntu1.8.10.1_all.deb) ...
Setting up firefox-3.0-branding (3.0.9+nobinonly-0ubuntu0.8.10.1) ...
Setting up firefox-3.0 (3.0.9+nobinonly-0ubuntu0.8.10.1) ...
Please restart all running instances of firefox-3.0, or you will experience problems.

Setting up firefox (3.0.9+nobinonly-0ubuntu0.8.10.1) ...
Setting up firefox-3.0-gnome-support (3.0.9+nobinonly-0ubuntu0.8.10.1) ...

Setting up ubufox (0.6-0ubuntu1.8.10.1) ...
ddddd@CCCCCC:~$ Desktop icon reappeared

Flash also still working fine.

---

