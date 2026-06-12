---
title: "[SOLVED] problem with apt-get upgrade"
date: 2008-01-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by darkenemy on 2008-01-06
when i try to install new things through add/remove i keep getting

```

E: ttf-opensymbol: subprocess post-installation script returned error exit status 40
E: openoffice.org-core: dependency problems - leaving unconfigured
E: openoffice.org-common: dependency problems - leaving unconfigured
E: openoffice.org-style-human: dependency problems - leaving unconfigured
E: python-uno: dependency problems - leaving unconfigured
E: openoffice.org-writer: dependency problems - leaving unconfigured
E: openoffice.org-calc: dependency problems - leaving unconfigured
E: openoffice.org-draw: dependency problems - leaving unconfigured
E: openoffice.org-impress: dependency problems - leaving unconfigured
E: openoffice.org-math: dependency problems - leaving unconfigured
E: openoffice.org-java-common: dependency problems - leaving unconfigured
E: openoffice.org-base: dependency problems - leaving unconfigured
E: openoffice.org: dependency problems - leaving unconfigured
E: openoffice.org-evolution: dependency problems - leaving unconfigured
E: openoffice.org-gtk: dependency problems - leaving unconfigured
E: openoffice.org-gnome: dependency problems - leaving unconfigured

```

and when i try a sudo apt-get upgrade, there is this

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
16 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ttf-opensymbol (1:2.3.0-1ubuntu5.3) ...
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
/usr/share/fonts/truetype/arphic: failed to write cache
/usr/share/fonts/truetype/freefont: failed to write cache
/usr/share/fonts/truetype/kochi: failed to write cache
/usr/share/fonts/truetype/thai: failed to write cache
/usr/share/fonts/truetype/ttf-arabeyes: failed to write cache
/usr/share/fonts/truetype/ttf-bitstream-vera: failed to write cache
/usr/share/fonts/truetype/ttf-gentium: failed to write cache
/usr/share/fonts/truetype/ttf-indic-fonts-core: failed to write cache
/usr/share/fonts/truetype/ttf-lao: failed to write cache
/usr/share/fonts/truetype/ttf-malayalam-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-mgopen: failed to write cache
/usr/share/fonts/truetype/unfonts: failed to write cache
/usr/share/fonts/type1: failed to write cache
/usr/share/fonts/type1/gsfonts: failed to write cache
/usr/local/share/fonts: failed to write cache
/var/lib/defoma/fontconfig.d/B: failed to write cache
/var/lib/defoma/fontconfig.d/E: failed to write cache
/var/lib/defoma/fontconfig.d/F: failed to write cache
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
/var/lib/defoma/fontconfig.d/U: failed to write cache
/var/lib/defoma/fontconfig.d/m: failed to write cache
/var/lib/defoma/fontconfig.d/u: failed to write cache
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 40
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 1:2.3.0); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on python-uno (>= 1:2.3.0); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
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
 openoffice.org depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-evolution depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gtk depends on openoffice.org-style-human; however:
  Package openoffice.org-style-human is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-common
 openoffice.org-style-human
 python-uno
 openoffice.org-writer
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-impress
 openoffice.org-math
 openoffice.org-java-common
 openoffice.org-base
 openoffice.org
 openoffice.org-evolution
 openoffice.org-gtk
 openoffice.org-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

does anyone know my problem?


this is a problem because it prevents me from installing other things, for instance
when i enter

sudo apt-get install linux-restricted-modules-generic restricted-manager

i get

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-generic is already the newest version.
restricted-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
16 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up ttf-opensymbol (1:2.3.0-1ubuntu5.3) ...
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
/usr/share/fonts/truetype/arphic: failed to write cache
/usr/share/fonts/truetype/freefont: failed to write cache
/usr/share/fonts/truetype/kochi: failed to write cache
/usr/share/fonts/truetype/thai: failed to write cache
/usr/share/fonts/truetype/ttf-arabeyes: failed to write cache
/usr/share/fonts/truetype/ttf-bitstream-vera: failed to write cache
/usr/share/fonts/truetype/ttf-gentium: failed to write cache
/usr/share/fonts/truetype/ttf-indic-fonts-core: failed to write cache
/usr/share/fonts/truetype/ttf-lao: failed to write cache
/usr/share/fonts/truetype/ttf-malayalam-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-mgopen: failed to write cache
/usr/share/fonts/truetype/unfonts: failed to write cache
/usr/share/fonts/type1: failed to write cache
/usr/share/fonts/type1/gsfonts: failed to write cache
/usr/local/share/fonts: failed to write cache
/var/lib/defoma/fontconfig.d/B: failed to write cache
/var/lib/defoma/fontconfig.d/E: failed to write cache
/var/lib/defoma/fontconfig.d/F: failed to write cache
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
/var/lib/defoma/fontconfig.d/U: failed to write cache
/var/lib/defoma/fontconfig.d/m: failed to write cache
/var/lib/defoma/fontconfig.d/u: failed to write cache
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 40
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 1:2.3.0); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on python-uno (>= 1:2.3.0); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

even though the command had nothing to do with open office or fonts (it was for an ATI driver)

---

### Post by darkenemy on 2008-01-07
bump

---

### Post by darkenemy on 2008-01-07
i was able to reduce the problem to just

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
16 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ttf-opensymbol (1:2.3.0-1ubuntu5.3) ...
Updating fontconfig cache...
/usr/share/fonts/truetype/thai: failed to write cache
/usr/share/fonts/truetype/ttf-indic-fonts-core: failed to write cache
/usr/share/fonts/truetype/unfonts: failed to write cache
"/usr/share/X11/fonts": not a directory, skipping
/var/lib/defoma/fontconfig.d/L: failed to write cache
/var/lib/defoma/fontconfig.d/N: failed to write cache
/var/lib/defoma/fontconfig.d/P: failed to write cache
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 6
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 1:2.3.0); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on python-uno (>= 1:2.3.0); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
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
 openoffice.org depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-evolution depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gtk depends on openoffice.org-style-human; however:
  Package openoffice.org-style-human is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-common
 openoffice.org-style-human
 python-uno
 openoffice.org-writer
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-impress
 openoffice.org-math
 openoffice.org-java-common
 openoffice.org-base
 openoffice.org
 openoffice.org-evolution
 openoffice.org-gtk
 openoffice.org-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


now where do i go from here?

---

### Post by sbassett on 2008-01-07
What is the output of

```
sudo dpkg-reconfigure fontconfig
```

---

### Post by darkenemy on 2008-01-07
the output is 

```
Cleaning up font configuration of fontconfig...
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category type1..
Updating font configuration of fontconfig...
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category type1..
Updating category type1..
Updating category truetype..
Updating category cid..
Regenerating fonts cache... failed.
See /var/log/fontconfig.log for more information.
done.

```


adn after that the output of sudo apt-get upgrade is

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
16 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ttf-opensymbol (1:2.3.0-1ubuntu5.3) ...
Updating fontconfig cache...
/usr/share/fonts/truetype/thai: failed to write cache
/usr/share/fonts/truetype/ttf-indic-fonts-core: failed to write cache
/usr/share/fonts/truetype/unfonts: failed to write cache
"/usr/share/X11/fonts": not a directory, skipping
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 1:2.3.0); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on python-uno (>= 1:2.3.0); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
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
 openoffice.org depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-evolution depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gtk depends on openoffice.org-style-human; however:
  Package openoffice.org-style-human is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-common
 openoffice.org-style-human
 python-uno
 openoffice.org-writer
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-impress
 openoffice.org-math
 openoffice.org-java-common
 openoffice.org-base
 openoffice.org
 openoffice.org-evolution
 openoffice.org-gtk
 openoffice.org-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by John.Michael.Kane on 2008-01-07
You can give the below steps a try.

1) Try to configure packages that are un-configured :
```
sudo dpkg --configure -a
```

2) Next try leting apt-get remove all problem packages automatically :
```
sudo aptitude -f remove
```

3) Retry configuring all packages that are un-configured :
```
sudo dpkg --configure -a
```

Another option manually remove the package/packages causing issues
```
sudo aptitude remove -f packageA
```

Also you may want to make sure you have the following item installed 

```
sudo aptitude install ubuntu-minimal ubuntu-standard
```

After all the above is done run through the below commands.
```
sudo aptitude update
```
```
sudo aptitude upgrade
```
```
sudo aptitude dist-upgrade
```

As a last step the machine may need a reboot
```
sudo reboot
```

---

### Post by darkenemy on 2008-01-07
the output of the first thing was

```
Setting up ttf-opensymbol (1:2.3.0-1ubuntu5.3) ...
Updating fontconfig cache...
/usr/share/fonts/truetype/thai: failed to write cache
/usr/share/fonts/truetype/ttf-indic-fonts-core: failed to write cache
/usr/share/fonts/truetype/unfonts: failed to write cache
"/usr/share/X11/fonts": not a directory, skipping
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 1:2.3.0); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org depends on openoffice.org-writer; however:
  Package openoffice.org-writer is not configured yet.
 openoffice.org depends on openoffice.org-calc; however:
  Package openoffice.org-calc is not configured yet.
 openoffice.org depends on openoffice.org-draw; however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-draw
 openoffice.org-gtk
 openoffice.org-calc
 openoffice.org-common
 openoffice.org-writer
 python-uno
 openoffice.org
 openoffice.org-evolution
 openoffice.org-style-human
 openoffice.org-gnome
 openoffice.org-java-common
 openoffice.org-impress
 openoffice.org-base
 openoffice.org-math

```





aptitude remove

```
Setting up ttf-opensymbol (1:2.3.0-1ubuntu5.3) ...
Updating fontconfig cache...
/usr/share/fonts/truetype/thai: failed to write cache
/usr/share/fonts/truetype/ttf-indic-fonts-core: failed to write cache
/usr/share/fonts/truetype/unfonts: failed to write cache
"/usr/share/X11/fonts": not a directory, skipping
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 1:2.3.0); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org depends on openoffice.org-writer; however:
  Package openoffice.org-writer is not configured yet.
 openoffice.org depends on openoffice.org-calc; however:
  Package openoffice.org-calc is not configured yet.
 openoffice.org depends on openoffice.org-draw; however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-draw
 openoffice.org-gtk
 openoffice.org-calc
 openoffice.org-common
 openoffice.org-writer
 python-uno
 openoffice.org
 openoffice.org-evolution
 openoffice.org-style-human
 openoffice.org-gnome
 openoffice.org-java-common
 openoffice.org-impress
 openoffice.org-base
 openoffice.org-math

```





and when i try again with teh reconfigure

```
Setting up ttf-opensymbol (1:2.3.0-1ubuntu5.3) ...
Updating fontconfig cache...
/usr/share/fonts/truetype/thai: failed to write cache
/usr/share/fonts/truetype/ttf-indic-fonts-core: failed to write cache
/usr/share/fonts/truetype/unfonts: failed to write cache
"/usr/share/X11/fonts": not a directory, skipping
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 1:2.3.0); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org depends on openoffice.org-writer; however:
  Package openoffice.org-writer is not configured yet.
 openoffice.org depends on openoffice.org-calc; however:
  Package openoffice.org-calc is not configured yet.
 openoffice.org depends on openoffice.org-draw; however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-draw
 openoffice.org-gtk
 openoffice.org-calc
 openoffice.org-common
 openoffice.org-writer
 python-uno
 openoffice.org
 openoffice.org-evolution
 openoffice.org-style-human
 openoffice.org-gnome
 openoffice.org-java-common
 openoffice.org-impress
 openoffice.org-base
 openoffice.org-math

```





for the remove packageA

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "packageA"
The following partially installed packages will be configured:
  openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-human openoffice.org-writer python-uno 
  ttf-opensymbol 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up ttf-opensymbol (1:2.3.0-1ubuntu5.3) ...
Updating fontconfig cache...
/usr/share/fonts/truetype/thai: failed to write cache
/usr/share/fonts/truetype/ttf-indic-fonts-core: failed to write cache
/usr/share/fonts/truetype/unfonts: failed to write cache
"/usr/share/X11/fonts": not a directory, skipping
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 1:2.3.0); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on python-uno (>= 1:2.3.0); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
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
 openoffice.org depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-evolution depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gtk depends on openoffice.org-style-human; however:
  Package openoffice.org-style-human is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-common
 openoffice.org-style-human
 python-uno
 openoffice.org-writer
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-impress
 openoffice.org-math
 openoffice.org-java-common
 openoffice.org-base
 openoffice.org
 openoffice.org-evolution
 openoffice.org-gtk
 openoffice.org-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up ttf-opensymbol (1:2.3.0-1ubuntu5.3) ...
Updating fontconfig cache...
/usr/share/fonts/truetype/thai: failed to write cache
/usr/share/fonts/truetype/ttf-indic-fonts-core: failed to write cache
/usr/share/fonts/truetype/unfonts: failed to write cache
"/usr/share/X11/fonts": not a directory, skipping
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 1:2.3.0); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org depends on openoffice.org-writer; however:
  Package openoffice.org-writer is not configured yet.
 openoffice.org depends on openoffice.org-calc; however:
  Package openoffice.org-calc is not configured yet.
 openoffice.org depends on openoffice.org-draw; however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-draw
 openoffice.org-gtk
 openoffice.org-calc
 openoffice.org-common
 openoffice.org-writer
 python-uno
 openoffice.org
 openoffice.org-evolution
 openoffice.org-style-human
 openoffice.org-gnome
 openoffice.org-java-common
 openoffice.org-impress
 openoffice.org-base
 openoffice.org-math
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
```







when i try the installation 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following partially installed packages will be configured:
  openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-human openoffice.org-writer python-uno 
  ttf-opensymbol 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up ttf-opensymbol (1:2.3.0-1ubuntu5.3) ...
Updating fontconfig cache...
/usr/share/fonts/truetype/thai: failed to write cache
/usr/share/fonts/truetype/ttf-indic-fonts-core: failed to write cache
/usr/share/fonts/truetype/unfonts: failed to write cache
"/usr/share/X11/fonts": not a directory, skipping
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 1:2.3.0); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on python-uno (>= 1:2.3.0); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
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
 openoffice.org depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-evolution depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gtk depends on openoffice.org-style-human; however:
  Package openoffice.org-style-human is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-common
 openoffice.org-style-human
 python-uno
 openoffice.org-writer
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-impress
 openoffice.org-math
 openoffice.org-java-common
 openoffice.org-base
 openoffice.org
 openoffice.org-evolution
 openoffice.org-gtk
 openoffice.org-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up ttf-opensymbol (1:2.3.0-1ubuntu5.3) ...
Updating fontconfig cache...
/usr/share/fonts/truetype/thai: failed to write cache
/usr/share/fonts/truetype/ttf-indic-fonts-core: failed to write cache
/usr/share/fonts/truetype/unfonts: failed to write cache
"/usr/share/X11/fonts": not a directory, skipping
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 1:2.3.0); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org depends on openoffice.org-writer; however:
  Package openoffice.org-writer is not configured yet.
 openoffice.org depends on openoffice.org-calc; however:
  Package openoffice.org-calc is not configured yet.
 openoffice.org depends on openoffice.org-draw; however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-draw
 openoffice.org-gtk
 openoffice.org-calc
 openoffice.org-common
 openoffice.org-writer
 python-uno
 openoffice.org
 openoffice.org-evolution
 openoffice.org-style-human
 openoffice.org-gnome
 openoffice.org-java-common
 openoffice.org-impress
 openoffice.org-base
 openoffice.org-math
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done     
```



the output of an aptitude upgrade is

```
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following partially installed packages will be configured:
  openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-human openoffice.org-writer python-uno 
  ttf-opensymbol 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up ttf-opensymbol (1:2.3.0-1ubuntu5.3) ...
Updating fontconfig cache...
/usr/share/fonts/truetype/thai: failed to write cache
/usr/share/fonts/truetype/ttf-indic-fonts-core: failed to write cache
/usr/share/fonts/truetype/unfonts: failed to write cache
"/usr/share/X11/fonts": not a directory, skipping
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 1:2.3.0); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on python-uno (>= 1:2.3.0); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
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
 openoffice.org depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-evolution depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gtk depends on openoffice.org-style-human; however:
  Package openoffice.org-style-human is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-common
 openoffice.org-style-human
 python-uno
 openoffice.org-writer
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-impress
 openoffice.org-math
 openoffice.org-java-common
 openoffice.org-base
 openoffice.org
 openoffice.org-evolution
 openoffice.org-gtk
 openoffice.org-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up ttf-opensymbol (1:2.3.0-1ubuntu5.3) ...
Updating fontconfig cache...
/usr/share/fonts/truetype/thai: failed to write cache
/usr/share/fonts/truetype/ttf-indic-fonts-core: failed to write cache
/usr/share/fonts/truetype/unfonts: failed to write cache
"/usr/share/X11/fonts": not a directory, skipping
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 1:2.3.0); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org depends on openoffice.org-writer; however:
  Package openoffice.org-writer is not configured yet.
 openoffice.org depends on openoffice.org-calc; however:
  Package openoffice.org-calc is not configured yet.
 openoffice.org depends on openoffice.org-draw; however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-draw
 openoffice.org-gtk
 openoffice.org-calc
 openoffice.org-common
 openoffice.org-writer
 python-uno
 openoffice.org
 openoffice.org-evolution
 openoffice.org-style-human
 openoffice.org-gnome
 openoffice.org-java-common
 openoffice.org-impress
 openoffice.org-base
 openoffice.org-math
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      

```





distro upgrade and rebooting did nothing special

but thanks for the try!  it wont let me install anything else untill this gets fixed... so im hoping it has a solution

---

### Post by John.Michael.Kane on 2008-01-07
Can you post your sources.list.

```
gedit /etc/apt/sources.list
```

---

### Post by sbassett on 2008-01-07
And after that:

```
df -h
```

Thanks for your patience.

---

### Post by darkenemy on 2008-01-07
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by darkenemy on 2008-01-07
oops and this too

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             224G  3.3G  209G   2% /
varrun               1008M   88K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M   72K 1008M   1% /dev
devshm               1008M     0 1008M   0% /dev/shm
lrm                  1008M   38M  970M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1             466G  353G  114G  76% /media/My Book

```

---

### Post by sbassett on 2008-01-07
Please see [http://ubuntuforums.org/showpost.php?p=2401087&postcount=4]("http://ubuntuforums.org/showpost.php?p=2401087&postcount=4")

*****AS ALWAYS - these commands require superuser access, please proceed with caution*****

basically, save the attachment and then execute 

```
sudo -i 
```

then

```
cat /home/USERNAME/cache_fail_folder_list.txt | xargs touch 
```

This seemed to help out the poor guy that fell into this last time.

Please let us know how it turns out.

---

### Post by darkenemy on 2008-01-07
```
touch: cannot touch `/usr/share/X11/fonts/100dpi': Not a directory
touch: cannot touch `/usr/share/X11/fonts/75dpi': Not a directory
touch: cannot touch `/usr/share/X11/fonts/Type1': Not a directory
touch: cannot touch `/usr/share/X11/fonts/encodings': Not a directory
touch: cannot touch `/usr/share/X11/fonts/encodings/large': Not a directory
touch: cannot touch `/usr/share/X11/fonts/misc': Not a directory
touch: cannot touch `/usr/share/X11/fonts/util': Not a directory

```

should i try touching each of them individually will that fix anything?

---

### Post by sbassett on 2008-01-07
well, it look like the original error was in regards to /usr/share/fonts/X11/. So let's verify that guy first. What is the output of 

```
ls /usr/share/fonts/X11/
```

---

### Post by sbassett on 2008-01-07
[http://soniahamilton.wordpress.com/2007/09/09/usrsharefonts-failed-to-write-cache/]("http://soniahamilton.wordpress.com/2007/09/09/usrsharefonts-failed-to-write-cache/")

take a look at the 2nd suggestion as well as the first comment.

---

### Post by darkenemy on 2008-01-07
the ls command gives me this 

```
100dpi  75dpi  encodings  misc  Type1  util

```

except it is in some weird shade of blue for some reason

---

### Post by darkenemy on 2008-01-07
the comments on that other post dont help....

---

### Post by darkenemy on 2008-01-07
i have no idea why


but it works...... lol

i did a sudo apt-get upgrade and got this


```
Setting up ttf-opensymbol (1:2.3.0-1ubuntu5.3) ...
Updating fontconfig cache...
"/usr/share/X11/fonts": not a directory, skipping

Setting up openoffice.org-core (1:2.3.0-1ubuntu5.3) ...
Setting up openoffice.org-style-human (1:2.3.0-1ubuntu5.3) ...
Setting up python-uno (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-writer (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-calc (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-draw (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-impress (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-math (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-gtk (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-gnome (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-common (1:2.3.0-1ubuntu5.3) ...
Updating OpenOffice.org's dictionary list... done.
No theme index file in '/usr/share/icons/locolor'.
If you really want to create an icon cache here, use --ignore-theme-index.

Setting up openoffice.org-java-common (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-base (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-evolution (1:2.3.0-1ubuntu5.3) ...


```


strange

but problem solved

YAY!

---

### Post by sbassett on 2008-01-07
I just took a full look at the .txt file. It looks as if it touches both /usr/share/fonts/X11/ and /usr/share/X11/fonts/ (not entirely sure why) but that is why you received the errors the first time you ran the file, In the meantime, it touched the files that needed to be created.

Glad you are all straightened out.

---

