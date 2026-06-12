---
title: "opera"
date: 2006-07-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by eleach on 2006-07-07
Is there a 64-bit version of Opera? I don't see one on the Opera site.

Can I make the i386 version (and plugins) work? how?

Thanks

---

### Post by hajk on 2006-07-08
There does not appear to be a 64-bit version of Opera to download. But it is perfectly possible to run a 32-bit version of Opera under AMD64 *provided* that you download/install the version of Opera 9 listed as "Other/Static DEB", which is basically a version compiled for the i386 OS with statically linked libraries. Install it with "sudo dpkg -i --force-architecture ....", and remember that it won't show up in Synaptic (because it's 32-bit).

As to 32-bit plugins (other than those already bundled with the above version) I can't help you.

---

### Post by Nicks Spleen on 2006-07-09
I use opera on my amd64 and love it. You have two options for installing it. Either you can use the static deb and live with the ugly fonts or you can istall ia32-libs-kde package and then you can use the ubuntu deb. I perfer using the ubunu deb. Either way you have to install using the --force-architecture option since they only make a 32bit opera. As for installing flash and other plugins, download them and read the readme. Normally you just have to drop a couple files in /usr/lib/opera/plugins. Flash for example you have to drop flashplayer.xpt and libflashplayer.so in the plugins directory.

---

### Post by hajk on 2006-07-09
> **Nicks Spleen said:**
> As for installing flash and other plugins, download them and read the readme. Normally you just have to drop a couple files in /usr/lib/opera/plugins. Flash for example you have to drop flashplayer.xpt and libflashplayer.so in the plugins directory.

Right, where do you get these 32-bit files from?

---

### Post by Kilz on 2006-07-09
> **hajk said:**
> Right, where do you get these 32-bit files from?
[Look here]("http://www.ubuntuforums.org/showthread.php?p=1174435#") Its my 32bit Firefox howto, but the Flash area will give you links to the installer, and how to install with it, just change the install location to the opera one above.

---

### Post by hajk on 2006-07-09
Thanks Kilz, that worked just fine. Nice HOWTO, are you going to add a plugin for QuickTime?

---

### Post by Kilz on 2006-07-09
> **hajk said:**
> Thanks Kilz, that worked just fine. Nice HOWTO, are you going to add a plugin for QuickTime?
I will try. I have been looking into adding other plugins. Im also thinking of writing it as a script.
Edit: Just added MPlayer-plugin, it playes quicktime.

---

