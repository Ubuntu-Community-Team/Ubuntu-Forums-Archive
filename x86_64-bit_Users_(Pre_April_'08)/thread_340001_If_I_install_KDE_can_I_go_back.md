---
title: "If I install KDE can I go back?"
date: 2007-01-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by cocteau on 2007-01-16
Hi

I've tried searching the forums for an answer, but nothing that applies directly seem to come up.

I'm having half a mind to install the kubuntu-desktop meta-package, in order to try out at few KDE programs, like Kate and Kdevelop. However, if I install the whole KDE shebang is there a safe way to go back if I should decide to?

Alternatively is there a way to install just the kde libs required to run these programs and safely remove them again if I choose to?

---

### Post by kimera99 on 2007-01-16
As I think, there won't be any problem with having both GNOME and KDE, since each use its libs, and you can choose your desktop while logging in

---

### Post by floke on 2007-01-16
That's right. Just 'sudo apt-get install kubuntu-desktop' (there's also an option for 'kde-core' in the repos, I think - but never tried that one) - and voila, you will have both KDE and Gnome. Once you've done that, then logout, and from the login screen select the option for sessions, you can now choose which one to use.

There are a few other desktops you can try if you get curious, including XFCE, Enlightenment, and Blackbox (amongst others).

You can always remove them later if you don't like them.

The one issue that some people have had with installing KDE on ubuntu is that is changes the splashscreen for the bootup to 'Kubuntu' (rather than Ubuntu), though you can also get rid of this - don't remember how but its here on the forum somewhere.

Good luck

---

### Post by Extreme Coder on 2007-01-16
I'd suggest installing KDE by using
```
 sudo aptitude install kubuntu-desktop #you can replace kubuntu-desktop with kde-core 
```
because then, if you use this command, you can remove KDE by using
```
 sudo aptitude remove kubuntu-desktop #same case here 
```

Extreme Coder

---

### Post by cocteau on 2007-01-17
Thanks.

KDE-core is being installed now :)

---

