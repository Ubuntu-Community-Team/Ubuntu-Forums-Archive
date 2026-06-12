---
title: "i took opensuse 11 (gnome) for a spin yesterday"
date: 2008-12-05
forum: openSUSE and SUSE Linux Enterprise
---

### Post by stinger30au on 2008-12-05
and being a user of ubuntu i had expected something relatively easy to setup.

I played around a few days ago with [Mandriva 2009 one]("http://www.mandriva.com/en/product/mandriva-linux-one") and it took a little while to figure it out but i got iyt up and running nicely in the end and i really like it.

how i wish i oculd say the same about [opensuse 11]("http://en.opensuse.org/Welcome_to_openSUSE.org")

the install was easy enough, nothing tuff there and once installed i decided i would get my nvidia fx5500 256meg video card up and running with compiz.

why not i decided as it i know it works well with ubuntu 8.04, mandriva 2009 one and with the newest drivers i can get it running in ubntu 8.10

i must confess i found their web site very easy to navigate and in no time i found a link to [install drivers for the nvidia cards]("http://en.opensuse.org/NVIDIA")

so i tried the first drive i could find and that was the driver labelled as nvidia (Geforce FX, Geforce 6 and newer)
my  card being a fx5500 i assumed it was this driver and let it install. once installed i restarted and i get a text box saying that the x server cant be configured blah,blah,blah 
i assumed it would be like ubuntu when the video driver breaks it will run a "safe mode" style x and allow you to run the gui in a low graphics mode


WRONG


you go back to a terminal screen

so that i tought would be easy fixxed, pop the cd back in the drive and reinstall opensuse 11

so did that and i thought ok, stupid me, i installed the wrong driver. thats cool. i can live with that.live and learn. i will install the other driver as it must be the right one as this driver has failed to run.

so i head off to the web page and download the other driver that says nvidia (Geforce 4 and older, TNT) driver and install it and restart pc and about now im thinking im kinda smart and proud of myself untill once again up pops the blue text box saying it cant configure x blah,blah,blah, need to check configs etc, blah,blah,blah

anyhow i thought well, this sux. so i reloaded opensuse 11 once again and decided to try it winth out 3d running. this sux as i wanted to try out google earth as well, but that aint going to happen.

i went hunting for info on how to install a pdf printer and again a few quick clicks from the documentation page and i found this info on[ how to setup a pdf printer]("http://en.opensuse.org/Printing_to_PDF_HOWTO")

after the major dissapointment of the video card i was not holding my hopes too high to get it working, but alas i followed the instrucitons and it worked.... amazing

next i thought i would try and playback a dvd

i insert a dvd and it telles me it needs to d/l drivers and i have a choice like mandriva 209 one to use the fluendo drivers or d/l the comminity drivers for free, so i opt for the commity free drivers as thats what i use in ubuntu and mandriva 2009 one and they work just fine thanks.

so i follow the prompts and it takes me to a web site and i need to click on a few buttons and type in passwords etc and it merrily downloads away and aftre a little while it says it has finsished and it was successfull at installing the s/w. so as a force of habbit from being a windows xp user i restart the pc just to be sure all is well

double click the dvd icon and get it to open with movie player and again it says it can not play as it needs another driver. from memory it was a mpg2 decoder. i went hunting thru the documentation as well and hunting thru the add/remove software in yast i belive it is called and i could not find anything on how to install this driver it was looking for


so in sheer disgust i removed the cd and walked to my kitchen and place the cd with opensuse 11 on it in to the bin and i seriously doubt i will ever try that distribution ever again.

incase your wondering the pc im testing it on is a pentium 4 3.4Ghz HT, with 1.5 gig ram, poineer dvd writer, and the hdd for testing purposed is a 20 gig ide samsung. nothing flash, but enough for me to test with, and nvidia fx5500 256 meg video card, and using onboard sound

---

### Post by ibutho on 2008-12-05
Some of your problems seem to be user related i.e. not being familiar with openSUSE. If your display stops working because you have used the wrong driver, you can revert back to the old settings by running "sax2" in the command line as root. According to the nvidia website, the correct driver for the Geforce fx5xxx series is the 173.14.12, so you had probably selected the right driver in the first place and all you needed to do was configure it correctly. I don't really bother with 3D effects and pdf printers, so can't be of much help there.

As for multimedia stuff, you can enable the Packman community repository (YaST -> Software -> Community repositories) and install libdvdcss, libxine and the various gstreamer plugins. You can even do this via a one click install which is available from [here]("http://opensuse-community.org/Multimedia").

---

### Post by stinger30au on 2008-12-06
quite probably was my fault, but farout, when you reload an os and try both drivers and niether works out of the box, and you need to tinker with it, makes you wonder why other ditros can make life easy but with this distro you must tinker with the driver after you d/l it


no thanks

not for me, and im sure many others are in the same boat

---

### Post by plb on 2008-12-06
> **stinger30au said:**
> quite probably was my fault, but farout, when you reload an os and try both drivers and niether works out of the box, and you need to tinker with it, makes you wonder why other ditros can make life easy but with this distro you must tinker with the driver after you d/l it


no thanks

not for me, and im sure many others are in the same boat

Try 11.1 RC1. I have a somewhat new laptop and tried opensuse 11 on it and it didn't go over so well however on 11.1 everything was detected and worked straight out of the box without issue. Ubuntu 8.10 couldn't even do that. Not to come off as a prick but this is why most people consider Ubuntu to be a newb distro is because newcomers to Linux expect everything to work out of the box. Sometimes it takes a bit of tinkering to get everything up and running.

---

### Post by ibutho on 2008-12-06
> **stinger30au said:**
> quite probably was my fault, but farout, when you reload an os and try both drivers and niether works out of the box, and you need to tinker with it, makes you wonder why other ditros can make life easy but with this distro you must tinker with the driver after you d/l it


no thanks

not for me, and im sure many others are in the same boat

If you can download your own drivers, then I don't see what the big deal is about if a bit of tinkering is needed in order to get your device working properly. 

If ever you try openSUSE again and you install a proprietary graphics driver, run "sax2" after installing the driver, it tends to do a good job of detecting the new proprietary driver and using it. One thing that may save you time, is to revert to using vesa or fbdev when you have problems with graphics settings instead of reloading/reinstalling. Another option would be to use the distros builtin tools to reconfigure the graphics to their original settings. Fedora uses system-config-display, Mandriva XFdrake and openSUSE uses sax2.

---

### Post by andras artois on 2008-12-06
When I tryed OpenSUSE 11 it was horrible. It looked very nice and at first seemed very nice. Loaded up my music into Banshee and it told me I needed to install some codec's, that's alright, it worked fine. Never tryed playing a dvd. Next I tryed to get my wireless to work. NOT A CHANCE. It wasn't happening, I tryed everything. Downloaded everything I could find to do with wireless drivers and it just wouldn't work. I though oh it isn't that bad, I'll get it working eventually with a big cable draped across the middle of my room so I at least had internet. So I carry on using it for another 1-2 weeks and it suddenyl crashes for no reason. No problem I'll just restart it and it'll be fine. Up pops a screen telling me so and so has crashed or not iniated blah blah blah. Malereproductiveorgans, I left it off for the rest of the day and then came back to it and it worked then it started freezing and crashing more regulary so I switched back to Ubuntu 8.10. :)

Sorry for the lack of paragraphing.

---

### Post by ibutho on 2008-12-06
Not to seem like an openSUSE fanboy, but I think every distro has its flaws and some things really depend on your hardware. For example on my laptop, wireless works out of the box with the latest Fedora, Mandriva and openSUSE releases but Ubuntu just won't play ball. Ubuntu does not autodetect my graphics settings correctly on my desktop computer, but other distros do and where they don't I have both graphical and command line tools to help me fix those problems whereas with Ubuntu 8.04 and 8.10, I have to hack my xorg.conf file manually. On other machines, Ubuntu works perfectly out of the box and others don't.

---

### Post by stinger30au on 2008-12-06
> **ibutho said:**
> Not to seem like an openSUSE fanboy, but I think every distro has its flaws and some things really depend on your hardware. For example on my laptop, wireless works out of the box with the latest Fedora, Mandriva and openSUSE releases but Ubuntu just won't play ball. Ubuntu does not autodetect my graphics settings correctly on my desktop computer, but other distros do and where they don't I have both graphical and command line tools to help me fix those problems whereas with Ubuntu 8.04 and 8.10, I have to hack my xorg.conf file manually. On other machines, Ubuntu works perfectly out of the box and others don't.

your probably right, but as you can see from my first post, there is nothing flash at all about my pc setup

anyhows, i wont be d/l another copy of this o/s to try for some time yet, if ever again after this experience

---

### Post by ryaxnb on 2008-12-18
My expierence was this:
1. I download 11.1 RC1
2. I pop it in VirtualBox
3. Play around with SaX2 screw it up
4. Reinstall
5. use kernel mode commands to set vesa mode
6. Everything works
7. Add 1-click install of third-party stuff
8. Multimedia works
9. Enable Soundcard on host Virtualbox, reboot
10. Sound works

Overall it was great, and YaST is far better than Ubuntu's toolbox, but I screwed up the first time around. The installer is also way nicer than Ubuntu. Overall I'm thrilled with openSuSE 11.1 and I would use it, but I have no problems with my Ubuntu install and I love the debian/Ubuntu repos.

---

### Post by CbrPad on 2008-12-19
I gave the KDE 4.2 beta version a lash there yesterday.  It installed nicely enough onto a spare drive but didn't pick up my wireless (intel3945) nor, more importantly as I don't have a dsl connection, my huawei E220 3g card, which left me completely high and dry.  

KDE looked nice enough but I couldn't stand the slab-type menu (I presume there is a gnome-type alternative somewhere?) and I disliked Dolphin and Konqueror.

---

### Post by wolfen69 on 2008-12-20
i just tried 11.1 (gnome) and have to say i can live without it. the package manager was quirky, the slab menu is too much information at once, and getting my tv tuner card configured was an excersise in futility. 

i'm sure open suse is wonderful for some people, but even if it did run perfect for me, it wouldn't offer me anything that debian doesn't. to me, nothing beats debian/ubuntu on most computers. but, to each their own.

---

### Post by shuttleworthwannabe on 2008-12-21
I have tried many distro's, incl fedora 10 and Mandriva 2009.1 (Gnome) and now OpenSuse 11.1; I keep coming back to Ubuntu. I am sure if I stayed long enough with them, I would begin to figure out how the system could be made to work on my hardware. But time is of the essence. The deal breaker is the package management application: can anything get better than apt-get/synaptic? and all the PPA channels that are so easy to load; also not forgetting the community...by favorite. It's all happening here...under one roof.

I agree, each to his own. However, where credit is due to OpenSuse, this should be in the looks department--they seem to understand what it means to make an interface look vibrant!

---

### Post by Antman on 2008-12-21
> **wolfen69 said:**
> 
i'm sure open suse is wonderful for some people, but even if it did run perfect for me, it wouldn't offer me anything that debian doesn't. to me, nothing beats debian/ubuntu on most computers. but, to each their own.

Substitute debian/ubuntu for **Slackware**, and these are my thoughts too.

---

### Post by jacobw.uk on 2008-12-21
openSUSE does have its problems though, I think it is basically because they keep the distro and popular ISV products separate and don't put the emphasis of user friendliness and task orientation that Ubuntu does.

The package management system although it is much better is still way too complicated to match APT/Synaptic in terms of use. The Ubuntu community is more proactive that openSUSE community in my opinion and thats makes a massive difference (also in my opinion :p)

---

### Post by exploder on 2008-12-21
I tried out OpenSuse 11.1 Gnome version a couple of days ago. The appearance of the system is very polished and attractive in every detail. There are still bugs that are unresolved. It is impossible to use a DVD-RW in OpenSuse 11.1 and the one click codecs install is convenient, not all multimedia playback works the way you would expect. Playback using Flash 10 has very low volume. 

I did like the appearance and would even say it is the most attractive Linux distribution out there. The usplash, icons, theme, background looks great. The selection of applications is very good and they really did think of everything you might want. 

There is a bug in the Live CD install that locks two desktop icons because the profile for "Linux" does not get completely removed. I was surprised that this bug was not noticed because if you do the install it immediately draws your attention with the lock symbols.

If someone were to write up a "How To" for fixing the few bugs that are present and speeding up the system it would be an excellent choice to run.

---

### Post by wolfen69 on 2008-12-21
> **shuttleworthwannabe said:**
> can anything get better than apt-get/synaptic? 

in my opinion, no. mandriva's was very good though.

in opensuse, i downloaded the ivtv drivers for my tv tuner and was told that 160mb of dependencies would also have to be downloaded! WTF! some of the "dependencies" for my tv tuner card included open office updates, some weird codecs, and other things that had nothing to do with my hauppauge card. that's ridiculous. long live apt-get.

---

### Post by jeffreyldavidson on 2008-12-21
I took an excursion to Arch and Suse 11.1 the past couple of days but am back now to Ubuntu.

Arch: I love the aspect of setting up and tinkering with your own system. But even more the idea of a rolling release, never having to upgrade. I did get everything up and running with Gnome and seemed to work OK. I was not though any faster for me and I was never able to get the wireless on my laptop to work - the deal breaker. So after all the work I just dumped it and decided to give Suse a go, although I may come back and try Arch again one day.

Suse: very pleasant to look at, did not care for the menu setup over Ubuntu. Its software repositories seemed confusing and very slow compared to Ubuntu. Additionally, it did not auto mount my CD/DVD drive. It is nice but just didn't feel right.

So after being away I have returned to still the best system out there...Ubuntu. I still may dive into Arch again one day but I am glad to be back home with the U. It just feels right.

---

### Post by NoSmokingBandit on 2008-12-21
I recently tried opensuse as well and i was incredibly impressed. Its the only distro i tired that didnt hate my crappy Trident video card. It was very easy to set up and use and, to be honest, it made ubuntu look very unprofessional imo.

---

### Post by RedDwarf on 2008-12-23
> **shuttleworthwannabe said:**
> The deal breaker is the package management application: can anything get better than apt-get/synaptic?
Well, we have the APT based package management applications that are unable to do his work in 0,61% of the cases (not meaning that it does the work *correctly* in all the other cases) and then we have the OPIUM/ZYpp (openSUSE) based applications that maths show us do their work perfectly in 100% of cases ([http://pho.ucsd.edu/rjhala/papers/opium.pdf](http://pho.ucsd.edu/rjhala/papers/opium.pdf)).
And isn't just the dependency resolution algorithm... are APT based apps able to automatically install a driver for your newly added hardware? (I'm not really sure, but I don't think so)
The nvidia problem from stinger30au was really easy to avoid. You just needed to run "zypper inr" and zypper will know which package is needed by your graphic card... you don't need to know if it's a NVIDIA FX5200, a NVIDIA 7600GT or an ATI. Since openSUSE 11.1 you don't even need to do anything, the update applet will automatically inform you that you need to install a new driver/package when you insert a new hardware.

> **shuttleworthwannabe said:**
> and all the PPA channels that are so easy to load
Because the openSUSE Build Service can't offer anything of what the PPAs offer... oh, wait!! And with 1-Click they aren't exactly difficult to load...

> **shuttleworthwannabe said:**
> also not forgetting the community...by favorite. It's all happening here...under one roof.
There are distros that are good because even if they fail the community will explain you how to fix your problems... and then there are these other distros for which the community isn't so important since they just work. :lolflag:



Package management from openSUSE is second to none.

---

### Post by Antman on 2008-12-23
> **wolfen69 said:**
> in my opinion, no. mandriva's was very good though.

in opensuse, i downloaded the ivtv drivers for my tv tuner and was told that 160mb of dependencies would also have to be downloaded! WTF! some of the "dependencies" for my tv tuner card included open office updates, some weird codecs, and other things that had nothing to do with my hauppauge card. that's ridiculous. long live apt-get.

This also happened to me in the openSUSE11.1 KDE4 version. I was trying to install vlc on my test box and Yast gui wanted to install OpenOffice dependencies, Bluetooth doogle drivers, and other non-sense. I canceled the install and tried zypper via konsole; which worked a lot better.
I'm not sure why the gui is so screwy.:confused:

---

### Post by eagleton on 2008-12-24
Another nice aspect of Opensuse's package handling is [delta-rpms]("http://www.novell.com/products/linuxpackages/opensuse/deltarpm.html").
They make downloads of updates much smaller, which is not trivial for lots of people. 

Apparently Ubuntu does not use such a feature by default, not sure if Debian does.

---

### Post by icecruncher on 2008-12-25
before switching to opensuse I was on Ubuntu. 
kde4.13 was a nightmare so I'm switching back to gnome. 
I like it quite a bit though I probably do prefer ubuntus variation. 
dunno, still need to play a bit

---

