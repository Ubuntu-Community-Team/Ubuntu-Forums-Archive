---
title: "Guide: Opera 9.20 + Flash working in Feisty!"
date: 2007-04-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by jouka on 2007-04-18
Hi, I like Opera a bit more than firefox (better mouse gestures IMO and takes a bit less memory when being open for a while with a lots of tabs opened) and thought that I could try to write clear instructions how I struggled to get Opera + flash (yeah to get those youtubes rolling) working in 64bit Feisty. It might be that some of these steps are not required but hey,  so is not a marriage but still ppl do it. :D Wonder why..  Feisty is out! Enough of bs, so here we go:

1. Download Opera 9.20 static from [http://www.opera.com/download/get.pl?distro=other%2Fstatic+deb&id=28912%2C28911&location=15&sub=++++&x=66&y=23](http://www.opera.com/download/get.pl?distro=other%2Fstatic+deb&id=28912%2C28911&location=15&sub=++++&x=66&y=23)
and do

sudo dpkg --force-architecture -i opera-static_9.20-20070409.1-qt_en_i386.deb 

2. Then download [http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fl%2Flesstif1-1%2Flesstif2_0.93.94-11.4ubuntu3_i386.deb&md5sum=80e79cdb32aba826fd35cf4d116d54a7&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fl%2Flesstif1-1%2Flesstif2_0.93.94-11.4ubuntu3_i386.deb&md5sum=80e79cdb32aba826fd35cf4d116d54a7&arch=i386&type=main)
and do 

sudo dpkg -i --force-architecture lesstif2_0.93.94-11.4ubuntu3_i386.deb

3. Then Download [http://www.opera.com/download/linux/motif/openmotif_2.1.30-5_i386.deb](http://www.opera.com/download/linux/motif/openmotif_2.1.30-5_i386.deb)
and do

sudo dpkg -i --force-all openmotif_2.1.30-5_i386.deb

4. Get Flash 9 from [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
extract it somewhere.. like aint no place like $home so there u go. Then go there and do

cd install_flash_player_9_linux/
sudo cp libflashplayer.so /usr/lib/opera/plugins
sudo cp flashplayer.xpt /usr/lib/opera/plugins

5. Some of these following packages are, and some are not required but what the hell, install them all. Why? Why a dog licks his balls? Yes my friend, because he can. So do

sudo aptitude install ia32-libs ia32-libs-sdl ia32-sun-java5-bin ia32-libs-gtk flashplugin-nonfree sun-java6-plugin sun-java6-jre

6. Get qt3 libs from: [http://mirrors.kernel.org/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8really3.3.7-0ubuntu5_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8really3.3.7-0ubuntu5_i386.deb) and do

sudo dpkg -i --force-architecture libqt3-mt_3.3.8really3.3.7-0ubuntu5_i386.deb

Now launch your awesome browser and go check out some por... news and stuff!

---

### Post by zsouthboy on 2007-04-19
thankyouthankyouthankyouthankyouthankyouthankyouthankyouthankyouthankyouthankyouthankyouthankyouthankyouthankyouthankyouthankyou


:D

I couldn't do without my Opera lovin!

x64 is such a bigger pain to deal with. ugh.

---

### Post by ronocdh on 2007-04-19
Bookmarking this post; I'll have to take a trip home to upgrade mother's box (could I have phrased that better? probably), and this'll come in handy!

=)

---

### Post by tibbar_eht on 2007-04-19
I loaded the programs like you said I had to leave the system for a while when it was downloading the files from the last step when I came back it had a user agreement showing in the terminal but I couldn't do much with it.  Opera is loaded and some of the web pages work better with Java working but the flash doesn't work.  wondering if I should retry everything.  Help would be appreciated.

Cheers

---

### Post by jouka on 2007-04-19
Could you be a bit more specific about the installation you did? Did you extract the tar.gz and copy those two flash files to location I told to put them in to? Is it a fresh Feisty installation or an upgrade? What does 'opera -debugplugin' say?

---

### Post by tibbar_eht on 2007-04-19
It is a fresh install of the beta a few days ago.  I down loaded everything exatly how you listed it.  Infact I even cut an pasted the commands (lazy on my part I know :)  ) I am not sure where to go to check opera -debugplugin.  Sorry I am new to Linux  I have some old Unix background but it was on a live server so I could not mess around and really learn things.  Part of the reason why I am here is to learn.  Thanks for the help.

Cheers

---

### Post by ronacc on 2007-04-19
ThankYou

---

### Post by tibbar_eht on 2007-04-20
I seemed to have worked through my issues.  I just hope I can start getting this Linux stuff.

Cheers

---

### Post by jan on 2007-04-20
Does this guide work for ordinarz 32 bit ubuntu too?

---

### Post by tibbar_eht on 2007-04-20
Man this is frustrating....I had to reload from scratch because I messed up loading video drivers.  Now I can't get the flash to load properly again.  ](*,) ](*,)   Why can't these people come out with stuff for 64 bit.

---

### Post by Cappy on 2007-04-20
Perfect! A+ for guide and links! I had used Opera before but Flash caused major audio and video lag. I had let automatix do it for me. Thanks for this guide! Opera works better with flash than firefox ever did (which crashed on me 5 times a day). 

I searched and found this to play WMVs in Opera but I'm not sure how to use it. I'll post back when I get to figuring it out.
[http://aur.archlinux.org/packages.php?do_Details=1&ID=8159](http://aur.archlinux.org/packages.php?do_Details=1&ID=8159)

---

### Post by tibbar_eht on 2007-04-20
Ok the village idiot got it working again.  I just hope I can get the proper drivers working for my Vidcard without having to reload.  I have to say your walkthough is very good.  I just need to get more familiar with my new system.

Cheers

---

### Post by Matteran on 2007-04-21
so I did everything you said, and flash works, but the sound doesn't work. Any ideas?

---

### Post by Cappy on 2007-04-21
Try running opera in the console and seeing if you get error messages. I had that problem and this fixed it (but your problem might be completely different!) :

[http://ubuntuforums.org/showthread.php?t=409056](http://ubuntuforums.org/showthread.php?t=409056)

Also ..
try closing all browsers/open programs and then using the command
```

killall esd

```
and then restarting opera.

---

### Post by jouka on 2007-04-21
Thanks for the response everyone!

> **jan said:**
> Does this guide work for ordinarz 32 bit ubuntu too?

I believe it might work, haven't tested it though. Of course you dont have to put --force-architecture when installing. Somebody might give this a try in 32-bit enviroment? I haven't installed vmware yet so can't test it now.

What comes to sound problem somebody was having, does your sound work when playing from two different programs at the same time? I believe this is a alsa/output/mixer issue and should be fixed with proper configurations to allow multiple sound sources.

---

### Post by ronacc on 2007-04-21
there may be a file that is needed that is not included in your guide , I used your guide on a box that  had been running feisty from herd2 and already had a semi functional opera9.10 installed  and it worked perfectly . on a different box with an absoultely fresh install of feisty (release) I followed all of the steps and opera would not start, from terminal it said  "/usr/lib/opera/opera*****/opera no such file" although the file was there and intact, changing permissions did not help. after installing some other things with automatix opera would start normaly , I assume that the prgs I installed with automatix "drug in" a file that opera needed that is not included with a fresh install of ubuntu (64bit). I installed too many things at once with automatix to say which one supplied the needed file .
  The "semi functional" opera I mentioned above had done the same thing until I installed superkaramba , then it started working atleast well enough to use.

---

### Post by SammyBoy247 on 2007-04-21
Nice walkthrough - all worked well - Opera is the best - thanks

---

### Post by veeravalli on 2007-04-21
Thank you! Perfect!

---

### Post by xflatlinex on 2007-04-21
WOW! It gets no easier than this my friends, thanks for the direct links and the awsome little guide, now if I can only get it to work with Firefox

---

### Post by jouka on 2007-04-22
> **ronacc said:**
> there may be a file that is needed that is not included in your guide , I used your guide on a box that  had been running feisty from herd2 and already had a semi functional opera9.10 installed  and it worked perfectly . on a different box with an absoultely fresh install of feisty (release) I followed all of the steps and opera would not start, from terminal it said  "/usr/lib/opera/opera*****/opera no such file" although the file was there and intact, changing permissions did not help.


I had the exact problem before I installed ia32-libs. After I installed them, all worked smoothly.

---

### Post by Case_f on 2007-04-22
> **Matteran said:**
> so I did everything you said, and flash works, but the sound doesn't work. Any ideas?

Install ia32-libs-sdl package. It's not mentioned in the guide here, but you need it if you want sound in Flash.

---

### Post by pokpig on 2007-04-22
a little reminder

for those who want to get java working, take a look at this [link]("http://www.opera.com/support/search/view/459/")

to enable java

thank you jouka for the guide

---

### Post by dheerajsp on 2007-04-23
i had to follow the last command to get flash working!!! not even opera -debugplugin worked!

thanx!

---

### Post by jouka on 2007-04-23
> **Case_f said:**
> Install ia32-libs-sdl package. It's not mentioned in the guide here, but you need it if you want sound in Flash.

Added it to guide if it's not installed as dependency, to make sure. Thanks.

---

### Post by vgrisham on 2007-04-25
> **jouka said:**
> 
5. Some of these following packages are, and some are not required but what the hell, install them all. Why? Why a dog licks his balls? Yes my friend, because he can. So do

sudo aptitude install ia32-libs ia32-libs-sdl ia32-sun-java5-bin ia32-libs-gtk flashplugin-nonfree sun-java6-plugin sun-java6-jre

Now launch your awesome browser and go check out some por... news and stuff!

:lolflag:

---

### Post by vgrisham on 2007-04-25
Okay, I followed the guide and I get this error when I try to launch Opera:

vaughn@vaughn-desktop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.20-20070409.6/opera: error while loading shared libraries: libqt-mt.so.3: wrong ELF class: ELFCLASS64

Any ideas?

Thanks,
Vaughn

---

### Post by Cappy on 2007-04-26
[http://mirrors.kernel.org/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8really3.3.7-0ubuntu5_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8really3.3.7-0ubuntu5_i386.deb)

download this and ```
sudo dpkg -i --force-architecture libqt3-mt_3.3.8really3.3.7-0ubuntu5_i386.deb
```

Just a quick explanation how I found it:
I searched in the [http://packages.ubuntu.com/](http://packages.ubuntu.com/) for feisty's "libqt3-mt". I got the 3 from ".so.3" and I tried adding it onto the end like "libqt-mt3" but that came up with nothing (oops!). The 3 goes on the "libqt".
You need the i386 library for Opera, that's why you have to download it and you can't use apt-get.

---

### Post by jouka on 2007-04-26
> **Cappy said:**
> 
You need the i386 library for Opera, that's why you have to download it and you can't use apt-get.

That's true, but I thought static Opera package already had qt in it. 

**People do not download the normal Opera version for Ubuntu. Go with the static package as I told in the first post.**

---

### Post by Cappy on 2007-04-26
Maybe it is needed for Opera to start flash

---

### Post by jouka on 2007-04-26
> **Cappy said:**
> Maybe it is needed for Opera to start flash

Okay I added it to guide to make sure everything's included. TY.

---

### Post by vgrisham on 2007-04-26
> **Cappy said:**
> [http://mirrors.kernel.org/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8really3.3.7-0ubuntu5_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8really3.3.7-0ubuntu5_i386.deb)

download this and ```
sudo dpkg -i --force-architecture libqt3-mt_3.3.8really3.3.7-0ubuntu5_i386.deb
```Just a quick explanation how I found it:
I searched in the [http://packages.ubuntu.com/](http://packages.ubuntu.com/) for feisty's "libqt3-mt". I got the 3 from ".so.3" and I tried adding it onto the end like "libqt-mt3" but that came up with nothing (oops!). The 3 goes on the "libqt".
You need the i386 library for Opera, that's why you have to download it and you can't use apt-get.

Thanks for the solution. 

I'm using kmymoney2, and libqt3-headers and libqt3-mt-dev are both dependencies. Since I keep our family's finances with kmymoney, it is probably the most important program I run.  If I follow the step above, am I taking a chance that kmymoney will have dependency problems?

Also, what do you guys mean about only using the "static" files when downloading Opera?

---

### Post by jouka on 2007-04-27
> **vgrisham said:**
> Thanks for the solution. 

I'm using kmymoney2, and libqt3-headers and libqt3-mt-dev are both dependencies. Since I keep our family's finances with kmymoney, it is probably the most important program I run.  If I follow the step above, am I taking a chance that kmymoney will have dependency problems?

Also, what do you guys mean about only using the "static" files when downloading Opera?

Not sure if it affects kmymoney2 mate, try and  find out. Opera has two different packages available, AFAIK static package includes all dependencies needed (like qt3 library) to run Opera. If somebody has more information about this or if I'm wrong, please correct. 

If you download Opera from the link I gave it's the static package.

---

### Post by vgrisham on 2007-04-27
> **jouka said:**
> Not sure if it affects kmymoney2 mate, try and  find out. Opera has two different packages available, AFAIK static package includes all dependencies needed (like qt3 library) to run Opera. If somebody has more information about this or if I'm wrong, please correct. 

If you download Opera from the link I gave it's the static package.

jouka, if I try it and kmymoney snuffs it, how would I go about undoing the changes to the qt3 library files outlined earlier in the thread?

---

### Post by vgrisham on 2007-04-27
Well of all the crazy-*** things. I just clicked the Opera icon again, and now the damn thing works. I've made no changes since installing it. Wacky. 

Flash still does not work (it does in Firefox however).

---

### Post by joepotter on 2007-04-27
If it is of any interest; this guide works for Debian Sid 64-bit also.

---

### Post by Atanvarno on 2007-04-27
> 3. Then Download [http://www.opera.com/download/linux/motif/openmotif_2.1.30-5_i386.deb](http://www.opera.com/download/linux/motif/openmotif_2.1.30-5_i386.deb)
and do

sudo dpkg -i --force-all openmotif_2.1.30-5_i386.deb
When it tries to install openmotif it says it depends on xlib6g, which I can't find anywhere.

I'm on a relatively clean install of feisty.

---

### Post by Cappy on 2007-04-27
The package I suggested has absolutely nothing in it .. lol

---

### Post by Atanvarno on 2007-04-27
> **Cappy said:**
> Install this:
[http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77.3_all.deb)

```

wget http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77.3_all.deb
sudo dpkg -i xlibs_6.8.2-77.3_all.deb

```Done. Terminal now returns:```
sudo dpkg -i --force-all openmotif_2.1.30-5_i386.deb
Selecting previously deselected package openmotif.
(Reading database ... 107542 files and directories currently installed.)
Unpacking openmotif (from openmotif_2.1.30-5_i386.deb) ...
dpkg: openmotif: dependency problems, but configuring anyway as you request:
 openmotif depends on xlib6g (>= 3.3.6-10); however:
  Package xlib6g is not installed.
Setting up openmotif (2.1.30-5) ...

Configuration file `/etc/X11/mwm/system.mwmrc-menu', does not exist on system.
Installing new config file as you request.

Configuration file `/etc/X11/app-defaults/Mwm', does not exist on system.
Installing new config file as you request.

```
So it looks like I still need xlib6g. :confused:

---

### Post by Cappy on 2007-04-27
Brief: I would just continue installing everything. It should work without it.

Long: I THINK that it doesn't matter. I think the --force-all set it up anyway because it doesn't REALLY need that obsolete package. I searched the packages for that and the files inside of packages for it but it doesn't exist in the ubuntu repositories.

---

### Post by jx3000 on 2007-04-28
Firstly, thankyou.

My question is, how or why does this work okay in Opera but many people (myself included) are having trouble with flash in firefox?

---

### Post by vgrisham on 2007-04-28
> **jx3000 said:**
> Firstly, thankyou.

My question is, how or why does this work okay in Opera but many people (myself included) are having trouble with flash in firefox?

I have the same question, conversely. Flash is working fine in Firefox for me; I'm not having any luck getting it to work with Opera.

---

### Post by hamil on 2007-04-29
Thank you for this guide!

---

### Post by popeyeray on 2007-05-02
You nothing short of a GOD sir! Automatix2 seems to be on the Fritz again due to some unscrupulousness interfering with their traffic. In any case i've commend you on your expert, and precise instructions! I needed only copy and paste you code into a console and now i'm going to launch my awesome browser and go check out some por...:lol:  news and stuff

---

### Post by quade888 on 2007-05-02
Adding information

to get your generic keys to work you have to make a symlink between /usr/lib/locale/ and /usr/lib32/

the code will be like this

sudo ln -s /usr/lib/locale/ /usr/lib32/locale


worked like crack for me

æøå

thnx for the excellent guide

---

### Post by perseas1 on 2007-05-03
Done! All ok!!!!
1ooooooooooooo thanks.
I use opera at win and i didnt want to change:))
Any idea about some nice fonts?the default do not show as at the mozilla.

---

### Post by teknosexual on 2007-05-10
To get Flash working in Opera, there is a much easier method (IMHO). Just open up Opera, go to Tools > Preferences > Advanced > Content > Plugin Options > Find New.

That should automatically find the Flash plugin you've already installed for Firefox.

To doublecheck that it installed okay in Opera, just to go Tools > Advanced > Plugins for a printout of the plugins installed for Opera. It should say something like 

Shockwave Flash:
application/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/opera/plugins/libflashplayer.so

Hope that helps some of you!

Edit: Sorry, I just noticed the topic title said Fiesty. My instructions were for Edgy, but I think they should be pretty similar in Fiesty.

---

### Post by dsiban on 2007-05-11
Thanks for this guide!  My only browser is Opera and now it works perfectly with Ubuntu!  

The Ubuntu community need to make it as easy as Windows though.   That was tough.

---

### Post by abhishek456 on 2007-05-19
when i tried to run opera browser through terminal it displays 

> exec: 264: /usr/lib/opera/9.20-20070409.1/opera: not found


I am using 64bit Ubuntu -feisty and had fallowed all the procedure explaned above

** I had installed openmotif_2.deb by forcing Dependency check as i could not find "lib6g" anywhere which was required dependency

---

### Post by il-luzhin on 2007-05-19
I concur, thank you my friend.  Thank you.

---

### Post by iam1e5 on 2007-05-19
i got an error for the 1st step :(

iam1e5@iam1e5-desktop:~$ sudo dpkg --force-architecture -i opera-static_9.20-20070409.1-qt_en_i386.deb 
Password:
dpkg: error processing opera-static_9.20-20070409.1-qt_en_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 opera-static_9.20-20070409.1-qt_en_i386.deb
iam1e5@iam1e5-desktop:~$

---

### Post by Cappy on 2007-05-19
> **abhishek456 said:**
> when i tried to run opera browser through terminal it displays 



I am using 64bit Ubuntu -feisty and had fallowed all the procedure explaned above

** I had installed openmotif_2.deb by forcing Dependency check as i could not find "lib6g" anywhere which was required dependency

OpenMotif does that, nothing to be worried about. I don't understand the error though, you did follow the whole guide and install everything on the "sudo aptitude" line?



iam1e5: you didn't change to the directory you downloading the package at. You need to do
```
cd ~/Desktop
``` if you downloaded it on your desktop

---

### Post by jouka on 2007-05-19
> **Cappy said:**
>  You need to do
```
cd ~/Desktop
``` if you downloaded it on your desktop

Yes. When people change from operating system to another, first thing they should learn is how the file system works and understand what are the restrictions in it.
You simply cant run a file from some location if you do not at least specify the location of the file. You cant do it in Windows, so what makes you think you can do it in Linux ?

Good luck to everyone with their 64 bit systems. I have almost everything I ever wanted working now. :KS

---

### Post by iam1e5 on 2007-05-19
> **Cappy said:**
> OpenMotif does that, nothing to be worried about. I don't understand the error though, you did follow the whole guide and install everything on the "sudo aptitude" line?



iam1e5: you didn't change to the directory you downloading the package at. You need to do
```
cd ~/Desktop
``` if you downloaded it on your desktop


thx thx~
didnt realise that~

---

### Post by iam1e5 on 2007-05-19
but then i got a problem~
vidz in youtube are not really smooth~
very jerky n sometimes the box just disappear~

---

### Post by Cappy on 2007-05-19
> **abhishek456 said:**
> when i tried to run opera browser through terminal it displays 



I am using 64bit Ubuntu -feisty and had fallowed all the procedure explaned above

** I had installed openmotif_2.deb by forcing Dependency check as i could not find "lib6g" anywhere which was required dependency

Google search revealed: [http://ubuntuforums.org/showthread.php?p=2651180](http://ubuntuforums.org/showthread.php?p=2651180)

---

### Post by abhishek456 on 2007-05-19
i don't really need  to go that long. Right now I am happy with my firefox. 

But i will surely fallow it when i need

Thanks much for u help CAPPY

---

### Post by bung33 on 2007-05-19
Thanks! It worked perfectly the first time...

---

### Post by Josiah4jc on 2007-05-20
I copied and pasted the instructions down into konsole, and wonder of wonders, Opera! I then decide to run adept updater, double click it by acident, it wont open, shut down the xserver with ctrl-alt-bckspace ... it wont go to the login screen ... instead it's a sort of off white screen with a text prompt that doesn't do anything execpt for allow me to type ... pressing enter goes to the next line, but doesn't actuall do anything. Rebooting doesn't get me any further than this point.

Ctrl-Alt-F1 ... I see that there have been some problems, and I quote:

Could not init font path element
/usr/x11r6/lib/x11/fonts/misc
/usr/share/fonts/x11/cyrillic
/usr/x11r6/lib/x11/fonts/Type1
removing from list!

I run startx and get this little message in a little window ... something about kinit not starting ... anyway I think that if someone could just tell me how to download and install these fonts using naught but the prompt I could get back on track.

---

### Post by Josiah4jc on 2007-05-21
I figured out that it was the qt3 package that was at fault... funny thing, everything's dependant on it, including all my usual networking software == no internet. Luckily I have my kubuntu dvd, found the qt3 libs on there, and installed the correct ones. 

Well, I am proud of myself. I did all that from the console. I guess nothing teaches you better than necessity. Do or die ... well, do or reinstall and don't get any sleep.

---

### Post by JSThePatriot on 2007-05-22
Worked perfectly for me as well!! Thanks a ton!

JS

---

### Post by Mikk Lukk on 2007-05-22
My Hero!

---

### Post by mhenriday on 2007-05-22
**Jouka**, am I right in assuming that **opera_9.21-20070510.6-shared-qt_en_i386.deb**, can be installed on an **AMD 64 X 2** computer using the procedure you outline above, *mutatis mutandi * - or is there anything additional I need to do ? I tried to install the above with the standard **GDebi** package installer after downloading it directly from the **Opera** download page, but got the usual error message : > Error : wrong architecture 'i386' It's a bit of a pain that so essential elements of computing as browsers and audio cards (in my case, **Creative Labs Sound Blaster X-Fi**) don't seem quite ready for 64-bit computing....

Henri

---

### Post by Meir on 2007-05-22
You need to use:
sudo dpkg -i --force-architecture opera_9.21-20070510.6-shared-qt_en_i386.deb
from the command line.

---

### Post by jouka on 2007-05-22
> **mhenriday said:**
> **Jouka**, am I right in assuming that **opera_9.21-20070510.6-shared-qt_en_i386.deb**, can be installed on an **AMD 64 X 2** computer using the procedure you outline above, *mutatis mutandi * - or is there anything additional I need to do ? I tried to install the above with the standard **GDebi** package installer after downloading it directly from the **Opera** download page, but got the usual error message :  It's a bit of a pain that so essential elements of computing as browsers and audio cards (in my case, **Creative Labs Sound Blaster X-Fi**) don't seem quite ready for 64-bit computing....

Henri

Give it a shot, see if it helps. ;)

---

### Post by mhenriday on 2007-05-22
Apart from the fact that the operations ```
sudo cp libflashplayer.so /usr/lib/opera/plugins
``` and ```
sudo cp flashplayer.xpt /usr/lib/opera/plugins
``` failed, as neither «libflashplayer.so» or «flashplayer.xpt» could be found, the installation of **Opera 9.21** went like a dream, with the following result :> Version information
Version
9.21 
Build
641
Platform
Linux
System
x86_64, 2.6.20-15-generic
Qt library
3.3.7
Java
Java Runtime Environment installed
Browser identification

Opera/9.21 (X11; Linux x86_64; U; en)While I must confess to being a **Firefox** man myself, I dislike having to rely upon a single browser, and always try to have **Opera** installed as well on whatever system I am running. Thanks a lot, **Jouka** !...

---

### Post by Princey on 2007-05-23
> **mhenriday said:**
> Apart from the fact that the operations ```
sudo cp libflashplayer.so /usr/lib/opera/plugins
``` and ```
sudo cp flashplayer.xpt /usr/lib/opera/plugins
``` failed, as neither «libflashplayer.so» or «flashplayer.xpt» could be found, the installation of **Opera 9.21** went like a dream, with the following result :While I must confess to being a **Firefox** man myself, I dislike having to rely upon a single browser, and always try to have **Opera** installed as well on whatever system I am running. Thanks a lot, **Jouka** !...

Did you extract the said files, i.e., libflashplayer and flashplayer.xpt?

---

### Post by jouka on 2007-05-23
> **Princey said:**
> Did you extract the said files, i.e., libflashplayer and flashplayer.xpt?

Yes, apparently you missed this step or did it a bit wrong:

4. Get Flash 9 from [http://fpdownload.macromedia.com/get...9_linux.tar.gz](http://fpdownload.macromedia.com/get...9_linux.tar.gz)
extract it somewhere.. like aint no place like $home so there u go. Then go there and do

cd install_flash_player_9_linux/
sudo cp libflashplayer.so /usr/lib/opera/plugins
sudo cp flashplayer.xpt /usr/lib/opera/plugins



So get the .tar.gz package that is mentioned, extract it somewhere and you should be able to find those files amongst the extracted files.

---

### Post by Angelbeast on 2007-05-25
Okay i'm not getting any sound on pogo games? has anyone else been having this  problem?

---

### Post by mhenriday on 2007-05-25
As a matter of fact, **jouka**, I had had the **Flash Player** extracted on my desktop previously, but despite this, the subsequent two operations failed, as mentioned in my post above. But just to make sure, I went to **Adobe**'s site and downloaded the tar.gz version, which I then extracted to my desktop. Again, however, my attempt to follow up with the cp commands failed ; here's what happened (the terminal uses Swedish) :
```
mhenriday@mhenriday-desktop:~$ cd install_flash_player_9_linux/
mhenriday@mhenriday-desktop:~/install_flash_player_9_linux$ sudo cp libflashplayer.so /usr/lib/opera/plugins
Password:
cp: kan inte ta status på "libflashplayer.so": Filen eller katalogen finns inte
mhenriday@mhenriday-desktop:~/install_flash_player_9_linux$
```
i e, the same result as previously. Any clues as to where I went wrong ?...

Another matter - I should like to download and install **Picasa 2**, with which I am familiar from use in **XP** and which finally is available for **Linux** distros, on my 64-bit **Feisty** setup. Unfortunately, it's not been coded for 64-bit operative systems, and when I try to open it with ```
sudo dpkg -i /tmp/picasa_2.2.2820-5_i386.deb
``` I get the standard error message saying «wrong architecture 'i386'». Can **Picasa** installation be forced, using the techniques, *mutatis mutandi,* you described to  force installation of **Opera** on a 64-bit machine ?...

Henri

---

### Post by mhenriday on 2007-05-25
Let me answer my own question - the technique does seem to be generalisable ! The following command enables **Picasa 2** on my **AMD 64 X 2** :```
sudo dpkg --force-architecture -i picasa_2.2.2820-5_i386.deb

```

Wonderful ! Now if only **Creative Labs** would release a driver that would make **Sound Blast X-Fi **work on **Ubuntu**, I could dump **Windows** completely....

Henri

---

### Post by Cappy on 2007-05-25
You should be able to find really cheap sound cards on ebay. You could get an Audigy 2/4 or Sound Blaster Live! or something. They delayed the X-Fi closed source drivers AGAIN so a $20 soundcard sounds good to me.

---

### Post by humojaguar on 2007-05-25
didnt work it said that there were no new plugins available
im using fiesty on a p4 3.0ghz 512ram ddr2, with 2 sata disks
yet im confused if is 32 bit or 64 bit

enlight me please
ps. Im a advanced windows EX user, but still a Linux Rookie
thanks
humo

---

### Post by jvc26 on 2007-05-27
Confused if what is 64bit? Opera? Thats 32bit, there isnt a 64bit version, this is how to install the 32bit one within the 64bit architecture version of Ubuntu. If you're wondering whether your Ubuntu install is 64bit, the simplest answer is which version did you install? I think you can get it from terminal via:
```
uname -a
```
Il

---

### Post by Cappy on 2007-05-27
It's
```
arch
```

If you're running 64-bit it will return "x86_64"

---

### Post by all4als on 2007-05-27
very new to linux, as well as the command line (terminal) and yada yada yada.

What do I need to do if I have already gone to opera's web site and downloaded and opened opera? I would like to have flash working, but I want to make sure its done right. Thanks for your help.

---

### Post by Echow on 2007-05-28
all4als: 
The steps on the very first post are pretty much perfect to help you set up. I think if you downloaded the Ubuntu version from the Opera website you will need to use this to install the package instead of the first step of the first post:
```
sudo dpkg --force-architecture -i opera_9.21-20070510.6_i386.deb
```
If it says you cannot access the file then try typing this:
```
cd ~/Desktop
```
before typing the stuff above.

Everything installed fine, except Opera seems to take at least 10 seconds to start up, especially if i have more tabs open. When its loading flash site (youtube) it tends to hang a bit while its loading the plugin. Is this normal behaviour? Also when I open Opera from terminal i get these messages:
```
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

Opera still works, apart from these things. Thanks for your help!
Ed

EDIT: Ok discovered that flash 9 has problems with Opera, at least for me. flash 7 doesn't hang it anymore, but still have those messages in terminal. I am using opera 9.21 (the one you download from opera.com), could that be the problem?

---

### Post by Cappy on 2007-05-28
Flash 9 is pretty unstable no matter what browser it is running in. Firefox will randomly just crash on me. Opera only hangs [for me] when I am right clicking on the address bar while something flash is loading. Opera is much more stable for me.

---

### Post by all4als on 2007-05-29
Thanks for the help Echow. But before I go down that road, what if i wanted to load Flash 7 instead of 9. Do I change the 9 to a seven in the flash file? 

This forum Rocks. i love the support and people willing to help.

---

### Post by Cappy on 2007-05-29
Most things like online video and games require Flash 9. No, changing the name of the file will not change the Flash version. I'm not even sure where you can get Flash 7 anymore.

---

### Post by swiftstealth on 2007-05-29
Hello all

I have Opera 9.21 and the latest edition of Fiesty(for 32 bit) and I have tried to download Flash player for Opera several times, and I've noticed that there is not a Flash player for Opera. The Flash player for Linux only supports FireFox, Mozilla, and seamonkey, All well and good, But I like opera best...:sulks: What should I do? (I'm also a total newbie as far as ubuntu is concerned. I knw very little about it/how to use it, though I did manage to install flashplayer for firefox...even though I didn't need it)

help anyone?

---

### Post by Cappy on 2007-05-29
> **swiftstealth said:**
> Hello all

I have Opera 9.21 and the latest edition of Fiesty(for 32 bit) and I have tried to download Flash player for Opera several times, and I've noticed that there is not a Flash player for Opera. The Flash player for Linux only supports FireFox, Mozilla, and seamonkey, All well and good, But I like opera best...:sulks: What should I do? (I'm also a total newbie as far as ubuntu is concerned. I knw very little about it/how to use it, though I did manage to install flashplayer for firefox...even though I didn't need it)

help anyone?

I can't figure out if I want to be sarcastic or not. Thinking .. thinking .. thinking .. no .. don't feel like it anymore. Check the first post in this thread, it tells you how to install flash 9 for Opera.

---

### Post by swiftstealth on 2007-05-29
haha, ouch. Felt that ;)
I probably deserved it though. I've finished reading through all of the back logged messages, and I have tried to do as the guide instructs, and it isn't working/I have no idea what I'm doing. The help that comes with ubuntu isn't very "helpful" and I'm barely able to function in ubuntu. is there a guide that you would recommend for me to become familiar with how to really work with linux (like how to use the terminal intelligently for instance? If you'd point me in the right direction I'd appreciate it :)

---

### Post by Meir on 2007-05-30
> **swiftstealth said:**
> haha, ouch. Felt that ;)
I probably deserved it though. I've finished reading through all of the back logged messages, and I have tried to do as the guide instructs, and it isn't working/I have no idea what I'm doing. The help that comes with ubuntu isn't very "helpful" and I'm barely able to function in ubuntu. is there a guide that you would recommend for me to become familiar with how to really work with linux (like how to use the terminal intelligently for instance? If you'd point me in the right direction I'd appreciate it :)

Do you have firefox32 or another 32 bit browser instaled where it is working?

---

### Post by Cappy on 2007-05-30
Maybe this: [http://www-rohan.sdsu.edu/doc/debian/ch-basics.html#s-basics-files](http://www-rohan.sdsu.edu/doc/debian/ch-basics.html#s-basics-files)
or
[http://tldp.org/LDP/GNU-Linux-Tools-Summary/html/working-files-folders.html](http://tldp.org/LDP/GNU-Linux-Tools-Summary/html/working-files-folders.html)

If you download to your desktop you need to ```
cd ~/Desktop
``` before you can run any of the commands on the first post.
"~" is your personally directory. You can type "cd Desk" and hit TAB and it will autocomplete to "Desktop". TAB is essential for terminal use.

---

### Post by Echow on 2007-05-30
> **all4als said:**
> Thanks for the help Echow. But before I go down that road, what if i wanted to load Flash 7 instead of 9. Do I change the 9 to a seven in the flash file? 

This forum Rocks. i love the support and people willing to help.

I got it from here:
[Flash 7 download]("http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp7_archive.zip")
If you unzip this archive under r69 (mebbe release 69? not sure) you can see the linux.tar.gz. Extract that to home folder just like this instructions tell you with flash 9, and then you can prob just enter this code in terminal:

cd install_flash_player_7_linux/
sudo cp libflashplayer.so /usr/lib/opera/plugins
sudo cp flashplayer.xpt /usr/lib/opera/plugins

I'm only using flash 7 atm because 9 just hangs my Opera too much. It could possible work for you...maybe follow the first post's instructions to install flash 9, and if it's too laggy install flash 7.
Yeh these forums are great arent they?

---

### Post by eliphant0723 on 2007-05-30
This guide ROCKS! :guitar:

Thanks for all the help everyone :KS

---

### Post by Echow on 2007-05-31
Hey just another observation. I have tried installing both the static and shared versions of opera. The shared version works great, smooth fonts and everything, PROVIDED i follow step 6:
6. Get qt3 libs from: [http://mirrors.kernel.org/ubuntu/poo...untu5_i386.deb](http://mirrors.kernel.org/ubuntu/poo...untu5_i386.deb) and do

sudo dpkg -i --force-architecture libqt3-mt_3.3.8really3.3.7-0ubuntu5_i386.deb
However, this overwrites my 64bit libqt3 which other programs depend on (although they were fairly minor).
On the other hand if I use the static version it seems I don't need step 6, but the fonts on the menus (across top/right click mouse menus) look all jagged and funny. I'm not sure if this has anything to do with this: [http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670), but I'm sure even before I installed those files the static version fonts were a bit ugly. 
Is this true for everyone else? Because it seems like most people are happy with the static version.....
Thanks, Ed

---

### Post by Cappy on 2007-05-31
Re-install your 64-bit qt3 and then do this:

```

sudo dpkg -x libqt3-mt_3.3.8really3.3.7-0ubuntu5_i386.deb libqt3
cd libqt3/usr/lib/
sudo mv * /usr/lib32/

```
It won't overwrite your amd64 libraries that way. 


As for the menu problems .. it looks fine for me. 
I did change the font in the Opera settings, though. I changed all instances of "Bitstream Vera Serif" to "Bitstream Vera Sans". One of those options is "browser menus" - maybe that is why it looks fine for me.

In Opera it is located at Tools-->Preferences-->(Tab)Advanced-->(Selection Box)Fonts

---

### Post by Case_f on 2007-05-31
> **Cappy said:**
> Re-install your 64-bit qt3 and then do this:

```

sudo dpkg -x libqt3-mt_3.3.8really3.3.7-0ubuntu5_i386.deb libqt3
cd libqt3/usr/lib/
sudo mv * /usr/lib32/

```
It won't overwrite your amd64 libraries that way. 


Or just install the ia32-libs-kde package ;) However installing the 32bit libqt package with --force-architecture is a VERY BAD IDEA indeed.

And yes, the static version of Opera has antialiasing disabled for menus (only for menus) and you can't change that, it's "hardcoded" in it.

---

### Post by Cappy on 2007-05-31
o yeah? I didn't know that it was in ia32-libs-kde.
*goes off to look in the ia32 packages to see what else he didn't know*

---

### Post by Echow on 2007-05-31
> **Case_f said:**
> Or just install the ia32-libs-kde package ;) However installing the 32bit libqt package with --force-architecture is a VERY BAD IDEA indeed.

And yes, the static version of Opera has antialiasing disabled for menus (only for menus) and you can't change that, it's "hardcoded" in it.

Wow I never knew that was a bad idea....at least it was easily recoverable. Il keep that in mind next time i force arch something. 
Thanks for the info on the static Opera, was getting a bit annoyed that I couldn't get it to work. I will try and download the ia32-libs-kde packages and see how they go.
Cheers,
Ed

---

### Post by s4lv1n0 on 2007-06-01
I would like to thank Jouka and every member of the Ubuntu community for this excelent howto, everything worked just fine without any error. Flash is enabled and so it's sound. YouTube is working great.

I'm using Xubuntu 64bits and I'm just loving this O.S. I used an other Linux distro but this (x)Ubuntu is so much better for me.

Once again, thank you!

---

### Post by crownz on 2007-06-02
Excellent! Worked like a treat without any errors at all.

Thank you so much.

---

### Post by Traceur-UK on 2007-06-03
I'm getting this error when I try launching opera:
> ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.20-20070409.1/opera: error while loading shared libraries: libX11.so.6: wrong ELF class: ELFCLASS64

I tried Cappy's solution but no luck. Any help much appreciated. :)

---

### Post by Cappy on 2007-06-03
It's the last line in the guide:
```

sudo aptitude install ia32-libs ia32-libs-sdl ia32-libs-kde ia32-sun-java5-bin ia32-libs-gtk flashplugin-nonfree sun-java6-plugin sun-java6-jre

```

mainly it is the ia32-libs but you'll need the other ia32 packages eventually anyway

---

### Post by Traceur-UK on 2007-06-03
Hmm...is working now, thanks alot. Thought I ran that line :S oh well haha. S'all good. Got my favourite browser working AND got flash working. Good day.

---

### Post by swiftstealth on 2007-06-05
Hey, thanks for the links cappy, I'm reading them now :) Unfortunately it's all academic as the computer with ubuntu on it has suffered some sort of system failure. but anyway I just wanted to say I appreciate that all of the people on this forum are willing to help so much. you guys rock!

---

### Post by Cappy on 2007-06-07
Kilz's Nspluginwrapper script:
[http://ubuntuforums.org/showthread.php?t=425672](http://ubuntuforums.org/showthread.php?t=425672)
can be run instead of the extracting of the flash files. If you do, firefox and opera will both have flash 9 installed.

---

### Post by Cappy on 2007-06-14
[http://blogs.adobe.com/penguin.swf/2007/06/fullscreen_beta.html](http://blogs.adobe.com/penguin.swf/2007/06/fullscreen_beta.html)

Says the new Flash does NOT work with Opera.

---

### Post by Case_f on 2007-06-15
Confirmed, it doesn't... :(

---

### Post by erfahren on 2007-06-15
I used the script by Kilz as well [http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)
for Firefox32, Flash, Java and all that so after this Howto all I had to do was copy the libflashplayer.so and flashplayer.xpt from /usr/lib32/firefox32/plugins to /usr/lib/opera/plugins set up Opera's Java path to --- /usr/lib/jvm/ia32-java-1.5.0-sun-1.5.0.11/jre/lib/i386/  --- and I now have Opera (with all my very much needed(?) overbloated Opera bookmarks)! YAY! =D>

but... does anyone know how to get the spellcheck function with Aspell working?

I found these (very outdated) directions from: [http://my.opera.com/citoyen/blog/show.dml/1953](http://my.opera.com/citoyen/blog/show.dml/1953)

> 
1. Install the latest version of Aspell and at least one dictionary
2. su
3. Add /usr/lib to /etc/ld.so.conf if it isn't already there


I did and added /usr/lib32 as well (Aspell is already installed).

> 
4. Go to /usr/lib and type: ln -s /usr/lib/libaspell.so.15 /usr/lib/libaspell.so


I had a symlink  "/usr/lib/libaspell.so.15" to /usr/lib/libaspell.so.15.1.4  there already. I tried putting symlinks in  /usr/lib32  to  /usr/lib/libaspell.so.15  and  /usr/lib/libaspell.so.15.1.4  respectively.

> 
5. Type: ldconfig
6. Type: locate spellcheck.so (do updatedb first if necessary)
7. Close Opera, and open the file /usr/share/opera/ini/spellcheck.ini. Edit its contents as follows:

[Spell Check]
Spell Check Engine=/usr/lib/opera/7.50-20040218.5/spellcheck.so
Default Language=en
Default Encoding=iso8859-1

Make sure the path for Spell Check Engine matches the path locate gave you. 


(/usr/lib/opera/9.20-20070409.1/spellcheck.so --   did exist)

spellcheck.ini didn't exist there so I created it as so (like the others there). 
```

Opera Preferences version 2.0
; Do not edit this file while Opera is running
; This file is stored in UTF-8 encoding

[Spell Check]
Spell Check Engine=/usr/lib/opera/9.20-20070409.1/spellcheck.so
Default Language=en
Default Encoding=iso8859-1 

```
> 
8. exit su
9. Start Opera. Spell check should now work.


... that didn't work for me. Anyone know how to do it?  I reely nead it! lol!

---

### Post by Angelbeast on 2007-06-17
silly question...how do i uninstall opera when it was installed like this? i didn't see it in either of the package managers...

---

### Post by Cappy on 2007-06-17
You use dpkg to remove things installed through .debs
```

sudo dpkg --remove opera-static

```

I type sudo dpkg --remove oper (TAB) and it auto-completed to the full name.

I assume this is just hypothetical, of course. No one in their right mind would want to uninstall Opera after having felt its smooth silky skin.

---

### Post by Angelbeast on 2007-06-17
> **Cappy said:**
> You use dpkg to remove things installed through .debs
```

sudo dpkg --remove opera-static

```

I type sudo dpkg --remove oper (TAB) and it auto-completed to the full name.

I assume this is just hypothetical, of course. No one in their right mind would want to uninstall Opera after having felt its smooth silky skin.

Thanks...and i did say it ws a silly question hehe  :-P

---

### Post by sambehera on 2007-06-20
thanks .... worked very well.... .. though i did have problems installing lesstif2 (failed dependencies [lib6g] ......... plus the link wasnt correct .... had to dive into the mirror and look for lesstif2 ... 

well ... it installed and worked fine though.... and now i have flash working fine within opera!

thank you!

now i can watch youtube! ... though id like flash in ff2 x64 coz it has extensions ...

---

### Post by erfahren on 2007-06-25
I struggled with trying to figure out how to get the Aspell spellchecking function working for quite awhile (I kind of gave up on it after no responses to my previous post. It was really driving me nuts not having a spellcheck function though). I came just short of trying to install the i386 version but (with my limited knowledge of this stuff) wasn't sure how it would effect the 64-bit version and other programs relying on it

(Apparently, from what I've noticed on various forums, spellchecking isn't that important to the younger generation nowadays!  :p </rant>)

Anyway, I ended up finding a little Javascript spellchecking widget that I didn't know existed and wanted to share it with y'all. -- [http://opera.gt500.org/ospell/](http://opera.gt500.org/ospell/)
Check it out!

---

### Post by mhenriday on 2007-06-28
> **sambehera said:**
>  ... though i did have problems installing lesstif2 (failed dependencies [lib6g] ......... plus the link wasnt correct .... had to dive into the mirror and look for lesstif2 ... .

Returning to this very useful thread after a re-installation of **Feisty**, I also found that the [link]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fl%2Flesstif1-1%2Flesstif2_0.93.94-11.4ubuntu3_i386.deb&md5sum=80e79cdb32aba826fd35cf4d116d54a7&arch=i386&type=main") **Jouka** provided a couple of months ago no longer works - when I try to download the programme from the mirror sources, I get the following unhelpful 404 error message :> The requested URL /ubuntu/pool/universe/l/lesstif1-1/lesstif2_0.93.94-11.4ubuntu3_i386.deb was not found on this server. Out of date ? I looked through the list of [**Debian** packages]("http://packages.ubuntu.com/feisty/allpackages") available for **Feisty** and found two **lesstif2 packages**, but neither of these seem relevant. You, however, seem to have found it , **sambehera** ; would you mind me asking you where and to provide a link, if possible ?...

Henri

---

### Post by erfahren on 2007-06-28
> **mhenriday said:**
> Returning to this very useful thread after a re-installation of **Feisty**, I also found that the [link]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fl%2Flesstif1-1%2Flesstif2_0.93.94-11.4ubuntu3_i386.deb&md5sum=80e79cdb32aba826fd35cf4d116d54a7&arch=i386&type=main") **Jouka** provided a couple of months ago no longer works - when I try to download the programme from the mirror sources, I get the following unhelpful 404 error message : Out of date ? I looked through the list of [**Debian** packages]("http://packages.ubuntu.com/feisty/allpackages") available for **Feisty** and found two **lesstif2 packages**, but neither of these seem relevant. You, however, seem to have found it , **sambehera** ; would you mind me asking you where and to provide a link, if possible ?...

Henri
Wow, I just used the original link a couple weeks ago. I still had the the package saved (I save everything! lol). I uploaded it here: [lesstif2_0.93.94-11.4ubuntu3_i386.deb](http://www.one-tweak-loop.net/misc_files/lesstif2_0.93.94-11.4ubuntu3_i386.deb) if you just want to get it from there.

I found [this](http://packages.ubuntu.com/feisty/libs/lesstif2) though, which is probably one of those you found. It was in the libraries section. It looks like an updated version which replaced the other one. Do you think that could be it?

---

### Post by JAmerican on 2007-06-29
> **erfahren said:**
> Wow, I just used the original link a couple weeks ago. I still had the the package saved (I save everything! lol). I uploaded it here: [lesstif2_0.93.94-11.4ubuntu3_i386.deb](http://www.one-tweak-loop.net/misc_files/lesstif2_0.93.94-11.4ubuntu3_i386.deb) if you just want to get it from there.

I found [this](http://packages.ubuntu.com/feisty/libs/lesstif2) though, which is probably one of those you found. It was in the libraries section. It looks like an updated version which replaced the other one. Do you think that could be it?

OMG thanks for the file and thanks jouka for posting this hilarious and useful guide. I've never seen Flash run so smoothly on my computer (that includes Windows and Mac OS X ) :).

JAmerican

---

### Post by sleepy_yellow on 2007-07-01
thanks so much! great guide 

bookmarked

---

### Post by Philatio on 2007-07-04
> **Cappy said:**
> I can't figure out if I want to be sarcastic or not. Thinking .. thinking .. thinking .. no .. don't feel like it anymore. Check the first post in this thread, it tells you how to install flash 9 for Opera.

Thank you very much Cappy!  You've been very helpful. :)

---

### Post by ihristov on 2007-07-14
> **erfahren said:**
> 
Anyway, I ended up finding a little Javascript spellchecking widget that I didn't know existed and wanted to share it with y'all. -- [http://opera.gt500.org/ospell/](http://opera.gt500.org/ospell/)
Check it out!

Ditto for OSpell. I did not even bother to try to make Opera-static recognize that there is an installed aspell. Directly installed OSpell and I am now a happy camper.

---

### Post by Cappy on 2007-07-14
> **ihristov said:**
> Ditto for OSpell. I did not even bother to try to make Opera-static recognize that there is an installed aspell. Directly installed OSpell and I am now a happy camper.

OSpell is awesome. w00t.

> OSpell does not actually check spelling. It transmits the text to be checked to an online server, and it is checked there. One of these server's is Google's GMail Spell Check. The other two (the orangoo and fearphage servers) are powered by GoogieSpell, which you can download and try for yourself. I would believe that GoogieSpell uses Aspell as it's back-end, and that Aspell does all of the actual spell checking work.

---

### Post by £Xo7XEEQK38037M# on 2007-07-20
After following this guide not all my flash issues have been solved.

1) I followed the installation steps from Adobe
2) I followed this guide
3) I removed the /usr/lib/mozilla and /usr/lib/netscape directories from the plugin path
4) I made sure opera would choose the opera directory for the flash plugin

Opening a movie on youtube finally got to work, however after some time (and the period varies) the video still turns grey. 

At this point I have not yet checked into the sound issue, but seen the major troubles I had to get going I assume it will take me some time to get that straight.

---

### Post by Crinos512 on 2007-07-23
OK, I finally got my [COLOR="Blue"]opera-static_9.20-20070409.1-qt_en_i386.deb[/COLOR] working somewhat,  but I have the following issues:

1. The fonts are very wide (Monospaced looking), even in the title bars and panels. I cannot figure how to alter them.
2. Oddly, I cannot connect to the internet with Opera. I get a page unavailable error, but I can open the same link in Firefox. Any ideas what could cause 1 to fail when the other can succeed?



Other than that, is there a reason you link to that version of Opera? (static vs shared?)

_currently available:_
[opera-static_9.22-20070710.1-qt_en_i386.deb]("http://snapshot.opera.com/unix/Weekly-652/intel-linux/opera-static_9.22-20070710.1-qt_en_i386.deb")
[opera_9.22-20070716.6-shared-qt_en_i386.deb]("http://www.opera.com/download/get.pl?id=29586&location=201&nothanks=yes&sub=marine")

---

### Post by £Xo7XEEQK38037M# on 2007-07-23
> **tneo said:**
> After following this guide not all my flash issues have been solved.

1) I followed the installation steps from Adobe
2) I followed this guide
3) I removed the /usr/lib/mozilla and /usr/lib/netscape directories from the plugin path
4) I made sure opera would choose the opera directory for the flash plugin

Opening a movie on youtube finally got to work, however after some time (and the period varies) the video still turns grey. 

At this point I have not yet checked into the sound issue, but seen the major troubles I had to get going I assume it will take me some time to get that straight.Anyone any thoughts about the flash boxes turning grey after some time?

---

### Post by Novakane on 2007-07-29
> **Echow said:**
> I got it from here:
[Flash 7 download]("http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp7_archive.zip")
If you unzip this archive under r69 (mebbe release 69? not sure) you can see the linux.tar.gz. Extract that to home folder just like this instructions tell you with flash 9, and then you can prob just enter this code in terminal:

cd install_flash_player_7_linux/
sudo cp libflashplayer.so /usr/lib/opera/plugins
sudo cp flashplayer.xpt /usr/lib/opera/plugins

I'm only using flash 7 atm because 9 just hangs my Opera too much. It could possible work for you...maybe follow the first post's instructions to install flash 9, and if it's too laggy install flash 7.
Yeh these forums are great arent they?

Using: Feisty, Opera 9.22.

Thanks for that Flash7 link! Couldn't get Flash9 to work at all, but F7 worked fine. Thanks also to all the others for their info.

The F7 link is to a ZIP file. I couldn't gunzip it, so I Samba'd it over to my XP machine. Unzipped it there, then Samba'd the tar.gz back to Ubuntu and extracted the files. Followed the cp instructions.  Worked fine. Firefox on the Ubuntu is still using Flash9, which is okay.

Thanks!

---

### Post by dreaswar on 2007-07-30
hi,
am a new bie to linux. 

just been working n lunix for the past one week. 

as i was using opera in windows i was happy that the same was available for linux. 

i installed opera 9.22 using synaptic.

opera didnt place a shortcu in menubar so i used the terminal to star it. 

i got lot of error messages but opera window opened. however it dosent retrieve any web pages. 

when i type an address it just dosent do anything. nothing happens in progress bar too....

here is what i got in the terminal....

dreaswar@ubuntu:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
  
please help...

thanks...

---

### Post by ihristov on 2007-07-30
> **Novakane said:**
> The F7 link is to a ZIP file. I couldn't gunzip it, so I Samba'd it over to my XP machine. Unzipped it there, then Samba'd the tar.gz back to Ubuntu and extracted the files.

gunzip cannot deal with ZIP files. There is a separate utility for that. It's called (as you can guess) unzip.

Also in Gnome if you double-click on the file in Nautilus it should open it in Archive Manager and it knows how to handle it.

---

### Post by ihristov on 2007-07-30
> **dreaswar said:**
> i installed opera 9.22 using synaptic.

opera didnt place a shortcu in menubar so i used the terminal to star it. 

i got lot of error messages but opera window opened. however it dosent retrieve any web pages. 

when i type an address it just dosent do anything. nothing happens in progress bar too....

here is what i got in the terminal....

dreaswar@ubuntu:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
  
please help...

thanks...

1. It should have placed a shortcut in your menu under "Internet". Try logging off and log back in and check the Internet menu. Having the shortcut of course does not matter at all, since
  a) starting it from a terminal by typing "opera" achieves the same
  b) you can create a shortcut yourself if you want to

2. From the error codes you are getting it seems that
  a) The error about not being able to open libjvm.so and libawt.so means you do not have Java installed. This is more of a warning and you can simply ignore this.
  b) X is complaining about some kind of unknown or malfunctioning input device. Did you do some manual adjustments in the X configuration file /etc/X11/xorg.conf ? Possibly because you were playing with Beryl? A quick search for " input device 169" revealed this [thread]("http://ubuntuforums.org/showthread.php?p=1762954"). Maybe you have the same issue?

3. Does Firefox work?

4. Which version of Ubuntu are you running? 7.04? Is it the 64-bit version? Have you applied all the updates?

---

### Post by dreaswar on 2007-07-30
thanks for the suggestion ..

after i posted i continued the search and googled it .. 

i installed Java , placed the link for java in opera under contents in advanced options.

after that the error mesage dissappeared from the terminal but opera still does not retrieve web pages. nothing happens. no errors nothing in progress bar....

i have dne nothing in X 11 files and do not have beryl.

firefox is runnig allright

i run ubuntu 7.04 , 32bit. 

any suggestions?

thnks.

---

### Post by ihristov on 2007-07-30
Again, based on the thread I pointed to earlier it seems to me for some reason Opera thinks it has to initialize the Wacom tablet as an input device. Not sure if you really have one. Are you by any chance running on a tablet PC?

I am not sure why this interferes at all with Opera. If Firefox works fine, this should mean you have connectivity, name resolution, etc configured properly and working.

Maybe you can try shutting down opera and removing the ~/.opera folder

If that does not help you can try to uninstall the package and install it again.

I personally am using the static build directly from Opera's web site (because for me Opera is not available in the standard repositories, since I am running AMD64). You can try the same. Basically remove the version you have installed via Synaptic and
 a) download the static package [executable]("http://opera.gundari.net/linux/922/final/en/i386/static/opera-static_9.22-20070716.1-qt_en_i386.deb")
 b) install it
```
sudo dpkg -i opera-static_9.22-20070716.1-qt_en_i386.deb
```

You can also try using Automatix to install Opera.
I am not sure, but actually I might have used Automatix to install Opera. not manually the static build.

---

### Post by Crinos512 on 2007-07-30
you need to disable IPv6, opera has issues with it.

[http://ubuntuforums.org/showthread.php?t=87798]("http://ubuntuforums.org/showthread.php?t=87798")  :)

---

### Post by dreaswar on 2007-07-30
i have tried just about everything you said..

i reinstalled opera

installed shared as well as the static versions.

tried installing java

installed an older version to see if that worked..

tried adding Qt library as one page in opera troubleshooting suggested 

deleted the folder in /home and reinstalled ...

nothing has worled ..

i do not use a tablet PC.

the next post suggested that i diasable IPV6.... what ever that is :confused:

i found out my IPV 6 status... it is enabled.

it is suggested in that thread that it might slow down the net.. but nothing happens to firefox..its blazing fast...

and its not as if net is slow in opera.. it dosent load at all... nothing happens...

i didnt do wht that post had suggested about disabling IPV 6 as i am only 1 week old in lunux world ...and post was not very newbie friendly....:confused:

any ideas??

thanks,,

---

### Post by Crinos512 on 2007-07-30
> 
**gksudo gedit /etc/modprobe.d/aliases**

Change

*alias net-pf-10 ipv6*
to
[I]alias net-pf-10 off
[/I]
Reboot.

Validate with
**lsmod | grep v6**
Should return nothing.

Why reboot? Because it's the easiest way to do it. It's possible to simply rmmod ipv6 but to do so you need to remove everything that has to do with networking, which means shutting down X, all services, removing your network card modules, etc, etc. It's much easier to just reboot.

try that. :D (BTW: I've been using Linux for less than a month myself.... it does get easier, trust me.)

---

### Post by AbredPeytr on 2007-07-30
Thanks Jouka for this install guide.  It worked perfect for me!  Opera rules!

---

### Post by AbredPeytr on 2007-07-30
Opera is working great, but Update Manager isn't. 

I installed Opera as described. Shortly thereafter the update button popped up. I clicked it and chose install and get the following message:

Software index is broken
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a termanal to fix this issue at first.

The problem seems to involve the qt lib because if I do teh sudo apt-get install -f, Opera doesn't work until I redo "sudo dpkg -i --force-architecture libqt3-mt_3.3.8really3.3.7-0ubuntu5_i386.deb"

Does anyone else have this problem? If yes, how did you fix it?

Thanks for the help.

---

### Post by ihristov on 2007-07-30
> **AbredPeytr said:**
> Opera is working great, but Update Manager isn't. 

I installed Opera as described. Shortly thereafter the update button popped up. I clicked it and chose install and get the following message:

Software index is broken
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a termanal to fix this issue at first.

The problem seems to involve the qt lib because if I do teh sudo apt-get install -f, Opera doesn't work until I redo "sudo dpkg -i --force-architecture libqt3-mt_3.3.8really3.3.7-0ubuntu5_i386.deb"

Does anyone else have this problem? If yes, how did you fix it?

Thanks for the help.

I would try using the static version of the deb. You are not going to depend on the installed version of QT this way

---

### Post by ihristov on 2007-07-30
> **AbredPeytr said:**
> Thanks Jouka for this install guide.  It worked perfect for me!  Opera rules!

Does anyone know if settings (passwords and such) can be used from a Windows version of Opera? I'd rather not have to try to remember all of my passwords (memory is shot).

Thanks.

My guess is that you can. Only need to find which file contains them and copy it over.

Try copying over wand.dat from
C:\Documents and Settings\YOUR_USER_NAME\Application Data\Opera\Opera920\profile\
to
/home/YOUR_USER_NAME/.opera/

---

### Post by AbredPeytr on 2007-07-30
Hi ihristov,

thanks for your excellent tip.  Installing the static version of Opera did the trick. I'll try your suggestion with the .dat file tomorrow.  It's after midnight and I always tell myself NOT to mess with the computer settings when I'm sleepy (have had some "unfortunate" incidences in the past when I broke this rule).

I bow down before you.

Cheers.

---

### Post by jpdamigaman on 2007-08-05
HI I tried origional post to install flash in opera but got this error message

cannot stat `libflashplayer.so': No such file or directory

whats up?

Jpdamigaman

---

### Post by erfahren on 2007-08-05
> 
4. Get Flash 9 from [http://fpdownload.macromedia.com/get...9_linux.tar.gz](http://fpdownload.macromedia.com/get...9_linux.tar.gz)
extract it somewhere.. like aint no place like $home so there u go. Then go there and do

cd install_flash_player_9_linux/
sudo cp libflashplayer.so /usr/lib/opera/plugins
sudo cp flashplayer.xpt /usr/lib/opera/plugins


"cannot stat `libflashplayer.so': No such file or directory" means it couldn't find it. sounds like you didn't change into the directory of the extracted files (cd install_flash_player_9_linux/). Either that or the files just didn't extract properly. you could just look in your home directory for the "install_flash_player_9_linux" folder and look inside of it. Or in the terminal change directory into it and type "dir" --- you chould see: flashplayer-installer  flashplayer.xpt  libflashplayer.so

In that install proceedure all you're doing is copying the two flashplayer plugin files into the opera plugins folder. 

just a note: I've found Flash 9 to be kind of buggy with opera. I've been trying Flash 7 out. Echow linked to the download [in his post here](http://ubuntuforums.org/showpost.php?p=2748464&postcount=85). It seems to include every Flash 7 version known to man though. I just opened the archive in Archive Manager and found the latest linux version and extracted just that.

good luck

---

### Post by jpkotta on 2007-08-06
I got aspell working in 64-bit with Opera.  Try it and see if I've missed something: [https://help.ubuntu.com/community/OperaBrowser#head-8b233e94ad0c1adc2f768dd1dd7c403b6f8ddd75](https://help.ubuntu.com/community/OperaBrowser#head-8b233e94ad0c1adc2f768dd1dd7c403b6f8ddd75).

---

### Post by colo505 on 2007-08-08
I get this error on running the first command:

File '/usr/share/applications/exaile.desktop' contains invalid MIME type 'MimeType=audio/musepack' that contains invalid characters

Any suggestions?

---

### Post by Cappy on 2007-08-08
```
gksudo gedit /usr/share/applications/exaile.desktop
```

Maybe look for the line that says
MimeType=audio/musepack

and make sure it doesn't have a ```
;
``` on the end or any weird characters. You may just be able to remove that line completely if you want.

That error isn't keeping you from installing opera I hope.

---

### Post by colo505 on 2007-08-08
Shall I remove this line:

MimeType=MimeType=audio/musepack;application/musepack;application/x-ape;audio/ape;audio/x-ape;audio/x-musepack;application/x-musepack;audio/x-mp3;application/x-id3;audio/mpeg;audio/x-mpeg;audio/x-mpeg-3;audio/mpeg3;audio/mp3;audio/x-m4a;audio/mpc;audio/x-mpc;audio/mp;audio/x-mp;application/ogg;application/x-ogg;audio/vorbis;audio/x-vorbis;audio/ogg;audio/x-ogg;audio/x-flac;application/x-flac;audio/flac;

---

### Post by Cappy on 2007-08-08
Try changing that line to
```

MimeType=audio/musepack;application/musepack;application/x-ape;audio/ape;audio/x-ape;audio/x-musepack;application/x-musepack;audio/x-mp3;application/x-id3;audio/mpeg;audio/x-mpeg;audio/x-mpeg-3;audio/mpeg3;audio/mp3;audio/x-m4a;audio/mpc;audio/x-mpc;audio/mp;audio/x-mp;application/ogg;application/x-ogg;audio/vorbis;audio/x-vorbis;audio/ogg;audio/x-ogg;audio/x-flac;application/x-flac;audio/flac

```
first

---

### Post by colo505 on 2007-08-08
Well, I removed the line and added it back after installing that package, and did the rest, and it works!

Thanks a lot!

Now let me do something about the fonts..

---

### Post by rubperezt on 2007-08-09
hello, im new with linux, i have been trying to get ANY browser to reproduce flash without getting crashed but i couldnt. even after following this steps opera would crash (randomly) when playing flash (like youtube videos for instance) and show me a gray rectangle where the video should be displayed. I ran it with the console and i got this "error"
```
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.

(process:4562): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:4562): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `GDK_IS_DISPLAY (display)' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);
opera: Plug-in 4562 is not responding. It will be closed.
opera: Define environment variable OPERA_KEEP_BLOCKED_PLUGIN to keep blocked plug-ins.

(process:4772): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:4772): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `GDK_IS_DISPLAY (display)' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);

```
I dont understand it, im hopping some of you can and maybe knows how to fix it.

---

### Post by Cappy on 2007-08-09
Videos turning "grey" for me while playing them has happened to me often ever since that last flash update with the security fix =(

---

### Post by netimen on 2007-08-15
After step 6 I have 32-bit version of qt3-libs installed on my system, but Amarok and many others require 64-bit version of these libs. How can I solve this problem?

---

### Post by Cappy on 2007-08-15
That means the library was ```
 dpkg -i --force-architecture
``` (or --force-all) which shouldn't have been in the guide. Forcing libraries doesn't work for that reason.

Do this instead:
(install the 64-bit libs now before you start)
(change directory to where you downloaded the package)
if it is on your desktop that is "cd Desktop".
```

dpkg -x libqt3-mt_3.3.8really3.3.7-0ubuntu5_i386.deb libqt3
sudo cp -R libqt3/usr/lib/* /usr/lib32/

```

---

### Post by netimen on 2007-08-15
Thank you very much, Cappy!

---

### Post by downsideup16 on 2007-09-02
Thank you.

---

### Post by blastradius on 2008-02-04
I installed Opera using this guide but I've decided that I'll stick with Firefox.

Can someone tell me how to uninstall everything?

Thanks

---

