---
title: "How to recover from this? Think I screwed my Ubuntu."
date: 2007-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by pokechu on 2007-03-13
When I was trying to install the latest GAIM 2.0.0 beta6, I tried looking for the net and downloaded .deb packages from other sources, some of them are newer versions than the Ubuntu ones.  While installing one of the dependency packages for GAIM, it shows some error and asks me to do

> sudo apt-get -f install

so that I could fix it. But after doing it in the terminal it still gives me this error.

The following packages have unmet dependencies:
  libfontconfig1: Depends: fontconfig-config (= 2.3.2-7ubuntu2) but 2.4.2-1.2 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

I tried opening Synaptics and Synaptic says the package is broken and it needs to be reinstalled, however, when I mark it for reinstallation, it says I have to remove around 220 packages that depended on it. It includes all the major programs. I'm afraid I can't get my system back if I remove all of them which are 780 mb in total. I don't wanna reinstall Linux!!

So, anyway to fix this? BTW, I'm a Linux newb, just started using Ubuntu or Linux one week ago. Hah, that's why I screwed this up.

---

### Post by solar george on 2007-03-13
While you are new to ubuntu you should stick with the packages in synaptic/apt. 

Try uninstalling the package in synaptic.

---

### Post by John.Michael.Kane on 2007-03-13
You can try these steps.

Try to configure all packages that are un-configured :
```
sudo dpkg --configure -a
```



Try to let apt-get remove all problematic packages automatically :
```
 sudo aptitude -f remove
```

Rerun this after running the command above:
```
sudo dpkg --configure -a
```

---

### Post by mixium on 2007-03-13
> **SD-Plissken said:**
> You can try these steps.

Try to configure all packages that are un-configured :
```
sudo dpkg --configure -a
```



Try to let apt-get remove all problematic packages automatically :
```
 sudo aptitude -f remove
```

Rerun this after running the command above:
```
sudo dpkg --configure -a
```

Nice tip.

:)

Michael

---

### Post by pokechu on 2007-03-14
Thanks for the help. It works. It's people like you who made the Ubuntu experience much more pleasant. Thanks! Will probably have more questions or problems in the future. Hah.

---

### Post by agamotto on 2007-03-14
You would be very rare if you didn't!

---

