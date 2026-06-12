---
title: "What's been your SUSE 10.1 experience?"
date: 2006-05-23
forum: openSUSE and SUSE Linux Enterprise
---

### Post by bored2k on 2006-05-23
The title says it all. I'll be getting a hold of it in a few days so I was just wondering what's been the experience* of the users on these forums who have tried.

* Constructive negativism? Yes. Trolling/bashing? Absolutely not.

---

### Post by helpme on 2006-05-23
Very nice in many respects, but the package management is severly broken.
Smart to the rescue and it's a very nice system to use.

---

### Post by bored2k on 2006-05-23
[QUOTE=helpme]Very nice in many respects, but the package management is severly broken.
Smart to the rescue and it's a very nice system to use.[/QUOTE]
The package manager of the **final** version is *severely* broken? Yikes. Could you be a little more verbose on that?

---

### Post by helpme on 2006-05-23
[QUOTE=bored2k]The package manager of the **final** version is *severely* broken? Yikes. Could you be a little more verbose on that?[/QUOTE]
Yep, that was also my reaction.
To be more precise, it was broken for me and looking around the net, others had similar experiences.

The root of the problem is that Suse is using a whole new backend for package management, which, if I understand it correctly, is supposed to bring the package management of yast and the redcarpet stuff together.
Now this is certainly a good idea, the only problem is that it doesn't work yet.

Problems I had:
I was unable to add online repositories in yast, that is, I could add them, but they wouldn't work.
As they didn't work, I wanted to remove them again, which also didn't work.

Turning to the new package management tools outside of yast (an other issue, the new stuff isn't really integrated yet, though at least in theory yast is supposed to use the new backend), I simply was unable to install anything with them.

The problem seems to be that the user management doesn't work. You are supposed to be able to use them after root has given you permission to use them. The first time you use them they'll prompt you for your root password and set up the permissions needed, at least in theory. However, at least for me, this didn't work and I'd always get an error messages after waiting for what seemed like ages.

The only thing that kind of worked for me was using the new command line tool rug, but though it worked, it's simply awfully slow.

To sum it up, they really borked it imho when it comes to package management. However, if you switch to smart, using the newest Suse is really fun.

---

### Post by catlett on 2006-05-23
My experience was like an ice cubes, frozen. I never got a good install. Just for a comparison I have installed about 10 different distros on this computer without issues. The mdm5 checked out fine but it froze every time.
The one thing I would advise against is doing the Yast update during install. This froze my install once and then it had errors on the 2nd time. I could never check the log because I couldn't get in.
I have an install of OpenSuse 10 but I don't even boot into it. The main reason is I'm not a kde person so I don't know the setup (OpenSuse runs kde as opposed to Suse running gnome as default)
I stayed away from yast because of the install issue and tried "Klik" which OPenSuse has prominently displayed on the system. There is an icon URL link to it on ther desktop as well as documentation in your home folder.
Nothing from klik went through. So I haven't been in Opensuse that much. I spend most my time in Ubuntu but if not,  I'm trying to learn more about my PC BSD install or my Belenix Open Solaris Live cd. I didn't care for Suse or novell's forum sites.
With all the different distros I have gone to, Ubuntu is as good if not better. They have a great Gnome, KDE and XFCE . All there window manager setups are top notch. And of course there are no other forums even close to Ubuntu's. You won't even get a reply from the other sites half the time. I have posts 2 and 3 months old on a couple of forums and they are still on the front page!

---

### Post by gruvsyco on 2006-05-24
Last week, I decided to give linux another shot, what with all the cool XGL stuff going on... I tried Gentoo, Kororaa, Mepis, SuSE and finally, Ubuntu.  My experience with SuSE was, overall, I loved the look and feel.  They did an incredible job of unifying the Gnome/KDE experience and the desktop really looks professional.  The broken package management was a real disappointment though.  Enough so that I ended up moving on.  I was also surprised that being the distribution from the driving force behind XGL, it wasn't easier to get it running on there.  Another deciding factor in dropping SuSE was after I visited a couple of sites and was seeing binaries for Debian, Fedora and Ubuntu but not much else (Mostly Debian and Fedora though).

Being a former Novell Netware admin, I have a special place in my heart for Novell.  I think they are on their way to having something great but, it's not there yet.

---

### Post by sophtpaw on 2006-05-24
Can i say: by the sounds of things SUSE SuX

???

Best stick with UBUNTU, huh?! :D

---

### Post by mostwanted on 2006-05-24
Package management was broken and even when you "fix" it the only place to get many important packages is by using unofficial repsitories.

Many of the included apps have many bugs as well (the update manager throws an error pretty much every time you use it).

It comes on 5 CDs and I needed 4 of those to get a localised install with JUST Gnome. I can get that on one CD with Ubuntu.

The default theme looks nice, but that's pretty much the only good thing about. The SUSE team uses a lot of time on graphical polish, but not on the rest.

---

### Post by bored2k on 2006-05-24
[QUOTE=sophtpaw]Can i say: by the sounds of things SUSE SuX

???

Best stick with UBUNTU, huh?! :D[/QUOTE]
:-/ . I've been reading what distrowatch called the best SUSE 10 review, and to be honest, nothing I read there impressed me at all (there's pretty much nothing that Ubuntu doesn't have), but I'm still interested because hey, it can't be that bad/inferior, right? I'm mostly worried about SUSE being even slower than Ubuntu in terms of performance. Not that ubuntu is slow, but say.. Arch beats it by a few miles.

---

### Post by helpme on 2006-05-24
[QUOTE=bored2k]:-/ . I've been reading what distrowatch called the best SUSE 10 review, and to be honest, nothing I read there impressed me at all (there's pretty much nothing that Ubuntu doesn't have), but I'm still interested because hey, it can't be that bad/inferior, right? I'm mostly worried about SUSE being even slower than Ubuntu in terms of performance. Not that ubuntu is slow, but say.. Arch beats it by a few miles.[/QUOTE]
Don't be to worried about performance, in my experience the new Suse is quite fast.

Also, I think there's one thing that Suse has that's really missing from Ubuntu and that's yast. Love it or hate it, but having a graphical configuration app for nearly everything sure is something that will atract many people.

---

### Post by bored2k on 2006-05-24
[QUOTE=helpme]Don't be to worried about performance, in my experience the new Suse is quite fast.

Also, I think there's one thing that Suse has that's really missing from Ubuntu and that's yast. Love it or hate it, but having a graphical configuration app for nearly everything sure is something that will atract many people.[/QUOTE]
That's the thing. I don't want it to attract many people, I'd just want it to attract me ;). yast is pretty, but that's not my priority. I'm going for performance first.

---

### Post by catlett on 2006-05-24
[QUOTE=bored2k]That's the thing. I don't want it to attract many people, I'd just want it to attract me ;). yast is pretty, but that's not my priority. I'm going for performance first.[/QUOTE]
Have you tried any of the BSD distros? For speed bsd is hard to beat. Not that you asked but PC BSD is real easy to install and gett running with kde. Free BSD is hard if your not fluent in text installs. I got through the install and setup but couldn't get X to start with gnome. Their forum is nothing like Ubuntu so I couldn't get a few commands to get it working and linux commands don't all work.
Another question you didn't ask is OpenSolaris. Right now it appears they are where the original debian and red hat must have been. They have a kernel but no full featured window manager. A couple of distros are trying to incorporate gnome or kde  but I haven't gotten a hard dislk install yet. But to have an open source OS that has had $500 million invested in development is unbelieveable. Opensolaris is the real deal. It's servers are run at the Department of Defense etc,  because of their stability. Open Solaris is the dark horse to watch. Even though it's another thing to learn. Who ever heard of slices anyway?:-D

---

### Post by ComplexNumber on 2006-05-24
[quote=bored2k]That's the thing. I don't want it to attract many people, I'd just want it to attract me ;). yast is pretty, but that's not my priority. I'm going for performance first.[/quote]
if you want performance, go for something like gentoo or arch

---

### Post by bored2k on 2006-05-24
[QUOTE=ComplexNumber]if you want performance, go for something like gentoo or arch[/QUOTE]
Let's say I have a love/hate/hate/love/die relationship with Arch. I install it every couple of weeks, use it for a few days, then go back to whatever I was using. It's close to what I'm looking for though.

---

### Post by ComplexNumber on 2006-05-24
[quote=bored2k]Let's say I have a love/hate/hate/love/die relationship with Arch. I install it every couple of weeks, use it for a few days, then go back to whatever I was using. It's close to what I'm looking for though.[/quote]
well, the best for performance are the ones that you have to build yourself from source. so choose from any one of them.

---

### Post by bored2k on 2006-05-24
[QUOTE=ComplexNumber]well, the best for performance are the ones that you have to build yourself from source. so choose from any one of them.[/QUOTE]
Yeah, I guess I'll finally end up with Arch as my main man. And by the way, on Arch you build from source only if you want to. The pacman repositories are quite good, specially when complemented with their community repositories, though of course, you eventually end up building a few dozen packages for yourself ;).

I'll try OpenSUSE and FreeBSD (which I heard is _very_ similar to Arch's installation) before I -probably- go back to Arch (which just released their 0.7.2 version).

Thanks to **catlett** for reminding me to try FreeBSD!

---

### Post by tseliot on 2006-05-24
[QUOTE=sophtpaw]Can i say: by the sounds of things SUSE SuX

???

Best stick with UBUNTU, huh?! :D[/QUOTE]
No, you're wrong: SUSE SaX (ok but the sound is the same) :p 

No, really I think that Suse doesn't like me (and not the other way round). After a while Yast's GUI stopped working for good and I had to use it from the command line. 

I had to install Totem-xine without dependecies in order to make it work.
Even after installing gstreamer plugins neither Banshee nor Rhythmbox (which BTW depended on Totem-gstreamer, if I'm not wrong) weren't able to play mp3s.

I had to use APT to install apps, etc.

Then I gave up. I had already given up with OpenSuse 10.0.

Of course OpenSuse can be the perfect distro for other people but not for me. This is just my experience. No distro bashing was meant

---

### Post by ComplexNumber on 2006-05-24
**bored2k**
i had suse 10 installed up until about a few weeks ago. it was very slow to boot up, and yast seemed to be quite slow. gnome seemed  slightly broken, whilst kde was surprisingly and relatively trouble-free. i really liked the package installer in yast.

you're a brave man to try arch and others of their ilk ;)

---

### Post by tseliot on 2006-05-24
[QUOTE=bored2k]I'll try OpenSUSE and FreeBSD (which I heard is _very_ similar to Arch's installation) before I -probably- go back to Arch (which just released their 0.7.2 version).

Thanks to **catlett** for reminding me to try FreeBSD![/QUOTE]
Absolutely. Arch is very similar to FreeBSD (as far as its installation is concerned). But keep in mind that if you want the latest and the greatest packages you will have to compile them (not that it's difficult).

---

### Post by ComplexNumber on 2006-05-24
> Even after installing gstreamer plugins neither Banshee nor Rhythmbox (which BTW depended on Totem-gstreamer, if I'm not wrong) weren't able to play mp3s. did you remember to type "gst-resgister" on the command line? if you didn't you wouldn't have been able to play mp3's. its a common mistake that most people make. this was necessary in 0.8, but i don't think it is in 0.10

---

### Post by mostwanted on 2006-05-24
I have the same problem. Even after gst-register and gst-register-0.8. All gstreamer 0.8 and 0.10 plugins are installed.

Also, Gaim doesn't work for me (asks for my keyring password to log in for some odd reason). Suse 10.1 is utterly terrible, I'm never leaving you again Ubuntu!

---

### Post by Lord Illidan on 2006-05-24
So it can't play mp3s, it can't handle package management, what else?
I've been downloading the dvd for hours now. If it is not worth the download, I will boycott SUSE on the spot.

---

### Post by tseliot on 2006-05-24
[QUOTE=ComplexNumber]did you remember to type "gst-resgister" on the command line? if you didn't you wouldn't have been able to play mp3's. its a common mistake that most people make. this was necessary in 0.8, but i don't think it is in 0.10[/QUOTE]
Yes, I did try that but I think that gst-register works only with gstreamer 0.8.

And BTW it didn't work

---

### Post by tseliot on 2006-05-24
[QUOTE=Lord Illidan]So it can't play mp3s, it can't handle package management, what else?
I've been downloading the dvd for hours now. If it is not worth the download, I will boycott SUSE on the spot.[/QUOTE]
It has one of the nicest bootsplash and sports a nice GUI for the installation.

You might like it (but I don't)

---

### Post by Jucato on 2006-05-24
[QUOTE=catlett]I have an install of OpenSuse 10 but I don't even boot into it. The main reason is I'm not a kde person so I don't know the setup (OpenSuse runs kde as opposed to Suse running gnome as default)[/QUOTE]

Pardon my ignorance, but I'm confused. OpenSUSE is different from SUSE? DistroWatch displays both OpenSUSE and SUSE as the same, and the download section in OpenSUSE labels the downloads as SUSE Linux.

Anyway, I'm currently trying out other distros. Would you recommend trying SUSE 10.1 to someone who has absolutely no RPM experience, or stick to the 10.0 release?

---

### Post by mostwanted on 2006-05-24
[QUOTE=Fenyx]Pardon my ignorance, but I'm confused. OpenSUSE is different from SUSE? DistroWatch displays both OpenSUSE and SUSE as the same, and the download section in OpenSUSE labels the downloads as SUSE Linux.

Anyway, I'm currently trying out other distros. Would you recommend trying SUSE 10.1 to someone who has absolutely no RPM experience, or stick to the 10.0 release?[/QUOTE]

Personally, I would recommend staying away from Suse :)

OpenSuse is what Suse is now called; it's a so called community distro like Fedora. There is also Suse Linux (Enterprise Edition) which is like Red Hat Enterprise Linux.

OpenSuse doesn't run KDE as default, it runs whatever you choose during install. Not sure about Suse Linux, my guess is that it's the same.

---

### Post by ComplexNumber on 2006-05-24
[quote=Fenyx] Pardon my ignorance, but I'm confused. OpenSUSE is different from SUSE?[/quote] i could be wrong, but i've been led to believe that suse is the generic name. opensuse refers to the free version whilst SLED refers to the enterprise version. they are both called suse, though. its similar to what mostwanted explains in regard to fedora and redhat.
SLED is gnome by default, whilst opensuse is whatever you choose.

---

### Post by Jucato on 2006-05-24
[QUOTE=mostwanted]OpenSuse is what Suse is now called; it's a so called community distro like Fedora. There is also Suse Linux (Enterprise Edition) which is like Red Hat Enterprise Linux.[/QUOTE]

Ok, let me check if I got this straight. OpenSUSE is the community distro while SUSE Linux is the enterprise distro? But then why does the download page on OpenSUSE calls it SUSE Linux? :confused: 

Oh, what the heck with names!

Anyway, I was planning to really try out SUSE, just to get a feel of some RPM-based distros. But I have been highly discouraged by the conflicting impressions/experiences regarding 10.1. There's almost an equal amount of good reviews and bad reviews, with the bad ones mostly focusing on package management. Since I have no prior RPM experience, I guess that means I have to stay away from it for a while... :(

---

### Post by ComplexNumber on 2006-05-24
> Since I have no prior RPM experience, I guess that means I have to stay away from it for a while...
i don't see why.

---

### Post by Jucato on 2006-05-24
Well, because most problems regarding the 10.1 seem to be related to package management. As such, I will be completely in the dark if a problem crops up because, like I've said, I have absolutely no experience in handling RPMs or any RPM-based distro. Although I'd really want to try SUSE out to experience first-hand what the fuss is all about (regarding big distros like Red Hat and SUSE), I'm a bit scared coz I'm going to tread on unknown territory. I also don't want my first RPM experience to be marred by a release which I think (based on some reviews/comments) is a bit unstable right now.

(And as I have only one unit at home, I can't be installing/customizing/fixing SUSE and be browsing for some help at the same time).

---

### Post by helpme on 2006-05-24
[QUOTE=Lord Illidan]So it can't play mp3s, it can't handle package management, what else?
[/QUOTE]
It can handle mp3s just fine, if you install the right engine. 
At the moment, I don't think mp3 support is available for gstreamer-10 in Suse, but for example, if you want to use banshee, just install the helix engine for banshee and if you want to use amarok, just install xine from packmann.

Also, you should really give smart a try for package management.

---

### Post by BarfBag on 2006-05-24
Here's my SUSE experience.

[http://forums.suselinuxsupport.de/index.php?showtopic=37148](http://forums.suselinuxsupport.de/index.php?showtopic=37148)

](*,)

---

### Post by tseliot on 2006-05-24
[QUOTE=helpme]It can handle mp3s just fine, if you install the right engine. 
At the moment, I don't think mp3 support is available for gstreamer-10 in Suse, but for example, if you want to use banshee, just install the helix engine for banshee and if you want to use amarok, just install xine from packmann.

Also, you should really give smart a try for package management.[/QUOTE]
Of course xine-engine worked (e.g. in Amarok) but if you want to use Rhythmbox or Banshee no xine-engine is available.

---

### Post by helpme on 2006-05-24
[QUOTE=tseliot]Of course xine-engine worked (e.g. in Amarok) but if you want to use Rhythmbox or Banshee no xine-engine is available.[/QUOTE]
For banshee, use the helix engine.
For rhythmbox, you're out of luck till someone builds the needed gstreamer plugin.

---

### Post by tseliot on 2006-05-24
[QUOTE=helpme]For banshee, use the helix engine.
For rhythmbox, you're out of luck till someone builds the needed gstreamer plugin.[/QUOTE]
Thanks but I wiped away my partition with Suse ( Ubuntu is on my other partition).

I put Simply Mepis in its place (but I will soon replace it with something else)

---

### Post by Lord Illidan on 2006-05-24
[quote=tseliot]It has one of the nicest bootsplash and sports a nice GUI for the installation.

You might like it (but I don't)[/quote]

Well, from screenshots I like what the GUI looks like.
However, I want it to be fast, and easy to use.

And as Ubuntu-like as possible...if possible...

---

### Post by Lord Illidan on 2006-05-24
Also, I heard that it will do a beagle index at firstboot, is it true? I hate beagle, it is the slowest thing I have on my system, and I have no need for it.

---

### Post by bored2k on 2006-05-24
[QUOTE=BarfBag]Here's my SUSE experience.

[http://forums.suselinuxsupport.de/index.php?showtopic=37148](http://forums.suselinuxsupport.de/index.php?showtopic=37148)

](*,)[/QUOTE]
Ok, for mostly everyone to agree with you **on** the SUSE forums? Now this really scares me. Heck, you guys are scary. So, does the majority here confirm that it's slower than Ubuntu in terms of performance, and that it has several issues with package management and multimedia playback? I know it's a GUI-centric distro, but are those GUIs slow enough for you to not want to use it?

/me holds DEL trigger.

*Whoa. I haven't tried SUSE since what, v9 PRO?*

---

### Post by Lord Illidan on 2006-05-24
Most tell you to install apt4rpm, and I remember synaptic + apt-get + Suse 10.0 not sucking so bad as YAST + Suse 10.0.

But If apt-get is so good, why doesn't Novell ditch rpm and switch to deb?

---

### Post by BarfBag on 2006-05-24
[QUOTE=Lord Illidan]Also, I heard that it will do a beagle index at firstboot, is it true? I hate beagle, it is the slowest thing I have on my system, and I have no need for it.[/QUOTE]

Yep.  It indexes at first boot.  If you read my post in SUSE Forums (link above), you'll notice that it caused problems for me.  It took WAY too long to index.  Over 20 minutes.  Also, it pretty much kills your PC while it's doing it.

---

### Post by Lord Illidan on 2006-05-24
[quote=BarfBag]Yep.  It indexes at first boot.  If you read my post in SUSE Forums (link above), you'll notice that it caused problems for me.  It took WAY too long to index.  Over 20 minutes.  Also, it pretty much kills your PC while it's doing it.[/quote]

Can anyone tell me what is the logic of indexing at first boot???  If you are installing on a fresh system, that is? Why?

Ok, so I won't install beagle... Anything else we need to know?

---

### Post by ComplexNumber on 2006-05-24
>  But If apt-get is so good, why doesn't Novell ditch rpm and switch to deb?
no point.
1) rpm is now the standard
2) you can get apt for rpm sytems
3) if you use a GUI, this makes the underlying apt, yum, whatever mostly irrelevant.
4) too much hassle.
5) rpm handles many things better than deb such as the ability to keep different versions of the same package on the same system, checksums,  etc

---

### Post by Lord Illidan on 2006-05-24
[quote=ComplexNumber]no point.
1) rpm is now the standard[/quote]

Says who?

---

### Post by RAV TUX on 2006-05-24
[quote=bored2k]The title says it all. I'll be getting a hold of it in a few days so I was just wondering what's been the experience* of the users on these forums who have tried.

* Constructive negativism? Yes. Trolling/bashing? Absolutely not.[/quote] 

I could never get it to install on my computer.











.

---

### Post by disturbed1 on 2006-05-24
edit to finish install

---

### Post by ComplexNumber on 2006-05-24
[quote=Lord Illidan]Says who?[/quote] says the Linux standard Base(ie the LSB). i'm surprised you didn't know.

---

### Post by Lord Illidan on 2006-05-24
Actually I didn't know about the LSB to begin with...

But judging from what people say and my experiences deb beats rpm, and is faster.

---

### Post by ComplexNumber on 2006-05-24
[quote=Lord Illidan]
But judging from what people say and my experiences deb beats rpm, and is faster.[/quote] i think you'll find its mostly sheep who are inanely  chanting the same old mantra about "rpm dependency hell" etc, but not knowing the reasons why or having any substance behind what they say. they chant it because they've heard other people on forums chanting it, so they use it as amunition to bash the specific rpm based distro that they want to bash. 
LSB chose rpm for good reasons, and thats that.

---

### Post by Lord Illidan on 2006-05-24
[quote=ComplexNumber]i think you'll find its mostly sheep who are inanely  chanting the same old mantra about "rpm dependency hell" etc, but not knowing the reasons why or having any substance behind what they say. LSB chose rpm for good reasons, and thats that.[/quote]

Actually as regards dependency hell, I find that rpm is not bad in resolving dependencies.

However, what about the sheer number of packages available for Ubuntu compared to Suse's?

---

### Post by ComplexNumber on 2006-05-24
>  However, what about the sheer number of packages available for Ubuntu compared to Suse's?but what percentage of those sheer number of ubuntu packages are deprecated or unsupported? the actual difference means that suse has more packages available that are supported by default  (4000 suse compared to 3180 in ubuntu)

---

### Post by mostwanted on 2006-05-24
[QUOTE=ComplexNumber]but what percentage of those sheer number of ubuntu packages are deprecated or unsupported? the actual difference means that suse has more packages available that are supported by default  (4000 suse compared to 3180 in ubuntu)[/QUOTE]

You have to remember, that is the *only* official repo that SUSE 10.1 has (apart from the small non-oss repo).

---

### Post by catlett on 2006-05-24
I got OpenSuse through the magazine Linux Format. Every issue comes with a distro disk. The disk says OpenSuse. The splash page says open suse and there readme says they are Suse with performance based tweaks.
As for kde and gnome I said default because when I chose desktop and not server during install Suse gave me Gnome and OpenSuse gave me KDE.
I would assume it is like Ubuntu and Kubuntu. People here list them as 2 seperate distros. They have different sections in the forum but I can run the Kubuntu install and end up with gnome and vice versa with ubuntu.
I'm not on my home computer and can't verify everything but since the issue came up I'll boot into OpenSuse and check their documentation. But my impression was they were suse but a performance version that used kde and installed some extras. Like I said they were big on klik. They had it front and center on the desktop and most importantly that install works.
I just don't care for it after all the original problems. I'm more turned on by BSD and OpenSolaris than another linux distro that has gnome or kde. I have the distro I want with Gnome, KDE and XFCE. It's Ubuntu and I have all three window managers at the tip of my mouse when I log in:-D

---

### Post by catlett on 2006-05-24
[http://en.opensuse.org/SLICK](http://en.opensuse.org/SLICK)
Now I know what I was forgetting. It is called OpenSuse Slick. THat is the variation. I knew it was something a little different and that kde was it's default. Anyways there is the link to slick if anyone is interested.

---

### Post by ComplexNumber on 2006-05-24
[quote=catlett][http://en.opensuse.org/SLICK]("http://en.opensuse.org/SLICK")
Now I know what I was forgetting. It is called OpenSuse Slick. THat is the variation. I knew it was something a little different and that kde was it's default. Anyways there is the link to slick if anyone is interested.[/quote] isn''t that for version 10 only at this present time? i remember that when it was released several months after opensue 10 on the cover of Linux Format. wait a few weeks/months and they'll probably release the optimised version of suse 10.1 (ie suse slick 10.1)

---

### Post by catlett on 2006-05-24
I apologise to everyone for confusing them. I was trying to say that when I downloaded Suse 10 I couldn't get it going. I had Linux Format with OpenSuse and it installed kde and worked. People posted saying it was the same thing. I checked and the difference was I had Opensuse Slick.
The disk I have from Linux Format is April 2006 but with magazines who knows how long April has been out. 
Just another quick comment. My other computer is as basic as it gets. A Gateway 700mhz with nothing added on. My printer doesn't work, my sound doesn't work and my mouse will inadvertently "hesitate" and freeze. This from a computer that has Fedora Core 5, Simply Mepis, Yoper, XP and a almost configured FreeBSD:-k  that all detect and run fine. Suse 10 never got up and running. I would boot into Gnome and then freeze. With Slick I get in but my mouse will hesitate and the sopund doesn't work. I don't really care to configure the Slick install. I prefer other things.
This is my newest interest [http://www.gnusolaris.org/gswiki](http://www.gnusolaris.org/gswiki)

---

### Post by helpme on 2006-05-24
[QUOTE=ComplexNumber]no point.
1) rpm is now the standard
[/QUOTE]
Actually, that's not really true.
All the lsb says is that compliant distros must support some subset of rpm. Distros are free to use any other package format otherwise.
sudo apt-get install lsb

Other than that, I agree with you, this uniformed flaming against rpm is also getting on my nerves.

---

### Post by gamma on 2006-06-26
I love the way Suse looks and feels, but yes lots of packages are broken. Update manager wanted to downgrade a package on a fresh install, and in order to do that I'd have to remove half my packages. YaST is very slow..

It's impossible to get gstreamer-plugins for restricted formats, forcing the user to use realplayer or xine.

Pretty artwork, nice bootsplash, nice looking fonts, the prettiest distro out there.

Stable, fast and easy to use.

---

### Post by nu2this on 2006-06-28
The main problem I had with SUSE no matter what(even .xorg.conf) was it gave me any screen resolution I wanted as long as it was 1208x1024!
Thanks & Praise Be for Ubuntu!

---

### Post by loren95404 on 2006-10-10
I'm running SUSE LDE 10.1 64-bit edition and I have to say my experience is pretty decent so far.

The only problems I've had so far is configuring SAMBA and Totem not having the proper GStreamer Liberaries.

I'm running an Opteron 165 with 2GB Ram, I think Novell is aiming for the future, and I'd say their money is on the right spot.

----

I was considering switching to Ubuntu because I hate the RPM package system, but when I started running into problems removing the hiteous Brown from Ubuntu, Installing Xgl, Cinerama, and a lack of auto-configing control panel I started to step down. If I can make Ubuntu Suitable in a nice blue (HumanAzul + Human-Blue) maybe I'll switch,

SuSE out of the box, 8.75/10

---

### Post by NeoLithium on 2006-10-10
I used openSUSE 10.1 for actually, a long time before I put Ubuntu on my laptop; the updater, did drive me nuts; but overall, I loved how well it worked. Plus, the only 2 distro's that have really done an excellent job of detecting all of my hardware, have been Ubuntu and SUSE.  10.2, from what I remember on the forums, has a greatly improved updater and package setup; which would be pretty welcome.

Still;now that I have Ubuntu installed,and setup, it'll be hard to get me to switch back...but who knows.  It's not really terrible; but their final 10.1 release seems as though it was rushed for some reason; at least with the time it's taking to put 10.2 to a final release, it's pretty encouraging that it won't be as choppy...

---

### Post by MepisReign on 2006-10-11
In few words, Installed Suse 10.1....a complete disaster, YaST updater is buggy and in general Suse didn't convinced me at all, went back to Mepis and now almost everything is just fine

Regards,

MepisReign

---

### Post by pain of salvation on 2006-10-14
Novell released OpenSUSE 10.1 "remastered", with all bugs fixed. I am downloading it right now..

[http://distrowatch.com/?newsid=03772#0](http://distrowatch.com/?newsid=03772#0)

---

