---
title: "Apt-get/Synaptic problems"
date: 2006-03-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by RedeyesUK on 2006-03-28
Hi there,

Sorry if this is a newbie question, or if it has been anwered before (I did a search and couldn't find it), but whenever I run apt-get for anything, I get this output:

```
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Running update (as suggested) doesn't solve it, and I've tried a few other options as well, but nothing seems to clear it. Running Synaptic produces the same error.

Firstly, is this a problem, or something I don't need to worry about? Secondly, how do I clear these warnings? Even if there's no real problems, it'd be nice to get rid of these.

Thanks in advance!

---

### Post by endersshadow on 2006-03-28
[QUOTE=RedeyesUK]Hi there,

Sorry if this is a newbie question, or if it has been anwered before (I did a search and couldn't find it), but whenever I run apt-get for anything, I get this output:

```
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Running update (as suggested) doesn't solve it, and I've tried a few other options as well, but nothing seems to clear it. Running Synaptic produces the same error.

Firstly, is this a problem, or something I don't need to worry about? Secondly, how do I clear these warnings? Even if there's no real problems, it'd be nice to get rid of these.

Thanks in advance![/QUOTE]

Hopefully you're running sudo apt-get update instead of just apt-get update, but I'll assume that you are.  Otherwise, quite simply, the repositories you're requesting are down.  To correct this (on your end), do this:

```
sudo gedit /etc/apt/sources.list
```

Next add a # in front of these lines:

```
deb http://antesis.freecontrib.org breezy/free Packages
deb http://antesis.freecontrib.org breezy/non-free Packages
deb-src http://antesis.freecontrib.org breezy/free Packages
deb-src http://antesis.freecontrib.org breezy/non-free Packages
```

So it looks (something) like this:

```
#deb http://antesis.freecontrib.org breezy/free Packages
#deb http://antesis.freecontrib.org breezy/non-free Packages
#deb-src http://antesis.freecontrib.org breezy/free Packages
#deb-src http://antesis.freecontrib.org breezy/non-free Packages
```

I'm not sure if PLF has another repository available, but you can check them out at [http://plf.zarb.org/](http://plf.zarb.org/)

---

### Post by RedeyesUK on 2006-03-28
Excellent, that worked perfectly. Thanks for that!

Funnily enough, I was just looking at that file earlier, and it didn't occur to me that that might fix it!](*,) 

Oh well, live and learn....:D

[QUOTE="endersshadow"]I'm not sure if PLF has another repository available, but you can check them out at [http://plf.zarb.org/](http://plf.zarb.org/)[/QUOTE]

Following the links in sources.list, it seems they've taken the AMD64 repository down. There's still an i386 equivalent, though.

---

### Post by endersshadow on 2006-03-28
Glad I could help :-D

---

