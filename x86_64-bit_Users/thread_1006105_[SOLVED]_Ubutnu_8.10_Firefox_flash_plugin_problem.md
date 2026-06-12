---
title: "[SOLVED] Ubutnu 8.10 Firefox flash plugin problem"
date: 2008-12-09
forum: x86 64-bit Users
---

### Post by pspmasterpro on 2008-12-09
I tried to install this plugin and it says it's installed but when I visit a site like youtube it still says I need flash player. So I downloaded the player manually but when I try to install it I get this error:
```

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

psplegendpro@psplegendpro-desktop:~$ 

```

So I install it manually using sudo apt-get install flashplugin-nonfree
and I get this error.
```

psplegendpro@psplegendpro-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kdebase-runtime-data-common librdf0 libqt4-test kdelibs5 phonon librasqal0
  libqt4-opengl khelpcenter4 libqt4-xmlpatterns libstrigiqtdbusclient0
  libsoprano4 kde-icons-oxygen libqt4-help libclucene0ldbl raptor-utils
  python-sip4 soprano-daemon libqt4-svg python-qt4-common libphonon4
  libqt4-assistant phonon-backend-gstreamer kdelibs-bin redland-utils libpq5
  libstreams0 libqt4-webkit libraptor1 kdelibs5-data kdebase-runtime
  kdebase-runtime-data kdebase-runtime-bin-kde4 libstreamanalyzer0
Use 'apt-get autoremove' to remove them.
Suggested packages:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/19.2kB of archives.
After this operation, 168kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 127171 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.12.36ubuntu1_amd64.deb) ...
Setting up flashplugin-nonfree (10.0.12.36ubuntu1) ...
Downloading...
--2008-12-09 00:05:08--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
Resolving fpdownload.macromedia.com... failed: Name or service not known.
wget: unable to resolve host address `fpdownload.macromedia.com'
download failed
The Flash plugin is NOT installed.

psplegendpro@psplegendpro-desktop:~$ 

```

So does this mean their is no support for flash for the 64-bit version of ubuntu?

---

### Post by tjwallace on 2008-12-09
```
Resolving fpdownload.macromedia.com... failed: Name or service not known.
```
Looks like it kind resolve the host name.  I checked the link and it is alive.  If you use DHCP, I would release and re-new your address.  (disable and re-enable your network connection with the network manager).  Also check /etc/resolv.conf and make sure it points to your routers IP address.

---

### Post by tjwallace on 2008-12-09
You should also try running
```
sudo apt-get install nspluginwrapper flashplugin-nonfree
```
as it says to in [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by FDF12389 on 2008-12-09
The threads below should point you in the right direction. 

[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)
[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

---

### Post by ladgrove on 2008-12-09
There is no "native" support for 64-bit flash in browsers, much the same is true for java plugin. Having said that, there are workarounds for flash; follow the previous post about using nspluginwrapper etc and that should get you started. As for java, there are plenty of open source plugin variants for 64-bit architecture, however, there are some java applets that only run on the sun java paradigm. Now, having said all that...!

My personal experience is that flash support was patchy, youtube vids would often stop halfway in between playing and simply 'gray-out' and I needed sun java for an online trading platform. How did I rectify this situation?
I installed 32-bit Ubuntu, and must say I'm quite pleased with the result. I am only using 4Gb DDR2 which is supported, and I really don't notice any 'speed difference'. Maybe if I'm rendering 3d models or constantly encoding videos would I notice a difference, but even then, only maybe.

My recommendation then, is though it's a pain in the backside, try 32-bit, unless you're sold on 64-bit architecture. This is not a solution, but it will make everyday things like java/flash far more simple.

Fingers crossed that Adobe & Sun provide some level of 64-bit Linux support in the near future.

Apologies if any details are horribly inaccurate, happily corrected :)

Cheers.

---

### Post by xebian on 2008-12-09
> **ladgrove said:**
> There is no "native" support for 64-bit flash in browsers, much the same is true for java plugin. Having said that, there are workarounds for flash; follow the previous post about using nspluginwrapper etc and that should get you started. As for java, there are plenty of open source plugin variants for 64-bit architecture, however, there are some java applets that only run on the sun java paradigm. Now, having said all that...!

My personal experience is that flash support was patchy, youtube vids would often stop halfway in between playing and simply 'gray-out' and I needed sun java for an online trading platform. How did I rectify this situation?
I installed 32-bit Ubuntu, and must say I'm quite pleased with the result. I am only using 4Gb DDR2 which is supported, and I really don't notice any 'speed difference'. Maybe if I'm rendering 3d models or constantly encoding videos would I notice a difference, but even then, only maybe.

My recommendation then, is though it's a pain in the backside, try 32-bit, unless you're sold on 64-bit architecture. This is not a solution, but it will make everyday things like java/flash far more simple.

Fingers crossed that Adobe & Sun provide some level of 64-bit Linux support in the near future.

Apologies if any details are horribly inaccurate, happily corrected :)

Cheers.

News travel slow down under , eh?  64-bit Flash plugin for Linux is now available since 11/17/2008.

---

### Post by Kilz on 2008-12-09
> **xebian said:**
> News travel slow down under , eh?  **the [COLOR="Red"]ALPHA[/COLOR] of **64-bit Flash plugin for Linux is now available since 11/17/2008.

Bold addition mine. The alpha isnt bad though.

---

### Post by ladgrove on 2008-12-09
Ha ha, well I am pleased to hear that. News travels just as fast, though you get bad reception riding kangaroos sometimes ;)

---

### Post by pspmasterpro on 2008-12-09
> **tjwallace said:**
> You should also try running
```
sudo apt-get install nspluginwrapper flashplugin-nonfree
```
as it says to in [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

Thanks it installed without any errors

```

2008-12-09 16:53:49 (55.5 KB/s) - `./install_flash_player_10_linux.tar.gz' saved [3958745/3958745]

Download done.
Flash Plugin installed.

```

---

