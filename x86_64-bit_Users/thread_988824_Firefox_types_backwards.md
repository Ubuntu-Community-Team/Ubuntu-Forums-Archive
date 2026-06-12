---
title: "Firefox types backwards"
date: 2008-11-20
forum: x86 64-bit Users
---

### Post by Lucid 3ntr0py on 2008-11-20
So after upgrading to Ubuntu 8.10 x64 , my Firefox 64bit will suddenly start typing backwards after I open a new tab. Whether I ctrl+t or right click, it will still do it. What I mean by typing backwards is if I were to type animals it would come out as slamina .

I have sudo apt-remove and apt-get . I manually removed it. Nothing has helped. Any thoughts?

Thank you.

---

### Post by kostkon on 2008-11-20
> **Lucid 3ntr0py said:**
> So after upgrading to Ubuntu 8.10 x64 , my Firefox 64bit will suddenly start typing backwards after I open a new tab. Whether I ctrl+t or right click, it will still do it. What I mean by typing backwards is if I were to type animals it would come out as slamina .

I have sudo apt-remove and apt-get . I manually removed it. Nothing has helped. Any thoughts?

Thank you.
It appears that your page direction is being set from left-right to right-left every time you open a new tab or something like that.

Here is [a similar bug]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/34582"). You can try [disabling the *Switch Page Direction* option]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/34582/comments/14") and see if that will make a difference.

---

### Post by rhm on 2009-01-26
```
killall java
``` got it to type normally again for me, without restarting Firefox. 

It happened twice today, after visiting a site with a java applet. The applet would crash, I would close its tab on firefox and then everything I typed afterwards came out backwards, like this: *sdrawkcab*. The first time I tried to restart firefox unsuccessfully. It complained that it was already running and could not start until it was completely closed, so that was reboot number one.

A quick search for *Firefox typing backwards* suggested changing the page-direction options or reinstalling Firefox. I know I have seen the page-direction option in the context menu, but could not find it this time. Besides, the page layout remained unaltered and only the typing was backwards, so that got ruled out.

Another search for *Firefox typing backwards Ubuntu* yielded this bug: [http://icedtea.classpath.org/bugzilla/show_bug.cgi?id=263]("http://icedtea.classpath.org/bugzilla/show_bug.cgi?id=263"). In there they suggest killing the java process from within firefox. I went with ```
killall java
``` and that has worked wonders (so far), but there's bound to be a better, cleaner way.

Further research showed that this is a very old bug (see [http://forums.mozillazine.org/viewtopic.php?f=38&t=103510]("http://forums.mozillazine.org/viewtopic.php?f=38&t=103510")) and that java takes most of the blame for it (see [http://kb.mozillazine.org/Java#Java_applet_causes_backwards_or_jumbled_typing_in_text_boxes]("http://kb.mozillazine.org/Java#Java_applet_causes_backwards_or_jumbled_typing_in_text_boxes")).

Hope this helps whomever stumbles upon this problem.

---

### Post by BiynaYahu on 2009-02-14
bump

---

### Post by crazysubguy on 2009-03-03
I'm having the same problem here, whenever I launch a website that uses java everything has to be typed backwards. Once I close the java program and restart firefox then I'm Ok. Seems kind of silly. (I'm getting better at typing backwards though)

---

