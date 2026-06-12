---
title: "[SOLVED] Flash player not working"
date: 2008-02-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by peddy on 2008-02-16
My flash is intermittently working and not working. I am running 64-bit Ubuntu Gutsy. The process 'npviewer.bin' becomes a zombie. Flash content disappears seemingly randomly and is replaced by a grey box. Can anyone please help me?

---

### Post by khensucat on 2008-02-16
Have you tried running kilz' excellent script in the sticky above, especially to revert to the previous version? This *always* solves flash problems for me, personally ;)

Edit: link is here:

[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

### Post by peddy on 2008-02-16
I will try that, thanks mate. But is there any way to make the context menu look normal with Kilz' version?


and btw if I refresh the page (sometimes) the flash loads correctly. Are there any logs or anything I can check?

---

### Post by peddy on 2008-02-16
OK, its still not working. Is it possible to run Firefox in some sort of debugging mode with terminal output?

---

### Post by khensucat on 2008-02-16
I don't know :-( I'm afraid that one is beyond me. Others should be along soon, though, that should be able to finish helping you, so just be patient, dear, and they'll guide you through ;)

---

### Post by dayanandasaraswati on 2008-02-16
Have you installed Gnash flash player or some thing else. Try installing flash player from nspluginwrapper. This is a fantastic tool to install flash.. If still problem persists try installing swiftweasel and using it. Its a browser built specially for ubuntu. Its basically a mutant of firefox. Try it. Its fantastic

---

### Post by Kilz on 2008-02-16
> **peddy said:**
> I will try that, thanks mate. But is there any way to make the context menu look normal with Kilz' version?


and btw if I refresh the page (sometimes) the flash loads correctly. Are there any logs or anything I can check?

Since you tried my script, please provide the requested info when reporting a problem.
The results of the following commands may help us see whats going on.
```
ls -al /usr/lib/mozilla//plugins/
ls -al /usr/lib/firefox/plugins/
```

---

### Post by Kikoolol on 2008-02-16
Same problem here. Since the last update of flashplugin-nonfree, nspluginwrapper crashes when several flash contents are displayed on a same page, or in 2 differents firefox tabs. 

Here is an example : 
1. Go to [http://www.beatport.com](http://www.beatport.com), everything's fine.
2. Open a new tab and try to watch a youtube video, nspluginwrapper crashes and a white/grey box is displayed instead of flash content.

My dmesg :
> 
[27189.149504] npviewer.bin[11964]: segfault at 00000000f774a5de rip 00000000f7a2c0ed rsp 00000000f5af1d80 error 7
[27189.149513] npviewer.bin[11947]: segfault at 0000000065786970 rip 00000000f77bfba8 rsp 00000000ffc189fc error 4
[27234.339108] npviewer.bin[12036]: segfault at 00000000f77385af rip 00000000f7a1a0ed rsp 00000000f5adfd80 error 7
[27234.339118] npviewer.bin[12019]: segfault at 00000000f77385af rip 00000000f7a1a0ed rsp 00000000ffb77910 error 7
[27255.741011] npviewer.bin[12061]: segfault at 0000000000000001 rip 00000000f7ac26fe rsp 00000000fff6b870 error 4


I hope this can help :)

Kkl

---

### Post by freerick on 2008-02-17
I have exactly the same problem on Ubuntu Gutsy 7.10 (and Kubuntu 7.10) on amd64 with an Intel Core 2 Duo 2.66Ghz, 2GB RAM.

I have experienced exactly the same problem with GNOME and KDE3/4 (grey box instead of flash). I am using flashplugin-nonfree, as it installed with apt-get. It runs as npviewer.bin (I'm assuming this is nspluginwrapper). I have to killall npviewer.bin and reload the page to get it to work again, sometimes. Often times, a restart of firefox is required to get things working again.

I also noticed that firefox, left to its own devices, is leaking memory like a waterfall. If left alone, it often takes up more than 1GB of my 2GB of RAM; I have a strong suspicion that this may be related to flash, but I'm not 100% sure. Further investigation is in order here, but if anyone has any info on any of this, please post it here.
Thanks!

---

### Post by Kilz on 2008-02-17
> **Kikoolol said:**
> Same problem here. Since the last update of flashplugin-nonfree, nspluginwrapper crashes when several flash contents are displayed on a same page, or in 2 differents firefox tabs. 

Here is an example : 
1. Go to [http://www.beatport.com](http://www.beatport.com), everything's fine.
2. Open a new tab and try to watch a youtube video, nspluginwrapper crashes and a white/grey box is displayed instead of flash content.

My dmesg :


I hope this can help :)

Kkl

Post 2 has given the link to the flash sticky.

> **freerick said:**
> I have exactly the same problem on Ubuntu Gutsy 7.10 (and Kubuntu 7.10) on amd64 with an Intel Core 2 Duo 2.66Ghz, 2GB RAM.

I have experienced exactly the same problem with GNOME and KDE3/4 (grey box instead of flash). I am using flashplugin-nonfree, as it installed with apt-get. It runs as npviewer.bin (I'm assuming this is nspluginwrapper). I have to killall npviewer.bin and reload the page to get it to work again, sometimes. Often times, a restart of firefox is required to get things working again.

I also noticed that firefox, left to its own devices, is leaking memory like a waterfall. If left alone, it often takes up more than 1GB of my 2GB of RAM; I have a strong suspicion that this may be related to flash, but I'm not 100% sure. Further investigation is in order here, but if anyone has any info on any of this, please post it here.
Thanks!


Post 2 has given the link to the flash sticky. [You might also want to try Swiftweasel]("http://swiftweasel.tuxfamily.org/"), its a little better on using resources. But if you have 5-10 tabs open with flash video's nothing is going to help.

---

### Post by peddy on 2008-02-17
Damn it feels good to not be alone ^^

```
apc@moonshine:~$ ls -al /usr/lib/mozilla//plugins/
total 1456
drwxr-xr-x 2 apc  users   4096 2008-02-16 21:25 .
drwxr-xr-x 3 root root    4096 2007-05-18 21:47 ..
lrwxrwxrwx 1 root root      37 2008-02-16 21:25 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 apc  users     34 2008-02-10 18:29 libgcjwebplugin.so -> ../../classpath/libgcjwebplugin.so
lrwxrwxrwx 1 apc  users     38 2007-11-19 19:34 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji.so
lrwxrwxrwx 1 apc  users     39 2008-02-10 18:29 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 apc  users     36 2007-10-19 16:33 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 apc  users     37 2007-10-19 16:33 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 apc  users     34 2007-10-19 16:33 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 apc  users     35 2007-10-19 16:33 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 apc  users     36 2007-10-19 16:33 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 apc  users     37 2007-10-19 16:33 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 apc  users     42 2007-10-19 16:33 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 apc  users     43 2007-10-19 16:33 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 apc  users 286688 2007-08-18 08:21 mplayerplug-in-dvx.so
-rw-r--r-- 1 apc  users   1021 2007-08-18 08:21 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 apc  users 286688 2007-08-18 08:21 mplayerplug-in-qt.so
-rw-r--r-- 1 apc  users   1021 2007-08-18 08:21 mplayerplug-in-qt.xpt
-rw-r--r-- 1 apc  users 286688 2007-08-18 08:21 mplayerplug-in-rm.so
-rw-r--r-- 1 apc  users   1021 2007-08-18 08:21 mplayerplug-in-rm.xpt
-rw-r--r-- 1 apc  users 286680 2007-08-18 08:21 mplayerplug-in.so
-rw-r--r-- 1 apc  users 286688 2007-08-18 08:21 mplayerplug-in-wmp.so
-rw-r--r-- 1 apc  users   1021 2007-08-18 08:21 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 apc  users   1021 2007-08-18 08:21 mplayerplug-in.xpt
lrwxrwxrwx 1 apc  users     48 2007-08-05 09:00 nphelix.so -> /home/arno/Desktop/RealPlayer/mozilla/nphelix.so
lrwxrwxrwx 1 apc  users     49 2007-08-05 09:00 nphelix.xpt -> /home/arno/Desktop/RealPlayer/mozilla/nphelix.xpt
lrwxrwxrwx 1 apc  users     60 2008-02-16 19:51 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
lrwxrwxrwx 1 apc  users     61 2007-10-19 20:05 npwrapper.so -> ../../../../usr/lib/nspluginwrapper/x86_64/linux/npwrapper.so
apc@moonshine:~$ 

```

and ls -al /usr/lib/firefox/plugins/

```
apc@moonshine:~$ ls -al /usr/lib/firefox/plugins/
total 28
drwxr-xr-x 2 apc  users  4096 2008-02-16 21:25 .
drwxr-xr-x 6 root root   4096 2008-02-09 14:59 ..
lrwxrwxrwx 1 root root     37 2008-02-16 21:25 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 apc  users    34 2008-02-10 18:29 libgcjwebplugin.so -> ../../classpath/libgcjwebplugin.so
lrwxrwxrwx 1 apc  users    39 2008-02-10 18:29 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 apc  users    36 2007-10-19 16:33 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 apc  users    37 2007-10-19 16:33 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 apc  users    34 2007-10-19 16:33 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 apc  users    35 2007-10-19 16:33 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 apc  users    36 2007-10-19 16:33 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 apc  users    37 2007-10-19 16:33 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 apc  users    42 2007-10-19 16:33 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 apc  users    43 2007-10-19 16:33 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 apc  users 11456 2008-02-08 00:07 libunixprintplugin.so
lrwxrwxrwx 1 apc  users    43 2007-11-29 19:54 mplayerplug-in-dvx.so -> ../../mozilla/plugins/mplayerplug-in-dvx.so
lrwxrwxrwx 1 apc  users    44 2007-11-29 19:54 mplayerplug-in-dvx.xpt -> ../../mozilla/plugins/mplayerplug-in-dvx.xpt
lrwxrwxrwx 1 apc  users    42 2007-11-29 19:54 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 apc  users    43 2007-11-29 19:54 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 apc  users    42 2007-11-29 19:54 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 apc  users    43 2007-11-29 19:54 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 apc  users    39 2007-11-29 19:54 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 apc  users    43 2007-11-29 19:54 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 apc  users    44 2007-11-29 19:54 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 apc  users    40 2007-11-29 19:54 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
lrwxrwxrwx 1 apc  users    48 2007-08-05 09:00 nphelix.so -> /home/arno/Desktop/RealPlayer/mozilla/nphelix.so
lrwxrwxrwx 1 apc  users    49 2007-08-05 09:00 nphelix.xpt -> /home/arno/Desktop/RealPlayer/mozilla/nphelix.xpt
lrwxrwxrwx 1 apc  users    60 2008-02-16 19:51 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
lrwxrwxrwx 1 apc  users    61 2007-08-03 19:17 npwrapper.so -> ../../../../usr/lib/nspluginwrapper/x86_64/linux/npwrapper.so

```


Everything is working for me now, unfortunately I do not know what I did. Everyone else, try purging and reinstalling the official flash player. This may have to do with !flashissue (on the ubuntu IRC channel). I will check back here however if anyone wants any info from me.

Thanks Kilz and khensucat for you help. It is greatly appreciated.


edit: ok its not working anymore. Maybe the above info can shed some light.

---

### Post by NightwishFan on 2008-02-17
Certain flash related plugins for Firefox caused the grey box problem for me. If I do not use them the flash works fine in 5+ windows,

---

### Post by peddy on 2008-02-17
I just had a thought, maybe its some FF plugins? Lets compare the ones we have installed :P

the list is attached, plus I have Adblock Plus

---

### Post by NightwishFan on 2008-02-17
Ubufox and Adblock +

It was the video downloader that caused the problem.

---

### Post by peddy on 2008-02-17
as you mentioned before, its only happening with some sites...youtube and [this](http://www.arthurdepins.com/petites_animsflash/Bg82.swf) (just stumbled upon it) seem to work. I wonder if its just random or what? Youtube has been working lately, but it didn't work before. o.O

---

### Post by peddy on 2008-02-17
Someone posted a bug report; This seems to be a very big problem. I hope it gets resolved quickly.

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/184157](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/184157)

---

### Post by impact on 2008-02-17
Same problem here. Is it caused by a plugin?

---

### Post by Kilz on 2008-02-17
> **peddy said:**
> Damn it feels good to not be alone ^^

Everything is working for me now, unfortunately I do not know what I did. Everyone else, try purging and reinstalling the official flash player. This may have to do with !flashissue (on the ubuntu IRC channel). I will check back here however if anyone wants any info from me.

Thanks Kilz and khensucat for you help. It is greatly appreciated.


edit: ok its not working anymore. Maybe the above info can shed some light.

Everything looks like it should with the official plugin install. But I find that plugin to not work a lot of the time or be real buggy. The r115 plugin is real bad. I recommend running my script for r48. But you may need to clean out these files first.
lrwxrwxrwx 1 root root      37 2008-02-16 21:25 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 apc  users     60 2008-02-16 19:51 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
lrwxrwxrwx 1 apc  users     61 2007-10-19 20:05 npwrapper.so -> ../../../../usr/lib/nspluginwrapper/x86_64/linux/npwrapper.so

---

### Post by Kikoolol on 2008-02-17
Kilz, things are solved for me using the script you provided in the sticky thread. 

I removed "flashplugin-nonfree" package using apt (even if I guess your script would have done this for me), then I ran your script to install flash r48 instead of the buggy r115 which was supplied in the "flashplugin-nonfree" package.

Thks a lot for your help :)

Kkl

---

### Post by khensucat on 2008-02-17
Good to hear!

As I said in post 2, using Kilz' script to revert to the older version seems to work like a charm every time ;-)

The problem with bug reports on Flash is that they can file them, but Flash isn't an Ubuntu or even an Open Source product - it's a proprietary program from Adobe, and *they* are the only ones who can officially fix it :confused:

---

### Post by peddy on 2008-02-17
> **Kikoolol said:**
> Kilz, things are solved for me using the script you provided in the sticky thread. 

I removed "flashplugin-nonfree" package using apt (even if I guess your script would have done this for me), then I ran your script to install flash r48 instead of the buggy r115 which was supplied in the "flashplugin-nonfree" package.

Thks a lot for your help :)

Kkl


just a question, do the flash player right-click context menus match with your system now? I know its a little thing, but I was just wondering if its only me.

Cheers

---

### Post by Kikoolol on 2008-02-18
Hi Peddy,

What do you exactly mean by saying "match with your system" ? I'll test that and give you a feedback this evening after work.

Kkl

---

### Post by Kikoolol on 2008-02-18
Peddy,

If I understood what you meant, you're right, the right-click menu does not match my system theme. And I'm pretty sure it was the case with r115 release. But I prefer flash working well even with an ugly menu :)

I Hope this answered your question !

Kkl

---

### Post by peddy on 2008-02-18
> **Kikoolol said:**
> Peddy,

If I understood what you meant, you're right, the right-click menu does not match my system theme. And I'm pretty sure it was the case with r115 release. But I prefer flash working well even with an ugly menu :)

I Hope this answered your question !

Kkl


I meant the old one (the stable one) doesn't match. The new one does. It sounds like you are saying that its the other way around? When I get home I will post screenshots. Here at school ubuntuforums.org is blocked so I have to use this crappy web proxy :P

---

### Post by Kikoolol on 2008-02-19
> I meant the old one (the stable one) doesn't match. The new one does.

Exactly.
r48 (old, stable) = doesn't match
r115 (last, unstable) = does match.

Cheers,

Kkl

---

### Post by peddy on 2008-02-20
Yeah, thats the way I see it too. A really weird thing is that the sound still works (if its flash content that automatically plays rather than you have to press start like in Youtube?)

This really sucks :P

---

### Post by Kilz on 2008-02-20
> **peddy said:**
> Yeah, thats the way I see it too. A really weird thing is that the sound still works (if its flash content that automatically plays rather than you have to press start like in Youtube?)

This really sucks :P

Feel free to voice your problems to Adobe. Flash is a closed source plugin. As such only Adobe can fix issues.

---

### Post by peddy on 2008-02-20
I will do that, and just btw I wasn't meaning this sucks in an angry way, in a mildy annoyed way. I have already switched to your wonderful script, its just I was so excited about the pretty context menus :P

Cheers, and thanks for the help.

---

### Post by Kilz on 2008-02-20
> **peddy said:**
> I will do that, and just btw I wasn't meaning this sucks in an angry way, in a mildy annoyed way. I have already switched to your wonderful script, its just I was so excited about the pretty context menus :P

Cheers, and thanks for the help.

I understand, I was just pointing out the place that the (even minor) complaints will do the most good.

---

### Post by peddy on 2008-02-21
Fix here: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/184157](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/184157)

Just remove and purge nspluginwrapper, and install the modified version. You may need to remove /usr/lib/nspluginwrapper (I had to do so manually), and you may need to reinstall flash player with apt-get install flashplugin-nonfree and your good to go. :)

---

### Post by Kilz on 2008-02-22
Can you see [this site? ]("http://www.mycokerewards.com/index.jsp#windowType:home")

---

### Post by peddy on 2008-02-22
Yep and the context menu looks fantastic.

---

### Post by Kikoolol on 2008-02-22
Same here, it works like a charm so far ... ;)

Thks !

Kkl

---

### Post by VvWolverinevV on 2008-02-22
> **peddy said:**
> Fix here: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/184157](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/184157)

Just remove and purge nspluginwrapper, and install the modified version. You may need to remove /usr/lib/nspluginwrapper (I had to do so manually), and you may need to reinstall flash player with apt-get install flashplugin-nonfree and your good to go. :)

Perfect!  I didn't even remove nspluginwrapper, just installed right over the existing version.  Will this automatically update via update manager when nspluginwrapper is next updated?

---

### Post by peddy on 2008-02-23
It will update, and I only uninstalled my old version of Nspluginwrapper because the fixed one wouldn't install because it thought the one I had already installed was a newer version. 


Cheers and w00tcakes!

---

### Post by Grone1985 on 2008-02-25
Thanks guys, works like a charm!

Cheers!

---

### Post by dwasifar on 2008-02-26
Had a similar problem with npviewer.bin going zombie on playing flash video.  Mostly the problem surfaced with Yahoo video.

Kilz' script solved it instantly.  Thanks Kilz!

---

### Post by Kilz on 2008-02-26
> **dwasifar said:**
> Had a similar problem with npviewer.bin going zombie on playing flash video.  Mostly the problem surfaced with Yahoo video.

Kilz' script solved it instantly.  Thanks Kilz!

Your welcome, Im glad some people have gotten flash to work by other methods. [But my script is still there for anyone who needs it. ]("http://ubuntuforums.org/showthread.php?t=476924")

---

