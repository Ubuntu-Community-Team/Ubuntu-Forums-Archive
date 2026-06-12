---
title: "Going crazy... cannot install ia32-libs"
date: 2008-08-14
forum: x86 64-bit Users
---

### Post by kameleon25 on 2008-08-14
Just a short rundown... 64 bit system with 8.04 (upgraded from 7.10 2 days after release of 8.04) mythbuntu. I have had vmware running on this exact system before. It quit working one day a month or two ago. It has happened before and I usually just need to re-run the install wizard and all is good. This time it tells me I need to install ia32-libs. So I try to install that and this is what I get:

```
kameleon@sienna:~$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ia32-libs: Depends: lib32asound2 but it is not going to be installed
E: Broken packages
kameleon@sienna:~$ sudo apt-get install lib32asound2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  lib32asound2: Depends: libasound2 (= 1.0.15-3ubuntu4) but 1.0.16-0ubuntu0.1 is to be installed
E: Broken packages
kameleon@sienna:~$ sudo apt-get install libasound2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libasound2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kameleon@sienna:~$
```

I have tried all the posts I can find on the ia32-libs issue but all my repositories are correct as far as I can tell. I have another 64bit machine that I tried it's sources.list also. I would really like to get ia32-libs installed so I can reinstall vmware and not have to rely on my puny p3 machine anymore. Thanks in advance.

---

### Post by cariboo on 2008-08-14
Have you tried installing the ubuntu-restricted-extras package, this might install all the dependencies needed.

Jim

---

### Post by kameleon25 on 2008-08-14
Just tried that. No go. Still te same errors.

---

### Post by bpl07 on 2008-08-14
Try downgrading libasound2 to 1.0.15 first (Package>Force Version in Synaptic).  I had to do this before it would let me upgrade some things, including ia32-libs.  It'll eventually let you upgrade back to 1.0.16 after other dependencies get installed.

If the version isn't available through force version, get the [.deb file here.]("http://packages.ubuntu.com/hardy/libasound2")

---

### Post by kameleon25 on 2008-08-14
How do you force the version via apt-get. As I am not in front of the machine at the moment all I have access to is the command line. Thanks for the leads.

---

### Post by bpl07 on 2008-08-14
If that's the case then I would just download the .deb file and install with dpkg.
```

wget http://mirrors.kernel.org/ubuntu/pool/main/a/alsa-lib/libasound2_1.0.15-3ubuntu4_amd64.deb
```

```
sudo dpkg -i libasound2_1.0.15-3ubuntu4_amd64.deb
```

---

### Post by kameleon25 on 2008-08-14
WOOHOO!!! Thank you. I actually just found the wonderful aptitude ncurses style interface. I forced the downgrade to the previous version and then was able to install all the other things it needed. Sometimes we just need nudging in the correct direction. Thanks again.

---

### Post by Kilz on 2008-08-14
The reason you are having problems is possibly because you have proposed packages selected in the repositories.

---

