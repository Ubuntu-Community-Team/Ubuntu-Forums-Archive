---
title: "nspluginwrapper error"
date: 2008-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rog-Mahal on 2008-03-02
So I attempted to get flash to run using nspluginwrapper using Kilz's script found [here.]("http://ubuntuforums.org/showthread.php?t=476924&highlight=nspluginwrapper")

However, it failed to work. When I attempt to manually load the libflashplayer plugin, I get the following error.

```
roger@hephaestos:~$ nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: 1: Syntax error: word unexpected (expecting ")")
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so

```

Any ideas? It looks like nspluginwrapper has some kind of bug, but I don't know how it could have just stopped working.

I am running Gutsy 64 bit with a custom 2.6.24 kernel.

---

### Post by rmtatum on 2008-03-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/177856](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/177856) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I built a patched package for nspluginwrapper using the nspluginwrapper's author patch and the repository source packages.

Download the package at [https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/177856](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/177856)
and the diff file at [http://launchpadlibrarian.net/11055616/npw.gthreads.diff](http://launchpadlibrarian.net/11055616/npw.gthreads.diff)

---

### Post by Rog-Mahal on 2008-03-03
what do i download? and what should I do with the diff file?
It's probably also worth noting that I had this problem with both the 48 and 115 versions.
Sorry, I'm new to some of this stuff. Thanks for the reply though!

---

### Post by Rog-Mahal on 2008-03-05
*Bump* am I the only one who's experienced this?

---

### Post by Kilz on 2008-03-05
I have only see this error once before. [It was on this page posts]("http://ubuntuforums.org/showthread.php?t=476924&page=86") 852 and 853. The person who reported it also had a custom kernel. I have no idea how to fix the issue. But since the only 2 people with this error both had custom kernels I think it would be smart to start looking there.

---

### Post by Rog-Mahal on 2008-03-05
Thanks for the link. I guess I will start searching/asking if anyone has a fix for this. Maybe I'm missing something?

---

### Post by Kilz on 2008-03-05
> **Rog-Mahal said:**
> Thanks for the link. I guess I will start searching/asking if anyone has a fix for this. Maybe I'm missing something?

I wish you luck with finding it. Its a rare error. If you ever do figure it out please post the solution.

---

### Post by Rog-Mahal on 2008-03-06
Thanks. By the way, does your 32bit firefox install script run on gutsy? maybe I'll just give in and go with the 32 bit browser if it will solve my plugin woes. Honestly, gnash just doesn't cut it.

---

### Post by Rog-Mahal on 2008-03-06
Well, I've discovered something. It's not all custom kernels. I was able to successfully load the plugin on my 2.6.23 custom kernel. So there is something specific that must have happened between my build of the 2.6.23 and the 2.6.24. I used a someone else's config file for the .24 kernel instead of make oldconfig, maybe I can narrow it down further.

---

