---
title: "&quot;Upgrade&quot; to 64 bit"
date: 2009-07-19
forum: x86 64-bit Users
---

### Post by blazemore on 2009-07-19
I'm running 32 bit Jaunty, and have just installed 4gb RAM.
Now obviously I need the 64 bit Jaunty.
I'm fairly proficient at Linux and Debian/Ubuntu in particular, but I'd like to check if it is possible to add 64 bit repos to my sources.list, and do some kind of dist-upgrade.
I understand I'd need new graphics card drivers, but would any other problems arise? The new 64 bit kernel should just drop in, right?

---

### Post by SuperSonic4 on 2009-07-19
In theory yes although I don't know how it would work in practice. You may have to force upgrade the kernel though

---

### Post by darco on 2009-07-19
> **blazemore said:**
> I'm running 32 bit Jaunty, and have just installed 4gb RAM.
Now obviously I need the 64 bit Jaunty.
I'm fairly proficient at Linux and Debian/Ubuntu in particular, but I'd like to check if it is possible to add 64 bit repos to my sources.list, and do some kind of dist-upgrade.
I understand I'd need new graphics card drivers, but would any other problems arise? The new 64 bit kernel should just drop in, right?

It would be only "obvious" if you had MORE than 4gb of memory ;)

Clean upgrade is the only way to go...you will have x32 libraries possibly causing conflicts w/you x64 bit libraries....

darco

---

### Post by blazemore on 2009-07-19
> **darco said:**
> It would be only "obvious" if you had MORE than 4gb of memory ;)

Clean upgrade is the only way to go...you will have x32 libraries possibly causing conflicts w/you x64 bit libraries....

darco


I think you're misunderstanding. A 32 bit OS can only address 4294967295 (2 ^ 32 - 1) bytes (4gb) of memory... INCLUDING GRAPHICS CARD MEMORY.
In binary, that's 11111111111111111111111111111111. So to have 1 more byte would be 100000000000000000000000000000000, requiring an extra bit.
I have 1gb graphics card memory.

Anyway that's not the point. I was just wondering what else to expect breakage in.
RE: the libraries, would not adding the 64 bit repos replace the existing libs?

---

### Post by bedtime_with_the_bear on 2009-07-19
> **blazemore said:**
> RE: the libraries, would not adding the 64 bit repos replace the existing libs?

No, If you could replace everything in one go, then maybe, just maybe it would work without a problem - however, you simply can't do that. each application, library, package would be replaced one after another with the 64 bit version. It won't take long before you've replaced a critical system library with the 64 bit version before you have 64 bit support elsewhere (the kernel for example) and then everything would come crashing down hard and you'll be left with the only option remaining - a clean install. Of course, dpkg will be 32-bit, and completely unable to use the shiny new 64-bit libraries, so you wouldn't even have the option of reverting to 32-bit.

With a 32-bit kernel, you cannot run 64-bit code at all. Once glibc or libstdc++ is replaced with the 64-bit version, no dynamically linked executable on your system will function. At all. Note, this includes all the package management tools, ls, even poweroff so you can't even gracefully shutdown your system (ldd `which exename` will tell you what libraries you need).

However, replace the kernel first, and you'll have no 64-bit libraries available so you won't be able to boot either.

Plus, I'm not certain but it seems reasonable to me that dpkg wouldn't even allow you to install incompatible packages on a dist-upgrade. Sure, you could install them manually and force the architecture, but you'll still have the problems I mention above.

Maybe, just maybe, you can boot from a live CD and install the new 64-bit packages that way, but I don't think you would really want to try that and besides, the consequences of missing even just one package could be quite severe if it's a critical package. Even if you did, then you're no better off than a clean install anyway

Unfortunately, the only sane option is to backup your data and do a clean install like darco recommends.

---

### Post by blazemore on 2009-07-19
Okay I have a separate /home partition. I'm going to back up /var/cache/apt/archives as well, to save bandwidth on updates/installations.
How can I get a list of packages installed on my system, to aid easy reinstall?

---

### Post by lisati on 2009-07-19
Being to lazy to research alternatives, I'd probably go for the Backup data->clean install of OS and applications->Restore data approach.

Edit: due to a momentary lapse, I forgot about PAE. Thanks, Temüjin!

---

### Post by Yellow Pasque on 2009-07-19
Those are all i386 packages in /var/cache/apt/archives, so it wouldn't help you anyway.

If you just want more addressable RAM, try a kernel with PAE rather than redoing your whole system.

---

### Post by bedtime_with_the_bear on 2009-07-19
To get the list:

dpkg --get-selections > ~/pkgs.txt

To restore after you've done the clean install:

apt-get update
cat ~/pkgs.txt | dpkg --set-selections
apt-get -u dselect-upgrade

The list you will get only contains the package name, so you'll get the 64-bit version where possible after the install.

You should also make sure you install at least ia32-libs too after you've installed 64-bit Ubuntu - they're the 32-bit compatibility libraries and you won't be able to run 32-bit code without them.

---

### Post by blazemore on 2009-07-19
Can someone tell me more about PAEx?

---

### Post by bedtime_with_the_bear on 2009-07-20
Take a look at [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

