---
title: "[SOLVED] ATi drivers... which version I have?"
date: 2008-05-11
forum: x86 64-bit Users
---

### Post by WenSes on 2008-05-11
Hello everyone, I have a question for all u good wise people:

How do I know which version of ati drivers I have? since I installed ubuntu (7.10) I only had accepted to use the restricted drivers to be able to have 3d acceleration. After having some time in this forum and others I have noticed about differences about drivers, specially on versions...

So... How do I know the version of it? 

And also, which version do you recommend to have installed? I've read that the latest version it's not the best, it's that true?

finally, if you have a thread or page with instructions about installing them I would be really thankful.

Hoping you can help e in order to have better 3d... see ya all!

---

### Post by shane2peru on 2008-05-11
> **WenSes said:**
> Hello everyone, I have a question for all u good wise people:

How do I know which version of ati drivers I have? since I installed ubuntu (7.10) I only had accepted to use the restricted drivers to be able to have 3d acceleration. After having some time in this forum and others I have noticed about differences about drivers, specially on versions...

So... How do I know the version of it? 

And also, which version do you recommend to have installed? I've read that the latest version it's not the best, it's that true?

finally, if you have a thread or page with instructions about installing them I would be really thankful.

Hoping you can help e in order to have better 3d... see ya all!
 
Hey, I just did this for my wife's computer.  You need to search for envy in synaptic, and install the gtk version if you are using Gnome, if you have Kubuntu, you want the envy-qt version.  After it gets installed, you can open the terminal: Applications ->  Accessories ->  Terminal  and type:  sudo envy-gtk  That will start an automatic install process.  I'm not 100% sure of the name I'm going off memory here, if you type envy- then hit the tab it should complete it for you, or show you what options are available.  Any questions post back, I'm sure someone more knowledgeable than me can help. :)

Shane

---

### Post by jocko on 2008-05-12
No, don't install envy.
To see what version of ati's driver you use, try the command:
```
fglrxinfo
```
If you use xgl, you may only see mesa instead of the correct driver, so try:
```
fglrxinfo -display :1
```
or
```
fglrxinfo -display :0
```

If you installed the driver from the repo or by building packages yourself, you will find the installed packages in synaptic.

The version in the gutsy repos is 8.37.6. fglrxinfo will report it like this:
```
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 1.2 (2.0.6473 ([COLOR=Red]8.37.6[/COLOR]))
```

My advice if you're still using gutsy is to stay with version 8.37.6, as the newer drivers (8.41.7 and later) still haven't reached the quality of the old ones (in my opinion).

---

### Post by WenSes on 2008-05-12
Thxs everyone! I used jocko's way and I'll be following that recommendation... but still my 3d is crappy... now I'm only hoping that drivers improve...

C-ya and thxs again!

---

### Post by shane2peru on 2008-05-12
> **jocko said:**
> No, don't install envy.
To see what version of ati's driver you use, try the command:
```
fglrxinfo
```
If you use xgl, you may only see mesa instead of the correct driver, so try:
```
fglrxinfo -display :1
```
or
```
fglrxinfo -display :0
```

If you installed the driver from the repo or by building packages yourself, you will find the installed packages in synaptic.

The version in the gutsy repos is 8.37.6. fglrxinfo will report it like this:
```
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 1.2 (2.0.6473 ([COLOR=Red]8.37.6[/COLOR]))
```

My advice if you're still using gutsy is to stay with version 8.37.6, as the newer drivers (8.41.7 and later) still haven't reached the quality of the old ones (in my opinion).

Is envy bad?  I just installed it to get the ATI drivers on my wife's machine working correctly, and keep it from locking up the computer.  :)  I honestly don't know much about setting up this ATI stuff, that is just what someone told me on IRC.  It seems to be working so far.  Talking in the Hardy realm here. 

Shane

**EDIT:** What about getting the drivers directly from the ATI page for Linux?

---

### Post by jocko on 2008-05-12
> **shane2peru said:**
> Is envy bad?  I just installed it to get the ATI drivers on my wife's machine working correctly, and keep it from locking up the computer.  :)  I honestly don't know much about setting up this ATI stuff, that is just what someone told me on IRC.  It seems to be working so far.  Talking in the Hardy realm here. 

Shane

**EDIT:** What about getting the drivers directly from the ATI page for Linux?

My main reason for advicing him not to install envy was because he asked how he can know which version he already have installed, not for a method to install the latest.

Envy is "bad" (in my opinion) because it installs drivers directly from ati's website instead of from the repo.
This may be good for someone who really want to use the latest driver, but a far easier and safer method is to use the restricted driver manager and let it install and configure the driver from the repo.
A driver installed from ati's installer will break when the kernel is updated and will need to be reinstalled by running envy from the command line, whereas a driver installed from the repo will always be updated together with the kernel, so it's less likely to break.
Another reason to stay with the repo driver (in gutsy) is because the newer versions are not as good as the version in the gutsy repos (at least not if you want to have xvideo overlay and decent TVout or dual screen functionality).

In hardy there's no real point in using envy (yet), as there are no big differences between the one in the hardy repos (Catalyst 8.3) and the latest from ati (Catalyst 8.4) (you can find the release notes on ati's driver download page to see that they just fixed a few minor bugs but did not fix any of the serious issues).

Much of this is of course my personal opinion, based on my experiences, so everyone is of course allowed to make up their own mind.

---

### Post by shane2peru on 2008-05-12
> **jocko said:**
> My main reason for advicing him not to install envy was because he asked how he can know which version he already have installed, not for a method to install the latest.

Envy is "bad" (in my opinion) because it installs drivers directly from ati's website instead of from the repo.
This may be good for someone who really want to use the latest driver, but a far easier and safer method is to use the restricted driver manager and let it install and configure the driver from the repo.
A driver installed from ati's installer will break when the kernel is updated and will need to be reinstalled by running envy from the command line, whereas a driver installed from the repo will always be updated together with the kernel, so it's less likely to break.
Another reason to stay with the repo driver (in gutsy) is because the newer versions are not as good as the version in the gutsy repos (at least not if you want to have xvideo overlay and decent TVout or dual screen functionality).

In hardy there's no real point in using envy (yet), as there are no big differences between the one in the hardy repos (Catalyst 8.3) and the latest from ati (Catalyst 8.4) (you can find the release notes on ati's driver download page to see that they just fixed a few minor bugs but did not fix any of the serious issues).

Much of this is of course my personal opinion, based on my experiences, so everyone is of course allowed to make up their own mind.

Thank you for giving me this info.  I know very little about the ATI drivers world.  I didn't realize he was using Gutsy. :)  Missed that part.  In Hardy, I had installed the ubuntu-restricted driver for ATI and my wifes computer crashed anyway.  In IRC I was advised to use the envy, seemed like an easy quick setup for me.  I will be aware of kernel updates, I wouldn't have known that.  :)  Thanks for the info, it was very informative, and I appreciate you taking the time to explain it to me.  

Shane

---

