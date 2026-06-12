---
title: "Get more 64 out of Intrepid (with Jaunty packages)"
date: 2009-10-08
forum: x86 64-bit Users
---

### Post by quequotion on 2009-10-08
Unfortunately a full upgrade is not an option for me, unless I buy a new graphics card.  I'm among the angry, unsupported, unappreciated ATI users with a card slightly over a year old.

If you're like me, and for whatever reason don't want to go fully Jaunty and if you check your system log and see this: ```
warning: 'something' uses 32-bit capabilities (legacy support in use)
```
Try installing the equivalent packages from Jaunty.
Of most importance are the packages which have been upgraded to **libcap2 **dependency, like **pulseaudio **and **avahi-daemon**.

It is a bit of a headache, but I can confirm that those two at least can be installed in Intrepid.  You'll have to download a lot of dependencies manually and install them with dpkg when your apt-cache gets broken.

I ended up with about a full third or more of my distribution being replaced by Jaunty packages (Jaunty's avahi-daemon depends on Jaunty's **libc6**, and just about everything depends on libc6) and it runs considerably more smoothly.

*Watch out for*

***Chicken-and-egg dependencies***. The solution for this problem with two that came up under **avahi-daemon**'s dependencies was to copy them to a folder and run```
dpkg -i -R folder/
```However this did not work as well for the same problem with two of **pulseaudio**'s dependencies--it only got one of the two to install. The second package I then installed normally.

***32bit and Dev libraries***.
This may actually be a bug in GDebi(or the whole apt system?), but because my actions are absolutely unsupported I don't think I have any right to file a bug report.
If you install updated versions of certain libraries and have their development and/or 32bit versions installed beforehand, GDebi may not recognize that the package you are installing will break their dependencies and it will allow you to install the package anyway.
GDebi then terminates with a message about "dependencies not fully installed" and a "broken [apt-]cache".
In all cases I was able to fix the problem by finding the 32bit and development libraries that match the updated package I had installed. 

Synatpic had suggested that I remove nearly every package on the system after installing Jaunty's libc6. If this happens to you, and I expect it will, ***don't panic.*** Work out the dependency chain by looking carefully through Synaptic and install the necessary packages one at a time with dpkg. (tip - start with the package you value most and work your way down it's dependency chain)

***Going too far***.
I got a little ambitious and tried to install some pulseaudio-module-udev from Karmic Koala. The catch was upgrading libpulse0, which breaks pavucontrol because it requires updated glib2 and other libraries which eventually led me into x11 dependencies. It came down to libxcb-xlib, which has been done away with after Intrepid, but is still essential to my system. in the process however I had "sucessfully" upgraded glib2 and gtk2, but upon reboot found that gdm would no longer start. No package installer had given me any grief and no errors appeared in the system log later. Mysterious yes? I was staring at that spinning mouse forever.
The fix was to switch to a terminal (ctrl-alt-f1), edit **/etc/apt/preferences** and add pins to favor Jaunty packages, then install Jaunty's glib2. If you run into any trouble by using Jaunty packages in Intrepid, try this first.

By the way, my base system beforehand:
Ubuntu Intrepid Ibex (8.10) AMD x86-64 with Ubuntu Studio.

Also, bad news for people who use the RTP-send feature of pulseaudio: It seems it's completely broken in Jaunty and if you upgrade to 0.9.14 it will be completely broken for you. On the plus side, you can turn RTP-send off and get a load off your system at the same time, but if you do need it then you're stuck with 32bit pulseaudio or upgrading to Karmic Koala.

---

### Post by Yellow Pasque on 2009-10-08
> Unfortunately a full upgrade is not an option for me, unless I buy a new graphics card. I'm among the angry, unsupported, unappreciated ATI users with a card slightly over a year old.
..or you could just upgrade to Jaunty, downgrade your xserver, and use Catalyst 9-3 if you really need the proprietary ATI driver.

---

### Post by quequotion on 2009-10-09
does that work?!

what else would have to be downgraded in that situation? I'm sure the driver is not the only thing with dependency on the new xserver.

UPDATE

answered my own questions... although I'm not sure what to say about the first one...

---

### Post by quequotion on 2009-10-19
i wrote the longest most helpful explanation of how to upgrade to jaunty, save your dmraid, and downgrade xserver without preventing updates to the xserver packages or the system.... and then swiftweasel crashed and took the clipboard with it...

i'm including two files that make the downgrade magic work, but i don't think i'll be able to type out that guide again today...

just to say, i did find a workaround for jaunty's raid woes and also be wary of the available guides on how to downgrade xserver.. they all prevent (permanently) either the intrepid xserver packages or the entire jaunty system from receiving updates. package pinning is the way to go, the debian way.

i'll try to explain tomorrow.

---

### Post by quequotion on 2009-10-19
Intrepid->Jaunty xserver=intrepid (+dmraid workaround)
Up-downgrade guide, v2.1

Let the games begin:
1. In a terminal or alt+f2 dialog type:
```
update-manager -d
``` (does that stand for update-manager mode doom?)
2. Check for new releases in the dialog that comes up.
3. Confirm to upgrade to Jaunty

If, like my foolish self, you have your entire system installed on a fakeRAID:
1. Try this in a terminal before rebooting: ```
update-initramfs -c -k all
``` I never had a chance to test this but it just might work. It should create new initramfs, which contain the dmraid binary, for all kernels.
2. Reboot.

If your system fails to boot due to failing to mount the root device:
1. Boot from a livecd/dvd.
2. Install dmraid
3. Mount, bind, and chroot into your system. (Google this part. There are plenty of good guides out there.)
4. In a terminal, try again: ```
update-initramfs -c -k all
```
5. Reboot
NOTE: *There is a patch out there for Jaunty's dmraid which requires the installation of about a dozen dependencies and compiling dmraid by yourself. I thought it might fix this problem but it didn't work for me and it wasn't at all worth the trouble. It may resolve another issue, but not mine: having a system installed onto a fakeRAID:0*.

To downgrade xserver:
First make sure all your jaunty packages are properly installed, no dependency problems, no held-back upgrades, etc. and give the free drivers a try if you're masochistic.

1. Duplicate all entries in /etc/apt/sources.list
2. Make one set for intrepid, leave the jaunty set alone.
3. In /etc/apt/preferences, pin all downgrading packages to release 8.10 (see examples in attachment above--note that it is intentionally an incomplete list as I used an alternate method) with Pin-Priority 1001.
4. ```
apt-get update && apt-get upgrade
```
!!If you see "x depends on y but it is not going to be installed" or the like, add y to /etc/apt/preferences like the rest and try again.

Alternatively, to downgrade xserver and avoid dependency hell (somewhat):
1. Duplicate all entries in /etc/apt/sources.list
2. **Temporarily** comment out the jaunty repos.
3. Append the above preferences file to your own and increase the priorities to 1001.
4. ```
 apt-get autoremove [all the packages listed in my preferences file] 
```
5. ```
 apt-get update && apt get upgrade 
```
!!if you see "x depends on y but it is not going to be installed" or the like, add y to /etc/apt/preferences like the rest and try again.
6. **Uncomment the jaunty repos.**
7. ```
apt-get update && apt-get upgrade
```
!!If apt suggests any upgrades say NO and add those packages to /etc/apt/preferences (like the rest) and try again.
!!If apt says packages are "held back" it's ok. Most likely these cannot and should not be upgraded because they are Intrepid packages with Intrepid dependencies that are pinned in /etc/apt/preferences. *
8. Install fglrx from the intrepid repo; NOT the ATI site. ATI's version is the latest, but it requires a further xserver AND kernel downgrade.
9. Reboot/Restart xserver.

***Why?***

By pinning packages to release 8.10, if any of those packages ever receive updates or patches in intrepid (or intrepid-updates, intrepid-backports, intrepid-security, intrepid-proposed, etc), the updates can be automatically installed by apt or synaptic, while the rest of the system will get updates for Jaunty as appropriate.

I have seen other guides suggesting to use the "lock version" feature of synaptic, but that would block automatic updates of Intrepid's packages should some patch come along and support for Intrepid doesn't end until 2011 so I expect some patching between now and then. Other guides are missing some means of Jaunty's repos regaining supremacy, so the *whole system* fails to update. At least one chat log on the matter suggested it would be dangerous to have both jaunty and intrepid repos in sources.list--it is not. By default, apt will never downgrade a package, which is why cutting off the Jaunty updates appears to work in some of these guides. Even if only Intrepid repos were available, Jaunty's packages won't be superseded unless a package has a pin-priority > 1000.

Further notes:
After the jaunty upgrade a number of configuration files were backed up. You can find your old xorg.conf in something like /etc/X11/xorg.conf.dist-upgrade########.
I lost some things during the upgrade (some are still missing... like compiz animationsaddons) and found a few haven't made it to Jaunty's repos, like zsnes, which I can now install from apt (intrepid's amd64 version).
Aside from the procedure itself being quite drastic, I haven't had much trouble so far. Of course, using two whole sets of repos makes apt-get update take a bit longer. It is unlikely that there is any need to duplicate third-party repositories, though I have "just in case".
* for a variety of reasons this can happen to just about any package. If you have seen this warning before starting the downgrade process, try to clear those packages up first.

---

