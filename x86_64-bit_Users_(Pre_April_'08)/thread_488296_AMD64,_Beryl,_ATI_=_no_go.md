---
title: "AMD64, Beryl, ATI = no go"
date: 2007-06-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Neon8787 on 2007-06-30
Hey,

I've been looking through the forums for quite some time now trying to find a solution for my problem but there are plenty of terms I simply don't understand and many cases that are almost what I have happening but don't seem quite right.

Basically after sitting around one lazy afternoon watching videos on the internet I saw how good-looking linux could be with the help of Beryl. Being one with a short attention span this seemed like just the thing to keep me interested in linux long enough to learn how to use it properly.

Decided Ubuntu was the best choice for Linux, resized a partition and installed it right away. Enabled the drivers for my graphics card and installed Beryl as per their instructions and it doesn't appear to work. Every time I switch to beryl the screen will flicker and then it rolls back to the default window manager. If this is just an AMD64 thing I can easily install the x86 version and go from there. Somehow I get the feeling it's to do with my graphics card drivers. Many people have posted telling others to use some open-source drivers but after checking the compatibility list my card is not on it. Any help you can give with as little linux jargon as possible would be tremendously appreciated as this is an OS I have wanted to become familiar with for a long time and hope to learn more about soon.

Trying to run on following system:
AMD Athlon 64 X2 4200+
ATI Radeon X1950PRO
2GB RAM
Ubuntu 7.04

---

### Post by red_plague on 2007-06-30
I'm also trying the 64 bit, and from my previous Linux experience, i'll have to install a so called "xgl" xorg server, and it should work. Just make sure to have direct rendering enabled 
(open a terminal and type:
glxinfo | grep direct
it should return a line saying: direct rendering: Yes

still researching on how to install the xgl thingy

Edit: heey!, you got my system specs there, only i have 1Gram

---

### Post by red_plague on 2007-06-30
i got it running
folowed normal instalation procedures
stage 1:
[http://ubuntuforums.org/showthread.php?t=488385&highlight=install+xgl](http://ubuntuforums.org/showthread.php?t=488385&highlight=install+xgl)
also install gnome-compiz-manager, it's for configuring stuff
sudo apt-get install gnome-compiz-manager
i had problens related to:
```

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0

```
solved by loading compiz-manager as:
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa compiz-manager

---

### Post by GumbyX on 2007-06-30
Have you made sure that you are using the "fglrx" drivers instead of the "ati" drivers? Other then that, make sure you have the right packages installed.

At the moment, I am having my own set of problemns with my 64bit install, but I found this how-to very helpful when I installed beryl and XGL on my laptop:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

Hope that helps.

---

### Post by Neon8787 on 2007-07-01
Thanks red_plague and GumbyX

I've followed all the guides you directed me to and am now at the point where I'm sure the fglrx driver is installed (as I run fglrxinfo and get the correct results). Beryl is also installed but doesn't seem to work. One of the guides mentioned that if you start beryl-manager from a terminal window you can get some information so I did and got the following:

** (beryl-manager:7202): CRITICAL **: can't execute beryl-xgl: Success

Any ideas?

red_plague - I didn't install compiz-manager because I don't quite understand how to fix the problems you described... Is it really that necessary?

EDIT -- Realised the problem was due to the wrong version of beryl-core. Followed instructions on Beryl to downgrade but I get an error saying there is a size mismatch.

EDIT -- Nevermind that. Got some system updates and it downgraded just fine. Now I get a white screen when starting Beryl though. :( *sigh* Looking for a solution to that problem now... Seems some others had the same problem but with an older release.

---

