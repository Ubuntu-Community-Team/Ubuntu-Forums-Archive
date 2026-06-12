---
title: "AMD64 chroot questions"
date: 2007-05-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Arnaud_B on 2007-05-05
Hi,

I just finished set up my new amd64 system and I am about to set up a chroot. But before starting I would like to have some info about it.

1/ Will the x86 apps inside the chroot be able to call apps in the 64bits OS. ex: if I click on an email address in Firefox (x86) can it open a Kmail window (amd64)?

2/ Are the fonts of the 64 bits OS available to apps within the chroot or do I need to have a separate set of fonts within the chroot?

3/ I am using kde and if I install firefox inside the chroot will I have to reinstall gtk-qt-engine or my present configuration will affect apps within the chroot?

4/ Is there any negative performance impact in using a chroot? ex: will firefox be as responsive inside the chroot than it is outside?

5/ Is it easy to remove a chroot? The idea would be to use it for now and get rid of it once the apps I need exist in 64bits...

6/ Also I would be interested in knowing any problems you might have encountered in using a chroot... thanks :-)

7/ Also I saw that usually people install a chroot in /var... I'm sure this is a very sensible thing to do but I was wondering what was the reason for this, I would have though that for a small number of apps like mine I could just put it in my /home.

In brief, the 32bits apps I need are fairly limited but not having them is kind of annoying. There are mplayer with w32codecs, skype, flash, and maybe acrobat. Actually among those I mostly want flash (yea the add-plugin but it's everywhere now :-( ) and skype, w32codecs I'm not really sure... my use of mplayer is kind of limited to real streams, quicktime stuff and maybe couple windows media files (rare I guess), do you know if I really *need* w32codecs for these cases?

Well also I heard about other methods besides the chroot but I have to admit that I don't know much about them so if you have an opinion about ia32-libs, nspluginwrapper, and gnash (does it finally work in youtube by the way?) for instance I would be interested :-)

In brief, I just want something clean, stable, integrated, upgradeable and without --force-arch type of thing ;-)

Thanks in advance for your help!

A.

---

### Post by Kilz on 2007-05-05
1. No a chroot is also called a jail. The chroot applicatiopns will not interact with applications outside of the chroot.
2. No, read #1 and place fonts in place of application.
3. No matter what you install it will not look outside of the chroot.
4. It will run as a 32bit application in a 32bit system. You will install a lot of unnecessary files. If you are only installing firefox a chroot is not needed. Matter of fact if all you need is flash you could use nspluginwrapper and the 64bit firefox.
5. Its not that hard, but if you are only needing it for firefox you dont need it.
6. Few people use them so you will not get many responses.
7. If you must install it place it where you want.

With the few applications you are concidering installing a chroot is a waste of time and space. [Take a look at the sticky]("http://ubuntuforums.org/showthread.php?t=191205") and follow a few howto's to install what you need.

---

### Post by Arnaud_B on 2007-05-06
Hi Kilz,
Thank you very much for your answer. I'm sorry I just realized that this was an extensively discussed topic here... please excuse my ignorance. ;-) I have used debian for several years but got a 64bits system just recently... :-) 
Still, you say that apps within the chroot cannot "talk" to apps outside, ok but will a 32 bits firefox installed within the regular system be able to do that (opening a kmail window for instance?)
What I need is indeed rather limited: skype (important), flash+ java + mplayer in iceweasel and maybe a couple more things I cannot think about like that... 
I'm thinking about simply using the 64 bits iceweasel + mplayer (without w32codecs) + java blackdown + nspluginwrapper for flash... I should be able to set up individual apps like skype easily... But I also saw that you have a script that install a 32 bits firefox with all these plugins :-) that seems great but before using this method I wanted to make sure that this will solve my problem of calling 64 bits apps (and using gtk-qt...). Still if I use it I would probably have to adapt it as it will be on a debian machine, if I do that I'll send you the changes back of course... :-)
Thanks again for your help!
A.

---

### Post by Kilz on 2007-05-06
> **Arnaud_B said:**
> Hi Kilz,
Thank you very much for your answer. I'm sorry I just realized that this was an extensively discussed topic here... please excuse my ignorance. ;-) I have used debian for several years but got a 64bits system just recently... :-) 
Still, you say that apps within the chroot cannot "talk" to apps outside, ok but will a 32 bits firefox installed within the regular system be able to do that (opening a kmail window for instance?)
What I need is indeed rather limited: skype (important), flash+ java + mplayer in iceweasel and maybe a couple more things I cannot think about like that... 
I'm thinking about simply using the 64 bits iceweasel + mplayer (without w32codecs) + java blackdown + nspluginwrapper for flash... I should be able to set up individual apps like skype easily... But I also saw that you have a script that install a 32 bits firefox with all these plugins :-) that seems great but before using this method I wanted to make sure that this will solve my problem of calling 64 bits apps (and using gtk-qt...). Still if I use it I would probably have to adapt it as it will be on a debian machine, if I do that I'll send you the changes back of course... :-)
Thanks again for your help!
A.

At this point you might want to at least try the 64bit rout, especially if you installed Feisty. There is a good java plugin, mplayer (this version doesnt need the codecs, it has native support), and nspluginwrapper for flash avilable for it.
I would try the java first. some people have crashing problems for some sites with java on 64bit. If you do then the 32bit Firefox (I also have 32bit iceweasel and flock in the howto and will be adding another soon as I have found a new project) may be a better solution. The only thing it cant start up in 64bit land is the print a page. But you can save pages to files and then print them out. You may also have to theme problems with selected kde themes.

---

### Post by Case_f on 2007-05-06
ad fonts: You can set up symlinks to your 64bit font directories (/usr/share/fonts, /usr/local/share/fonts) so they show up in 32bit chroot. It's even mentioned in the chroot HOWTO, I think.

As for the mplayer, I think mplayer32+w32codecs are no longer necessary, really, mplayer now natively supports almost every decoder except RealMedia and you can add native 64bit codecs for that (see download section on mplayer website).

---

### Post by Arnaud_B on 2007-05-06
Thanks for your help!
Yes I think I will be trying first with a 64 bits iceweasel and see how it goes :-)
I ignored that now mplayer included native support for some of the w32codecs now... You are referring to the version 1.0rc1 in feisty I guess right? Oh and about the java plugin I guess the only one working is the blackdown java... I'll try this out...
Thanks again!
A.

---

