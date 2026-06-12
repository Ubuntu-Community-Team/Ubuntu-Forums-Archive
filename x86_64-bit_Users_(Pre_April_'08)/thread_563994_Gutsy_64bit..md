---
title: "Gutsy 64bit."
date: 2007-09-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Freddy on 2007-09-30
Hi all.

I just recently decided to try out Gnome and after using it since tribe5 of Gutsy Gibbon came out I decided to install the 64bit version off it on my new computer. The install went fine but after GRUB boots everything went black and I had to make a ctrl-alt-delete. Gutsy is going smooth on this machine with it's 32bit version but it's just no go with the 64bit version.

My specs are:
Amd X2 6000+
Asus M2N-MSI deluxe

Have anyone experiencing anything similar with Gutsy 64bit or is it just me? and what can I do about it.

/Freddy

---

### Post by Kilz on 2007-09-30
> **Freddy said:**
> Hi all.

I just recently decided to try out Gnome and after using it since tribe5 of Gutsy Gibbon came out I decided to install the 64bit version off it on my new computer. The install went fine but after GRUB boots everything went black and I had to make a ctrl-alt-delete. Gutsy is going smooth on this machine with it's 32bit version but it's just no go with the 64bit version.

My specs are:
Amd X2 6000+
Asus M2N-MSI deluxe

Have anyone experiencing anything similar with Gutsy 64bit or is it just me? and what can I do about it.

/Freddy
Sounds like a video card problem, did you report this on launchpad so it can be looked into and fixed? [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

---

### Post by Freddy on 2007-10-01
Yeah This was a already posted bug regarding usplash, when Gutsy 64 should show usplash in fails but it's still bootable with nosplash.

---

### Post by Anubis on 2007-10-01
I upgraded from Fiesty. In order to use the 2.6.22 kernel I had to safe boot because the new failsafe gdm X tool would not get me to desktop, although it does for my fiesty kernel, 2.6.20. So I just installed source, downloaded nvdia driver, and compiled it. Now I'm in Gutdy no problem. Gnome just starts my bottom panel late, I have to click the area where it should be. Nothing critical. Very nice.

---

### Post by Kilz on 2007-10-01
The thing is, anything like panels starting late, etc needs to be reported as a bug on launchpad. Testers should not pretend it doesn't matter.

---

