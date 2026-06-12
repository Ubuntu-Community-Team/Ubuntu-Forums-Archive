---
title: "Anyone on 10.3?"
date: 2007-10-02
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Incense on 2007-10-02
I downloaded and installed the RC1 of 10.3, and to be honest, I'm really not too impressed. Package Managment through YaST feels worse then it did before, and overall it just feels less polished then 10.2 did. I've been a SUSE user for years, and I don't know if Novell is just leaving a bad taste, or what is going on, but Kubuntu 7.10 is looking pretty nice right about now. Anyone else feeling the same way?

---

### Post by santiagoward2000 on 2007-10-02
> **Incense said:**
> I downloaded and installed the RC1 of 10.3, and to be honest, I'm really not too impressed. Package Managment through YaST feels worse then it did before, and overall it just feels less polished then 10.2 did. I've been a SUSE user for years, and I don't know if Novell is just leaving a bad taste, or what is going on, but Kubuntu 7.10 is looking pretty nice right about now. Anyone else feeling the same way?

Hey, sorry man, but... 10.3? What distro are you talking about? SUSE?

---

### Post by Incense on 2007-10-02
> **santiagoward2000 said:**
> Hey, sorry man, but... 10.3? What distro are you talking about? SUSE?

Yeah OpenSUSE 10.3 Sorry, thought I put it in the OpenSUSE section.

---

### Post by igknighted on 2007-10-02
Really?  I thought 10.3 was the best in a long time.  Yast was great, it automatically added all the community repos I wanted (atheros, pacman, etc.), and was much faster than 10.1/10.2.  The GUI version didn't seem to want to use the YUM repos, but using zypper via the CLI (which is so much better anyways) worked perfectly.

I thought the green was a welcome change from the drab blue that we have had the past few releases.  Also the desktop just felt a little more responsive (although suse is always one of the least responsive distro's for me, unfortunately).

I still prefer Mandriva and Fedora over it, but Suse 10.3 is a great release, and I'll keep my eye on it in the future.

---

### Post by santiagoward2000 on 2007-10-02
Actually, I'm pretty new in Linux, and haven't tried any distro apart from the Ubuntu family. How is it?

---

### Post by sstusick on 2007-10-02
I haven't had good luck with SuSE...used 10.2 for 5 months...and it was one headache after the other. Crashing, YaST was slow, system slowness in general...an overrated distro, IMO. I finally gave up and went back to Windows for a couple months before trying Ubuntu and everything worked fine with NO issues and had the speed to boot.

---

### Post by theonlyrealperson on 2007-10-03
I'm on 10.3, and there are definitely pluses and minuses.

Pluses:
1. Yast seems a LOT faster. It's still not quick - not by a longshot - but it is much faster than the glacial 10.2.
2. Color scheme is much better.
3. Being able to add in repos without searching the net. Nice...
4. ONE DISK. Very nice. Still downloads a couple of gig during the install though. 

Minuses:
1. I know it's a release candidate, but it doesn't seem as solid as 10.2. I don't know if it's 10.2 vs. 10.3 or Gnome vs. KDE though. I've crashed a couple of times, the window manager will lose my USB drives, X11 never configures my resolution correctly after every reboot, etc. I moved from Gnome 10.2 to KDE 10.3, so I don't know if it's a version or manager deal...
2. Compiz-Fusion worked flawlessly in 10.2. Can't even get the sucker to install correctly in 10.3. Even with the 1-Click installer. 
3. Still a HUGE distro, comparatively. Need lots of / space.

I'm actually thinking of going back to 10.2 until a couple of months after 10.3 goes final. I don't know...

---

### Post by LuisAugusto on 2007-10-03
I'm using OpenSUSE 10.3

Overall, it's one (if not) the best distro I have ever use.
It's fast, it can be install with one CD (finally), BuildService is great, it have the best configuration tool ever made (YaST), it has a nice desktop by default (both KDE and GNOME versions), it only down it's possibly that package management is a little slow, BECAUSE IT REFRESH EVERY DAMN TIME THE REPOS (I can't understand why it behavior that way).  

It feels very polished, and pro, it doesn't feel like a toy or a distro to play around some days (I love elive and e17, but, don't they give you that feeling?)

---

### Post by Erunno on 2007-10-03
I've been using the GNOME flavour of 10.3 since RC1 since I was curious about the current state of GNOME (can't participate in flame wars when I completely don't know what I'm talking about ;-)). Some random impressions and obersavations:

GRUB cannot be installed on a XFS partition and this is not fixable with an online update since they are applied after the basic installation. I'm hoping that this is fixed on the gold master.

There are still some bugs left on my installation: Totem and Banshee don't work due to some GStreamer bug. The updater applet hangs after successfully installung updates (it just freezes).

The new unified look of the application browser, the control center and Yast gives the desktop a very coherent look.

You can easily add additional repositories right via the Yast module "Community repositories" although the selection is a bit strange (KDE4 for instance is missing).

Yast is a LOT faster than in 10.3. On the other hand, it's nigh to impossible that it could be any slower. It still refreshes the repositories each time you start it but from what I've read you can tweak this behaviour by increasing the intervall between refreshes.

I really like SLAB. Like Kickoff once I added my favourite applications to the favourite list I rarely visited the application browser. What I miss from Kickoff is the inline output of search results, SLAB opens a separate window for that.

I really don't like the new GNOME frontend to the Yast software management. It feels cramped and has some real shortcomings: It's slow (switching between different views takes too long), it feels very cramped and it doesn't show which dependencies will be installed until you hit the accept button (which forces me into a "Accept / Cancel" loop in order to check the dependencies). There are also some up and down arrows and it's not obvious to me what they do.

There's no way to see which package upgrades will be installed via the GUI. Even the details view only shows which (incremental) updates will be installed, not new package versions. You'll have to check the logs or use the CLI tool.

Adding the online repositories before the installations results in Yast adding about a GB of additional packages without asking the user first. Not adding the repositories will result in a non-localized (not translated) desktop with no obvious way to fixing this except looking for the translation packages yourself. Pick your poison.

Virtuals desktop functionality is disabled on the GNOME desktop, meaning that they use only one desktop and removed the applet for switching. I'm curious why this was done.

Verdict: Very good release with some bugs left to iron out and some questionable design decisions. The GNOME implementation is excellent, and that is coming from a KDE user.

---

### Post by Incense on 2007-10-03
I'm just going to reinstall from scratch then (wipe my home part) and see what I get. I was expecting the experience that you are all describing, which is why I asked. My problem with YaST is that Resolving Dependencies box that pops up for a second, every time I click on a package. The community repo's are very easy to add, but I could not get Guru to load for some reason. I do like the green, it's a very nice change, and the KDE4 games look great. Thanks for the replies, I'll try again.

---

### Post by Erunno on 2007-10-03
> **Incense said:**
> I'm just going to reinstall from scratch then (wipe my home part) and see what I get. I was expecting the experience that you are all describing, which is why I asked. My problem with YaST is that Resolving Dependencies box that pops up for a second, every time I click on a package. The community repo's are very easy to add, but I could not get Guru to load for some reason. I do like the green, it's a very nice change, and the KDE4 games look great. Thanks for the replies, I'll try again.

If you're using the Qt frontend to Yast just disable the "Automatic Dependency checking" or whatever it is called, that should get rid of the popup (never noticed it to be honest). Guru is in the process of being absorbed by Packman so in the long run it shouldn't be necessary to use them both. I don't know how far the merging is.

Apropos, it seems like the gold master leaked 2 days ago:

[http://www.isohunt.com/torrents/opensuse+10.3+GM]("http://www.isohunt.com/torrents/opensuse+10.3+GM")

---

### Post by RedDwarf on 2007-10-03
I'm going to use Smart with 10.3. Even if YaST package manager would be the faster one I would still prefer the smart interface... with Smart it's a lot easier to know what are you doing, what packages are adding what dependencies, etc. Smart needs a little hand made configuration with repository priorities and some package locks... but after that the updates/upgrades that Smart proposes are always the ones that make sense.
YaST has some nice features... "patterns" are usefull to install all the translations to your language for the installed packages if you need to. But his interface looks counterintuitive to me. When everything goes fine it's ok, but when there are problems... you want to use Smart.
But if you forget the YaST package manager everything is ok, at least for a KDE user.

---

### Post by darksong on 2007-10-03
I am on 10.3 now, some server didn't lock the folder that it was in so i downloaded it and installed it. The only differences i can tell from 10.2  is;

1 - more confusing package management
2 - green instead of blue
3 - poorer fonts and icons

The package manager is different. But not better, it may be faster but the sheer lack of description and decent categories makes it fell crappy. Also i can't get any online repo's, none are listed in the software sources.  One of the package mangers is the same as the one in 10.2.

Overall its not bad, the theme is practically the same as 10.2, the icons in YAST are of much lower resolution than in 10.2, fonts not as nice, green, different package manager.

---

### Post by LuisAugusto on 2007-10-03
> **darksong said:**
> I am on 10.3 now, some server didn't lock the folder that it was in so i downloaded it and installed it. The only differences i can tell from 10.2  is;

1 - more confusing package management
2 - green instead of blue
3 - poorer fonts and icons

The package manager is different. But not better, it may be faster but the sheer lack of description and decent categories makes it fell crappy. Also i can't get any online repo's, none are listed in the software sources. 

Overall its not bad, the theme is practically the same as 10.2, the icons in YAST are of much lower resolution than in 10.2, fonts not as nice, green, different package manager.

It didn't lose anything. Just use the Qt front-end of YaST.

What in the world do you want from them? Isn't Build Service enough by itself? The new gnome? New KDE? New Kernel? New X.org?New GTK YaST front-end? New SLAB Menu? Booting a lot faster than 10.2 (and than Ubuntu...)? Using the new libzyyp, which is a lot faster?

I believe they did a nice job with this release.

---

### Post by RedDwarf on 2007-10-03
> **darksong said:**
> The package manager is different. But not better, it may be faster but the sheer lack of description and decent categories makes it fell crappy.
I don't see a single difference between the interface of the YaST package manager from 10.2 and the one from 10.3. The only difference is libzypp... and for sure now it's better.

> **darksong said:**
> Also i can't get any online repo's
Since they will not be available until tomorrow, with the official release, isn't a surprise.

> **darksong said:**
> the icons in YAST are of much lower resolution than in 10.2
Crystal theme is still available in 10.3. But anyway... if you make a rpm -ql yast2-theme-openSUSE for the two packages you will see both are of the same resolution.

> **darksong said:**
> fonts not as nice
Isn't everybody using the Microsoft ones? Because the file /etc/fonts/suse-generic-names.conf hasn't been modified a byte.

---

### Post by Erunno on 2007-10-03
> **RedDwarf said:**
> I don't see a single difference between the interface of the YaST package manager from 10.2 and the one from 10.3..

The GNOME version of 10.3 has a brand new GTK+ based Yast frontend which in my humble opinion is pretty crappy (at least the software management module ) for reason already outlined.

---

### Post by RedDwarf on 2007-10-03
> **Erunno said:**
> The GNOME version of 10.3 has a brand new GTK+ based Yast frontend which in my humble opinion is pretty crappy (at least the software management module ) for reason already outlined.
Sure. I have not tried it, but being new I expect something worse than the QT version. But darksong has not said anything about GTK+, and since it is comparing with the 10.2 version I suppose he is talking about the QT one.

---

### Post by screaminj3sus on 2007-10-03
I haven't had the chance to try 3 yet, but the damn package management in 2 was so impossibly slow, and the boot time was the worst, RIDICULOUSLY slow, I mean even vista roared past suse in boot time. Took suse like over 2 damn minutes to boot, ubuntu is damn near instant. Hopefully things improve in 10.3 I have always loved suse's level of polish on the gui and their great gnome implementation.

---

### Post by sstusick on 2007-10-04
Is Suse 10.3 final now officially released?

---

### Post by tehhaxorr on 2007-10-04
> **theonlyrealperson said:**
> I'm on 10.3, and there are definitely pluses and minuses.

Pluses:
1. Yast seems a LOT faster. It's still not quick - not by a longshot - but it is much faster than the glacial 10.2.
2. Color scheme is much better.
3. Being able to add in repos without searching the net. Nice...
4. ONE DISK. Very nice. Still downloads a couple of gig during the install though. 

Minuses:
1. I know it's a release candidate, but it doesn't seem as solid as 10.2. I don't know if it's 10.2 vs. 10.3 or Gnome vs. KDE though. I've crashed a couple of times, the window manager will lose my USB drives, X11 never configures my resolution correctly after every reboot, etc. I moved from Gnome 10.2 to KDE 10.3, so I don't know if it's a version or manager deal...
2. Compiz-Fusion worked flawlessly in 10.2. Can't even get the sucker to install correctly in 10.3. Even with the 1-Click installer. 
3. Still a HUGE distro, comparatively. Need lots of / space.

I'm actually thinking of going back to 10.2 until a couple of months after 10.3 goes final. I don't know...

Did you report the bugs?

[http://en.opensuse.org/Submit_a_Bug](http://en.opensuse.org/Submit_a_Bug)

No use complaining if you aren't prepared to tell them what's wrong.

---

### Post by subzero1266 on 2007-10-04
> **sstusick said:**
> Is Suse 10.3 final now officially released?
It is scheduled to release today (Oct 4). But I am still seeing 10.2 downloads in the official site.

---

### Post by sstusick on 2007-10-04
> **subzero1266 said:**
> It is scheduled to release today (Oct 4). But I am still seeing 10.2 downloads in the official site.
Thanks.

---

### Post by michaeljking on 2007-10-04
I managed to grab the Torrent for it from the Distrowatch weekly news feedback section, I have had the KDE version on my spare computer for a few days and I am impressed with the overall feel and running.  Nothing too suprising, but I have not found any problems yet like I did with the pre-release version.   The install took hours and hours though  (CD version grabs the extra stuff of the internet)
The funny thing was that I had been running fedora 7 on it and it couldnt access my Ubuntu or windows partitions but Suse found them and gave them there own grub screen sub menu.  It was very bizarre seeing ubuntu 6.06 again!!

I used the [http://opensuse-community.org/Multimedia](http://opensuse-community.org/Multimedia)   page to install the codecs to get things running, though I have heard that mp3's work out of the box through amarok.   It was easy to set up though I did need to download the KDE british english package using YAst.  (Yast is better but still slower than Synaptic on Ubuntu/debian)

My main PC runs Ubuntustudio that I love using and wont be changing in any hurry, and my main laptop runs Ubuntu 7.04  

Looking forward to Gutsy!!

---

### Post by Antman on 2007-10-04
I'm downloading via torrent now. hmm... I **hope** this version is a lot quicker then 10.2

---

### Post by Incense on 2007-10-04
The download page is showing 10.3 now. I got it reinstalled and so far it's working great! Much better then before, and much faster this time round. It's really too bad this such a great distro is being ignored by a lot of the linux community due to the whole Novell deal.

---

### Post by mindtrick on 2007-10-04
Using it (Gnome Version) now in Virtualbox, I'm very tempted to install it to my harddrive. 

*Thinks a bit

-Where's my blank cd!

---

### Post by mindtrick on 2007-10-04
Does anyone know how to enable font smoothing for Firefox? It's very irritating that they've changed this setting.

---

### Post by Antman on 2007-10-04
> **mindtrick said:**
> Does anyone know how to enable font smoothing for Firefox? It's very irritating that they've changed this setting.

Go here:
[http://opensuse-community.org/SubpixelHinting]("http://opensuse-community.org/SubpixelHinting")

---

### Post by mindtrick on 2007-10-04
Oh, thanks.

---

### Post by sstusick on 2007-10-04
I guess I'll download 10.3 and try it. I've heard nothing but good things about it. I didn't have much luck with 10.2.

---

### Post by Antman on 2007-10-04
One thing that has always irked me about Suse is the long install times. Even the 10.3 gnome CD took a over 30 minutes to install (i started to play xBox while waiting... :lolflag: ). I have been so used to super fast 6 to 10 minute installs from my main distros that I forgot that installs could still be slow on other distros.

But once installed, it's not too bad. I love the theme and colors. I think I'll install KDE and use it instead though, the menus in the Gnome version is making me dizzy.

---

### Post by Incense on 2007-10-04
> **Antman said:**
> One thing that has always irked me about Suse is the long install times. Even the 10.3 gnome CD took a over 30 minutes to install (i started to play xBox while waiting... :lolflag: ). I have been so used to super fast 6 to 10 minute installs from my main distros that I forgot that installs could still be slow on other distros.

But once installed, it's not too bad. I love the theme and colors. I think I'll install KDE and use it instead though, the menus in the Gnome version is making me dizzy.

Yeah, my install two near two hours. One thing I do like about Ubuntu is the super fast install, and playing with the live CD while the install is going on. It's all good though. I'm really digging the new release.

---

### Post by Antman on 2007-10-04
> **Incense said:**
> Yeah, my install two near two hours. One thing I do like about Ubuntu is the super fast install, and playing with the live CD while the install is going on. It's all good though. I'm really digging the new release.

Yes install is slow, but after the install it is certainly faster then 10.2. Also I like the fact that you can add the extra repos just by clicking on yast> community repos... and clicking on the ones you want. I don't recall if that was in 10.2 or not.:confused: 

So far on my laptop:
1. Suspend works
2. Wireless works (ipw3945)
3. Logictech QuickCam® Ultra Vision SE webcam doesn't work (works out of the box in Ubuntu)
--   a. installed webcam drivers in the webcam repo with no luck so far
4. Haven't tried video accelleration yet.

---

### Post by justin whitaker on 2007-10-04
I have to say, it's nice to see openSUSE swinging for the fences. The new features list looks pretty good...I've downloaded it, just trying to figure out what partition I want to blow up.

Man, with Gutsy, 10.3, and Mandriva 2008 it's a great season to be a Linux user. :)

---

### Post by WanderingKnight on 2007-10-04
I'm downloading the DVD before going to bed now, should be done by tomorrow morning. It'll be my first time installing OpenSUSE.

I'm wondering, some people were talking about the huge space required by OpenSUSE... I've got two free partitions (6 GB and 20 GB) I was planning to use for the installation, but now I'm wondering if the 6 GB partition will be enough to hold the system. Currently it holds a 2 GB Debian install which has broken fonts and an unknown root password (I forgot it, haven't booted it in a long time. Originally it was a rescue partition in case something went wrong with Ubuntu) so I'm planning on nuking that ASAP.

Also, were I to install GRUB on the MBR, it should recognize and let me boot Ubuntu perfectly, right?

---

### Post by sstusick on 2007-10-05
A Friend of mine said his install of 10.3 took over 2 hours... I think that's ridiculous.

---

### Post by Erunno on 2007-10-05
> **WanderingKnight said:**
> I'm downloading the DVD before going to bed now, should be done by tomorrow morning. It'll be my first time installing OpenSUSE.

I'm wondering, some people were talking about the huge space required by OpenSUSE... I've got two free partitions (6 GB and 20 GB) I was planning to use for the installation, but now I'm wondering if the 6 GB partition will be enough to hold the system. Currently it holds a 2 GB Debian install which has broken fonts and an unknown root password (I forgot it, haven't booted it in a long time. Originally it was a rescue partition in case something went wrong with Ubuntu) so I'm planning on nuking that ASAP.

Also, were I to install GRUB on the MBR, it should recognize and let me boot Ubuntu perfectly, right?

People are vastly exaggerating when it comes to SuSE's disk requirements: A default installation from either of the CDs takes up about 1.6 GB space. In case you activate the online repositories before the installation it will grow to 2.3 GB. As an additional benefit SuSE allows you to add or remove packages before the installation takes place. I've been using a 5 GB root partitions for years and never ran out of space but your mileage may vary.

And it *should* recognize the Ubuntu partition, just check the GRUB configuration before starting the install process (that is, before any changes to the disk are made).

---

### Post by mjwhitfield on 2007-10-05
> **sstusick said:**
> A Friend of mine said his install of 10.3 took over 2 hours... I think that's ridiculous.Maybe he should have picked the packages he wanted to install more carefully? My install took about 15 mins.

---

### Post by sstusick on 2007-10-05
> **mjwhitfield said:**
> Maybe he should have picked the packages he wanted to install more carefully? My install took about 15 mins.
Yeah... didn't think of that. He probably selected them all. He isn't too swift anyway.

---

### Post by mjwhitfield on 2007-10-05
If people are too lazy to customise their installs, they deserve a long wait and a clunky system.

I'm joking of course.  Next time maybe suggest he tries the KDE/GNOME CD install.

---

### Post by sstusick on 2007-10-05
I believe he downloaded the GNOME CD. He's s a newb and complained to me for 2 hours at how long the install was taking. I told him it shouldn't take that long and remembered when I had installed SuSE 10.2, the installation took less than 30 minutes.

---

### Post by mjwhitfield on 2007-10-05
Even with all the packages being selected on the CD, it shouldn't take that long.

Either a duff burn, or a dying CD drive.

---

### Post by kiran_aryan on 2007-10-05
Downloaded Gnome CD and installed. It took about 30mins in total for the installation. So far, my experiences -

1. Black screen at the GDM on my first boot. So, I had to change nv to vesa in my xorg.conf in the failsafe mode and restart.

2. Couldn't configure my DSL connection because the Gnome CD was missing smpppd.rpm (This rpm was included in KDE CD installation!). So, I had to download the package using Ubuntu live cd (which has pppoeconf to configure my DSL). After installing the rpm, I could connect to the internet.

3. 1-click install is good. I installed nvidia drivers and multimedia codecs & plugins with that but the servers were a bit slow.

4. YaST is fast...really very fast when compared to my openSUSE 10.1 experience.

5. Boot times are quick and the OS is much more responsive than what I thought. PC is stable.

Overall a good release! My Rating - 8.5/10

---

### Post by sstusick on 2007-10-05
I'm installing 10.3 into Virtual Box as I type this, about 20 minutes left of installation time. 

I'll post my thoughts on the release after I evaluate it a little.

---

### Post by Antman on 2007-10-05
Ok, after trying the OpenSuse Gnome CD install for about an hour or two, I burnt the DVD edition and quickly reinstalled OSuse 10.3 with KDE instead. 
I have to say that so far I like the KDE version a lot better then the Gnome version. The KDE kicker is pretty good and well laid out, compared to the gnome counterpart.

Also, this time I had my Logitech Ultra Vision usb webcam plugged into the laptop during the whole install and when I logged in for the first time and fired up Kopete, the webcam was working. :)

Suspend works when I press the suspend button, wireless works, Openoffice launched pretty quickly, and the system in general is pretty snappy compared to 10.2.

So I guess I'll keep this on my test laptop for a while longer so I can try it out more. Hmm... if this keeps up, I may have to partition my desktop HD again to make room for OpenSuse. ;)

---

### Post by r4ik on 2007-10-05
While downloading 10.3 i wonder if anyone can tell me something about Flash.
Is it less buggy in firefox or does the problem in Youtube as an example remains.
If it is there no reason for me to install.
Thanks !

---

### Post by Incense on 2007-10-05
> **Incense said:**
> Yeah, my install two near two hours. One thing I do like about Ubuntu is the super fast install, and playing with the live CD while the install is going on. It's all good though. I'm really digging the new release.

I have to retract this statement. I was using an old beta of 10.3 to reinstall, and I had to download a lot of packages. I just reinstalled (again) using the GM DVD, and it only took about 30 mins. I am really digging this release. It looks beautiful, it's very fast, I just need to find a good NES emulator for it. ;)

---

### Post by Incense on 2007-10-05
> **r4ik said:**
> While downloading 10.3 i wonder if anyone can tell me something about Flash.
Is it less buggy in firefox or does the problem in Youtube as an example remains.
If it is there no reason for me to install.
Thanks !

You want to try the update your flash player and see if that helps. 

[http://labs.adobe.com/technologies/flashplayer9/]("http://labs.adobe.com/technologies/flashplayer9/")

---

### Post by Antman on 2007-10-05
> **r4ik said:**
> While downloading 10.3 i wonder if anyone can tell me something about Flash.
Is it less buggy in firefox or does the problem in Youtube as an example remains.
If it is there no reason for me to install.
Thanks !

Flash 9 in linux SUCKS. In EVERY distro I have tried so far Firefox will hang after awhile of watching youtube or Cnet vids. Flash 7 seems to work a lot better for youtube. unfortunately cnet and other site force you to use flash 9 now. :(

---

### Post by Antman on 2007-10-05
> **Incense said:**
> You want to try the update your flash player and see if that helps. 

[http://labs.adobe.com/technologies/flashplayer9/]("http://labs.adobe.com/technologies/flashplayer9/")

Cool, this was released Oct, 1. Hopefully it fixes the crashing issues.

---

### Post by greymongrey on 2007-10-05
It's my first time to try OpenSuse and I must say I am impressed. It's probably not as easy to set up as PCLinuxOS but it is on the same level as Ubuntu. I really love Yast, though I haven't quite got the hang of it yet. I think I will keep it on my computer for a while. :)

---

### Post by Antman on 2007-10-05
> **Incense said:**
> You want to try the update your flash player and see if that helps. 

[http://labs.adobe.com/technologies/flashplayer9/]("http://labs.adobe.com/technologies/flashplayer9/")

Well... I thought this update fixed the firefox freezing issue, but after playing on Youtube for about 45 minutes, it froze. It's an improvement though, firefox froze after about 8 minutes before the update... lol

---

### Post by RedDwarf on 2007-10-05
> **sstusick said:**
> I believe he downloaded the GNOME CD. He's s a newb and complained to me for 2 hours at how long the install was taking. I told him it shouldn't take that long and remembered when I had installed SuSE 10.2, the installation took less than 30 minutes.
He downloaded the Gnome CD... and then installed 4GB of packages from the online repository through a 56Kbps modem?

---

### Post by Incense on 2007-10-05
> **greymongrey said:**
> It's my first time to try OpenSuse and I must say I am impressed. It's probably not as easy to set up as PCLinuxOS but it is on the same level as Ubuntu. I really love Yast, though I haven't quite got the hang of it yet. I think I will keep it on my computer for a while. :)

Let us know if you have any questions. It's a great distro.

---

### Post by Antman on 2007-10-05
hmmm... interesting. Can't seem to get the ati flgx drivers to work. I activated the ati repo in Yast and downloaded installed the driver for my kernel with no luck.

Time to hunt on the Suse forum to see what step i missed.:confused:

---

### Post by r4ik on 2007-10-05
> **Incense said:**
> You want to try the update your flash player and see if that helps. 

[http://labs.adobe.com/technologies/flashplayer9/]("http://labs.adobe.com/technologies/flashplayer9/")

Thanks for you're reply.
II pulled in PClos and in the short period i used it it seems to have fixed my probs with flash.
It is far to early to even guess what the reason is and  i only hope the Gutsy release has it fixed.

---

### Post by Antman on 2007-10-05
> **Antman said:**
> hmmm... interesting. Can't seem to get the ati flgx drivers to work. I activated the ati repo in Yast and downloaded installed the driver for my kernel with no luck.

Time to hunt on the Suse forum to see what step i missed.:confused:

Ok, got Ati accelleration working. while in init 3 had to: 
```

aticonfig --initial 
sax2 -r
and then reboot

```

---

### Post by LuisAugusto on 2007-10-05
> **Antman said:**
> hmmm... interesting. Can't seem to get the ati flgx drivers to work. I activated the ati repo in Yast and downloaded installed the driver for my kernel with no luck.

Time to hunt on the Suse forum to see what step i missed.:confused:

As far as I know, you have to download the ATI driver from the ATI web, and install it like this:
```

./(alotofcraponthefilename).run --builpkg SuSE/SUSE102-IA32
```

and then install the generate rpm normally.

After you install it run:

```
aticonfig --sysinstall -i -r
```

And you're done :P

PS: Pff, you found the solution at the same time I posted this trying to help XD

---

### Post by ferpadro on 2007-10-06
Right now im installing Opensuse 10.3 on a 8 GB hard disk virtual machine, and i came into my first doubt. The default partitioning is 1 partition for swap, other for /home and other for root. What are the advantages of having 1 partition for the /home and other for root over having only one unified?

---

### Post by mindtrick on 2007-10-06
> **ferpadro said:**
> Right now im installing Opensuse 10.3 on a 8 GB hard disk virtual machine, and i came into my first doubt. The default partitioning is 1 partition for swap, other for /home and other for root. What are the advantages of having 1 partition for the /home and other for root over having only one unified?

It's easier to reinstall a system if you have a separate /home partition. (You keep your personal files here like music, videos, photos) You don't format /home and keep it with different distros etc.

---

### Post by Incense on 2007-10-06
> **ferpadro said:**
> Right now im installing Opensuse 10.3 on a 8 GB hard disk virtual machine, and i came into my first doubt. The default partitioning is 1 partition for swap, other for /home and other for root. What are the advantages of having 1 partition for the /home and other for root over having only one unified?

It really is (IMO) the best method to have a separate root and home.  If you decide yo do not want to use OpenSUSE any more, you can just throw in ubuntu (or whatever) and tell it to use that partition as your new home. Providing that you do not format the home partition, all of your data will be preserved. Your programs will be gone though as they reside in your root. You can even run multiple distros at once, and allow them to share all your settings and files by both using that /home.

---

### Post by sstusick on 2007-10-06
Well I've just finished installing SuSE into Virtual Box and so far I am unimpressed. First of all, as soon as SuSE boots up after the install it wants me to login as root. It did not ask me during setup to setup users. I mine as well use Windows if I am going to run with a setup like that. Second, it did not want to connect to the internet via Virtual Box when every other Virtual Machine I have setup in Virtual Box works with no hassle whatsoever. 

All I can say is, thank god for Ubuntu. I think SuSE is an overrated distro and is getting worse with each release. If you're going to run SuSE you might as well run Windows.

---

### Post by sstusick on 2007-10-06
> **RedDwarf said:**
> He downloaded the Gnome CD... and then installed 4GB of packages from the online repository through a 56Kbps modem?
He is on a high-speed cable connection. He said he downloaded 700 MB's within 10 minutes...

---

### Post by RedDwarf on 2007-10-06
> **sstusick said:**
> First of all, as soon as SuSE boots up after the install it wants me to login as root. It did not ask me during setup to setup users.
If I remember correctly the first thing the "after first reboot installation" asks is the root password. So... perhaps are you confusing the root password configuration with a login?
The installation setups users in one of the last steps.

---

### Post by sstusick on 2007-10-06
> **RedDwarf said:**
> If I remember correctly the first thing the "after first reboot installation" asks is the root password. So... perhaps are you confusing the root password configuration with a login?
The installation setups users in one of the last steps.
Nope...after I setup the root account, it asks me to login.

---

### Post by Antman on 2007-10-06
> **sstusick said:**
> Nope...after I setup the root account, it asks me to login.

I don't recall that step in my two installs of 10.3 (Gnome CD and DVD version), but maybe I'm getting old.

---

### Post by sstusick on 2007-10-06
I have re-installed it 3 times, but still get the same process. I login as root and sit there looking stupid.

---

### Post by Antman on 2007-10-06
Ok... it's been fun playing with the new OpenSuse, but I really need a distro that is faster then this. Time to remove Opensuse 10.3 from my laptop and prepare to play with some new distros. hmmm... Zenwalk 4.8 was just released. :guitar:

---

### Post by greymongrey on 2007-10-07
I agree. 10.3 is very slow and clunky.

---

### Post by pain of salvation on 2007-10-07
openSUSE 10.3 slow?? Come on... I am a Arch Linux user, and openSUSE 10.3 boot and shutdown times are almost as fast as Arch.


Gnome is VERY responsive, too... 

Ubuntu aways was slower compared to openSUSE.

---

### Post by Antman on 2007-10-07
> **pain of salvation said:**
> openSUSE 10.3 slow?? Come on... I am a Arch Linux user, and openSUSE 10.3 boot and shutdown times are almost as fast as Arch.


As fast as Arch?!?! Not on my machines.

> Gnome is VERY responsive, too... 

Ubuntu was the first distro to get me to like Gnome. But OpenSuse made me like KDE. OpenSuse 10.3 KDE is SOOoOOo freaking pretty.:)

But while using it and installing applications, it just took way longer to install stuff via yast and the repos, then using apt-get via command line in debian distros. 

I guess I need to research it more, but I'm sure there is a way to only use the command line to install stuff in Suse.

---

### Post by pain of salvation on 2007-10-07
Yes, its is as fast as Arch on a Core 2 Duo 6300, Asus P5B-Delux, 1G RAM. I can say the shutdown time is even faster.

---

### Post by Erunno on 2007-10-07
> **Antman said:**
> I guess I need to research it more, but I'm sure there is a way to only use the command line to install stuff in Suse.

You're looking for [Zypper]("http://en.opensuse.org/Zypper"). The documentation on the wiki seems to be a bit outdated though.

---

### Post by Antman on 2007-10-07
> **Erunno said:**
> You're looking for [Zypper]("http://en.opensuse.org/Zypper"). The documentation on the wiki seems to be a bit outdated though.

Cool... thanks I'll try it out when I test OpenSuse again.

---

### Post by Incense on 2007-10-07
> **greymongrey said:**
> I agree. 10.3 is very slow and clunky.

Mine runs very slow if I don't uninstall Beagle.

---

### Post by greymongrey on 2007-10-07
> **Incense said:**
> Mine runs very slow if I don't uninstall Beagle.
Ah, nice tip. I'll remember that the next time I play with it.

---

### Post by sstusick on 2007-10-07
I don't know what you people are smoking, but I'd like some. In my experience, SuSE was as slow as Windows including crashing and locking up...though Windows never locked up on me just because I was browsing with Firefox. Ubuntu is much faster than both Windows and SuSE.

---

### Post by ferpadro on 2007-10-07
> **sstusick said:**
> I don't know what you people are smoking, but I'd like some. In my experience, SuSE was as slow as Windows including crashing and locking up...though Windows never locked up on me just because I was browsing with Firefox. Ubuntu is much faster than both Windows and SuSE.

I second that! OpenSUSE was slower than ubuntu in every aspect. Whenever I pressed alt+f2 the windows took like 2 seconds to appear. Scrolling down in firefox is less smoother than usual, and YaST....well, YaST is a slug. It may be the jewel of OpenSUSE's crown but i was waiting for like 30 minutes just to install VLC (and i have a 768 kbps internet connection.
Anyways, i'm installing Ubuntu again. The only thing i liked about OpenSUSE was the green boot splash image :lolflag:

---

### Post by sstusick on 2007-10-07
> **ferpadro said:**
> ....and YaST....well, YaST is a slug. It may be the jewel of OpenSUSE's crown but i was waiting for like 30 minutes just to install VLC (and i have a 768 kbps internet connection.
Anyways, i'm installing Ubuntu again. The only thing i liked about OpenSUSE was the green boot splash image :lolflag::lolflag: :lolflag:

---

### Post by Antman on 2007-10-07
> **sstusick said:**
> I don't know what you people are smoking, but I'd like some. In my experience, SuSE was as slow as Windows including crashing and locking up...though Windows never locked up on me just because I was browsing with Firefox. Ubuntu is much faster than both Windows and SuSE.

Wow... luckily OpenSuse 10.3 has not locked up on me while I was using it (except firefox freezing after 45 minutes of viewing flash vids on YouTube, but **every** distro I have tried so far does that thanks to adobe's crappy linux flash player).

---

### Post by sstusick on 2007-10-07
Yeah, the Flash for Linux sucks.. always crashes Firefox when viewing YouTube videos. But at least Firefox doesn't take the whole operating system with it (at least, not on Ubuntu).

---

### Post by Frak on 2007-10-07
Would be on it, exept this is the first and only distribution that lacks support for the Intel Integrated networking, which I may add, is fully OSS.

---

### Post by ferpadro on 2007-10-07
> **sstusick said:**
> Yeah, the Flash for Linux sucks.. always crashes Firefox when viewing YouTube videos. But at least Firefox doesn't take the whole operating system with it (at least, not on Ubuntu).

Odd. Firefox never crashed for me while watching youtube videos.  The only thing i know is that i always come back to Ubuntu. So far i've tried PCLOS and Opensuse. Didn't like PCLOS kde setup and didnt like the slowness of pclos either.

---

### Post by Antman on 2007-10-07
> **sstusick said:**
>  But at least Firefox doesn't take the whole operating system with it (at least, not on Ubuntu).

So, you are implying that the firefox/flash9 combo has brought down OpenSuse 10.3? That hasn't happened to me. I can normally just kill the firefox process and relaunch (works in all the distros I have tried so far except puppy)

Also, the newest flash9 plugin on the adobe labs site offers a version that is a little more stable then the one that comes with most current linux distros.

---

### Post by sstusick on 2007-10-07
No, I was referring to SuSE 10.2.

---

### Post by sstusick on 2007-10-07
> **ferpadro said:**
> Odd. Firefox never crashed for me while watching youtube videos.  The only thing i know is that i always come back to Ubuntu. So far i've tried PCLOS and Opensuse. Didn't like PCLOS kde setup and didnt like the slowness of pclos either.
I find KDE is slow in general. No matter which distro I've used, including SuSE, Kubuntu, and PCLOS. I tire of the 'flashyness' and Windows look of KDE very easily. I don't tire of Gnome though.

---

### Post by xArv3nx on 2007-10-07
> **sstusick said:**
> I don't know what you people are smoking, but I'd like some. In my experience, SuSE was as slow as Windows including crashing and locking up...though Windows never locked up on me just because I was browsing with Firefox. Ubuntu is much faster than both Windows and SuSE.
Quit being stupid.

---

### Post by sstusick on 2007-10-07
> **xArv3nx said:**
> Quit being stupid.
Quit being stupid? Hey, don't get mad at me if my experience with SuSE has been poorer than yours. It's all in the user experience, like hit or miss. Mine with SuSE was a miss and I found a hit with Ubuntu. 

Though many people agree, Ubuntu = faster than SuSE. So I can't be far off in my assumption.

---

### Post by the_darkside_986 on 2007-10-08
I hadn't used it since 10.1 so I was tempted to download the CD(s) and try it. I used the KDE CD and the non-oss addon cd.

So, the installation process looked very nice and professional, except the part where it asked for CD1 but it really meant the addon cd. 

When I got to the desktop, the KDE default setup was very nice looking, and the K menu interface was something new and different from other KDE installations.

I wanted to go online for more software but it could never configure my wireless card. My idea was to boot into Ubuntu, grab the madwifi tar ball, and throw it on to my Suse partition.

I was going to build the madwifi package since YaST couldn't help me with my wireless card, but the build tools are not available on the disks, and I had no way of grabbing all the RPM's needed from the network since I had no network card access from openSUSE. I thought about doing some guessing about which RPM's to get and download them from Ubuntu, but I'd rather avoid getting into RPM dependency hell. So I had to give up and delete openSUSE.

I share the sentiments with the oss-purists but if my network card cannot be functional, then I cannot use the system.

I remember when openSUSE 10.1 had 6 CD's I could get software from, not just 2. Are there extra CD's like this for openSUSE 10.3? If so I guess I could grab gcc and kernel source from those and try it again someday.

---

### Post by RedDwarf on 2007-10-08
> **Frak said:**
> Would be on it, exept this is the first and only distribution that lacks support for the Intel Integrated networking, which I may add, is fully OSS.
10.3 supports even iwlwifi...
> **the_darkside_986 said:**
> I wanted to go online for more software but it could never configure my wireless card. My idea was to boot into Ubuntu, grab the madwifi tar ball, and throw it on to my Suse partition.
madwifi hosts a repository for openSUSE -> [http://madwifi.org/suse/10.3/](http://madwifi.org/suse/10.3/)
> **the_darkside_986 said:**
> I remember when openSUSE 10.1 had 6 CD's I could get software from, not just 2. Are there extra CD's like this for openSUSE 10.3? If so I guess I could grab gcc and kernel source from those and try it again someday.
There is the 4GB DVD.

---

### Post by the_darkside_986 on 2007-10-08
But the thing is, it makes no since to add an online repository when I have no internet access by any means except wireless.

I could make the DVD on my system, which has a bootable DVD drive, but what if I were trying to recommend openSUSE for other people who only have the CD drive? 

I really miss the days of having 6 CD's. At least Debian has 21 CD's but that is too many for me to burn :P

I might try the DVD some day but I am still concerned about setting up dual-boot with Ubuntu. I think the next time I will set it to be a different file system type and on one partition (not splitting / and /home). And I hope there is an option to NOT install the bootloader. I must use the one of Ubuntu. Also, this time, I will not accidentally mess up my Ubuntu installation or confuse it into thinking my /home partition is missing.

---

### Post by RedDwarf on 2007-10-08
> **the_darkside_986 said:**
> But the thing is, it makes no since to add an online repository when I have no internet access by any means except wireless.
But you just need to download two files from this repository from Ubuntu, no need for build tools.

---

### Post by bodhi.zazen on 2007-10-08
WOW 10.3 is Awesome.

Features almost auto configured during the install:

1. My network shares were recognized and fstab was configured (All I had to provide was the server address and what options I wanted for fstab [via a gui interface for fstab]).

2. Separate /home with the option to encrypt.

3. Repos were configured (I seem to recall this was not the case with previous installs of SUSE) and the system checked for updates (at the time of installation). Now I know it was just released, still I for one appreciate the option to install updates out of the box rather then one of the first tasks post install.

4. Outstanding package selection (or deslection).

5. Multimedia support was outstanding.

Post install I was surprised to find that, unlike previous versions, the bloat has been reduced (there is still some ...) but previous versions of SUSE have been frankly sluggish where 10.3 was not.

What a pleasure.

---

### Post by bodhi.zazen on 2007-10-08
> **sstusick said:**
> Quit being stupid? Hey, don't get mad at me if my experience with SuSE has been poorer than yours. It's all in the user experience, like hit or miss. Mine with SuSE was a miss and I found a hit with Ubuntu. 

Though many people agree, Ubuntu = faster than SuSE. So I can't be far off in my assumption.

Yes, previous versions of SUSE were quite bloated and slow.

Open suse 10.3 is a significant improvement in performance.

You can try out the live CD (although it is gnome) and see for yourself.

I was so impressed, I installed, and am very impressed so far (see my post above).

---

### Post by the_darkside_986 on 2007-10-08
> **RedDwarf said:**
> But you just need to download two files from this repository from Ubuntu, no need for build tools.

Well, if there are no other dependencies that cannot be satisfied by the install CD, then I will have to try to manually grab those rpm files. Thanks.

I am just not sure I want to make a mess of my hard drive trying to install it now since I got FreeBSD somewhat working. That took a very long time and I still have to reinstall the nvidia driver everytime I boot up to get x to work.

---

### Post by xArv3nx on 2007-10-08
> **sstusick said:**
> Quit being stupid? Hey, don't get mad at me if my experience with SuSE has been poorer than yours. It's all in the user experience, like hit or miss. Mine with SuSE was a miss and I found a hit with Ubuntu. 

Though many people agree, Ubuntu = faster than SuSE. So I can't be far off in my assumption.
I was referring to the "what are you guys smoking?" remark.

---

### Post by xang on 2007-10-08
I installed 10.3 in virtualbox today.
As mentioned before, there are some pretty kewl features about 10.3

1. The encrypted /home option is a pretty neat feature IMO.
2. Adding the community repos and making that process streamlined 
    definitely a plus.


Still a little undecided on the "application browser". It does seem a tad bit slow, although I am not sure if it because I am running the distro as a VM. I am not a big fan of the slab type menu, but maybe it will grow on me.
That being said, the artwork is sharp, and it certainly gives you the feel of polish.

---

### Post by floke on 2007-10-08
Installed last night. Played with it this morning.
Felt sick. Went back to Debian/Arch.

Things are better now.:-\"

---

### Post by Antman on 2007-10-08
> **floke said:**
> Installed last night. Played with it this morning.
Felt sick. Went back to Debian/Arch.

Things are better now.:-\"

:lolflag:

---

### Post by Incense on 2007-10-08
> **xang said:**
> 
Still a little undecided on the "application browser". It does seem a tad bit slow, although I am not sure if it because I am running the distro as a VM. I am not a big fan of the slab type menu, but maybe it will grow on me.
That being said, the artwork is sharp, and it certainly gives you the feel of polish.

I actually really do not like the application browser. It feels like way too many steps to simply run an application. I know the thought is the applications you use the most will show in the SLED menu, but to me it's just a bit counter productive. One reason why I'll stick with KDE. Love the KDE menu!
.

---

### Post by greymongrey on 2007-10-08
I went back and tried openSuse again and I tried to like it, I really did. But it's just a mess. Yast is nothing short of a disaster. It is so slow and it just takes forever to do anything. If this is the best Novell can do they need to hang it up. It's gone for good on my computer and I will look in other places for a second distro.

---

### Post by sw1995 on 2007-10-08
I was bored and needed a project so I decided to give 10.3 a shot. I tried 10.2 a couple of times and really wanted to like it but it just felt a bit clunky to me. With 10.3 I have to admit I am finally starting to see the attraction to OpenSUSE. Although I like to think I am a fairly committed Ubuntu user, I am going to give this one a week or so so I may develop an informed opinion about the pros and cons of rpm based distros. So far it is running like a champ on my five year old laptop and I have to say it is nice to have such a nice looking desktop right out of the box (I know I know, that is just a matter of opinion).

---

### Post by ferpadro on 2007-10-31
> **ferpadro said:**
> I second that! OpenSUSE was slower than ubuntu in every aspect. Whenever I pressed alt+f2 the windows took like 2 seconds to appear. Scrolling down in firefox is less smoother than usual, and YaST....well, YaST is a slug. It may be the jewel of OpenSUSE's crown but i was waiting for like 30 minutes just to install VLC (and i have a 768 kbps internet connection.
Anyways, i'm installing Ubuntu again. The only thing i liked about OpenSUSE was the green boot splash image :lolflag:

Im quoting myself after trying opensuse 10.3 KDE edition, and it flies. I would had never thought that the performance was going to be so different using one DE and the other. Im also impressed because i always thought that KDE in general was slower than GNOME. And the kde setup is beautiful, love it. I only have a problem, i need to add update repositories and i don´t know how to do it =/

---

### Post by Incense on 2007-10-31
> **ferpadro said:**
> Im quoting myself after trying opensuse 10.3 KDE edition, and it flies. I would had never thought that the performance was going to be so different using one DE and the other. Im also impressed because i always thought that KDE in general was slower than GNOME. And the kde setup is beautiful, love it. I only have a problem, i need to add update repositories and i don´t know how to do it =/

I beleive that you just head over to YaST -> Software -> Community Repositories. I think your update repos, along with every other community repo will be there.

---

### Post by DJiNN on 2007-11-03
I've just installed 10.3 (gnome edition) and took it for a spin, and although once it's installed it "Looks" great, the install process is probably "THE SLOWEST" that i have ever come across..... it's AWFUL!!

It was OK to use, but nothing really makes a great deal of sense to me the way that it's laid out..... I can't seem to find anything, but that's probably because i'm not used to Suse..... and now that i have removed it, i shan't be getting used to it.

I really wanted to enjoy suse and have a positive experience, but all in all i found it quite a let down. :(

I'll stick with Xubuntu i think..... It was worth a try, but i'm definitely not a suse person. :)

Has anyone here had any "Positive" experience with suse?

---

### Post by Antman on 2007-11-03
> **DJiNN said:**
> 

Has anyone here had any "Positive" experience with suse?

I like the KDE desktop version of OpenSuse 10.3 but dislike the Gnome version.
Even though Yast is slower then Apt, I like how it includes virtually everything in a gui form.

Also it's one of the few distros out there that will suspend2Ram and suspend2disk my laptop while running ATI's drivers. 
So, right now on my laptops I run Sidux and OpenSuse. 
I tested out SLED 10sp1 on my desktop for awhile, but ZEN didn't want to play nice, so I put sidux on that too. I may just put Debian Etch on there though since I want my desktop to stay like a stable fortress until Lenny hits stable.

---

### Post by Incense on 2007-11-03
> **DJiNN said:**
> Has anyone here had any "Positive" experience with suse?

Another KDE user, and I love it. It's very stable, and (for me at least) much faster then Ubuntu on my hardware. I feel the same way about the gnome install. It feel clunky, and nothing really makes sense, especially when you compare it to the gnome in Ubuntu.Suse does still run Beagle, which I have to remove at install because it kills my system and makes everything run dog slow. That may have been part of your problem. If you decide to try it again, try the KDE side. You may like it.

---

### Post by RebounD11 on 2007-11-04
> **DJiNN said:**
> 
Has anyone here had any "Positive" experience with suse?

I did ... with both Gnome and KDE. I didn't get around to customize my KDE yet but my Gnome looks, works, feels great. 

There's a screenshot of my Gnome desktop with CF on.

---

### Post by DJiNN on 2007-11-05
Antman & Incense, thanks for the positive replies. I don't generally use KDE because i've always found it a bit too much. It looks great, but there's just too much available and i've always felt that this gets in the way for most of the stuff that i want to do.....

Having said that i think i'll still give the KDE version a try. Opensuse "Looks" great, very polished and it's certainly a mature distro, so worth a second look  i think. :) 

RebounD11  -  Thanks for the info & the screenie. Looks nice, and glad to hear that it's working well for you..... Now all i've gotta do is D/L OpenSuse again.... :)

Thanks guys, appreciate the replies.

---

### Post by RebounD11 on 2007-11-05
Anytime :D

---

### Post by Bachstelze on 2007-11-05
I installed openSUSE 10.3 this morning out of boredom, I thought it would take me half an hour to be back in Gentoo but I'm actually playing around with it since then :p

I must admit I was very pleasantly surprised, especially when I remember the last time I tried SuSe (I think it was 7.2), which was a very bad experience.

---

### Post by Incense on 2007-11-06
> **HymnToLife said:**
> I must admit I was very pleasantly surprised, especially when I remember the last time I tried SuSe (I think it was 7.2), which was a very bad experience.

 I think my first go at linux may have been with 7.x. I don't think I lasted long. :lolflag:

---

### Post by b9anders on 2007-11-06
I liked 10.3 - first suse I tried. Very smooth and very complete graphical experience. Definitely the distro with the best polish.

The speed was ok to good for kde. Certainly workable for my 3 year old laptop. YaST is a fantastic tool.

However, the problems with getting compiz fusion to work properly and the overwhelmingly slow speed of updates and installing software led me to abandon it after a few weeks. Too bad, as they have a great thing going with the general setup and one-click install is a fantastic feature.

Another negative is the installer which needs work for newbies. If not for that one, OpenSUSE would be the distro I'd recommend to newbies with fairly new machines without reservation.

---

### Post by dca on 2007-11-06
IMHO it's definitely the most polished GNU/Linux distro out there on both the KDE & Gnome side...  That polish alone should be the basis for all desktop Linux systems...

---

### Post by wolfen69 on 2007-11-09
i just installed the gnome version and was mildly impressed. i could see myself using it as my day to day OS if i were to quit using ubuntu for some reason. im gonna try the KDE version next. i just need to figure out how to watch TV with my Hauppauge PVR150. (which works great in ubuntu)


:guitar:

---

### Post by dca on 2007-11-09
> **wolfen69 said:**
> i just installed the gnome version and was mildly impressed. i could see myself using it as my day to day OS if i were to quit using ubuntu for some reason. im gonna try the KDE version next. i just need to figure out how to watch TV with my Hauppauge PVR150. (which works great in ubuntu)


:guitar:

If you decide to install openSuSE10.3, the last panel after installation is a hardware detection screen, I'm pretty sure there's a good shot at detecting that TV card...  I want to say it was a PVR-100 or 150 (which soon will be worthless now thanks to the US switching to digi signals next year) that worked in open10.2 & Ubuntu 606LTS using MythTV....  Gave up on the whole media center dealie over a year ago when it was deemed cheaper & easier to just get a DVR from your cable company...

---

### Post by zero244 on 2007-11-09
I looked at Suse myself just to check it out. And from reading about it, it looked like a good setup especially for power users or business.
But if I recall it was like a five cd install so I didnt continue with installing it.
I also checked into freebsd about the same time, and trying to get that installed is no easy matter. Possibly hours of compiling etc.
I realize compiling everything for your specific hardware is probably the most secure and stable way to use a unix system. But Ubuntu is more than stable enough for my needs.

---

### Post by Incense on 2007-11-09
> **zero244 said:**
> I looked at Suse myself just to check it out. And from reading about it, it looked like a good setup especially for power users or business.
But if I recall it was like a five cd install so I didnt continue with installing it.
I also checked into freebsd about the same time, and trying to get that installed is no easy matter. Possibly hours of compiling etc.
I realize compiling everything for your specific hardware is probably the most secure and stable way to use a unix system. But Ubuntu is more than stable enough for my needs.

There is a one disc live CD with an installer now for OpenSUSE.

---

### Post by Frak on 2007-11-09
> **zero244 said:**
> I looked at Suse myself just to check it out. And from reading about it, it looked like a good setup especially for power users or business.
But if I recall it was like a five cd install so I didnt continue with installing it.
I also checked into freebsd about the same time, and trying to get that installed is no easy matter. Possibly hours of compiling etc.
I realize compiling everything for your specific hardware is probably the most secure and stable way to use a unix system. But Ubuntu is more than stable enough for my needs.
They dropped the 5 CD installation due to complaints, so they now only have 1 CD and 1 DVD.

---

### Post by RedDwarf on 2007-11-10
> **Frak said:**
> They dropped the 5 CD installation due to complaints, so they now only have 1 CD and 1 DVD.
And the boxed version comes with two dual layer DVDs that have the full FTP repositories for both x86 and x86-64.
openSUSE hasn't a ShipIt program, but they will send you a copy of the boxed version for free if you were an "upstream package maintainer, openSUSE translation team member or active bug reporter". And I received my first one with just 3 or 4 bug/enhancement reports, not something really difficult to archieve.
[http://news.opensuse.org/?p=493](http://news.opensuse.org/?p=493)

There were no complains about the 5CDs. But it became 6CDs because the teTeX to TeXLive transition. So between alpha5 and alpha6 they stopped releasing the 6CDs saying "let's see if someone complains". Since just a few people complained...

---

