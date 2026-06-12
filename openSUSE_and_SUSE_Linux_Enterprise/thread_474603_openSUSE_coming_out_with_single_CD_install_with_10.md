---
title: "openSUSE coming out with single CD install with 10.3"
date: 2007-06-15
forum: openSUSE and SUSE Linux Enterprise
---

### Post by igknighted on 2007-06-15
OpenSUSE is now coming out with 2 single CD installers (one for gnome, one for KDE).  I'm not sure if they are live CDs or not, but it certainly is a break for those who do not want a whole DVDs worth for the installer.

---

### Post by Erunno on 2007-06-17
Good stuff. Maybe people will be more inclined now to give openSUSE a try and maybe realize that K/Ubuntu is not the end of all things when it comes to highly polished distributions (actually, it's far away from it).

---

### Post by karellen on 2007-06-18
[http://lists.opensuse.org/opensuse-announce/2007-06/msg00004.html](http://lists.opensuse.org/opensuse-announce/2007-06/msg00004.html)
yes...they say both cd's contain a small desktop, then the rest of apps can be downloaded if a network connection can be established. sound nice, it's easy to work with 1 cd then with 5/6

---

### Post by 67GTA on 2007-07-05
I just tried the alpha 5 version last night. It is not a live cd(bummer). It basically installs a base system without the bloat. This might cause them to climb the distrowatch ladder. If they would change to Synaptic(I hate Yast), and have a wizard for installing ATI/Nvidia drivers, I would use Suse.

---

### Post by Erunno on 2007-07-06
> **67GTA said:**
> I just tried the alpha 5 version last night. It is not a live cd(bummer). It basically installs a base system without the bloat. This might cause them to climb the distrowatch ladder. If they would change to Synaptic(I hate Yast), and have a wizard for installing ATI/Nvidia drivers, I would use Suse.

1 CD distributions have their own share of problems as evidenced by Ubuntu itself. How often ideas get rejected because there's not enough space on the CD? Desktops tend to become larger due to various factors (artwork, functionality etc) and space can quickly become a restriction to innovation.

I don't know any plans about changing to Synaptic but the developers are working on improving zypper for 10.3 and package management in general.

As for a convenient way to install drivers (and some other things):

[http://www.kde-apps.org/content/show.php?content=43378]("http://www.kde-apps.org/content/show.php?content=43378")

---

### Post by igknighted on 2007-07-07
> **67GTA said:**
> I just tried the alpha 5 version last night. It is not a live cd(bummer). It basically installs a base system without the bloat. This might cause them to climb the distrowatch ladder. If they would change to Synaptic(I hate Yast), and have a wizard for installing ATI/Nvidia drivers, I would use Suse.

1) There is already a net install, plus you can do a ground-up barebones install from the CD set or the DVD.  This one CD install is nice, but really not a big deal for me.  I will use the DVD anyways as I prefer to custom pick the packages I install.

2) Synaptic is available, as is smart.  Just install the package manager you prefer.  If you want CLI package management tools, the command is 'zypper'.

3) Suse handles the nvidia drivers better than any other distro (even those that pre-install it).  You add the nvidia repo (available on the opensuse page with the other add-on repos), and then install the driver (clearly labeled in yast/synaptic/smart).  The Sax2 application tweaks the driver to perfection and sets up monitor resolution and refresh rates (plus xinerama and more) in a friendly GUI.  Plus unless you start compiling your own kernel the kernel modules are more reliable than other distro's (it's packaged by nvidia directly).  ATI works similarly to nvidia, although I don't use it so I cannot officially vouch for it.

Look closer, because if these are your main complaints about Suse, I think they are very easily taken care of and you may want to reconsider suse.

---

### Post by benx009 on 2007-07-21
Wow, finally, just one CD!!! It's about time.  I never really liked all the "bloatware" that came with Opensuse (I used v.10.1).  Ten programs all to do the same thing.  It just got annoying after a while, as all my application menus were crowded w/ items.  I love Opensuse (it beats Ubuntu in a lot of ways) so I will try my best to support this.

---

### Post by LuisAugusto on 2007-07-21
I'll probably complete migrate to OpenSuSE 10.3 (I use alpha 5 as my main OS xD) or Fedora 8.
Ubuntu is not inovating, while OpenSuSE is (and Fedora will use KDE 4 as default).

And the new YaST is sooo fast at search, and is working pretty fine in apha 5 (i didn't upgrade to alpha 6 yet).

And, of course, YaST Control Center is the best configuration tool on any distro.

The reason that keep me having Ubuntu installed is THE COMUNITY REPOSITORIES, they're so big, they let me use my time in other stuff instead of compile, or look on rpm search.

---

### Post by RedDwarf on 2007-07-22
> **LuisAugusto said:**
> And the new YaST is sooo fast at search, and is working pretty fine in apha 5 (i didn't upgrade to alpha 6 yet).
Well, the new libzypp was not integrated until alpha6...

> **LuisAugusto said:**
> The reason that keep me having Ubuntu installed is THE COMUNITY REPOSITORIES, they're so big, they let me use my time in other stuff instead of compile, or look on rpm search.
[http://packages.opensuse-community.org/](http://packages.opensuse-community.org/)

---

### Post by Amphios on 2007-07-22
I would like to know how the KDE/GNOME dependencies are handled when installing the KDE/GNOME 1 CD. In the current distribution 10.2, there are KDE and GNOME libraries mixed up. I don't like such a mix and would prefer a "blank" GNOME or KDE release. Is this possible with the new 1 CD installer (by default)?

---

### Post by Erunno on 2007-07-22
Even Kubuntu installs a couple of GTK+ / GNOME libs, it's the GNOME packagers who seem to be allergic to the thought of installing Qt / KDE libraries. There'a a subproject within openSUSE that intends to write a GNOME frontend but I'm not sure how far it has proceeded.

---

### Post by LuisAugusto on 2007-07-22
> **RedDwarf said:**
> Well, the new libzypp was not integrated until alpha6...


[http://packages.opensuse-community.org/](http://packages.opensuse-community.org/)

I didn't mean those kind of packages, I was talking about stuff like the treviños sources.list.

And yes, I know that it wasn't in alpha 5, so whats your ponit? I worked fine whit it, and I had a nice experience, period.

---

### Post by Alexander2007 on 2007-07-30
> **Erunno said:**
> Good stuff. Maybe people will be more inclined now to give openSUSE a try and maybe realize that K/Ubuntu is not the end of all things when it comes to highly polished distributions (actually, it's far away from it).
True, openSUSE is a beautiful and polished distribution. The only thing I hate in openSUSE is Yast!!! That Software Manager is annoying and still KDE based. I have installed openSUSE 10.1 before and came running back to Ubuntu, because nothing would install or work with Yast. I guess thats why so much software was installed by default. Yast? Oh please!

---

### Post by igknighted on 2007-07-30
> **Alexander2007 said:**
> True, openSUSE is a beautiful and polished distribution. The only thing I hate in openSUSE is Yast!!! That Software Manager is annoying and still KDE based. I have installed openSUSE 10.1 before and came running back to Ubuntu, because nothing would install or work with Yast. I guess thats why so much software was installed by default. Yast? Oh please!

Ummm... why did you use 10.1?  10.1's package management was indeed broken OOTB.  10.2 was fixed (although still slow), and 10.3 should be significantly improved still.  Plus, if you find yast distasteful (technically Yast2, but w/e) then install smart and use the smart repo's, or install apt4rpm and synaptic.  Both of these are decent package managers.  Personally I like the zypper CLI package tool on Suse, but there are options if you look around.

---

### Post by walkerk on 2007-07-30
looking forward to the release.. i switched from 10.2 to ubuntu because of suse's package manager.. i hope they've solved this issue.. took way to long to load.. very irritating.

---

### Post by Alexander2007 on 2007-07-30
> **igknighted said:**
> Ummm... why did you use 10.1?  10.1's package management was indeed broken OOTB.  10.2 was fixed (although still slow), and 10.3 should be significantly improved still.  Plus, if you find yast distasteful (technically Yast2, but w/e) then install smart and use the smart repo's, or install apt4rpm and synaptic.  Both of these are decent package managers.  Personally I like the zypper CLI package tool on Suse, but there are options if you look around.

Ok, I will give openSUSE 10.3 a try when it is out. Peace!

---

### Post by Incense on 2007-07-31
OpenSuse 10.2 + SMART is a great experience. I look forward to useing 10.3 when it comes out. I tired out the GNOME disc, and my desktop would not load. That's an alpha for ya.

---

### Post by Amphios on 2007-08-04
> **Erunno said:**
> Even Kubuntu installs a couple of GTK+ / GNOME libs, it's the GNOME packagers who seem to be allergic to the thought of installing Qt / KDE libraries. There'a a subproject within openSUSE that intends to write a GNOME frontend but I'm not sure how far it has proceeded.

I just gave the new Alpha 7 a try and there where NO KDE-libs installed. YaST was installed with a full-functional GNOME-based frontend. Furthermore, it's much faster than previous (open)SUSE distributions. One problem of the last distributions was their package management. If this is adressed in the current development, I have no more open wishes (can you say that in english this way?). Can't wait for the final release in October. :-)

---

### Post by Erunno on 2007-08-05
Yeah, Alpha 7 introduced a GNOME frontend for Yast which was probably necessary due to space limits on the 1 CD installation medium. I don't mind having GTK+ and some GNOME libs installed with my KDE desktop but I hope they get rid of some of these dependencies now that zmd has been dropped in favour of a native solution.

---

### Post by g2g591 on 2007-08-31
synaptic is NOT available, I tried searching for it and adept this morning, nethier was there, but I think yast is slowly growing on me

---

### Post by Altarbo on 2007-08-31
> **Amphios said:**
> I just gave the new Alpha 7 a try and there where NO KDE-libs installed. YaST was installed with a full-functional GNOME-based frontend. Furthermore, it's much faster than previous (open)SUSE distributions. One problem of the last distributions was their package management. If this is adressed in the current development, I have no more open wishes (can you say that in english this way?). Can't wait for the final release in October. :-)I tried it out recently was really impressed by how fast it was, too.  I had wanted to try KDE in the past, but Mandriva ran too slow on my box and I found both the straight KDE and Kubuntu packages to be still too slow.  I'm checking it out now with one of the openSUSE 10.3 discs.  

I don't think KDE itself is really my style, but I'm still impressed by how quickly it's running.  Window drawing, icon clicking, page rendering, etc. all seem incredibly fast.

---

### Post by RedDwarf on 2007-08-31
> **g2g591 said:**
> synaptic is NOT available, I tried searching for it and adept this morning, nethier was there, but I think yast is slowly growing on me
[http://download.opensuse.org/repositories/home:/rbos/openSUSE_10.2/repodata/repoview/synaptic-0-0.57.2-11.5.html](http://download.opensuse.org/repositories/home:/rbos/openSUSE_10.2/repodata/repoview/synaptic-0-0.57.2-11.5.html)

---

