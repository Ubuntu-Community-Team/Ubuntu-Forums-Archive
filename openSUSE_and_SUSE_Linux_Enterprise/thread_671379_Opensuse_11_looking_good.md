---
title: "Opensuse 11 looking good"
date: 2008-01-18
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Antman on 2008-01-18
Ok so it's still only Alpha 1, but it looks pretty darn good so far. I think I will download the Alpha1 DVD and play a little. I'm hoping that version 11 hits a home run in June.
[http://news.opensuse.org/2008/01/18/announcing-opensuse-110-alpha1/]("http://news.opensuse.org/2008/01/18/announcing-opensuse-110-alpha1/")
 :guitar:

---

### Post by Dark Star on 2008-01-19
[CENTER][IMG]http://www.imgx.org/pfiles/4661/Opensuse_7.gif[/IMG][/CENTER]

A very early alpha version of openSUSE, 11.0 Alpha 1, was launched and it is available for download and testing. Although it is just a development release, this version starts the new year with a lot of improvements,.
 
 **Changes since openSUSE 11.0 Alpha 0**
 
Suse 11 Aplha 1 have seen 1026 package check-ins since Alpha0 and countless bugs fixed. The main changes against Alpha0 are:[LIST]
[*] Sat Solver integration
[*]Michael Schröder’s “sat solver” library is now the default package solver for libzypp, so make sure you doublecheck the selected packages - there might be suprises ahead. Please note that we need test cases for things that look funny to you (wiki link)[/LIST][LIST=1]
[*] Heavy changes to the appearance of the Qt installation (ported to qt4)
[*] KDE 4.0.0
[*] perl 5.10
[*] glibc 2.7
[*] NetworkManager 0.7
[*] CUPS 1.3.5
[*] Pulseaudio[/LIST][CENTER]
 [[IMG]http://www.imgx.org/pthumbs/large/4660/installer.jpg[/IMG]]("http://www.imgx.org/public/view/full/4660")
 ***The Beautiful New Look of the Installer***[/CENTER]

 **Most Annoying Bugs**
 
Due to the huge amount of changes, there are also several noticeable bugs:[LIST]
[*] The new solver does not yet have a “ignore this requirement” choice, i.e. it’s not possible to create a broken system. Developers aere still discussing if this is a bug or a feature :guitar:
[*]The CDs lack a huge amount of software. Many packages had to be taken out to make way for others. The CDs should still have a a completely working desktop, however.
[*]The Qt port and its theme are early releases and create noticeably more flickering and drawing glitches, e.g. the progress bar is only visible on some installations
[*]jpackage packages are broken and one package will complain during installation - just ignore
[*]The installation crashes at the end when creating the x11 proposal: in this case, your desktop will still have a working X config, it just might not be the perfect one. You may need to call sax2 after it happens
[*]PPC cannot be installed as the bootloader config can’t be written out. However, you can get a working PPC system when updating from alpha0[/LIST]**open SUSE 11 Roadmap overview**[LIST]
[*]    Dec 6 openSUSE 11.0 Alpha 0
[*]    Jan 17 openSUSE 11.0 Alpha 1
[*]    Feb 07 openSUSE 11.0 Alpha 2
[*]    March 18 openSUSE 11.0 Alpha 3
[*]    April 17 openSUSE 11.0 Beta 1
[*]    May 2 openSUSE 11.0 Beta 2
[*]    May 13 openSUSE 11.0 Beta 3
[*]    May 29 openSUSE 11.0 Release Candidate 1
[*]    June 12 openSUSE 11.0 Goldmaster (internal)
[*]    June 19 openSUSE 11.0 Public release[/LIST][B]
Download : [i386 DVD Torrent]("http://download.opensuse.org/distribution/11.0-Alpha1/iso/torrent/openSUSE-11.0-Alpha1-DVD-i386.torrent") | [X86/64 DVD Torrent]("http://download.opensuse.org/distribution/11.0-Alpha1/iso/torrent/openSUSE-11.0-Alpha1-DVD-x86_64.torrent")[/B]

---

### Post by Incense on 2008-01-19
Is that really what the new installer looks like? I had read that it was only a mock up. If they really use it, then I am very impressed. They have not changed the YaST installer since.... uh....hmmmm... ever. Sounds very nice so far! I may have to give it a go on my test partition.

---

### Post by Kingsley on 2008-01-21
I'm looking forward to this release. KDE 4 will be much further along by the time this release is final.

---

### Post by 67GTA on 2008-01-26
How is the "ONE" thing that has always kept me from using opensuse? [COLOR="Red"]THE PACKAGE MANAGER[/COLOR]
There were supposed to be improvements. If they would use apt/synaptic or something similar, they would probably be #1. Why can't they see that? I often wonder if the suse devs have ever used apt/synaptic?

---

### Post by Incense on 2008-01-26
> **67GTA said:**
> How is the "ONE" thing that has always kept me from using opensuse? [COLOR="Red"]THE PACKAGE MANAGER[/COLOR]
There were supposed to be improvements. If they would use apt/synaptic or something similar, they would probably be #1. Why can't they see that? I often wonder if the suse devs have ever used apt/synaptic?

It's not the default, but no one is stopping you from setting it up yourself.

[http://en.opensuse.org/APT]("http://en.opensuse.org/APT")

 I also am hopeful for some more YaST improvements in 11, I don't think anything as been done with the alpha's yet though.

---

### Post by 67GTA on 2008-01-26
Thanks for the link. That wasn't available when I last tried 10.3. There were only installation instructions, but no repos. I might try installing it again to see how it works. I installed Synaptic before when I had it installed, but was not smart enough to add any repos. No one at the opensuse forums wanted to talk about it either.

---

### Post by Incense on 2008-01-26
> **67GTA said:**
> Thanks for the link. That wasn't available when I last tried 10.3. There were only installation instructions, but no repos. I might try installing it again to see how it works. I installed Synaptic before when I had it installed, but was not smart enough to add any repos. No one at the opensuse forums wanted to talk about it either.

Most SUSE users tend to just stick it out with YaST, or use SMART PM. YaST does get better with each release, and 10.3 saw the death of ZMD. I can only imagine that YaST will get better with the 11 release. Good luck with APT. 

Has anyone tried the 11 alpha? I have not had time to load it in a VM yet.

---

### Post by Antman on 2008-01-26
> **Incense said:**
> 
Has anyone tried the 11 alpha? I have not had time to load it in a VM yet.

I installed the KDE CD on my laptop. The installer is quite nice. It also seems to use the iwl3945 wifi driver as default instead of the ipw3945, which is good since I like the iwl3945 driver better; unfortunately I couldn't get wireless to work after the install. 

The theme and desktop look just like 10.3 so it looks as though most of this alpha focuses on changes under the hood and the installer.
I'll try it again once it goes beta.

---

### Post by 67GTA on 2008-01-27
I installed it in VMWare. I got apt/synaptic up and running. There is even a script to convert the default suse  repos to work with Synaptic. I will have to install it to one of my empty HD partitions and play with it some more.

---

### Post by RebounD11 on 2008-01-27
> **67GTA said:**
> I installed it in VMWare. I got apt/synaptic up and running. There is even a script to convert the default suse  repos to work with Synaptic. I will have to install it to one of my empty HD partitions and play with it some more.

That script was missing :) ... Man I struggled with apt until I could get it to use all my repos .

---

### Post by tms240 on 2008-03-27
Hi 67GTA, RebounD11 -

I would appreciate it if you guys give some step by step directions for getting apt (and synaptic too if it's not a lot more to do) working with suse repos.

Thanx

---

### Post by 67GTA on 2008-03-27
I eventually gave up and started using Yast. I got everything working with apt/synaptic except for the pacman repo. Maybe RebounD11 had more luck and can give you some help.

---

### Post by Antman on 2008-03-28
> **tms240 said:**
> Hi 67GTA, RebounD11 -

I would appreciate it if you guys give some step by step directions for getting apt (and synaptic too if it's not a lot more to do) working with suse repos.

Thanx

Have you checked out the openSUSE wiki?
[http://en.opensuse.org/APT]("http://en.opensuse.org/APT")

---

### Post by tms240 on 2008-03-29
Hi ANTMAN -

Thanks for the link.  I totally overlooked that page.

My apologies to the list for the unnecessary question.

---

### Post by hhhhhx on 2008-03-29
wow i think that i'll haft to start looking into suse ! :)

---

### Post by miggols99 on 2008-03-31
You should have a look at the Alpha 3. It's looking better than ever!

[http://news.opensuse.org/2008/03/19/announcing-opensuse-110-alpha-3/](http://news.opensuse.org/2008/03/19/announcing-opensuse-110-alpha-3/)

---

### Post by Antman on 2008-03-31
> **miggols99 said:**
> You should have a look at the Alpha 3. It's looking better than ever!

[http://news.opensuse.org/2008/03/19/announcing-opensuse-110-alpha-3/](http://news.opensuse.org/2008/03/19/announcing-opensuse-110-alpha-3/)

Unfortunately, KDE4 is not looking that great to me. I hope the openSUSE Beta adds some suse tweaks to the desktop because I just don't like it. And it's not just openSUSE's implementation, Fedora 9's KDE4 liveCD doesn't look that great either IMHO. 
GNOME is looking better and better to me now.

---

### Post by Incense on 2008-04-01
> **Antman said:**
> Unfortunately, KDE4 is not looking that great to me. I hope the openSUSE Beta adds some suse tweaks to the desktop because I just don't like it. And it's not just openSUSE's implementation, Fedora 9's KDE4 liveCD doesn't look that great either IMHO. 
GNOME is looking better and better to me now.

As big a KDE guy as I am, I have to admit I'm on the same page as you. Every distro that is putting out KDE 4, looks and works the same across the bored. I love openSUSE because of the KDE they put out. I would hate to see that get lost in that blue ripple wallpaper, and this KDE 4 default desktop everyone seems to be using. I have no doubt that they will as the theming is always the last thing they throw in. ATM through, I'm still using 3.5.9. 

I actually used GNOME all last week, and it's a lot nicer then I remember. KDE does have the apps though.

---

### Post by RebounD11 on 2008-04-04
> **Incense said:**
> As big a KDE guy as I am, I have to admit I'm on the same page as you. Every distro that is putting out KDE 4, looks and works the same across the bored. I love openSUSE because of the KDE they put out. I would hate to see that get lost in that blue ripple wallpaper, and this KDE 4 default desktop everyone seems to be using. I have no doubt that they will as the theming is always the last thing they throw in. ATM through, I'm still using 3.5.9. 

I actually used GNOME all last week, and it's a lot nicer then I remember. KDE does have the apps though.

KDE has a little to many apps... and I wish they didn't come in packs... I only want some of each... like I don't need KWord and KSpreadsheet when I have Abiword and GNUmeric... but in order to get rid of them I have to erase the whole KOffice Suite.

---

### Post by Erunno on 2008-04-04
> **RebounD11 said:**
> KDE has a little to many apps... and I wish they didn't come in packs... I only want some of each... like I don't need KWord and KSpreadsheet when I have Abiword and GNUmeric... but in order to get rid of them I have to erase the whole KOffice Suite.

That's usually up to the packager. For instance, Gentoo splits KOffice into seperate application packages (i.e. you can install kword and its dependencies without pulling the whole koffice). But sometimes KDE applications are so tightly integrated with each other that they need to pull other apps for their own functionality. I think that KWord uses KSpreadsheat for its own spreadsheet functionality. This is a good thing as it avoid unnecessary code duplication.

---

### Post by RebounD11 on 2008-04-05
> **Erunno said:**
> That's usually up to the packager. For instance, Gentoo splits KOffice into seperate application packages (i.e. you can install kword and its dependencies without pulling the whole koffice). But sometimes KDE applications are so tightly integrated with each other that they need to pull other apps for their own functionality. I think that KWord uses KSpreadsheat for its own spreadsheet functionality. This is a good thing as it avoid unnecessary code duplication.

That makes sense :)

---

### Post by Growbag on 2008-04-08
Have they fixed the bug where the icons re-appear each time you log in?  That was driving me nuts.

I delete/re-arrange my desktop icons and they would rearrange/re-appear on next login!

And is KDE4 any faster?  It always seems to run really slow on my computer (Nvidia 8400).

---

### Post by quickshade on 2008-04-11
I noticed about 2 days ago you could use apt with SUSE. download apt from repos and then had to one click install synaptics. It had a bunch of pre-made sources but I wanted to use the real ones. I got them all in but it failed to download. Then I realized I had to use rpm-mod or whatever it is not just plain RPM. After that it downloaded everything. The 14.2 OSS file is what makes me hate opensuse. They need to break up the repos a bit more so I'm not downloading that much from one sources. I also had to edit the start command on synaptics otherwise it would only start though root terminal.

As for 11.0, I used it in VMware in Alpha 2 and then figured I install it on my main machine test drive. While I'm fairly impressed by alot of what opensuse has done there is still way to many bugs and problems for me to make a full switch. And while I agree that all KDE4 distros look the same the opensuse art team said that most artwork won't be in place until the later beta stages. I just updated and notice my window outline is now blue....so it's getting their. The art team stated that they want KDE4 to look different from the rest of the distros....BUT said that they might wait until 11.1 for a full art update. Anyways if they makes 11 a bit more stable and do some minor tweaks I'm going to have to consider switching my main machine over (Laptop is running 10.3)

---

### Post by RedDwarf on 2008-04-11
$ rpm -qa "*branding*"
kde4-kio_sysinfo-branding-openSUSE-11.0-36.3
kdebase4-workspace-branding-openSUSE-11.0-36.3

---

