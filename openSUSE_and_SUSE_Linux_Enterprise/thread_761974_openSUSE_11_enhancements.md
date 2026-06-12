---
title: "openSUSE 11 enhancements"
date: 2008-04-21
forum: openSUSE and SUSE Linux Enterprise
---

### Post by some-guy on 2008-04-21
A few things that will be enhanced in opensuse 11:
- Zypper has a SAT solver that makes it faster than anything now. [link]("http://duncan.mac-vicar.com/blog/archives/296")
- PackageKit is now used in addition to YaST's module. (This also uses super-fast zypper)
- Artwork is much better and looks much more professional
- Provides: Gnome, KDE3, KDE4, Xfce, plain X11, and no X at all

List any others!

:guitar:

---

### Post by quickshade on 2008-04-21
An installer that rivals anything else out there.
A KDE 4 that works properly

---

### Post by izanbardprince on 2008-04-21
> **quickshade said:**
> An installer that rivals anything else out there.
A KDE 4 that works properly

I second the KDE 4 comment.

Kubuntu's feels broken and like half of it is missing, it's no wonder they don't want to officially support it.

---

### Post by quickshade on 2008-04-21
> **izanbardprince said:**
> I second the KDE 4 comment.

Kubuntu's feels broken and like half of it is missing, it's no wonder they don't want to officially support it.
I was seriously disappointed in the KDE4 option in Kubuntu, Fedora at least tried to make it a little better, but made it default while it is still missing a lot of functionality. It's not a real usable desktop yet. Opensue was at least smart enough to backport features to make it work, and give it a nice theme while they were at it. I know fedora and kubuntu had releases that were earlier than opensuse, So I'll give them a break about not porting features over, but making it the default was a bad idea.

---

### Post by generalguy on 2008-04-23
Ubuntu needs to grab opensuse's installer. It blows everything else out of the water.

---

### Post by andlinux21 on 2008-04-23
Generalguy is that installer really that good?

---

### Post by Antman on 2008-04-24
> **generalguy said:**
> Ubuntu needs to grab opensuse's installer. It blows everything else out of the water.
It certainly looks nice and n00b friendly.

---

### Post by quickshade on 2008-04-24
The use of images for install was a great idea. Fedora DVD and a couple of others took an hour at least. Opensue 10.3 DVD took 58 minutes for me. I now install Beta 1 in about 25 minutes. According to the developers by Beta 3 it should be down to 20 minutes.

---

### Post by Incense on 2008-04-24
The new installer is beautiful, and very fast. I had a complete install done in under 20 mins. I am very impressed by their release of KDE 4, and this is only their beta. I tried out Kubuntu KDE 4, and it was very disappointing. The SUSE devs did an amazing job creating a consistant look across Gnome and the KDE's. It's really too bad XFCE is pretty vanilla. Even so, I think this will be something amazing. 

OpenSUSE KDE 4

[IMG]http://files.opensuse.org/opensuse/en/thumb/f/f4/OS11.0beta1-kde4-2.png/750px-OS11.0beta1-kde4-2.png[/IMG]

---

### Post by quickshade on 2008-04-25
I always thought KDE4 was cool looking but just lacking in general. Everyone always complained about the kicker and I never really had a problem with the color of it. Now that I've tried this beta, I see no reason to go back to that black kicker. The OpenSUE one not only kicks *** but looks really sweet.I wish they would include KDE 4.1 as the default and just delay openSUSE by 3 weeks. But whatever, I'll just upgrade when it's released.

---

### Post by generalguy on 2008-04-26
The nice thing about the installer is that it's very thorough. By the time you finish, you will have a complete system set up: all user accounts, package management and online repositories, hardware dectected,partitioning and of course the actual installation. Most installers do that, but OS's is graphically pleasing, generally well thought-out, has a help sidebar, and does not skimp on the options. The partitioner is fairly intuitive and beats ubiquity on power (but ubiquity is less confusing at first). If you are an intermediate to advanced user, openSUSE will be easier to work with. A beginner should stick to ubuntu. KDE is quite different than GNOME (openSUSE offers both). 

YaST > nearly all control panels. It provides a nice interface to some of the more obscure linux options.

zypper/YaST package manager are not so good. Their UI is not great, they throw lots of little windows up, and were not tested well for usability.

In openSUSE 11, they've improved, but some things are questionable. For example, good package managers like smart will download all packages in parallel and install them serially, YaST will download and install serially,meaning that your cd drive will spin up and down as large packages trigger the "rest" mechanism.

openSUSE also has an enabled-by-default root account.

---

### Post by shuttleworthwannabe on 2008-04-27
the one thing I check before I try a distro is that it will like my ATI card from the beginning: Ubuntu Hardy albeit in alternate CD (not lIve CD) picked up the correct resolution (1900x1200) in vesa mode and then prompted me to install the restricted fglrx drivers; without having to go thru balck screens or wobbly GUI screens (blurred because driver not installed).

My question: does OpenSuse KDE4 do the same; or will I end up in black screen, then how do I trouble shoot from blank screen?

---

### Post by Erunno on 2008-04-27
> **shuttleworthwannabe said:**
> My question: does OpenSuse KDE4 do the same; or will I end up in black screen, then how do I trouble shoot from blank screen?

openSUSE does not include closed source drivers by default so you'll have to install fglrx via an one-click-installer. A little less convenient than with Ubuntu but you'll always have the latest fglrx drivers since the installer points to the official AMD repositories and Ubuntu's decision to include closed source drivers has always been a questionable one.

Anyway, I seriously doubt that you'll suffer from a blank screen, X should be able to run correctly in VESA mode at least. And Novell has been developing the radeonhd driver for some time so I reckon it's possible that they'll include it by default (if it's stable enough).

---

### Post by shuttleworthwannabe on 2008-04-27
thanks erunno. I just downloaded the live CD KDE4, and unfortunately, as I predicted, the live desktop loads but just: the screen shakes and is not readable. I thought I would do a full HD install, and it hung at the agreement section. I have couple of questions:

1. Is there a boot parameter to enter at boot up so that by default it uses VESA drivers; so in this way I can at least get to the desktop and do a install; then follow a 1-click-installer for fglrx.
2. Is there an alternative CD that allows installation without having to go thru a Live Desktop? Point me to the download please if so.

To get back to the OP: OpenSUSE 11.0 Beta1 KDE4 has a great looking KDE4 desktop---talk about polish and refinement; in my previous attempts to advocate for a similar move in Ubuntu was received by forumites by mixed reaction--mainly that it was not necessary to go for the "eye-candy". Seriously, the Desktop and the attention to detail, just blows the wits out of Kubuntu (I tried that too, but quickly went back to GNOME Ubuntu)

---

### Post by quickshade on 2008-04-27
You will have to download the DVD to do an install as the LiveCD is broken. I'm not sure if they will use a regular CD for install (just installer) for this release or not. Will have to ask. 

After you install it the system will detect your hardware and you can set it to use the vesa driver until you can install your driver. But I'm not sure if the graphical installer will work.

You could try creating a bug report and see if they will include a fix for your problem. No promises that they will, but if it's a quick fix or enough people ask they will.

---

### Post by shuttleworthwannabe on 2008-04-28
thanks dude; I think I will visit their bugs page and see if there are others with similar difficulties; if not then surely file a bug there.

---

