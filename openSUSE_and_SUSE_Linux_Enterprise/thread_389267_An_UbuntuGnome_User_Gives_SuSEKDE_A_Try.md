---
title: "An Ubuntu/Gnome User Gives SuSE/KDE A Try"
date: 2007-03-20
forum: openSUSE and SUSE Linux Enterprise
---

### Post by talkingwires on 2007-03-20
I've been using Ubuntu since the first beta back in 2004. By extension, that means I've been using Gnome (and occasionally XFCE), too. The past two releases of Gnome have been very disappointing in terms of new features, innovation, and growth. To me, it seems like Gnome has stagnated. Meanwhile, I've been the "[Road to KDE 4]("http://dot.kde.org/")" articles and using Amarok as my primary music player. So I got to thinking, "Hey, maybe I should give KDE another whirl, and why not try another distro while I'm at it?"

I decided to go with OpenSuSE, as I'd used SuSE 9 back in the day, and they were a KDE-centric distro (well, at least they used to be), and I wanted to see what they've been up to. Here's a rundown of my experience:[LIST]
[*]The internet installation disc could not download the list of packages from SuSE's repos. I tried fifteen different mirrors listed on SuSE's site, and every single one errored off with a  "connection reset" messsage.Which leads to...
[*]There is no "one CD" installation. You have to download five whole CDs to get a basic desktop. During the installation, SuSE only needed five or six files off three of the discs. I spent an hour downloading each disc and then burned them to CD-Rs only to find the installer needed about ten megabytes of stuff off of each.
[*]The kernel would do a hard lock if I had my PCMCIA wireless card plugged in. This was before and after the install. This same setup works fine in Ubuntu.
[*]The community support is non-existent compared to Ubuntu's. I spent a whole day trying to find information on my PCMCIA problem. I found many posts, but only a few had responses with methods to try. But the only one anyone had replied to saying it worked was the suggestion of plugging in the card during a specific part of the boot process. It didn't work for me, and with no way to diagnose a hard lock at boot, I gave up. It looks like this problem has been around in one form or another since the SuSE 9.1 days.
[*]The desktop is very polished. I liked SuSE's replacement for KDE's menu. It was much more easy to navigate than KDE's default. (A Win95 menu filled with sixty applications that all begin with the letter "K"? Give me a break. KDE's menu is one of primary reasons I've stuck with Gnome.) That said, it seemed very "twitchy" when moving my cursor around in it. I'd make a selection, but as my cursor moved away, it would accidentally activate a different tab. This problem may have been compounded by using a synaptic pad on a laptop instead of a proper mouse.
[*]The integrated Kerry/Beagle search was nice, but for some reason, SuSE installed half of the Gnome desktop in order for it work.
[*]Having all the configuration tools in one utility (YaST) is convenient. But the presentation feels very cobbled together. Clicking on something would launch a new window, and another, and another. And it would run some sort of linking script after you used each one, often if you were just canceling out of it.
[*]Clicking on some YaST modules would issue a prompt saying they were not installed. (Why are the appearing in YaST if they're not installed?) I would insert the CD it prompted me for, but YaST would not recognize it. If SuSE can download online updates, why can't it install packages from the Internet, too?
[*]The default theme is very nice. Hell, the installer's spash screen blew me away. It's doubly impressive on an LCD screen. Try it, and you'll see what I mean.
[*]I loved being able to pick and choose the packages I wanted to install without worrying about the ubuntu-desktop metapackage. But why is OpenOffice an all-or-nothing package? Why do I have to install 330Mb of stuff just to use Writer?
[*]After using RPMs again, I remembered why I jumped to Debian in the first place. Ugh. (Which reminds me. I haven't used Debian in years, either. Maybe it's time to see what they've been up to?)
[*]I just can't get over the KDE environment itself. Everything feels cobbled together, and you can really tell that it has a hundred people working on a hundred different parts of it. There are dozens of little applets and icons splayed all over the screen. SuSE's menu helps reduce the clutter significantly, but I just like how Gnome fits together perfectly and each app has a consistent interface. If a little bloat and loss of configurability is the price to pay, then so be it.
[*]That said, I really like many of KDE's applications. Amarok has no peer. Some may call it bloated, but try managing 40Gb of music and syncing that to an iPod with XMMS. It can be done, but not with the speed and convenience of Amarok. K3B is the best Linux burning tool, hands down. And even with it's shockingly cluttered interface, I appreciate Konqueror's I/O slaves that make CD ripping and iPod syncing a cinch. (Now that I think of it, Konqueror is probably the second reason, after the menus, that I haven't been able to get into KDE. Everytime it launches, and those dozens of sidebars, text-based toolbars, icon-based toolbars, dropdown boxes, collapsible lists, footers, and panes appear, I feel a sinking feeling in my stomach. That said, it launches in a third of the time it takes Nautilus.)
[/LIST]
In the end, the broken PCMCIA system was a deal-breaker. Even if it had worked, there were too many things about the experience that were frustrating compared to Ubuntu.

I popped in my Feisty Herd Four disc, answered six questions, ran "sudo apt-get update && sudo apt-get dist-upgrade", and was back to the comforts of Gnome and Ubuntu, with everything working perfectly out of the box. (And Feisty is an alpha(!) release.)

---

### Post by karellen on 2007-03-20
I know what you mean, I've tried opensuse/sled myself ;)

---

### Post by julian67 on 2007-03-20
> **talkingwires said:**
> :[LIST]
[*]The internet installation disc could not download the list of packages from SuSE's repos. I tried fifteen different mirrors listed on SuSE's site, and every single one errored off with a  "connection reset" messsage.Which leads to...
[*]There is no "one CD" installation. You have to download five whole CDs to get a basic desktop. During the installation, SuSE only needed five or six files off three of the discs. I spent an hour downloading each disc and then burned them to CD-Rs only to find the installer needed about ten megabytes of stuff off of each.
[*]The kernel would do a hard lock if I had my PCMCIA wireless card plugged in. This was before and after the install. This same setup works fine in Ubuntu.
[*]The community support is non-existent compared to Ubuntu's. I spent a whole day trying to find information on my PCMCIA problem. I found many posts, but only a few had responses with methods to try. But the only one anyone had replied to saying it worked was the suggestion of plugging in the card during a specific part of the boot process. It didn't work for me, and with no way to diagnose a hard lock at boot, I gave up. It looks like this problem has been around in one form or another since the SuSE 9.1 days.
[*]The desktop is very polished. I liked SuSE's replacement for KDE's menu. It was much more easy to navigate than KDE's default. (A Win95 menu filled with sixty applications that all begin with the letter "K"? Give me a break. KDE's menu is one of primary reasons I've stuck with Gnome.) That said, it seemed very "twitchy" when moving my cursor around in it. I'd make a selection, but as my cursor moved away, it would accidentally activate a different tab. This problem may have been compounded by using a synaptic pad on a laptop instead of a proper mouse.
[*]The integrated Kerry/Beagle search was nice, but for some reason, SuSE installed half of the Gnome desktop in order for it work.
[*]Having all the configuration tools in one utility (YaST) is convenient. But the presentation feels very cobbled together. Clicking on something would launch a new window, and another, and another. And it would run some sort of linking script after you used each one, often if you were just canceling out of it.
[*]Clicking on some YaST modules would issue a prompt saying they were not installed. (Why are the appearing in YaST if they're not installed?) I would insert the CD it prompted me for, but YaST would not recognize it. If SuSE can download online updates, why can't it install packages from the Internet, too?
[*]The default theme is very nice. Hell, the installer's spash screen blew me away. It's doubly impressive on an LCD screen. Try it, and you'll see what I mean.
[*]I loved being able to pick and choose the packages I wanted to install without worrying about the ubuntu-desktop metapackage. But why is OpenOffice an all-or-nothing package? Why do I have to install 330Mb of stuff just to use Writer?
[*]After using RPMs again, I remembered why I jumped to Debian in the first place. Ugh. (Which reminds me. I haven't used Debian in years, either. Maybe it's time to see what they've been up to?)
[*]I just can't get over the KDE environment itself. Everything feels cobbled together, and you can really tell that it has a hundred people working on a hundred different parts of it. There are dozens of little applets and icons splayed all over the screen. SuSE's menu helps reduce the clutter significantly, but I just like how Gnome fits together perfectly and each app has a consistent interface. If a little bloat and loss of configurability is the price to pay, then so be it.
[*]That said, I really like many of KDE's applications. Amarok has no peer. Some may call it bloated, but try managing 40Gb of music and syncing that to an iPod with XMMS. It can be done, but not with the speed and convenience of Amarok. K3B is the best Linux burning tool, hands down. And even with it's shockingly cluttered interface, I appreciate Konqueror's I/O slaves that make CD ripping and iPod syncing a cinch. (Now that I think of it, Konqueror is probably the second reason, after the menus, that I haven't been able to get into KDE. Everytime it launches, and those dozens of sidebars, text-based toolbars, icon-based toolbars, dropdown boxes, collapsible lists, footers, and panes appear, I feel a sinking feeling in my stomach. That said, it launches in a third of the time it takes Nautilus.)
[/LIST]
In the end, the broken PCMCIA system was a deal-breaker. Even if it had worked, there were too many things about the experience that were frustrating compared to Ubuntu.

I popped in my Feisty Herd Four disc, answered six questions, ran "sudo apt-get update && sudo apt-get dist-upgrade", and was back to the comforts of Gnome and Ubuntu, with everything working perfectly out of the box. (And Feisty is an alpha(!) release.)

I can maybe address a few of those issues: 

Not connecting to repos...odd, never experienced this except with 10.1 and its notorious flaky new package management...not heard of it from anyone else either.  10.2 is fixed, works fine. But there's no denying that the Debian and Ubuntu mirrors are more widespread and faster than openSuse's, and probably every other distro too. 

You don't need 5 CDs for the desktop. > You need CDs 1-3 for a normal installation with just GNOME or KDE in english, french, italian, spanish, german, brasilian portugese, chinese, japanese and czech That's clearly stated on the opensuse download page. You also have the option of a net install using one small CD. I've never tried it with openSuse but it worked well for me with Debian. 

Community support: perhaps a matter of taste but Suse has been around a long time and it shows in the 2 main forums with the expertise and depth of knowledge on hand. The forums are pretty clearly about openSuse and there isn't really an attempt to make a gigantic forum like this one with sections encompassing politics, religion, other operating systems, cafe, christian edition and so on. I use both Ubuntu and openSuse and I find the technical advice  at Suse forums is at least as good as here, but if you want to just hang out and shoot the breeze suse forums are not the place to do it...not unfriendly at all, just focussed.   Novell also publishes 1st class documentation, podcasts and so on. Ubuntu docs are high quality but there are plenty of gaps. Suse has just been around longer so has the advantage. 

If you install beagle on a KDE desktop (from any distro) you're going to get  some Gnome libraries. It's not a Gnome application but needsGLib and depending on any other Gnome apps you selected further Gnome libraries might be installed to make Beagle work with them.   

I have to agree with you that K3b and Konqueror are impressive .....that's why I use them even on my openSuse Gnome desktop :) Given a little time you could probably configure Konqueror to look less busy....though when I install Kubuntu i make sure I restore  to default as Kubuntu Konqueror is strangely and unfortunately "simplified". Gnome in openSuse is great too....except for the horrible slab menu...that soon went from my desktop, replaced by the traditional Gnome menu.

YaST:  On Debian and derivatives I find gui config tools are spread out among different menus and sub-menus and if you really want to get down to the nitty gritty it's still the command line. Something people often miss with YaST is that the gui  tool is YaST2. The original still can be run in the terminal, so you don't even need x server up to run it, and it can be run remotely *edit - added:* from any terminal, again no x server required.  It also means if you do something real clever like break your x-server/DE you can likely fix it using a menu driven tool instead of navigating from the prompt and typing commands. 

RPM vs deb: Really it all depends on how well the applications are packaged. I've had situations where apt couldn't resolve dependencies but I could. It's not the tool it's the package. As an aside you might soon find that Ubuntu moves away from apt and favours Smart. Mark Shuttleworth has been talking about this recently. 

As for your PCMCIA wireless card I don't know the hardware or specific problem so can't comment but my experience with Ubuntu and openSuse hasn't made me think either has any superiority in hardware detection.

As for the slow install, there's no denying it. It can take nearly as long to install openSuse as it does to install Ubuntu and then remove all the stuff I didn't want but wasn't asked ;)

edit: reading your post again and the odd problems you had I'm wondering if your CDs were good. md5sum checked? Burns verified? Quality media? Just a thought.

---

### Post by talkingwires on 2007-03-20
> **julian67 said:**
> Not connecting to repos...odd, never experienced this except with 10.1 and its notorious flaky new package management...not heard of it from anyone else either.I ran into this issue while using the internet installation CD. It would download most of the repository information, then seem to time out. I'm on DSL, and it's not the fastest connection in the world, but it should be good enough to download some package descriptions without getting kicked from the server. I tried many mirrors, all with the same result. I'm not sure what the issue was, so I just downloaded the whole installation.

> You don't need 5 CDs for the desktop.  That's clearly stated on the opensuse download page.You're right. I actually configured my install to remove a lot of stuff I wouldn't use, but now that I think about it, I added SuSE's "build-essential" meta package at the last minute. (Sorry for the Debian-centric description. ;))

> Community support: perhaps a matter of taste but Suse has been around a long time and it shows in the 2 main forums with the expertise and depth of knowledge on hand.It's true that many of the replies I read were quite technical. It was a nice change, where here many of the replies are pretty hazy, along the lines of "Do an lsmod and tell us the output." The SuSE guys skipped right to the chase, which was actually a nice change and the responders clearly knew the system well. But none of them were able to resolve something as fundamental as PCMCIA freezing a laptop. It's not their fault, but if neither the devs and the community can solve the issue, it's a dealbreaker.

> If you install beagle on a KDE desktop (from any distro) you're going to get  some Gnome libraries.Well, it's a Mono app, so I'd expect some Gnome packages. But looking at the final install, it looked like half the Gnome desktop had been installed. Random things, like gnome-keyring and gnome-panel. Surely Beagle doesn't depend on gnome-panel? After playing with Kubuntu, which installs without any packages from other DEs, I thought it was very odd and seemed a little sloppy. Then again, I know that SuSE is concentrating on Gnome now, so providing a clean KDE environment probably isn't their highest priority.

> YaST:  On Debian and derivatives I find gui config tools are spread out among different menus and sub-menus and if you really want to get down to the nitty gritty it's still the command line.I agree completely, but I think this is more of an issue with Gnome and KDE. Debian and Ubuntu don't really seem to be pushing for an integrated configuration utility, which is a shame.

> Something people often miss with YaST is that the gui  tool is YaST2. The original still can be run in the terminal, so you don't even need x server up to run it, and it can be run remotely[QUOTE]sudo dpkg-reconfigure xserver-xorg ;)
I know, I know, it's not even in the same league as YaST. I guess the point I was trying to make in the OP was that YaST feels very hack-y. It was just the impression I got when I saw what looked like terminal output being spewed each time I closed a window. It looked and ran very similarly to the way I remember it from SuSE 9. It's nice that it's there, but after all the work Novell has done, I guess I was just expecting more polish. Maybe I should have spent more time with it to appreciate its ins and outs.

[QUOTE]As for your PCMCIA wireless card I don't know the hardware or specific problem so can't comment but my experience with Ubuntu and openSuse hasn't made me think either has any superiority in hardware detection.My system is a Dell Latitude 640. It is a laptop system that is configured for businesses, not consumers. (I picked it up from my father. It was standard issue at the military base where he works, so I can only assume that it is standard issue at all US Marine bases. My point is, it is very common hardware.) My wireless card is a Netgear MA401. I've used both with Windows,  Ubuntu, and Knoppix without any issues. True, those distros are all based on Debian, but still, c'mon.

> edit: reading your post again and the odd problems you had I'm wondering if your CDs were good. md5sum checked? Burns verified? Quality media? Just a thought.I only checked the first disc. But I downloaded the discs over Bittorrent, which validates files as it goes. As for the media itself, I haven't had an issue with it before, but you're right, I didn't verify it before installing.

Anyway, thanks for your comments. I guess I'm just disappointed, as I would have liked to spend more time with SuSE, as it looked promising.  But the PCMCIA problem really is a show stopper, since it leaves me without wireless Internet. I just wish I knew how to diagnose the problem, but I'm not familiar enough with SuSE to know where to begin. Like I said, it's hard to tell what's going on when the whole system freezes a few seconds into the boot process.

---

### Post by tubasoldier on 2007-03-21
Interesting, I use KDE on Ubuntu. You could say I use Kubuntu but I never use the Kubuntu disk to install because it's installer always hangs on the partitions. On my laptop and desktop.

I just install kde-core and then any other KDE programs that I like using. 
Your description of Konqeror is the reason I use it. Of course I personalize it a bit so there is no sidebar. This helps unclutter it quite a bit. But the KIO Slaves are totally cool. I do believe that KDE has too many options. Having the choice between an easier configuration tool and an all out configuration tool would be great. The fact that in order to tweak Gnome you have to go into gconf isn't very exiting to me. And the little things like only one background image at a time. No random wallpaper. No random wallpaper on different desktops. No tabs available in Nautilus. Tabs are extremely useful and help keep the desktop clutter down. Maybe one day Gnome will give its users a little more functionality, but until then I'll just stick with KDE.

---

### Post by julian67 on 2007-03-21
> **talkingwires said:**
> I ran into this issue while using the internet installation CD. It would download most of the repository information, then seem to time out. I'm on DSL, and it's not the fastest connection in the world, but it should be good enough to download some package descriptions without getting kicked from the server. I tried many mirrors, all with the same result. I'm not sure what the issue was, so I just downloaded the whole installation.

hmm maybe it's from the networking defaulting to ipv6 not ipv4 which is very nice and up to date on openSuse's part but not terribly useful if your router or some other part of the network, even your ISP,  doesn't fully support it yet. Typically you get very slow domain name resolution and this would time you out of pretty much any ftp server. It's easily fixed
 ```
 
 echo "alias net-pf-10 off" >> /etc/modprobe.conf
 echo "alias ipv6 off" >> /etc/modprobe.conf]
``` 

This can of course be done via YaST but not quite so fast :) 

The beagle/Gnome thing. openSuse is pretty much desktop agnostic. If you just choose a Gnome install you'll still get a few KDE apps, and vice versa, unless you pick through the package selection on install. I guess you missed one ;)

Yes YaST gui can be a bit of a maze but in the terminal it's lean and structured and  easy to use. 

Netgear MA401 generally should out of the box on openSuse 10.2, but I found this comment at the openSuse Hardware Compatibility List > 10.2 - yast recognizes and configures.. I needed to add "exclude irq 3" in /etc/pcmcia/config.opts to avoid the card from using IRQ 3 on reboot which conflicted... this could be unique to my HW...  Again if this isn't isn't the issue then I'd be feeling even more suspicious about the install media.

I hope this helps you if you want to try again, and maybe is useful for anyone else browsing around

---

### Post by wxnker on 2007-03-24
> I do believe that KDE has too many options. Having the choice between an easier configuration tool and an all out configuration tool would be great. The fact that in order to tweak Gnome you have to go into gconf isn't very exiting to me. And the little things like only one background image at a time. No random wallpaper. No random wallpaper on different desktops. No tabs available in Nautilus. Tabs are extremely useful and help keep the desktop clutter down. Maybe one day Gnome will give its users a little more functionality, but until then I'll just stick with KDE.

I use Mandriva One 2007 KDE. It's so simple and everything blends in together. Every application looks as part of ONE OS. KDE does not have to be something with to many options. In fact I find Gnome to be less user friendly than KDE in some cases. Gnome is trying to keep things so simple that the intermediate user has to do way to many things manually. (I kinda share the opinion of "Linus" there). :)  When using Gnome I had to make scripts, download scripts to give basic functionality that comes out of the box in most KDE distro's.

I can really recommend trying out Mandriva. The orange look isn't exactly pretty but it can be changed in a minute or two. Everything worked for me "out of the box" ... MP3, XGL, Compiz etc.and I haven't even touched files like "xorg.conf" yet, lol. Even Grub can be setup and edited from the menu. The Mandriva Control Center also make a lot of settings real easy to configure. 

I guess this is merely a matter of taste but I absolutely disagree in "Gnome has a more consitent interface". Most KDE applications blend in beautifully when using a finished KDE product like Mandriva. 

I also believe it's natural to find a new OS a bit messy if you have been using Gnome for a long time. After a short time with KDE I found it to be very efficient and easy to use. It's just a bit different.

It's also a matter of finding the right KDE distro. Kubuntu seems unfinished to me compared to Ubuntu. Ubuntu must be the main priority I guess. Kubuntu could easily be made much more user friendly with a little effort and I hope it will be soon because it's a real great Linux distro.
If you ask me the Kubuntu developers should do a little Mandriva brainstorming hehe.

Cheers

---

