---
title: "NVU for 64-bit?"
date: 2007-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tanker Bob on 2007-04-20
Does anyone know of or have a 64-bit DEB for the NVU html editor?  I just switched over to 64-bit feisty today.  Overall, it works quite nicely, but NVU fails to install, receiving an error message that says there's a platform mismatch.  Can anyone help?

---

### Post by Kilz on 2007-04-20
> **Tanker Bob said:**
> Does anyone know of or have a 64-bit DEB for the NVU html editor?  I just switched over to 64-bit feisty today.  Overall, it works quite nicely, but NVU fails to install, receiving an error message that says there's a platform mismatch.  Can anyone help?

There is one in the repositories. Make sure you havwe the universe and multivers repositories enabled, then search for it in synaptic.

---

### Post by Tanker Bob on 2007-04-20
> **Kilz said:**
> There is one in the repositories. Make sure you havwe the universe and multivers repositories enabled, then search for it in synaptic.
I have both enabled, but NVU is not listed.

---

### Post by temna on 2007-04-20
I enabled everything in the repositories.  When I try Nvu, the listing is there but no one is home.  No version number, no description, nothing..  It does mention something about it's not being listed may mean it was EOL'ed or obsoleted or something. It's in the list, but more like a dead link. Can anyone help?  I tossed Frontpage on my Windows XP box because I love Nvu.  I want it back on my Ubuntu box. :eek:

---

### Post by Tanker Bob on 2007-04-20
Well, I got NVU to work under 64-bit feisty, but it probably wasn't the most elegant solution.  I downloaded the nvu-1.0.ubuntu.5.04.rpm file from the NVU website.  I then converted it to deb (first line installs alien if you don't already have it):

```

sudo aptitude install alien
sudo alien nvu-1.0.ubuntu.5.04.rpm

```

Then I forced the install with dpkg:

```

sudo dpkg --force-architecture -i nvu-1.0.ubuntu.5.04.deb

```

This came up with three broken libraray dependencies related to gnome: libbonobo2-0, libgnomevfs2-0, and libgnome2-0.  Since I'm running KDE with Kubuntu, I then used aptitude to install them:

```

sudo aptitude install libbonobo2-0 libgnomevfs2-0 libgnome2-0

```

Aptitude ended up installing a lot of libraries that these three apparently depend upon--a bunch of gnome-related libraries by the looks of the list.  At this point, I uninstalled then reinstalled NVU, although I could (probably should) have uninstalled it right after the first install failed:

```

sudo dpkg -r nvu
sudo dpkg --force-architecture -i nvu-1.0.ubuntu.5.04.deb

```

This worked like a champ.  NVU now works fine under 64-bit Kubuntu Feisty.  I'm a happy camper, and I hope that this helps others.

---

### Post by temna on 2007-04-20
Looks like you can skip a few steps just by downloading the Ubuntu 5.10 version of [Nvu]("http://www.nvu.com/download/nvu-1.0.ubuntu.5.04.deb")..  Just downloaded it and ran:  > sudo dpkg --force-architecture -i nvu-1.0.ubuntu.5.04.deb

Seems to work so far.  Still, seems like a pain to have to use an older version..

---

### Post by Tanker Bob on 2007-04-20
Yea, that works if you're running GNOME desktop.

Unfortunately, it looks like the "current" version of NVU may be the last version.  OTOH, it works fine for the most part.

---

### Post by temna on 2007-04-22
Wait, development has stopped on the best WYSIWYG editor out there???  Frack!

---

### Post by paul_banks on 2007-04-25
> **temna said:**
> Looks like you can skip a few steps just by downloading the Ubuntu 5.10 version of [Nvu]("http://www.nvu.com/download/nvu-1.0.ubuntu.5.04.deb")..  Just downloaded it and ran:  

sudo dpkg --force-architecture -i nvu-1.0.ubuntu.5.04.deb

Seems to work so far.  Still, seems like a pain to have to use an older version..

I couldn't find Nvu in my synaptic package manager either (multiverse and universe repositories enabled)...

So I downloaded and installed the deb file as per temna's instructions (thanks!). Now, when I try to run Nvu, it appears to load (shows up in taskbar for a few seconds), but then just disappears. I'm **very** new at this, so apologies if I'm missing something reeeally obvious! 

Also, what about Kompozer? I'm coming from Dreamweaver on xp, and have read that Kompozer is still under development after forking from Nvu, and doing quite well. Anyone with experience running it in Feisty 64?

---

### Post by mynona on 2007-04-25
> **paul_banks said:**
> I couldn't find Nvu in my synaptic package manager either (multiverse and universe repositories enabled)...

So I downloaded and installed the deb file as per temna's instructions (thanks!). Now, when I try to run Nvu, it appears to load (shows up in taskbar for a few seconds), but then just disappears. I'm **very** new at this, so apologies if I'm missing something reeeally obvious! 

Also, what about Kompozer? I'm coming from Dreamweaver on xp, and have read that Kompozer is still under development after forking from Nvu, and doing quite well. Anyone with experience running it in Feisty 64?


There is a AMD64 NVU-package in the edgy repos you can install and try. Here's the link:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvu&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvu&searchon=names&subword=1&version=edgy&release=all)

---

### Post by brian j on 2007-04-25
> **temna said:**
> Wait, development has stopped on the best WYSIWYG editor out there???  Frack!
Question Is the Nvu project still active?
    Answer Yes! Daniel Glazman is currently leading development on the next generation HTML editor. It is being completely redone to take advantage of new features in the Firefox development branch. For more information please visit our forums...[http://forum.nvudev.org/:](http://forum.nvudev.org/:))

---

### Post by paul_banks on 2007-04-25
> **mynona said:**
> There is a AMD64 NVU-package in the edgy repos you can install and try. Here's the link:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvu&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvu&searchon=names&subword=1&version=edgy&release=all)

Worked -- thanks!

... though I'm still curious to hear how Kompozer compares to this...

---

### Post by mynona on 2007-04-25
> **paul_banks said:**
> Worked -- thanks!

... though I'm still curious to hear how Kompozer compares to this...


There's no AMD64 Kompozer package, as far as I know. We all are waiting for the successor of NVU, which is mentioned in the post before.

---

### Post by Tanker Bob on 2007-04-29
> **mynona said:**
> There is a AMD64 NVU-package in the edgy repos you can install and try. Here's the link:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvu&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvu&searchon=names&subword=1&version=edgy&release=all)

Thanks for the link!  I uninstalled (purged) my forced 32-bit install and installed the 64-bit from the Edgy repository.  The first try I didn't purge and the 64-bit NVU didn't work when installed.  After purging the 32-bit version and deleting the program directory it worked fine.

I tried Amaya from the repository, but it's harder to use and a bit goofy.  I'll stick with NVU until its successor comes along.

---

### Post by master_kernel on 2007-09-14
There is also this: [http://ubuntuforums.org/showthread.php?t=551060](http://ubuntuforums.org/showthread.php?t=551060)

---

### Post by Tanker Bob on 2007-10-05
Kompozer 0.7.10 is out now, but only an i386 package at SourceForge. Anybody know if an i686 package is out somewhere? Google and Yahoo came up empty. Or can someone create a 64-bit deb?

---

### Post by dcstar on 2007-10-06
> **Tanker Bob said:**
> Kompozer 0.7.10 is out now, but only an i386 package at SourceForge. Anybody know if an i686 package is out somewhere? Google and Yahoo came up empty. Or can someone create a 64-bit deb?

Why?, just install that version with the architecture override:

```
sudo dpkg -i --force-a kompozer-0.7.10-i386.deb
```

I seriously doubt a 64 bit version of this particular app is going to perform any differently than the 32 bit version.

---

### Post by michael37 on 2007-10-06
Kompozer 64-bit deb package is available from getdeb.

I run it and it works great.

[http://www.getdeb.net/app.php?name=Kompozer](http://www.getdeb.net/app.php?name=Kompozer)

---

### Post by steveneddy on 2007-10-06
> **michael37 said:**
> Kompozer 64-bit deb package is available from getdeb.

I run it and it works great.

[http://www.getdeb.net/app.php?name=Kompozer](http://www.getdeb.net/app.php?name=Kompozer)

Cool - this worked great for me, also.

Thanks.

:popcorn:

---

