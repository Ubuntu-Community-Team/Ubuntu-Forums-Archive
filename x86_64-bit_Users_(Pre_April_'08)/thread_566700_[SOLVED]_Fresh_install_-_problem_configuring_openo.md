---
title: "[SOLVED] Fresh install - problem configuring openoffice.org and fonts"
date: 2007-10-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by keithlommel on 2007-10-03
Hello,

I successfully installed x64 Feisty a few days ago, got everything set up nicely (thanks to the how-tos and other guidance from this forum) and was really enjoying Ubuntu. So much so that I decided to repartition to take away space from my Windows XP install and give more to Ubuntu. So I popped the install disk in, redid the partitions and installed fresh. I figured everything went so smoothly the first time, the second time would be a breeze!

Not so. This time, the auto update system seems to have difficulty configuring openoffice.org and a bunch of fonts. This appears to be having an effect on both Firefox and Swiftweasel, in that some text doesn't seem to be positioned correctly on certain websites. Additionally, where last time the operating system was very snappy and quick, now it seems very sluggish. Opening any program involves a delay of about 5-6 seconds. This is true even for something as simple as opening a terminal window - you click on "Terminal" under "Accessories" and a tab appears on the bottom toolbar saying "Starting Terminal". Then 5-6 seconds later, the terminal opens. This used to be pretty much instantaneous. I'm not sure how (or if) this is related to the openoffice.org and font problem.

Anyway, here's the set of error messages I get when I do a sudo apt-get update:

> [FONT="Courier New"]sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
16 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ttf-opensymbol (2.2.0-1ubuntu4) ...
Updating fontconfig cache...
/usr/share/fonts: failed to write cache
/usr/share/fonts/X11: failed to write cache
/usr/share/fonts/X11/100dpi: failed to write cache
/usr/share/fonts/X11/75dpi: failed to write cache
/usr/share/fonts/X11/Type1: failed to write cache
/usr/share/fonts/X11/encodings: failed to write cache
/usr/share/fonts/X11/encodings/large: failed to write cache
/usr/share/fonts/X11/misc: failed to write cache
/usr/share/fonts/X11/util: failed to write cache
/usr/share/fonts/truetype: failed to write cache
/usr/share/fonts/truetype/arphic: failed to write cache
/usr/share/fonts/truetype/baekmuk: failed to write cache
/usr/share/fonts/truetype/freefont: failed to write cache
/usr/share/fonts/truetype/kochi: failed to write cache
/usr/share/fonts/truetype/thai: failed to write cache
/usr/share/fonts/truetype/ttf-arabeyes: failed to write cache
/usr/share/fonts/truetype/ttf-bengali-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-bitstream-vera: failed to write cache
/usr/share/fonts/truetype/ttf-dejavu: failed to write cache
/usr/share/fonts/truetype/ttf-devanagari-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-gentium: failed to write cache
/usr/share/fonts/truetype/ttf-gujarati-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-kannada-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-lao: failed to write cache
/usr/share/fonts/truetype/ttf-malayalam-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-mgopen: failed to write cache
/usr/share/fonts/truetype/ttf-oriya-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-punjabi-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-tamil-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-telugu-fonts: failed to write cache
/usr/share/fonts/type1: failed to write cache
/usr/share/fonts/type1/gsfonts: failed to write cache
/usr/share/X11/fonts: failed to write cache
/usr/share/X11/fonts/100dpi: failed to write cache
/usr/share/X11/fonts/75dpi: failed to write cache
/usr/share/X11/fonts/Type1: failed to write cache
/usr/share/X11/fonts/encodings: failed to write cache
/usr/share/X11/fonts/encodings/large: failed to write cache
/usr/share/X11/fonts/misc: failed to write cache
/usr/share/X11/fonts/util: failed to write cache
/usr/local/share/fonts: failed to write cache
/var/lib/defoma/fontconfig.d: failed to write cache
/var/lib/defoma/fontconfig.d/A: failed to write cache
/var/lib/defoma/fontconfig.d/B: failed to write cache
/var/lib/defoma/fontconfig.d/C: failed to write cache
/var/lib/defoma/fontconfig.d/D: failed to write cache
/var/lib/defoma/fontconfig.d/E: failed to write cache
/var/lib/defoma/fontconfig.d/F: failed to write cache
/var/lib/defoma/fontconfig.d/G: failed to write cache
/var/lib/defoma/fontconfig.d/H: failed to write cache
/var/lib/defoma/fontconfig.d/J: failed to write cache
/var/lib/defoma/fontconfig.d/K: failed to write cache
/var/lib/defoma/fontconfig.d/L: failed to write cache
/var/lib/defoma/fontconfig.d/M: failed to write cache
/var/lib/defoma/fontconfig.d/N: failed to write cache
/var/lib/defoma/fontconfig.d/O: failed to write cache
/var/lib/defoma/fontconfig.d/P: failed to write cache
/var/lib/defoma/fontconfig.d/R: failed to write cache
/var/lib/defoma/fontconfig.d/S: failed to write cache
/var/lib/defoma/fontconfig.d/T: failed to write cache
/var/lib/defoma/fontconfig.d/U: failed to write cache
/var/lib/defoma/fontconfig.d/V: failed to write cache
/var/lib/defoma/fontconfig.d/a: failed to write cache
/var/lib/defoma/fontconfig.d/j: failed to write cache
/var/lib/defoma/fontconfig.d/m: failed to write cache
/var/lib/defoma/fontconfig.d/u: failed to write cache
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 66
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on python-uno (>= 2.2.0); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org depends on openoffice.org-writer; however:
  Package openoffice.org-writer is not configured yet.
 openoffice.org depends on openoffice.org-calc; however:
  Package openoffice.org-calc is not configured yet.
 openoffice.org depends on openoffice.org-impress; however:
  Package openoffice.org-impress is not configured yet.
 openoffice.org depends on openoffice.org-draw; however:
  Package openoffice.org-draw is not configured yet.
 openoffice.org depends on openoffice.org-math; however:
  Package openoffice.org-math is not configured yet.
 openoffice.org depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 2.2.0) | openoffice.org-core-experimental (>> 2.2.0); however:
  Package openoffice.org-core is not configured yet.
  Package openoffice.org-core-experimental is not installed.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-mobiledev:
 openoffice.org-filter-mobiledev depends on openoffice.org-java-common (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-filter-mobiledev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 python-uno
 openoffice.org-writer
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-impress
 openoffice.org-math
 openoffice.org-base
 openoffice.org
 openoffice.org-gtk
 openoffice.org-gnome
 openoffice.org-common
 openoffice.org-java-common
 openoffice.org-filter-mobiledev
 openoffice.org-style-human
E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT]


I'm running this on a Dell 1505 notebook with a Core 2 Duo 2.0GHz processor and an ATI Mobility Radeon X1400.

I appreciate your assistance!
--Keith

---

### Post by Jouke74 on 2007-10-04
Yeah I got that error a few times as well. It starts when you mess with Openoffice ttf-opensymbol and aptitude. The problem is centered in the font ttf-opensymbol. If you fix this than your Openoffice dependency problems will subsequently be fixed as well. 

To solve it you need to use a trick, namely you need to "touch" the directory's where the fonts are in that are causing problems. Let me check for the right threads on this, ah: 

[http://ubuntuforums.org/showthread.php?t=326341&highlight=ttf-symbol+touch+font&page=2](http://ubuntuforums.org/showthread.php?t=326341&highlight=ttf-symbol+touch+font&page=2)

and here:

[http://ubuntuforums.org/showthread.php?t=400473&highlight=ttf-symbol+touch+font](http://ubuntuforums.org/showthread.php?t=400473&highlight=ttf-symbol+touch+font)

Basically
- First make a list of the directories (copy paste and clean out all non-directory characters).
- Then run the specified touch command.
- Reinstall ttf-symbol
- Update your font-cache: "fc-cache" 
- Reinstall packages you wish, or remove packages you wish. 
- Clean apt: "sudo apt-get autoremove"

---

### Post by keithlommel on 2007-10-04
Thanks a lot. That appears to have done the trick, although I'm still puzzled as to why I had this problem. I certainly didn't monkey around with ttf-opensymbol or aptitude or whatever. I literally just installed from the CD and then allowed the updater to install all the updates since the CD was released...

Anyway, thanks for the help.

---

### Post by Jouke74 on 2007-10-04
Yes, an update in ttf-opensymbol caused it, if you check your list carefully it will show an update on this file. Somehow it not always happens. Please put the thread on solved.

---

### Post by keithlommel on 2007-10-04
Thanks again.

---

