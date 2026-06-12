---
title: "Direct rendering is disabled"
date: 2011-07-26
forum: Wine
---

### Post by k1piee on 2011-07-26
Hi,

I just got myself an AMD Radeon HD6870, I installed the latest Catalyst drivers 11.6 64-bit and it workes just fine.

I had a Nvidia 9600 GT before this one and it worked just fine too.

However, with the Radeon HD6870 I can't seem to get World of Warcraft working as it should. I get this error message when I start it:

```
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
```

And the rendering looks like this:

[IMG]http://data.fuskbugg.se/skalman02/4e2ea646d5745_phpYnAYPQAM.jpg[/IMG]

I tried both the Wine version in the repos and the dev version 1.3.25 and got the same error.


I checked so that direct rendering actually was enabled and it is:

```
patricf@PatricF:~$ glxinfo | grep "direct rendering"
direct rendering: Yes

```

I've googled a bit but can't really find anything on the subject.
Has anyone else had this issue or maybe using the same card and got it working just fine?


Any help appreciated!


EDIT: I have also tried with deleting the .wine folder and run winecfg to create a new one but there where no change.
EDIT: I run Ubuntu 11.04 64-bit

---

### Post by jakejw93 on 2011-07-26
> **k1piee said:**
> Hi,

I just got myself an AMD Radeon HD6870, I installed the latest Catalyst drivers 11.6 64-bit and it workes just fine.

I had a Nvidia 9600 GT before this one and it worked just fine too.

However, with the Radeon HD6870 I can't seem to get World of Warcraft working as it should. I get this error message when I start it:

```
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
```

And the rendering looks like this:

[IMG]http://data.fuskbugg.se/skalman02/4e2ea646d5745_phpYnAYPQAM.jpg[/IMG]

I tried both the Wine version in the repos and the dev version 1.3.25 and got the same error.


I checked so that direct rendering actually was enabled and it is:

```
patricf@PatricF:~$ glxinfo | grep "direct rendering"
direct rendering: Yes

```

I've googled a bit but can't really find anything on the subject.
Has anyone else had this issue or maybe using the same card and got it working just fine?


Any help appreciated!


EDIT: I have also tried with deleting the .wine folder and run winecfg to create a new one but there where no change.
EDIT: I run Ubuntu 11.04 64-bit

Maybe, annoyingly enough - it wasn't the best choice card for Linux, I've heard about ATI not being too great In Linux..saying that I've only heard these rumours since I have myself stuck to Nvidia cards... I hope for your sake that it isn't because of the graphics card!!

---

### Post by k1piee on 2011-07-28
Yeah I know, I've always stayed with Nvidia cards due to the better drivers. However lately ATi have been getting better drivers so I thought I would try one and see. And I sometimes use this computer as an "Hackintosh", a regular PC with Mac OS X installed and it have better support for ATi card than Nvidia card.

Just checked ATi's site and they just released an update, 11.7, two days ago. I installed it and it work flawlessly now :)

I don't know if it's because of the different installation method I used or if the update fixed it.

I installed it using this:

```
sh ati-driver-installer-11-7-x86.x86_64.run --buildpkg Ubuntu/natty
```


Hope this can help someone else!

EDIT: Here's a link if someone want to check it out: [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

---

