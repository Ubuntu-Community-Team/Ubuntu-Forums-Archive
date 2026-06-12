---
title: "I tried opensuse 11, i dont like it."
date: 2008-07-05
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Polygon on 2008-07-05
So, on my new Compaq Presario f700 laptop, Ubuntu works, but has a few quirks, like sometimes after entering sleep and resume, it freezes for some unknown reason, and a few other things. Point is, i wnated to see if any other distros worked any better

Open suse 11 just came out a while ago, so i thought, eh why not?

I downloaded the gnome live cd as i dont like kde, and i booted it up. The boot loader looks very nice.

Anyway, i installed the OS, using i guess a new version of their installer that is less complicated then 10.3's. It was all pretty straight forward, except for the fact that it does not let you name your computer, it was automatically named linux-lxpi or something.

Anyway...after the installation, i booted it up for the first time, and the theme looks really nice. I went to the Network manager (the new 7.0 version) and tried to connect to my network. no dice. Doesn't even see the network. After asking on the opensuse irc they said i need to install madwifi manually and directed me to a page. It had this 'one click install' button that i clicked and it downloaded this file that told it to install madwifi i guess, so i did that, and had to wait about 30 minutes for opensuse's package manager to completely update my system on my slow wireless bridge connection rather then downloading JUST madwifi like i told it to. Annoying.

Anyway, i installed it and i tried to "modprobe ath_pci", only to find that it said 'modprobe: command not found". Again asking on irc, i was told that i need to type /sbin/modprobe ath_pci  ....another annoying feature that isnt present in ubuntu. Why cant it look in /sbin/ as well as /bin/ for commands by default?

anyway, even after all that, my wireless still doesnt work. I then tried to compile the newest version of madwifi to see if it was any better, and soon i realized i need the compiling tools. I asked on irc if there was an equivalent  to the ubuntu meta package 'build-essential' that installs most everything needed for compiling..and was told that i need to install C++ development tools and Base development, both of which were kinda of complicated to find in the YAST installer thing.But i found it, and it took a long time to download and install for some reason...and then i tried to compile it again. Oops! I need to install the kernel source as well...another trip to yast and after that it finally did compile. Geez, build-essential is really a time saver...

Anyway, after compiling, i again had to /sbin/modprobe the drivers. AFter that, i waited a few seconds and tried to access my wifi network, and again it wasnt even detected. I tried iwconfig, and it says command wasnt found, even with /sbin/iwconfig. I tried dmesg and it says Madwifi: hardware didn't respond as usual". Great...no wireless. That makes my laptop quite useless.

Other things: Sleep does not work...at all. Im not sure what the problem is, but if i try sleep or suspend, all it does is just take me to the log in screen again (the one after you lock your screen). And it works in ubuntu....

Installing the nvidia drivers was a hassle as well, as im just used to clicking a button and restarting, now i had to manually add the nvidia repo, click a one click install button, and then AFTER I install it, some program called sax2 doesnt 'detect' the nvidia drivers so i have to type 'sax2 -r' to make it re detect it and then it works', but i get a slower fps then what i did on ubuntu with glxgears

I disabled touchpad taps on the touchpad settings (which is missing an icon, btw) and i guess as a result every time i start up the computer, my touchpad is disabled unless i click the button on my laptop to turn off the touch pad, and then turn it back on and wait like 10 seconds, and then it magically starts working again.

The weird menu thing opensuse uses is annoying, it only holds 2 applications and if i want to use an app that isnt on the 'recently used' app list, i have to click more applications, and scroll through a list.... I know there is the 'traditional gnome menu' thing, but the icon is ugly and i couldent figure out how to make it show the "Applications / places / system" thing rather then just the icon.

However, the fact that my wireless doesn't work even after i installed the drivers from yast, and even attempted to compile and install them makes this distro for my laptop worthless. Even though it works perfectly with ubuntu. Also,  the lack of easy methods to install restricted drivers which i know a lot of people MUST use, and the hassle it is to use certain commands that are located in /sbin/ just makes this distro highly unappealing to me...even though the theme it uses looks good. Oh well

---

### Post by RebounD11 on 2008-07-06
You're making the same mistake as people coming from Windows to Linux: you expect openSUSE to be just like Ubuntu.

Did you try their wiki, or the HCL List (which is the best thing that any distro should have)? That's the place to search before going to their IRC channel.

Here's the HCL for Compaq laptops:

[http://en.opensuse.org/HCL/Laptops/Compaq](http://en.opensuse.org/HCL/Laptops/Compaq) with a hint of what to do with your wireless.

As I know your wireless card is a Broadcom BCM94311MCG wlan mini-PC rev 2, right? Well that doesn't work in Ubuntu out-of-the-box either. I know that Novell doesn't have such a vast forum as Ubuntu, that's why you can "steal" knowledge from UF.

That being said, you also could try adapting what is says here for you to do in Ubuntu, to the commands in openSUSE 11:

[http://ubuntuforums.org/showthread.php?t=780212](http://ubuntuforums.org/showthread.php?t=780212) (go to post #5)

Good luck if you think of trying openSUSE again, the choice is yours. What I want to say is don't ditch a distro just because it's different than what you know.

---

### Post by Polygon on 2008-07-06
My wireless card is a Atheros AR242x on this laptop, (i didnt give the exact laptop model number, sorry, it appears that there are multiple F700's out there, and mine is a F767NR)

And it IS supported by ubuntu out of the box, although i have to compile a newer version of madwifi in order for it to work on ubuntu, but by the time the intrped comes out, im sure it will be included (with the default drivers, it works, but suspend causes a kernel panic, the newer version fixes it)

in all honesty, if my wifi card worked, i would of tried it longer, but you must realize i spent nearly a day trying to get it to work, and at the end of the day when all i could show for my work was dmesg telling me "hardware not responding as expected", i just had to go back to ubuntu.  A laptop without wireless is pretty useless, especially since all i HAVE is wireless, no ethernet connection I bought this laptop knowing that it had atheros wireless and it WOULD be supported by linux, and and i dont want to resort to using ndiswrapper when its supposed to be working natively.

and again suspend didnt work, which is important for a laptop but i could of worked through that by just shutting the thing off

I know it was different, , and if my wireless worked i would of given it a better try, but i NEED this wireless, and it doesnt work, and i cant use it (opensuse)....i didnt stop using it because it was different.

anyway ill edit that wiki, put the info down for this specific model of laptop and wait for a later version.

---

### Post by ibutho on 2008-07-06
From your post, it seems like some of your problems are due to the fact that you probably have only used Ubuntu based distros which work differently to most Linux distros and Unix operating systems. Had you taken some time out to learn about other distros (even whilst using Ubuntu as your main distro), you wouldn't have had so many problems.

The last time I installed from the openSUSE live disc, I had the option to change the networking settings, so I gave my computer a hostname I desired. I'm not sure how you missed that option, because I am positive its there.

The */sbin directories are typically only in roots path because they contain commands that are used for system administation and commands that are supposed to be run as root only, so normal users shouldn't have access to them. This is the way most distros and other Unix OSes are setup except Ubuntu and derivatives. In Ubuntu, things are different because of the use of sudo, so the */sbin dirs are in everyones path. In your case, you needed to switch to root first using the command "su -" and then run "modprobe ath_pci". Better still, after installing the madwifi driver, you should have just used YAST to configure your network card and network settings. One a side note, some people have had problems with Atheros cards, so take a look [here]("http://www.susegeek.com/wireless/unable-to-set-atheros-wireless-card-with-madwifi-in-opensuse-110/") for a possible solution if you ever try openSUSE again.

As for manually adding repos, there was no need for this. You can easily add repos by going to YAST -> Software -> Community Repositories and select the repositories you want to enable. To install the driver, so to YAST -> software -> Software Management and search for the driver. Sax2 would not recognise the new driver because when you call it using just sax2, it tries to configure your system using the old configuration. If you have installed any new drivers, then "sax2 -r" is the correct option for reconfiguring the graphics settings from scratch.

As for the GNOME, menu, you can remove the openSUSE SLAB menu and add the menubar (the one with Applications, Places and System) or add the traditional menu. Can't help with the suspend or sleep issues.

For me openSUSE just works (on my laptop and desktop), but then again I tend to choose hardware that is typically supported out of the box in most Linux distros.

---

### Post by some-guy on 2008-07-06
> **Polygon said:**
> Anyway, i installed the OS, using i guess a new version of their installer that is less complicated then 10.3's. It was all pretty straight forward, except for the fact that it does not let you name your computer, it was automatically named linux-lxpi or something.
I didn't like that either it let you do it in 10.3, but not in 11

> **Polygon said:**
> Anyway...after the installation, i booted it up for the first time, and the theme looks really nice. I went to the Network manager (the new 7.0 version) and tried to connect to my network. no dice. Doesn't even see the network. After asking on the opensuse irc they said i need to install madwifi manually and directed me to a page. It had this 'one click install' button that i clicked and it downloaded this file that told it to install madwifi i guess, so i did that, and had to wait about 30 minutes for opensuse's package manager to completely update my system on my slow wireless bridge connection rather then downloading JUST madwifi like i told it to. Annoying.
The packages are most likely made for the latest opensuse kernel, which requires you update the kernel

> **Polygon said:**
> Anyway, i installed it and i tried to "modprobe ath_pci", only to find that it said 'modprobe: command not found". Again asking on irc, i was told that i need to type /sbin/modprobe ath_pci  ....another annoying feature that isnt present in ubuntu. Why cant it look in /sbin/ as well as /bin/ for commands by default?
the /sbin's are for root-only, users aren't supposed to use them, if you run 'su', you will become root and that will add the /sbin's to your PATH

> **Polygon said:**
> anyway, even after all that, my wireless still doesnt work. I then tried to compile the newest version of madwifi to see if it was any better, and soon i realized i need the compiling tools. I asked on irc if there was an equivalent  to the ubuntu meta package 'build-essential' that installs most everything needed for compiling..and was told that i need to install C++ development tools and Base development, both of which were kinda of complicated to find in the YAST installer thing.But i found it, and it took a long time to download and install for some reason...and then i tried to compile it again. Oops! I need to install the kernel source as well...another trip to yast and after that it finally did compile. Geez, build-essential is really a time saver...
running 'zypper si -d madwifi madwifi-kmp-`uname -r | cut -d"-" -f3`' will install all the build deps for madwifi

> **Polygon said:**
> Anyway, after compiling, i again had to /sbin/modprobe the drivers. AFter that, i waited a few seconds and tried to access my wifi network, and again it wasnt even detected. I tried iwconfig, and it says command wasnt found, even with /sbin/iwconfig. I tried dmesg and it says Madwifi: hardware didn't respond as usual". Great...no wireless. That makes my laptop quite useless.
you need to use /usr/sbin/iwconfig, man, why don't you jut su? that's suse's standard way of handling root, not sudo.

> **Polygon said:**
> Other things: Sleep does not work...at all. Im not sure what the problem is, but if i try sleep or suspend, all it does is just take me to the log in screen again (the one after you lock your screen). And it works in ubuntu....
might be because the kernel is 2.6.25, not 2.6.24, not sure about this one though

> **Polygon said:**
> Installing the nvidia drivers was a hassle as well, as im just used to clicking a button and restarting, now i had to manually add the nvidia repo, click a one click install button, and then AFTER I install it, some program called sax2 doesnt 'detect' the nvidia drivers so i have to type 'sax2 -r' to make it re detect it and then it works', but i get a slower fps then what i did on ubuntu with glxgears
HARDER??? you don't need to add any repo the one-click does that *for* you, just click the right one from here: [http://opensuse-community.org/1-click-collection#Drivers](http://opensuse-community.org/1-click-collection#Drivers)

> **Polygon said:**
> The weird menu thing opensuse uses is annoying, it only holds 2 applications and if i want to use an app that isnt on the 'recently used' app list, i have to click more applications, and scroll through a list.... I know there is the 'traditional gnome menu' thing, but the icon is ugly and i couldent figure out how to make it show the "Applications / places / system" thing rather then just the icon.
use the 'custom menu bar' applet

> **Polygon said:**
> However, the fact that my wireless doesn't work even after i installed the drivers from yast, and even attempted to compile and install them makes this distro for my laptop worthless. Even though it works perfectly with ubuntu. Also,  the lack of easy methods to install restricted drivers which i know a lot of people MUST use, and the hassle it is to use certain commands that are located in /sbin/ just makes this distro highly unappealing to me...even though the theme it uses looks good. Oh well
this is most likely due to using the 2.6.25 kernel, which is brand-new and not yet well supported by proprietary drivers, as well as (madwifi?)

---

### Post by Polygon on 2008-07-06
yes i realize im no linux expert, but i guess i just hate memorizing unnecessary stuff, like the path of every single linux executable.... someone on the opensuse irc told me how to fix it so its like ubuntu, but i was to preoccupied with my wifi not workig =P

and i didnt try running as root (program name) because im under the mentality that root should only be used to administrate stuff, why do i need to use root to use iwconfig (just to see if it detects a wireless network)

and....suspend didnt work even when my system was pure, no nvidia drivers, no wifi drivers. So, i dont know what they did with that version of the kernel but they must of messed something up, or its a suse problem

also, the thing about adding the nvidia repo, i got that info from here: [http://en.opensuse.org/NVIDIA#Installation](http://en.opensuse.org/NVIDIA#Installation) 

> NOTE: It's absolutely critical that you have access to the online YAST software repositories. You must add these manually (or select them during your SUSE installation). Failure to have access to the online repositories (both SUSE OSS and SUSE Update) will cause dependency issues when attempting to install NVIDIA driver via the 1-click install. [1] 

---

### Post by some-guy on 2008-07-06
read that again, it says to have the OSS and Update repos there, which are there by default

---

### Post by ibutho on 2008-07-06
> **Polygon said:**
> yes i realize im no linux expert, but i guess i just hate memorizing unnecessary stuff, like the path of every single linux executable.... someone on the opensuse irc told me how to fix it so its like ubuntu, but i was to preoccupied with my wifi not workig =P

and i didnt try running as root (program name) because im under the mentality that root should only be used to administrate stuff, why do i need to use root to use iwconfig (just to see if it detects a wireless network)

and....suspend didnt work even when my system was pure, no nvidia drivers, no wifi drivers. So, i dont know what they did with that version of the kernel but they must of messed something up, or its a suse problem

also, the thing about adding the nvidia repo, i got that info from here: [http://en.opensuse.org/NVIDIA#Installation](http://en.opensuse.org/NVIDIA#Installation)

The problem here as been mentioned before is that you are approaching other Linux distros with an Ubuntu mentality. There is no need to memorise paths of all the executables, just switch to root and the appropriate sysadmin commands will be in your path. This is standard on most Linux and Unix systems except Ubuntu and its derivatives. For those commands that you want to be able to access as a normal user without switching to root e.g. iwconfig, you can use sudo. For example on my laptop running openSUSE, I used sudo to give myself permissions to stop and start the wireless connection without being root.

What you need to do is approach other distros with an open mind and not expect everything to be like Ubuntu because Ubuntu deviates a lot from other Linux distros (even Debian from which its based).

---

### Post by Polygon on 2008-07-08
which is what  happened, my wireless didnt work in opensuse, unlike in ubuntu. :lolflag:

eh maybe ill try it on my other computer which has an older version of an atheros wifi card which has a better chance of working.

---

### Post by AE6QE on 2008-07-09
I have a Compaq C727US, and tried Opensuse 11 over the weekend.  While I loved the fact that the 2.6.25 kernel allowed me to use my Broadcom 4311 without ndiswrapper and still maintain 54 MBps, I was dismayed by how much slower the OS ran on my machine.  

The clincher that made me find my Linux Mint CD again, was that for some reason my touchpad worked very erratically.  This machine has an Alps touchpad, and Opensuse would frequently hang my curser on various areas and revert to a scrolling function as I tried to move the cursor.  Maybe I could have figured it out given enough time and the right Google searches, but alas I was more concerned at that point in performance vice experimentation.

I think I am sold on Ubuntu-based distros, and can't wait until 8.10.

Rickey

---

### Post by Vorian Grey on 2008-07-10
I tried 11 recently and I hated it. It seemed to take 3 steps to do even simple things and I loath Yast. To see a control center done right just look at Mandriva. To bad Mandriva runs so slow. 

Ubuntu makes things so easy that I sometimes forget how difficult Linux can be.

---

### Post by L815 on 2008-07-22
You can't expect OpenSUSE to be like Ubuntu. Suse is unique, and their way of doing things is a bit different.

Just like Ubuntu is a bit different than Debian, even though Ubuntu is based of Debian.

---

### Post by Darkchef on 2008-07-27
> **Polygon said:**
> 
Anyway, i installed it and i tried to "modprobe ath_pci", only to find that it said 'modprobe: command not found". Again asking on irc, i was told that i need to type /sbin/modprobe ath_pci  ....another annoying feature that isnt present in ubuntu. Why cant it look in /sbin/ as well as /bin/ for commands by default?


Yeah your right about that, and the wiki says to use "modprobe ath_pci" when its quite obvious that it doesn't work. It was actually this post that helped me to eventually get the wireless connection working. 

First impressions are that its using a considerably less amount of cpu on my laptop than ubuntu hardy heron does, and the interface does look nice, however they need to fix that wiki error and also fix their yast package system. i took me a while to realize that i needed to install make as a separate package ?? build-essentials really is a time saver and a much easier way of getting everything you need to compile.

---

### Post by RedDwarf on 2008-07-28
> **Darkchef said:**
> however they need to fix that wiki error
"They"??? Since it's a wiki, just edit it yourself!!!
> **Darkchef said:**
> and also fix their yast package system. i took me a while to realize that i needed to install make as a separate package ?? build-essentials really is a time saver and a much easier way of getting everything you need to compile.
openSUSE has "Base Development", "Gnome Development", "KDE Development", "Cell Development", ".NET Development", "C/C++ Development"....... patterns. A very modular time saver that gives you whatever you need.

---

### Post by Growbag on 2008-07-28
That *problem* is actually a "security feature" believe it or not!

Some mouldy old-school thinking that dictates: "users shouldn't use any progs in /sbin or /usr/sbin (usr in this case obviously doesn't mean **you sonny Jim**!) because that is only for root".

So they simply remove the */sbin* and other useful paths from your .bashrc file.

It is extremely annoying, and in my opinion also bloody stupid because the commands won't even run unless you are root or have the su password in the first place!

I think the confusion comes in because in Debian based distros one uses sudo, and in RPM based distros one uses an actual root account (su).

So if you simply issue the command:

```
sudo su
```

You become root and inherit root's path, so the commands work again.

This also works under Ubuntu, and you don't have to mess around with the root account either.  Simply type **sudo su** and off you go, you are now root without having to enable the root account :).

You can also edit your .bashrc file and add this to the end:

```
export PATH=$PATH:/usr/sbin:/sbin:
```

Then all is rosy again.

I also know a nice trick that enables no root password needed for your normal user account, but the "Security Police" paranoids here would hang me out to dry by the smalls!  :D.

---

