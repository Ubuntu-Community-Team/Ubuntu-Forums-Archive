---
title: "Positive Experience"
date: 2007-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Macinux on 2007-10-20
I just had to post and say I have tried Linux distro's since Slackware 3.0, I've tried most all of them at one point or another. Recently I was trying to install any version of Linux on a MacBook Core 2 Duo, I tried Debian but never could get anything configured properly, also never could get kernel to compile. I was then told by a friend to try LinuxMint, it was okay, but still couldn't get certain things to act right with this MacBook, plus that community seemed a little uninterested in trying to help with the issues I was having. The whole time another friend kept telling me "install Ubuntu", I don't know why I didn't try it sooner!

After all else failed I downloaded 7.04 amd64 version, it installed beautifully! Crossed my fingers and installed 915resolution and madwifi; Perfect! After 3 days of banging my head against the wall I was finally online wireless with 1280x800 res, and you know what I never had one issue! Every HowTo I followed posted by community members worked perfectly.

I didn't want to reinstall 7.10 Gutsy but I knew since I was so new with installing Ubuntu and 7.10 just came out I'd be stupid not to have at least the latest version. This morning I woke up and decided to make a day of trying to upgrade to 7.10. I ran the updates yesterday, brought up the updater again done a check, there it was a button saying upgrade t 7.10. I bit the bullet and pressed the button, it took about 2 hours to download, install, clean, and reboot, but you know what? It went off without a hitch! I did need to redo my madwifi wireless setup, I had to make Xchat and Pidgin again, but that was it VLC Player still worked with no problems etc.

I just want to extend a very big thank you to Ubuntu and its community for having such a great distro, I hd been disappointed and let down so many times by other distros and the community that followed. I would get discouraged and quit dealing with Linux all together. Being new to Linux is very hard, I don't have anyone to depend on in real life because no one I know uses Linux. I have to read a lot and figure it all out myself, this community is tight there's a lot of good information out there, a lot of Howto's on just about everything you need to do to get your install working properly.

After I finish this term in online college and being required to use MS Excel 2007 to complete my course I am totally converting to Ubuntu on my desktop PC. I am currently reading up on Virtual Machine and WINE, so maybe I can convert sooner and not even deal with MS Windows or MAC OS X every again.

Again thank you, everyone, all your knowledge and posts make Ubuntu something great. I plan on telling everyone I meet who run anything other than Ubuntu just how great it is.

Lotta love and respect to you all!

---

### Post by Denn1s on 2007-10-20
its great you were successfully with Ubuntu, remember there are millions of linux howtos and besides any help you need you  have this forums which are very active were very smart people will help you,  you just post it

---

### Post by rickwood on 2007-10-20
> **Macinux said:**
> I did need to redo my madwifi wireless setup

I've got a Macbook core 2 duo and I'm fighting with madwifi under amd64 Gutsy (i.e., it sees networks, but can't connect).  What process did you use to set it up on yours?  The one in the macbook wiki?  And what version of madwifi are you using?

---

### Post by Macinux on 2007-10-20
I went to [http://snapshots.madwifi.org/](http://snapshots.madwifi.org/) and got the one in the main directory madwifi-dfs-current.tar.gz after you make install I brought up a terminal window. This is what I typed

sudo ifconfig eth0 down
sudo ifconfig ath0 up
sudo wlanconfig ath0 list scan
sudo iwlist scan
sudo iwconfig ath0 key <wep>
sudo iwpriv ath0 authmode 2
sudo dhclient ath0
ping <any random site>

Only thing I can't figure out is, I have to type that every time I power down and bring Ubuntu back up to get WiFi working

---

### Post by Macinux on 2007-10-21
I did figure it out this evening on why I was entering that every time, and fixed it. I set ath0 to roam, now it picks up any WiFi in the area, and shows the signal strength meter in the upper right. I can click that and choose the network, and if there's a WEP to enter I get the prompt to enter it.

Super sweet now, I'm all set.

I even installed VMware server this evening and loaded my XP Pro CD on it. Also, since I'm in college at the moment I had a 90 day trial of MS Office 2007 I have never opened for my spreadhsheets class I'm taking. I got it to install under the virtual machine, it took a little longer than normal to install. I just let it run, and chatted in Pidgin, and Xchat for a bit. Once it was done it was solid, can load Excel, Word, Powerpoint 2007. That's all I needed so thats  all I selected to install, it all works great.

I've been so impressed with Ubuntu GG so far, I just can't get over how solid everything has been. I have everything I need to be mobile, I have everything I need for school, and I've had no real issues that I had to deal with, just the minor editing and doing some light work in the terminal.

This is the first time I've ran Linux since a few years back and I had just started learning it a little then. Words just can't describe, I tell ya... awesome distro.

---

### Post by rickwood on 2007-10-21
Macinux,

Thanks for the instructions.  I tried that, but it still didn't work.  I finally installed i386 version of ubuntu.  Same results with madwifi -- I could see the networks but couldn't connect.  So I gave up and installed ndiswrapper and networking is working fine now (although I'm obviously stuck with i386 version of ubuntu rather than amd64).

---

### Post by Eberbachl on 2007-10-22
> **Macinux said:**
> I just had to post and say I have tried Linux distro's since Slackware 3.0, I've tried most all of them at one point or another. Recently I was trying to install any version of Linux on a MacBook Core 2 Duo, I tried Debian but never could get anything configured properly, also never could get kernel to compile. I was then told by a friend to try LinuxMint, it was okay, but still couldn't get certain things to act right with this MacBook, plus that community seemed a little uninterested in trying to help with the issues I was having. The whole time another friend kept telling me "install Ubuntu", I don't know why I didn't try it sooner!

After all else failed I downloaded 7.04 amd64 version, it installed beautifully! Crossed my fingers and installed 915resolution and madwifi; Perfect! After 3 days of banging my head against the wall I was finally online wireless with 1280x800 res, and you know what I never had one issue! Every HowTo I followed posted by community members worked perfectly.

I didn't want to reinstall 7.10 Gutsy but I knew since I was so new with installing Ubuntu and 7.10 just came out I'd be stupid not to have at least the latest version. This morning I woke up and decided to make a day of trying to upgrade to 7.10. I ran the updates yesterday, brought up the updater again done a check, there it was a button saying upgrade t 7.10. I bit the bullet and pressed the button, it took about 2 hours to download, install, clean, and reboot, but you know what? It went off without a hitch! I did need to redo my madwifi wireless setup, I had to make Xchat and Pidgin again, but that was it VLC Player still worked with no problems etc.

I just want to extend a very big thank you to Ubuntu and its community for having such a great distro, I hd been disappointed and let down so many times by other distros and the community that followed. I would get discouraged and quit dealing with Linux all together. Being new to Linux is very hard, I don't have anyone to depend on in real life because no one I know uses Linux. I have to read a lot and figure it all out myself, this community is tight there's a lot of good information out there, a lot of Howto's on just about everything you need to do to get your install working properly.

After I finish this term in online college and being required to use MS Excel 2007 to complete my course I am totally converting to Ubuntu on my desktop PC. I am currently reading up on Virtual Machine and WINE, so maybe I can convert sooner and not even deal with MS Windows or MAC OS X every again.

Again thank you, everyone, all your knowledge and posts make Ubuntu something great. I plan on telling everyone I meet who run anything other than Ubuntu just how great it is.

Lotta love and respect to you all!

What a great post ;)

As a Ubuntu noob I'd like to echo those comments. I've tried a number of Linux distros over the years, and this one has been fantastic. Whilst the install didn't work flawlessly (ATI Driver problem on PPC Mac mini), the great community here and clear, concise howto's has meant that each fix has been easily implemented, and now I'm enjoying Gutsy :D

Thanks to the Ubuntu community for the great distro and great support.

:D

---

### Post by nss0000 on 2007-10-22
BigD:

  **REM** '...millions of linux howtos...' equals noise. One automagic UBUNTU install equals wisdom.

---

