---
title: "Can't install wine1.7 from PPA"
date: 2015-10-29
forum: Wine
---

### Post by Fibonacci on 2015-10-29
Hello.

I tried to install wine1.7 from the WINE PPA on a fresh 15.10 install, and this was the result:

```
$ sudo apt-get install wine1.7
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.7 : Depends: wine1.7-amd64 (= 1:1.7.44-0ubuntu1) but it is not going to be installed
           Depends: wine1.7-i386 (= 1:1.7.44-0ubuntu1)
E: Unable to correct problems, you have held broken packages.
$ sudo apt-get install wine1.7-amd64
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.7-amd64 : Depends: libgphoto2-port10 (>= 2.5.2) but it is not installable
                 Depends: wine1.7:any (= 1:1.7.44-0ubuntu1)
                 Recommends: libgnutls26 but it is not installable
                 Recommends: wine-gecko2.34 but it is not installable
                 Recommends: wine-mono4.5.4 but it is not installable
E: Unable to correct problems, you have held broken packages.

```

What should I do here?

---

### Post by zerubbabel on 2015-11-02
I have the same problem, unable to install Wine 1.7 on a clean install of Ubuntu 15.10, and I have a single Windows application that I really depend on that won't run under Wine 1.6, so I hope for a way to get around this problem...

---

### Post by yoshii on 2015-11-02
I would consult the people at [http://wineHQ.com](http://wineHQ.com)

---

### Post by mJayk on 2015-11-03
Might not be the perfect fix but for now you can install wine1.7 using playonliux

---

### Post by Bucky Ball on 2015-11-03
Why are you using a third-party PPA? A version of Wine which has been tested for your release of Ubuntu is available in the repos (Software Centre). You have specific reasons for using 1.7?

[QUOTE=mJayk]Might not be the perfect fix but for now you can install wine1.7 using playonliux [/QUOTE]

Sure, which will drag in the Wine version in the repositories, as Playonlinux is a front-end for Wine and depends on Wine being installed, so it has to drag in Wine or have Wine installed in the first instance.

Which takes us back to the question: why use the PPA? Is 1.7 the version in 15.10 repos already? I'm on 14.04 so can't check easily.

---

### Post by zerubbabel on 2015-11-03
No, version 1.7 is not available in the Ubuntu repository, which is why I am using the third-party repository, as the application I need to run does not run on Wine 1.6, but only 1.7.

---

### Post by mJayk on 2015-11-03
> **Bucky Ball said:**
> Why are you using a third-party PPA? A version of Wine which has been tested for your release of Ubuntu is available in the repos (Software Centre). You have specific reasons for using 1.7?



Sure, which will drag in the Wine version in the repositories, as Playonlinux is a front-end for Wine and depends on Wine being installed, so it has to drag in Wine or have Wine installed in the first instance.

Which takes us back to the question: why use the PPA? Is 1.7 the version in 15.10 repos already? I'm on 14.04 so can't check easily.


There is a bug in the ubuntu 15.10 wine repo it will not install wine 1.7 from there, currently the version of win on 15.10 without the repo is 1.6x which is will wont let some programs run. So installing via the repo does NOT work however letting pol install wine1.7 does work. 


However you put it installing via pol works, installing via the wine repo does not.


Edit: link to bug [https://bugs.launchpad.net/ubuntu/+source/wine/+bug/1509159](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/1509159)

---

### Post by Fibonacci on 2015-11-05
> **mJayk said:**
> There is a bug in the ubuntu 15.10 wine repo it will not install wine 1.7 from there, currently the version of win on 15.10 without the repo is 1.6x which is will wont let some programs run. So installing via the repo does NOT work however letting pol install wine1.7 does work. 


However you put it installing via pol works, installing via the wine repo does not.


Edit: link to bug [https://bugs.launchpad.net/ubuntu/+source/wine/+bug/1509159](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/1509159)

I don't think the PPA maintainers read the Launchpad bugs, but at least I know I'm not the only one experiencing this. Should someone tell the WINE team?

---

### Post by mc4man on 2015-11-05
This may just be a matter of the 15.10 build being copied from a trusty build in another wine testing ppa. I believe that method doesn't due a rebuild so it has  trusty's libgphoto2-port10 as a dep/ldd instead of the version in 15.10, libgphoto2-port12
If that's the case then simply doing an actual build would suffice, a few minutes time to put up.

---

### Post by brianr2 on 2015-11-05
It doesn't look like the wine team is maintaining that PPA any longer. There hasn't been any activity is some time.

---

### Post by zerubbabel on 2015-11-06
So should I be able to build Wine 1.7 from source on Ubuntu 15.10, in spite of the missing dependencies?

---

