---
title: "Citrix ICA Client"
date: 2006-02-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by rastamufasta on 2006-02-01
Has anyone been able to get Citrix ICA Client working with Firefox on an amd64 pc?

I installed manually with setupwfc - I couldn't convert the rpm to a .deb package with my amd64 arch. I had to make some symbolic links for libXt.so and libXext.so to get firefox to run, but I'm still getting this error each time I start firefox:

LoadPlugin: failed to initialize shared library /usr/lib/ICAClient/npica.so [/usr/lib/ICAClient/npica.so: cannot open shared object file: No such file or directory]

npica.so is in /usr/lib/ICAClient and in /usr/lib/mozilla-firefox/plugins/

Any ideas?

I also tried manually opening with wfica.sh, but no luck there either.

Thanks

---

### Post by websavages on 2006-02-02
Nope, I'm having similar problems and am putting the cause down to the fact that the linux citrix client is 32 bit. Seeing that we are running 64 bit I'm guessing the client is a few bits short of a byte....

Cheer ws

---

### Post by Jonathan Knowles on 2006-02-08
Hi there

It is certainly possible to get the 32-bit ICA client working on a 64-bit Ubuntu system. It's a *bit* involved, but here's one nice way you can achieve this:

[LIST=1]
[*]Set up a 32-bit **chroot** environment, by carefully following the instructions [here]("http://tinyurl.com/c9odr").
[*]Install 32-bit Firefox within your new chroot environment, by following the instructions [here]("http://tinyurl.com/d8ejh").
[*]Download the latest 32-bit ICA client from the [Citrix download page]("http://tinyurl.com/8tvvu").
[*]From *within* your new chroot environment, run setupwfc as normal. Accept all of the default options, when prompted, including the default installation path.
[*]Your 32-bit Firefox should now have the 32-bit ICA client plugin installed. You can check this by looking in: Edit > Preferences > Downloads > Plugins.
[/LIST]
If the above steps are successful, you should now be able to launch apps from 32-bit Firefox.  :D 

Good luck!

Jonathan

---

### Post by jkroto on 2006-12-08
> **rastamufasta said:**
> Has anyone been able to get Citrix ICA Client working with Firefox on an amd64 pc?

Thanks

I was able to get it working without chroot, I wrote up how [here](http://www.ubuntuforums.org/showthread.php?p=1860514#post1860514).

---

### Post by Didjit on 2006-12-09
FYI, I use the 32 bit Swiftfox (Easy install by Automatix) and Citrix works fine. Havn't tried it FF 2.X

Didijit

---

