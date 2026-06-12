---
title: "After update to 9.10 Firefox crash on startup"
date: 2009-11-04
forum: x86 64-bit Users
---

### Post by vukasin0 on 2009-11-04
Hi,

After upgrade from 9.04 x86_64 to 9.10 x86_64, I've lost my firefox at all -- it crashed during start.

Here is output from CLI when try to start:

```

ubuntu:~/Desktop$ firefox
Segmentation fault (core dumped)

```


This is from /var/log/messages
```

Nov  2 15:43:05 vukasin-t60 kernel: [29716.527336] firefox[950]: segfault at ffffffffa0762560 ip 00007f059c500679 sp 00007fff833c8d50 error 4 in libgobject-2.0.so.0.2200.0[7f059c4f1000+44000]
Nov  2 15:43:05 vukasin-t60 kernel: [29823.512112] firefox[1789]: segfault at ffffffff8ee62560 ip 00007f2c8ac00679 sp 00007fff0b151fd0 error 4 in libgobject-2.0.so.0.2200.0[7f2c8abf1000+44000]
Nov  2 15:43:05 vukasin-t60 kernel: [29838.638795] firefox[1906]: segfault at 51362560 ip 00007fcd4d100679 sp 00007fff55351b60 error 4 in libgobject-2.0.so.0.2200.0[7fcd4d0f1000+44000]
Nov  2 15:43:08 vukasin-t60 kernel: [29848.596587] firefox[1973]: segfault at 46162560 ip 00007fc541f00679 sp 00007fff295d61d0 error 4 in libgobject-2.0.so.0.2200.0[7fc541ef1000+44000]

```


Same happen to my friend - he updated his Kubuntu.

Seems that I have problem with "libgobject-2.0.so"

BTW - I've downloaded firefox from mozilla's site and it is working like a charm but without java support.

I've noted that eclipse crash with similar error related to  "libgobject-2.0.so".

Any idea - solution?

Thx,
Vukasin

---

### Post by bford16 on 2009-11-04
Actually I would suspect you have one or more bad plugins (or extensions).  What happens if you start firefox (in a terminal window) with the following command?```
firefox -safe-mode
```

---

### Post by vukasin0 on 2009-11-05
I've tried and noting changed:

```

vukasin@vukasin-t60:~/Desktop$ firefox -safe-mode
Segmentation fault (core dumped)

```

I'm using firefox binaries downloaded from mozilla's site and it is working with same profiles with which "ubuntu firefox" crash.

I think I have problem with "libgobject-2.0.so" because **eclipse** crash with similar error like firefox.

Yesterday I've noted that some libraries are not updated to newer version used by 9.10. When tried to install Virtual Box "Keramic Koala" precompiled, it dispaly error about version of libxml2(I have that lib in system). Solution - I've installed VBox Janty precompiled.

How can I see of which package is "libgobject-2.0.so" part ?


thx,
Vukasin

---

### Post by mission88 on 2009-11-05
I too am experiencing the segmentation fault with Firefox.

I actually started experiencing it earlier tonight on Jaunty. Update Manager offered me updates which included Firefox-3.5 (which was running as Shiretoko) and after those updates I could not run Firefox.

Since I run almost nothing else except VLC and Firefox, I decided to upgrade to 9.10 just in case it fixed it.

But same issue here.

I have completely removed and reinstalled Firefox tonight using, the Software manager, apt-get etc., and by manually deleting all of my Firefox folders under /usr/lib/ and again with each method I just mentioned.

I also tried to install Conqueror and I get a Segmentation fault with that as well.

---

### Post by mission88 on 2009-11-08
I have fixed my Firefox segfault (I had no known Gmail issue). I will say in advance that I had installed Firefox 3.5 as Shiretoko and late last week the Update Manager tried to upgrade Firefox... that was before (and the reason for) my 9.10 upgrade.

During the upgrade Karmic removed the install location from my sources. so I ran the following:

> sudo gedit /etc/apt/sources.list

and then I found the lines referencing

> intrepid-backports main restricted universe multiverse

uncommented them, and changed intrepid to karmic.

I also uncommented the line which read:

> deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main

Then I ran update manager and it found updates for Firefox. They fixed whatever issue was causing this.

---

