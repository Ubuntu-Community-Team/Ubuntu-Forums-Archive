---
title: "How do I fix an unstable system?"
date: 2007-06-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by mikerobinson on 2007-06-26
Due to a bug in Adept Manager I deleted many packages I had installed without wanting to. I had to manually restore them by going through the log files, but I'm still getting a lot of dependency errors:

```
$ sudo aptitude -f install
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  abiword abiword-gnome avidemux gstreamer0.10-plugins-bad-multiverse k3b
  kde kubuntu-desktop libavcodec0d mplayer
The following packages are unused and will be REMOVED:
  adept-batch amor blinken edict eyesapplet fifteenapplet indi kalzium
  kalzium-data kanagram kanjidic kasteroids katomic kbackgammon kbattleship
  kblackbox kbounce kbruch kdeedu kdeedu-data kdegames kdegames-card-data
  kdelibs kdetoys keduca kenolaba kfouleggs kgoldrunner khangman kig kiten
  kjumpingcube klatin klettres klettres-data klickety klines kmahjongg
  kmines kmoon kmplot knetwalk kodo kolf konquest kpager kpat kpercentage
  kpersonalizer kpoker kreversi ksame kshisen ksirtet ksmiletris ksnake
  ksokoban kspaceduel kstars kstars-data kteatime ktip ktouch ktron
  ktuberling kturtle ktux kverbos kvoctrain kweather kwin4 kwordquiz
  kworldclock libboost-python1.33.1 libkdeedu3 libkiten1 lskat
  openoffice.org-base openoffice.org-filter-binfilter
  openoffice.org-filter-mobiledev ttf-dustin ttf-sjfonts
The following packages will be automatically REMOVED:
  adept kde-amusements kde-core kdebase language-selector-qt openoffice.org
The following packages will be REMOVED:
  adept adept-installer digikam kde-amusements kde-core kde-guidance
  kde-guidance-powermanager{p} kde-style-polyester kde-systemsettings
  kdebase kdepasswd khelpcenter klipper kmenuedit kmplayer-konq-plugins{p}
  konqueror-nsplugins ksmserver ksplash ksplash-engine-moodin{p} ksysguard
  ktorrent kubuntu-default-settings kubuntu-docs{p}
  kubuntu-konqueror-shortcuts{p} kwin-style-crystal{p} language-selector-qt
  libfaac0 libmjpegtools0c2a libmp4v2-0 mozilla-firefox openoffice.org
  openoffice.org-calc openoffice.org-draw openoffice.org-impress
  openoffice.org-kde{p} openoffice.org-math openoffice.org-writer
  python-kde3{p} python-uno{p} scim-qtimm{p} transcode
0 packages upgraded, 1 newly installed, 123 to remove and 0 not upgraded.
Need to get 2797kB of archives. After unpacking 319MB will be freed.
The following packages have unmet dependencies:
  kubuntu-desktop: Depends: adept but it is not installable
                   Depends: kde-guidance but it is not installable
                   Depends: kde-style-polyester but it is not installable
                   Depends: kde-systemsettings but it is not installable
                   Depends: kdepasswd but it is not installable
                   Depends: khelpcenter but it is not installable
                   Depends: klipper but it is not installable
                   Depends: kmenuedit but it is not installable
                   Depends: kmplayer-konq-plugins but it is not installable
                   Depends: ksmserver but it is not installable
                   Depends: ksplash but it is not installable
                   Depends: ksplash-engine-moodin but it is not installable
                   Depends: ksysguard but it is not installable
                   Depends: ktorrent but it is not installable
                   Depends: kubuntu-default-settings but it is not installable
                   Depends: language-selector-qt but it is not installable
  avidemux: Depends: libfaac0 (>= 1.24clean) but it is not installable
  gstreamer0.10-plugins-bad-multiverse: Depends: libfaac0 (>= 1.24clean) but it is not installable
                                        Depends: libmjpegtools0c2a (>= 1:1.8.0) but it is not installable
  abiword: Conflicts: abiword-gnome but 2.4.6-1.1ubuntu2 is installed.
  mplayer: Depends: libfaac0 (>= 1.24clean) but it is not installable
           Depends: libmp4v2-0 (>= 2.0.0+cvs20040908+mp4v2+bmp) but it is not installable
  libavcodec0d: Depends: libfaac0 (>= 1.24clean) but it is not installable
  k3b: Depends: transcode but it is not installable
  kde: Depends: kde-core (>= 5:47) but it is not installable
       Depends: kde-amusements (>= 5:47) but it is not installable
  abiword-gnome: Conflicts: abiword but 2.4.6-1.1ubuntu2 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
kde
kubuntu-desktop

Keep the following packages at their current version:
abiword [Not Installed]
libfaac0 [1.24clean-0ubuntu4 (feisty, now)]
libmjpegtools0c2a [1:1.8.0-0.2ubuntu3 (feisty, now)]
libmp4v2-0 [2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3 (feisty, now)]
transcode [2:1.0.2-0.8ubuntu3 (feisty, now)]

Leave the following dependencies unresolved:
ubuntu-desktop recommends openoffice.org
Score is -1101

Accept this solution? [Y/n/q/?] y
The following packages are unused and will be REMOVED:
  adept-batch amor artsbuilder atlantik atlantikdesigner blinken cervisia
  dcoprss dirmngr docbook-defguide edict eyesapplet fifteenapplet gnuift
  gnuift-perl gnupg-agent gnupg2 gpgsm indi juk kaboodle
  kaddressbook-plugins kalarm kalzium kalzium-data kanagram kandy kanjidic
  kappfinder kasteroids kate-plugins katomic kbackgammon kbattleship
  kblackbox kbounce kbruch kcalc kcharselect kdat kdeaccessibility
  kdeaddons kdeaddons-kfile-plugins kdeadmin kdeartwork
  kdeartwork-emoticons kdeartwork-misc kdeartwork-style
  kdeartwork-theme-icon kdeartwork-theme-window kdeedu kdeedu-data kdegames
  kdegames-card-data kdegraphics kdelibs kdelirc kdemultimedia
  kdemultimedia-kappfinder-data kdenetwork kdepim kdepim-kfile-plugins
  kdessh kdetoys kdeutils kdewallpapers kdewebdev kdf kdict kdvi kedit
  keduca kenolaba kfax kfaxview kfilereplace kfloppy kfouleggs kgamma kget
  kgoldrunner kgpg khangman khexedit kicker-applets kiconedit kig
  kimagemapeditor kiten kjots kjumpingcube klaptopdaemon klatin kleopatra
  klettres klettres-data klickety klines klinkstatus kmahjongg kmid kmines
  kmoon kmouth kmplot kmrml knetwalk knewsticker kodo kolf kolourpaint
  kommander kompare konquest konsolekalendar korn kpackage kpager kpat
  kpercentage kpersonalizer kpilot kpoker kpovmodeler krec kreversi kruler
  ksame ksayit kshisen ksig ksim ksirc ksirtet ksmiletris ksnake ksokoban
  kspaceduel kstars kstars-data ksync ksysv ktalkd kteatime ktip ktnef
  ktouch ktron kttsd ktuberling kturtle ktux kuser kverbos kview kviewshell
  kvoctrain kweather kwifimanager kwin4 kwordquiz kworldclock kxsldbg
  libarts1-audiofile libarts1-mpeglib libarts1-xine libboost-python1.33.1
  libcvsservice0 libdate-manip-perl libdb4.3++c2 libgnuift0c2a libindex0
  libio-socket-ssl-perl libkdeedu3 libkdegames1 libkgantt0 libkiten1
  libksba8 libmal1 libmrml1c2a libnet-ssleay-perl libparse-yapp-perl
  libpth20 librss1 libtiff-tools libxml-dom-perl libxml-handler-trees-perl
  libxml-libxml-common-perl libxml-libxml-perl libxml-namespacesupport-perl
  libxml-perl libxml-regexp-perl libxml-sax-expat-perl libxml-sax-perl
  libxml-writer-perl libxml-xql-perl lilo-config lisa lskat mpeglib noatun
  noatun-plugins openbsd-inetd openoffice.org-base
  openoffice.org-filter-binfilter openoffice.org-filter-mobiledev perl-tk
  pinentry-curses pinentry-qt quanta quanta-data secpolicy superkaramba
  talk tetex-base tetex-bin tetex-doc tex-common ttf-dustin ttf-sjfonts
  ytalk
The following packages will be automatically REMOVED:
  adept kde kde-amusements kde-core kdebase kubuntu-desktop
  language-selector-qt openoffice.org
The following packages will be REMOVED:
  adept adept-installer digikam kde kde-amusements kde-core kde-guidance
  kde-guidance-powermanager{p} kde-style-polyester kde-systemsettings
  kdebase kdepasswd khelpcenter klipper kmenuedit kmplayer-konq-plugins{p}
  konqueror-nsplugins ksmserver ksplash ksplash-engine-moodin{p} ksysguard
  ktorrent kubuntu-default-settings kubuntu-desktop kubuntu-docs{p}
  kubuntu-konqueror-shortcuts{p} kwin-style-crystal{p} language-selector-qt
  mozilla-firefox openoffice.org openoffice.org-calc openoffice.org-draw
  openoffice.org-impress openoffice.org-kde{p} openoffice.org-math
  openoffice.org-writer python-kde3{p} python-uno{p} scim-qtimm{p}
0 packages upgraded, 0 newly installed, 260 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 679MB will be freed.
Do you want to continue? [Y/n/?]  
```

Any ideas as to how to fix this would be greatly appreciated. I have a feeling if I removed these 260 packages my system would be pretty useless.

---

### Post by CompactDestruction on 2007-06-26
Lordy. That looks pretty messed up. I'm sorry I have no idea how to fix it I'm quite new myself but I'm sure someone can help.

Is reformatting/reinstalling the OS an option or is there too much on it?

---

### Post by tiger99tiger on 2007-06-26
It is rather messed up! Now I hope that the developers will be working on a simple way of restoring a messed-up system to a basic working state, which seems to be lacking right now (likely because they think it is not needed very often), but in the meantime we need to look at a way of fixing this manually. This has happened to me too, just as badly, and I think that exactly the same packages were involved.

I would start by checking that **/etc/apt/sources.list **has a correct set of repositories, and is not corrupt. That could be why certain packages are marked as not installable

Then s**udo apt-get remove <list of packages marked as BROKEN>**. These are likely what is causing the problem, and there are not too many. These can easily be replaced.

Then try **sudo apt-get install adept synaptic**, which should get you two package managers and lots of dependent stuff. (Sometimes synaptic will do things that adept can't, but it needs parts of Gnome to be installed.)

You can do everything from the command line, but it is not  a realistic proposition due to the number of packages involved. Also, in adept, it is easy to see the package descriptions and other info, and there may be clues therein about the origin of the problem. (You are obviously using Kubuntu rather than Ubuntu, as Adept and kde stuff is appearing in your package list. But likely everything here applies to Ubuntu too.)

If you do get adept running, go through the entire list of packages, and cancel changes on any that are marked for removal. Preview the changes and see what it really wants to do. Try selecting purge for the broken packages, preview again, and just keep at it, cancelling suspicious changes, etc, until you get a reasonable set of actions in preview. You may find that removing one of the meta-packages such as kde helps (it does not actually remove the kde system!) Then apply.....

Here is a list of the kde bits that adept reports as installed on my working system: k3b, kaddressbook, kaffeine, karm, katapult, kate, kbstate, kcontrol, kcron, kde-guidance, kde-guidance-powermanager, kde-icons-mono, kde-style-polyester, kde-systemsettings, kdeadmin-kfile-plugins, kdebase-bin, kdebase-data, kdebase-kio-plugins, kdebluetooth, kdeedu-data, kdegraphics-kfile-plugins, kdelibs-data, kdelibs4-dev, kdelibs4c2a, kdemultimedia-kfile-plugins, kdemultimedia-kio-plugins, kdenetwork-filesharing, kdenetwork-kfile-plugins, kdepasswd, kdepim-kio-plugins, kdepim-kresources, kdepim-wizards, kdeprint, kdesk-scripts, kdesktop, kdm, kdnssd, keep, kexi, kfind, kformula, kghostview, khelpcenter, kicker, kig, klipper, klogic, kmag, kmail, kmailcvt, kmenuedit, kmilo, kmix, kmousetool, knetworkconf, knetworkmanager, knotes, koffice-data, koffice-libs, konq-plugins, konqueror, konsole, kontact, konversation, kopete, korganiser, kpdf, kppp, krdc, krfb, kscreensaver, ksimus, ksmserver, ksnapshot, ksplash, ksplash-engine-moodin, kstars, ksvg, ksysguard, ksysguardd, ktorrent, ktrack, kwalletmanager, kwin, kwin-style-crystal. 

You will see that most of these are optional, and  in particular, kde and kde-core are not installed. So you need not worry about removing those. But you do need katapult, kdebase-bin, kdebase-data, kdebase-kio-plugins, kdelibs-data, kdelibs4c2a (maybe?),  kdesktop, kdm, kicker, konqueror, ksmserver, kwin as a minimum usable subset of kde. So if you have those installed, you can safely let it remove the others, for now. They can be reinstalled later.

If all else fails, and you have made /home a seperate partition, you can always reinstall without losing your user data. Just make a note of what device it is on first (use mount to get a list of device mounts, it will be something like /dev/hda5) and when you install, set that partition for mounting as /home. but not to be formatted. If not, backup now, if you can.

By the way, do you have Automatix installed? If so, uninstall it first, as it is often the cause of these problems. It is unsafe, and has trashed several systems that I know of, including my own, because it is not properly integrated with the package management system. All functionality that can be achieved via Automatix is available by other means, such as **[http://ubuntuforums.org/showthread.php?t=202537&highlight=firefox+real+player](http://ubuntuforums.org/showthread.php?t=202537&highlight=firefox+real+player)**, for some useful stuff. Search the forums, or use Google, for alternatives to whatever you require. The only thing that beat me was Acroread, it remains a manual, and very buggy, install, and will break when some things are updated. But at least the reinstall is quick.

Good luck!

---

### Post by b00gie on 2007-06-26
Hello. I suggest you to install **aptitude** by:
```
sudo apt-get install aptitude
```
and then:
```
sudo aptitude install kubuntu-desktop
```And from now on use aptitude to manage installing every packet until u fix your system. This script will help you to choose the best option to get all installed (even if something needs to be removed first). Hope it will help a bit. Good luck.

P.S. Sorry for bad english...

---

### Post by kuja on 2007-06-26
Simple copy & pastable potential solution that won't remove anything:


```
sudo apt-get install --reinstall adept adept-installer digikam kde kde-amusements kde-core kde-guidance kde-guidance-powermanager{p} kde-style-polyester kde-systemsettings kdebase kdepasswd khelpcenter klipper kmenuedit kmplayer-konq-plugins{p} konqueror-nsplugins ksmserver ksplash ksplash-engine-moodin{p} ksysguard ktorrent kubuntu-default-settings kubuntu-desktop kubuntu-docs{p} kubuntu-konqueror-shortcuts{p} kwin-style-crystal{p} language-selector-qt mozilla-firefox openoffice.org openoffice.org-calc openoffice.org-draw openoffice.org-impress openoffice.org-kde{p} openoffice.org-math openoffice.org-writer python-kde3{p} python-uno{p} scim-qtimm{p}
```

---

### Post by mikerobinson on 2007-06-26
> **tiger99tiger said:**
> It is rather messed up! Now I hope that the developers will be working on a simple way of restoring a messed-up system to a basic working state, which seems to be lacking right now (likely because they think it is not needed very often), but in the meantime we need to look at a way of fixing this manually. This has happened to me too, just as badly, and I think that exactly the same packages were involved.
Agreed completely!

> I would start by checking that **/etc/apt/sources.list **has a correct set of repositories, and is not corrupt. That could be why certain packages are marked as not installableEverything seems fine.

> Then s**udo apt-get remove <list of packages marked as BROKEN>**. These are likely what is causing the problem, and there are not too many. These can easily be replaced.I tried removing them, but still no go.

> Then try **sudo apt-get install adept synaptic**, which should get you two package managers and lots of dependent stuff. (Sometimes synaptic will do things that adept can't, but it needs parts of Gnome to be installed.)I already had Synaptic installed since I have ubuntu-desktop as well. I actually got my system to the point where apt-get doesn't say there's anything wrong, but aptitude does. It's weird because all of the packages aptitude says are "not installable" are up and running just fine.

> If you do get adept running, go through the entire list of packages, and cancel changes on any that are marked for removal. Preview the changes and see what it really wants to do. Try selecting purge for the broken packages, preview again, and just keep at it, cancelling suspicious changes, etc, until you get a reasonable set of actions in preview. You may find that removing one of the meta-packages such as kde helps (it does not actually remove the kde system!) Then apply.....None of them are marked for removal right away. I tried doing this, but couldn't come to a happy solution.

> If all else fails, and you have made /home a seperate partition, you can always reinstall without losing your user data. Just make a note of what device it is on first (use mount to get a list of device mounts, it will be something like /dev/hda5) and when you install, set that partition for mounting as /home. but not to be formatted. If not, backup now, if you can./home is on the same partition as /. I'm thinking about reinstalling, but obviously I would have to backup everything in /home first.

> By the way, do you have Automatix installed? Nope.

> **b00gie said:**
> Hello. I suggest you to install **aptitude** by:
```
sudo apt-get install aptitude
```
and then:
```
sudo aptitude install kubuntu-desktop
```And from now on use aptitude to manage installing every packet until u fix your system. This script will help you to choose the best option to get all installed (even if something needs to be removed first). Hope it will help a bit. Good luck.

P.S. Sorry for bad english...I had aptitude installed. None of the solutions it offers are viable since they all want me to remove 200+ packages.

> **kuja said:**
> Simple copy & pastable potential solution that won't remove anything:


```
sudo apt-get install --reinstall adept adept-installer digikam kde kde-amusements kde-core kde-guidance kde-guidance-powermanager{p} kde-style-polyester kde-systemsettings kdebase kdepasswd khelpcenter klipper kmenuedit kmplayer-konq-plugins{p} konqueror-nsplugins ksmserver ksplash ksplash-engine-moodin{p} ksysguard ktorrent kubuntu-default-settings kubuntu-desktop kubuntu-docs{p} kubuntu-konqueror-shortcuts{p} kwin-style-crystal{p} language-selector-qt mozilla-firefox openoffice.org openoffice.org-calc openoffice.org-draw openoffice.org-impress openoffice.org-kde{p} openoffice.org-math openoffice.org-writer python-kde3{p} python-uno{p} scim-qtimm{p}
```I tried this first (since it was just a simple copy/paste) but it didn't affect anything. 

Thanks for all the suggestions guys. The weird thing is that everything seems to be working fine. The packages it says are not installable are all functioning. KDE is working and my computer got turned off last night and I could reboot back into it (after a few fsck runs). I think I'm just going to leave it for now. I might reinstall one of these days with a fresh 32 bit kubuntu.

---

### Post by tiger99tiger on 2007-06-27
Thinking about this some more, I suspect that Adept was not going to remove anything vital anyway, so you could just let it do its thing, and from the command line "sudo apt-get install xxxxx" where xxxx is anything that it removed that you really needed. Looking at the list of kde stuff, which is the majority, some of it is metapackages for installation convenience, I think, and may well not matter, as your system is still working, which we are all glad to hear!

Maybe it might be best to wait a while, and install the regular updates, which will fix Adept if it is broken, before doing anything radical like re-installing. In Debian-based systems, having to do a complete reinstall is quite rare except for users of Automatix, so it is said. The 64 bit system does work quite well, albeit with some 32 bit stuff still required, till Adobe and others recognise that the world is going 64-bit.....

I notice that Adept is far less buggy than it was six months ago, and is updated quite often.

If you are sure that all is well (sufficiently to have a stable, bootable system, even if some minor stuff is missing) "sudo dpkg --configure -a" may well restore normality to the package management system. It is sometimes necessary after a failed install, or an Adept crash anyway.

---

### Post by praxis22 on 2007-06-27
If you can add a fat32 file system, (USB stick or drive) and then once it's mounted you can backup your /home with tar:

```
 sudo tar cf /fat/home.tar /home
```

reinstal from scratch, then replug your USB drive

and do:

```
cd /
sudo tar xvf /fat/home.tar 
```

That will recover everything, firefox extensions, bookmarks, desktop image, the works.

---

