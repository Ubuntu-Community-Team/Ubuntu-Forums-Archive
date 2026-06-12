---
title: "Need help installing DOSBox 0.70 i386 deb on x86-64"
date: 2007-07-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by phoenix_fire2005 on 2007-07-28
Ok, I made a thread asking how to force install i386 deb packages on x86-64 ubuntu, and I was told to enter: sudo dpkg -i --force-architecture somethingi386.deb

Well, I tried this with a deb package of DOSBox 0.70 for Feisty i386 by entering:
> sudo dpkg -i --force-architecture dosbox_0.70-0~getdeb1_i386.deb
but I got this:
> dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 105060 files and directories currently installed.)
Preparing to replace dosbox 0.70-0~getdeb1 (using dosbox_0.70-0~getdeb1_i386.deb) ...
Unpacking replacement dosbox ...
dpkg: dependency problems prevent configuration of dosbox:
 dosbox depends on libsdl-net1.2; however:
  Package libsdl-net1.2 is not installed.
 dosbox depends on libsdl-sound1.2; however:
  Package libsdl-sound1.2 is not installed.
dpkg: error processing dosbox (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dosbox

The command seems to work fine, but I get errors during the install about some sort of dependencies that I'm assuming I need to install first, but I do not know how to do this. Any help would be appreciated.

On a side note, I am confused as to why ubuntu (and apparently other Debian-based distros) choose not to include 32-bit libraries on their 64-bit versions... it seems odd that they make you download and install them being as most 32-bit apps need them from what I can gather.

---

### Post by John.Michael.Kane on 2007-07-28
You can try the command below. it will install the the two dependencies.

```
sudo aptitude install libsdl-net1.2 libsdl-sound1.2
```

---

### Post by phoenix_fire2005 on 2007-07-28
> **SD-Plissken said:**
> You can try the command below. it will install the the two dependencies.

```
sudo aptitude install libsdl-net1.2 libsdl-sound1.2
```

Ok, the code seems to have worked, and I'm pretty sure DOSBox installed properly. However, it gives me this message when I try to run it (by typing dosbox in the terminal):
```
dosbox: error while loading shared libraries: libSDL_sound-1.0.so.1: cannot open shared object file: No such file or directory
```

This leaves me confused... is this some other dependency that wasn't reported by the deb installer?

---

### Post by Kilz on 2007-07-29
You are going to need the 32bit versions of those files, whenever you force install a i386 package you need 32bit libs. ia32 packages contain 32bit libs packaged for the 64bit os. You are in luck, there is a ia32-libs-sdl package. Never, ever, ever, ever force install a i386 library package.
```
sudo apt-get install ai32-libs-sdl
```
should install it.

---

### Post by amgeex on 2007-07-30
Yo dudes, isn't dosbox in the repos? I just give aptitude some action and boom, I got dosbox...

---

### Post by phoenix_fire2005 on 2007-07-30
> **amgeex said:**
> Yo dudes, isn't dosbox in the repos? I just give aptitude some action and boom, I got dosbox...

well, last i checked it was only ver 0.65, but i just checked today and found 0.70 and installed it, and it works! i never did get the i386 ver of 0.70 i downloaded working...

---

