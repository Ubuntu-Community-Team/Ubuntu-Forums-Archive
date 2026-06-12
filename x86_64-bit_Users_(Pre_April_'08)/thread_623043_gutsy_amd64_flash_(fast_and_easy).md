---
title: "gutsy amd64 flash (fast and easy)"
date: 2007-11-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cirrocco on 2007-11-25
I was unable to find appropriate help on the ubuntuforums so I went out and found this site: [http://codeside.org/2007/08/23/gutsy-gibbon-amd64-flash/](http://codeside.org/2007/08/23/gutsy-gibbon-amd64-flash/)

it discusses how to reconfigure your nswrapper plugin to make flash work.

just put this in a terminal (no root required):

```
$ nspluginwrapper -v -a -i
```


worked perfectly for me.

---

### Post by Kilz on 2007-11-25
What you are suggesting is adding additional steps that are not needed. You dont need to do any configuration in Gutsy, just install flashplugin-nonfree.

```

sudo apt-get install flashplugin-nonfree
```

---

### Post by rsambuca on 2007-11-25
Cirrocco - You can also just to go to a site that uses flash.  You will be prompted to install the plugin.  Let's not make things more difficult than they need to be.

---

### Post by Cirrocco on 2007-11-26
rsambuca: I tried that, nothing happened for me.

Kilz: what you mentioned was a stepping stone on the journey.  problem was when I did that - it told me I already had it.

I just thought I'd share the thing that made it work for me when every other how-to failed...

---

### Post by Kilz on 2007-11-26
Did you install Gutsy fresh or did you upgrade an existing Feisty install?

---

### Post by roncrump on 2007-11-27
> **Kilz said:**
> Did you install Gutsy fresh or did you upgrade an existing Feisty install?

I hope nobody minds if I join this thread, only I'm struggling to get flash up and running since upgrading to gutsy.

I had flash running on feisty having used Kilz's script. I think I uninstalled everything before upgrading - I followed the uninstallation/removal commands used in the script. Upgraded to gutsy, not a fresh install.

Installed flashplugin-nonfree from synaptic and it won't work. Uninstalled it, after which nspluginwrapper -l showed nothing, and then uninstalled nspluginwrapper. Reinstalled it with synaptic.

nspluginwrapper -l gives the following, but it still won't work:

/usr/lib/mozilla/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib64/mozilla/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib/firefox/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib64/firefox/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5

Suggestions welcomed. Apologies for butting into your conversation.

Ron.

---

### Post by roncrump on 2007-11-27
Just tried:
> 
nspluginwrapper -v -a -i

and that seems to have fixed it.
Ron.

---

### Post by rsambuca on 2007-11-27
Hey, glad we could help ;)

---

### Post by Kilz on 2007-11-27
The reason this is working for you is because you upgraded an existing system that already had nspluginwrapper installed. Simply removing the old nspluginwrapper before installing flashplugin-nonfree will do the same thing. Users with a fresh install need only install flashplugin-nonfree.

---

### Post by Cirrocco on 2007-11-27
negative.

I installed a fresh copy the day before.

---

### Post by Kilz on 2007-11-27
> **Cirrocco said:**
> negative.

I installed a fresh copy the day before.

Did you file a bug report on launchpad?

---

### Post by Alpinist on 2007-11-27
I was having a similar problem since upgrading from Feisty.  I think the problem was that I had uninstalled nspluginwrapper from Adept and so didn't get the message that it hadn't removed the /usr/lib/nspluginwrapper folder because the directory wasn't empty.

Manually renamed that folder after an uninstall then reinstalled flashplugin-nonfree and now seems to be working.

---

### Post by Cirrocco on 2007-11-28
Kilz:  no, I didn't file a bug report.

I didn't know it was a bug.
I was under the impression that flash simply didn't work on 64bit, and to make it work required a hack.

---

### Post by Kilz on 2007-11-28
> **Cirrocco said:**
> Kilz:  no, I didn't file a bug report.

I didn't know it was a bug.
I was under the impression that flash simply didn't work on 64bit, and to make it work required a hack.

Negitive, in Gutsy flash in 64bit should "just work" and be installable with apt/synaptic. The flashplugin-nonfree is all that should need to be installed (along with its requirements). Its a feature for 64bit gutsy. If you have issues after doing that on a clean install, it is a bug that needs to be reported so the developers can fix it.

---

### Post by ophion on 2007-12-04
> **Kilz said:**
> Negitive, in Gutsy flash in 64bit should "just work" and be installable with apt/synaptic. The flashplugin-nonfree is all that should need to be installed (along with its requirements). Its a feature for 64bit gutsy. If you have issues after doing that on a clean install, it is a bug that needs to be reported so the developers can fix it.


Doing that today on Gutsy on amd64 gives me:

md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

---

### Post by th1rst on 2007-12-04
when I click on the link in youtube to get the latest version it tells me that it's not compatible with 64-bit, and if I download it from the popup it doesn't work

---

### Post by skenliv on 2007-12-04
Flash is broken in all ubuntu, they are working on a fix for this.

---

### Post by rsambuca on 2007-12-04
> **skenliv said:**
> Flash is broken in all ubuntu, they are working on a fix for this.

What is the point of posting baseless lies like this?

---

### Post by Roland123 on 2007-12-05
> **rsambuca said:**
> What is the point of posting baseless lies like this?

So 64bit flash isn't broken on gutsy? If not, please tell me how get past this md5checksum error.

Currently, after much hassle i managed to get flash working on a 32bit firefox, but i'd like to use the 64bit one.

---

### Post by rsambuca on 2007-12-05
sudo apt-get install flashplugin-nonfree

If that doesn't work, then switch your repository mirrors.

---

### Post by crjackson on 2007-12-05
> **Roland123 said:**
> So 64bit flash isn't broken on gutsy? If not, please tell me how get past this md5checksum error.

Currently, after much hassle i managed to get flash working on a 32bit firefox, but i'd like to use the 64bit one.

No, I don't think flash is broken on Gutsy.  I think something about your install is broken on Gutsy.  I have several machines in my house running Gutsy 64 and all of them are running with flash.  The flash was installed using the package manager, the add/remove dialog in the applications menu, or using apt-get.  I couldn't have been lucky 7 times...

---

### Post by skenliv on 2007-12-05
maybe it is automatix 2 that is the cause of this, because that is where i originally got this error!

---

### Post by rsambuca on 2007-12-05
> **skenliv said:**
> maybe it is automatix 2 that is the cause of this, because that is where i originally got this error!

Things are so much easier with Gutsy that Automatix is really not necessary.

---

### Post by kyke on 2007-12-05
> **Cirrocco said:**
> I was unable to find appropriate help on the ubuntuforums so I went out and found this site: [http://codeside.org/2007/08/23/gutsy-gibbon-amd64-flash/](http://codeside.org/2007/08/23/gutsy-gibbon-amd64-flash/)

it discusses how to reconfigure your nswrapper plugin to make flash work.

just put this in a terminal (no root required):

```
$ nspluginwrapper -v -a -i
```


worked perfectly for me.

Fresh install from today, have the "md5sum check" error too with the ubuntu package.

Thanks, tip worked just fine, ;)

---

### Post by Kilz on 2007-12-05
> **kyke said:**
> Fresh install from today, have the "md5sum check" error too with the ubuntu package.

Thanks, tip worked just fine, ;)

Did you report your problems with the flashplugin-nonfree as a bug on launchpad?

---

### Post by jdos2 on 2007-12-05
Is sound working for those who have to use Alsa 1.0.15 to get *any* sound? 

I never got past that point- 32 bit applications (except those that run under... Wine) don't have sound, and won't, until Alsa puts their thunk back (as I understand it)

---

### Post by Roland123 on 2007-12-05
i have a fresh install... (2 days old.) 

```
name@computer:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 137 not upgraded.
Need to get 0B/18.1kB of archives.
After unpacking 160kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 124105 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb) ...
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--00:45:48--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 84.53.166.70
Connecting to fpdownload.macromedia.com|84.53.166.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,036,127 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%   48.29 KB/s

 2950K .......... ....                                       100%   21.07 KB/s

00:46:20 (95.73 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.
```

---

### Post by rsambuca on 2007-12-05
> **Roland123 said:**
> i have a fresh install... (2 days old.) 

```
name@computer:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 137 not upgraded.
Need to get 0B/18.1kB of archives.
After unpacking 160kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 124105 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb) ...
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--00:45:48--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 84.53.166.70
Connecting to fpdownload.macromedia.com|84.53.166.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,036,127 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%   48.29 KB/s

 2950K .......... ....                                       100%   21.07 KB/s

00:46:20 (95.73 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.
```

Apparently the flash binary has been updated, but the md5sums haven't been updated yet.  You may try a fix as indicated [in this thread]("http://ubuntuforums.org/showthread.php?t=632322"), or just wait for a day or two.

---

### Post by Kilz on 2007-12-05
> **rsambuca said:**
> Apparently the flash binary has been updated, but the md5sums haven't been updated yet.  You may try a fix as indicated [in this thread]("http://ubuntuforums.org/showthread.php?t=632322"), or just wait for a day or two.

They will be waiting forever if they dont report it so it can be fixed. Thats a problem with work arounds, people ignore the problem thinking this is a real solution and never report it or think someone else will do it.

---

### Post by craiga. on 2007-12-05
thanks for posting this, it really helped a lot. :D

---

### Post by Roland123 on 2007-12-06
**[SIZE="3"]md5sum mismatch problem solved[/SIZE]**

Txukie  ( [LINK]("http://ubuntuforums.org/showthread.php?p=3898317#post3898317")    ) found a solution for this problem and i copied it here. Hope this helps someone.

**SOLUTION:**

> **Txukie said:**
> Problem is that there is a new version of the flahplayer plugin but the file from the internet is called the same.

The .deb checks the sum of this file and obviously gets it wrong, since its looking for the md5sum of the old version and is getting the new version.

A quick workaround for this is to modify the post-install script for this package.

That is after apt-getting the flashplugin-nonfree and it failing you do
 (if you don't have vi installed, you can use some other text editor like kate or gedit - roland123)
sudo vi /var/lib/dpkg/info/flashplugin-nonfree.postinst

You go here:

        # verify MD5 checksum of (copied or downloaded) tarball
        rm -rf install_flash_player_9_linux/
        echo "821cc72359a937caef85bb4cc74ef5cd  install_flash_player_9_linux.tar.gz"| md5sum -c > /dev/null 2>&1 \
                || fp_exit_with_error "md5sum mismatch install_flash_player_9_linux.tar.gz"

        # unpacking and checking the plugin
        tar xzf install_flash_player_9_linux.tar.gz || fp_exit_with_error "cannot unpack plugin"
        echo "be5a2f9032f8fc8bccbbf5d96c5028f9  install_flash_player_9_linux/libflashplayer.so"| md5sum -c > /dev/null 2>&1 \
                || fp_exit_with_error "plugin changed, not trusted"
        echo "a81fd3b03b8c6d6e5a14298110718d3f  install_flash_player_9_linux/flashplayer.xpt"| md5sum -c > /dev/null 2>&1 \
                || fp_exit_with_error "plugin changed, not trusted"


And you change it as such:

        # verify MD5 checksum of (copied or downloaded) tarball
        #rm -rf install_flash_player_9_linux/
        #echo "821cc72359a937caef85bb4cc74ef5cd  install_flash_player_9_linux.tar.gz"| md5sum -c > /dev/null 2>&1 \
         #       || fp_exit_with_error "md5sum mismatch install_flash_player_9_linux.tar.gz"

        # unpacking and checking the plugin
        tar xzf install_flash_player_9_linux.tar.gz || fp_exit_with_error "cannot unpack plugin"
        #echo "be5a2f9032f8fc8bccbbf5d96c5028f9  install_flash_player_9_linux/libflashplayer.so"| md5sum -c > /dev/null 2>&1 \
          #      || fp_exit_with_error "plugin changed, not trusted"
        #echo "a81fd3b03b8c6d6e5a14298110718d3f  install_flash_player_9_linux/flashplayer.xpt"| md5sum -c > /dev/null 2>&1 \
          #      || fp_exit_with_error "plugin changed, not trusted"



Of course you can actually change the md5sums so that they match this new version but this option is just quicker.

What are we supposed to do after editing the postinst file? How to install?

sudo dpkg-reconfigure flashplugin-nonfree
nspluginwrapper -v -a -i

---

### Post by Squizz on 2007-12-06
> **Cirrocco said:**
> 
```
$ nspluginwrapper -v -a -i
```


Worked great for me too - just upgraded from Feisty.

---

### Post by Squizz on 2007-12-06
Actually, thats a lie - the sound won't work.

---

### Post by jdos2 on 2007-12-06
> **Squizz said:**
> Actually, thats a lie - the sound won't work.

That's where I get, too.

Alsa 1.0.15 to support the Intel stuff on the Toshiba Laptop. Something about the 32 bit compatibility libraries not being included anymore.
OSS is reported to work, though. That's next to try.

---

### Post by borisattva on 2007-12-07
> **Cirrocco said:**
> negative.

I installed a fresh copy the day before.

just wanted to second this.

today i installed a fresh amd64 from a DVD and installed the nonfree adobe plugin though the firefox popup. i get the same pop up when i visit any flash site.. restart didnt help.

my previous install was from a cd and it did work straight out. one thing that i believe may have damaged this is i had a second instance of firefox running on the 2nd desktop while the 1st desktop was doing the update. later today i will try to uninstall the plugin, restart and reinstall it with just one firefox running. if that wont work, i'll repeat the process by reinstall from the repo, and post the results here.

---

### Post by daradib on 2007-12-08
This is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree.

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

### Post by guitarman_usa on 2007-12-08
This solution worked for me.  I was having the problem that flash wouldn't work at all in firefox (neither with the adobe nor gnash) after a clean install of gutsy.  It's now fixed!!  Thanks!!

---

### Post by daradib on 2007-12-09
No problem. It's the Ubuntu spirit.

---

### Post by apothecaryaaron on 2007-12-10
> **daradib said:**
> This is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.
 
[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)
 
This causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.
 
If you want an immediate fix, do the following.
 
Using Synaptic Package Manager, remove the package flashplugin-nonfree.
 
Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree
 
Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)
 
If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)
 
Ahhh, thank you.  Flash worked perfectly on my 64 bit laptop, then I tried it on my desktop and it didn't.  Now I know why.  Next step:  how to compile from binary, which I am sure is in these forums... *Time for the search button...*

---

### Post by IeU on 2007-12-10
> **rsambuca said:**
> sudo apt-get install flashplugin-nonfree

If that doesn't work, then switch your repository mirrors.


```
felipe@felipe-desktop:~/regnum$ sudo apt-get install flashplugin-nonfree
[sudo] password for felipe:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavahi-qt3-1 libarts1c2a kdelibs4c2a libartsc0 python-wxgtk2.6 libboost-date-time1.34.1 liblualib50 libopenexr2c2a libboost-thread1.34.1
  libtorrent10 libqt3-mt kdelibs-data liblua50 libadns1 libkdegames1 libaudio2 python-wxversion
Use 'apt-get autoremove' to remove them.
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.1kB of archives.
After unpacking 160kB of additional disk space will be used.
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 105052 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb) ...
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Downloading...
--15:50:57--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 84.53.166.70
Connecting to fpdownload.macromedia.com|84.53.166.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,036,127 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  297.92 KB/s
   50K .......... .......... .......... .......... ..........  3%  768.25 KB/s
  100K .......... .......... .......... .......... ..........  5%  978.67 KB/s
  150K .......... .......... .......... .......... ..........  6%    1.47 MB/s
  200K .......... .......... .......... .......... ..........  8%    1.15 MB/s
  250K .......... .......... .......... .......... .......... 10%    1.18 MB/s
  300K .......... .......... .......... .......... .......... 11%    1.23 MB/s
  350K .......... .......... .......... .......... .......... 13%    1.01 MB/s
  400K .......... .......... .......... .......... .......... 15%    1.45 MB/s
  450K .......... .......... .......... .......... .......... 16%    1.07 MB/s
  500K .......... .......... .......... .......... .......... 18%    1.47 MB/s
  550K .......... .......... .......... .......... .......... 20%    1.12 MB/s
  600K .......... .......... .......... .......... .......... 21%    1.16 MB/s
  650K .......... .......... .......... .......... .......... 23%    1.24 MB/s
  700K .......... .......... .......... .......... .......... 25%    1.47 MB/s
  750K .......... .......... .......... .......... .......... 26%    1.17 MB/s
  800K .......... .......... .......... .......... .......... 28%    1.26 MB/s
  850K .......... .......... .......... .......... .......... 30%    1.47 MB/s
  900K .......... .......... .......... .......... .......... 32%    1.30 MB/s
  950K .......... .......... .......... .......... .......... 33%    1.49 MB/s
 1000K .......... .......... .......... .......... .......... 35%    1.21 MB/s
 1050K .......... .......... .......... .......... .......... 37%    1.20 MB/s
 1100K .......... .......... .......... .......... .......... 38%    1.43 MB/s
 1150K .......... .......... .......... .......... .......... 40%    1.19 MB/s
 1200K .......... .......... .......... .......... .......... 42%  639.84 KB/s
 1250K .......... .......... .......... .......... .......... 43%  420.26 KB/s
 1300K .......... .......... .......... .......... .......... 45%   19.65 MB/s
 1350K .......... .......... .......... .......... .......... 47%  287.88 KB/s
 1400K .......... .......... .......... .......... .......... 48%  429.56 KB/s
 1450K .......... .......... .......... .......... .......... 50%    1.02 MB/s
 1500K .......... .......... .......... .......... .......... 52%    1.36 MB/s
 1550K .......... .......... .......... .......... .......... 53%    1.37 MB/s
 1600K .......... .......... .......... .......... .......... 55%    1.41 MB/s
 1650K .......... .......... .......... .......... .......... 57%    1.35 MB/s
 1700K .......... .......... .......... .......... .......... 59%    1.14 MB/s
 1750K .......... .......... .......... .......... .......... 60%    1.35 MB/s
 1800K .......... .......... .......... .......... .......... 62%  915.81 KB/s
 1850K .......... .......... .......... .......... .......... 64%    1.52 MB/s
 1900K .......... .......... .......... .......... .......... 65%    1.44 MB/s
 1950K .......... .......... .......... .......... .......... 67%  913.19 KB/s
 2000K .......... .......... .......... .......... .......... 69%    1.45 MB/s
 2050K .......... .......... .......... .......... .......... 70%  903.55 KB/s
 2100K .......... .......... .......... .......... .......... 72%    1.47 MB/s
 2150K .......... .......... .......... .......... .......... 74%    1.50 MB/s
 2200K .......... .......... .......... .......... .......... 75%  910.67 KB/s
 2250K .......... .......... .......... .......... .......... 77%  915.86 KB/s
 2300K .......... .......... .......... .......... .......... 79%    1.16 MB/s
 2350K .......... .......... .......... .......... .......... 80%    1.04 MB/s
 2400K .......... .......... .......... .......... .......... 82%    1.17 MB/s
 2450K .......... .......... .......... .......... .......... 84%    1.12 MB/s
 2500K .......... .......... .......... .......... .......... 86%    1.45 MB/s
 2550K .......... .......... .......... .......... .......... 87%  957.82 KB/s
 2600K .......... .......... .......... .......... .......... 89%    1.18 MB/s
 2650K .......... .......... .......... .......... .......... 91%    1.49 MB/s
 2700K .......... .......... .......... .......... .......... 92%  985.33 KB/s
 2750K .......... .......... .......... .......... .......... 94%    1.23 MB/s
 2800K .......... .......... .......... .......... .......... 96%  965.08 KB/s
 2850K .......... .......... .......... .......... .......... 97%    1.51 MB/s
 2900K .......... .......... .......... .......... .......... 99%    1.23 MB/s
 2950K .......... ....                                       100%    1.40 MB/s

15:51:00 (1.01 MB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.


```

---

### Post by rsambuca on 2007-12-10


You might consider reading the threads you are posting in.  There was an explanation, along with a temporary fix just 4 posts back (Post #36).

---

### Post by daradib on 2007-12-10
Please see [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

This includes everything about the current flash player plugin bug (or so I hope I didn't forget anything), including how to compile from source.

---

### Post by buntunub on 2007-12-10
Problem: The flash package you built does not work. It only loads youtube sites but fails on disney.com and nick.com. Any ideas?

---

### Post by Sighn on 2007-12-10
> **ophion said:**
> Doing that today on Gutsy on amd64 gives me:

md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

I got this same problem in Gutsy x86, earlier (new install).

I installed Flash via the Synaptics Manager, anyway. With that installed (I took it that the  'NOT installed' message was strictly referring to the browser plugin) I did the following

The browser 'plugin' file is   libflashplayer.so     Download and unpack the tar.gz package from the Adobe Flash site [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)
 libflashplayer.so  goes in  /usr/lib/firefox/plugins.

Solved the problem, for me, as far as x86 goes

---

### Post by Kilz on 2007-12-11
> **buntunub said:**
> Problem: The flash package you built does not work. It only loads youtube sites but fails on disney.com and nick.com. Any ideas?

Solution - Flash is installed, no one said it was perfect. That it works on youtube shows its installed. File bug reports with Adobe, nspluginwrapper, and Ubuntu to make bugs known to developers.

---

### Post by daradib on 2007-12-11
> **Sighn said:**
> I got this same problem in Gutsy x86, earlier (new install).

The browser 'plugin' file is   libflashplayer.so     Download and unpack the tar.gz package from the Adobe Flash site [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)
 libflashplayer.so  goes in  /usr/lib/firefox/plugins.

Solved the problem, for me, as far as x86 goes

That would work, but the method provided in [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397) would be a better option for 32-bit Ubuntu and necessary for 64-bit Ubuntu.

---

### Post by Sighn on 2007-12-11
As I've just finished installing the 64-bit version, I'll try the link. Thanks :)

---

