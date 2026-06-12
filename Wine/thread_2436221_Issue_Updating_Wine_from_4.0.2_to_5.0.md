---
title: "Issue Updating Wine from 4.0.2 to 5.0"
date: 2020-02-02
forum: Wine
---

### Post by 151mp137471n on 2020-02-02
.Hello community. 

Today I updated Wine from 4.0.2 to 5.0, but when I run **wine --version** I get this:
```
wine-4.0.2 (Ubuntu 4.0.2-1)
```

I have this on my **sources.list**, just for reference
```
deb https://dl.winehq.org/wine-builds/ubuntu/ eoan main
deb-src https://dl.winehq.org/wine-builds/ubuntu/ disco main

```

Just so you know, I had to manually install **wine-stable-amd64** to update **wine-stable**, because apt told me it was held.
I'm preety sure the issue is coming from either manually installing a package that was held or because of having Windows apps installed on the Wine Prefix.
I don't want to delete the **.wine32 **and** .wine** prefixes before hearing some new ideas while I try to wrap my head around this. 
Of course I can make a backup and nuke the prefixes to test if this is the case, but I'm not in a rush.

Attached is a screenshot of the final steps of installing **wine-stable **(after installing **wine-stable-amd64**), and the output of **wine --version**.

Thanks in advance!

---

### Post by thehipho on 2020-02-05
Hi, you could see where it's installed:  ```
 whereis -b wine
``` Or which ver. ```
 which -a wine
```

---

### Post by 151mp137471n on 2020-02-11
Thanks. I decided to go with the development version (**4.17**) fomr the winehq repo. I was really just curious because I just use wine to play a couple of games I'm hooked for life and as long as they run well, I'm ok.
I was just wondering why were there two versions of wine installed on my system, but nevermind, thanks again.

-**7471n**

---

### Post by thehipho on 2020-02-11
> Thanks. I decided to go with the development version (**4.17**) fomr  the winehq repo. I was really just curious because I just use wine to  play a couple of games I'm hooked for life and as long as they run well,  I'm ok.I was just wondering why were there two versions of wine installed on my system,


Glad you figured it out! You had two versions installed, they're different sources.

There's also **PlayOnLinux**, it install Windows games, IE, as well as many others.

---

### Post by mastablasta on 2020-02-13
> **thehipho said:**
> Glad you figured it out! You had two versions installed, they're different sources.

There's also **PlayOnLinux**, it install Windows games, IE, as well as many others.

And Proton (found on Steam) and Lutris and...

anyway i too find it easier if there is a GUI. especially to handle the various versions available.

---

