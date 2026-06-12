---
title: "Wine 2.3 on Ubuntu 16.04"
date: 2017-03-13
forum: Wine
---

### Post by Priswell on 2017-03-13
OK, I'm trying to install Wine 2.3 on a fresh install of Ubuntu 16.04. Funny thing is, I just did this on my laptop, and now the same procedure that worked before, isn't working.

```
sudo dpkg --add-architecture i386 
```

```
sudo add-apt-repository ppa:wine/wine-builds
```

```
sudo apt-get update
```

```
sudo apt-get install --install-recommends winehq-devel
```

```
sudo apt-get install wine
```

I've also tried:

```
sudo apt-get install wine2.3
```


I keep getting:

```
The following packages have unmet dependencies:
 wine : Depends: wine1.6
E: Unable to correct problems, you have held broken packages.

```

Can someone steer me in the right direction?

---

### Post by Priswell on 2017-03-13
OK, this matter has been resolved, but in a roundabout way. I went round and round installing and uninstalling the Wine repositories with corresponding updates, and installing and uninstalling Wine itself by way of the commandline. 

Then I went to the Software Center after making sure that the Wine repository was installed and found an entry for the Ubuntu package Wine 1.6 and a second one described as the Development Version of 1.9. I was trying to install version 2.3, but recalled reading in the Wine DB that the program I needed to run was doing well on version 1.9, so out of desperation, I installed this from the Software Center. After it was installed, I checked the version, and it reported as 2.3 from there, I installed my Windows program, and now all is well.

---

