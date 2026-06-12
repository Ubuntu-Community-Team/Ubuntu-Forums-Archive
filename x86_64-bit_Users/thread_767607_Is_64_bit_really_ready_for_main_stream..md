---
title: "Is 64 bit really ready for main stream."
date: 2008-04-25
forum: x86 64-bit Users
---

### Post by OldGaf on 2008-04-25
OK.... let me say I have been using Linux for many years now and I am not scared of digging in and getting my hands dirty. I moved away from Kubuntu and went to Debian as I was getting hanging issues like many others and could not find a fix.

Now, I am thinking of giving Hardy Heron a go, and while I am at it trying 64 bit :-k

So, my question is.... is 64 bit K/Ubuntu realy ready... as in I don't need to tweak this, that and the other thing to make it work?

Are there any applications that I will not be able to use.... VirtualBox for example is a must....

What about KDE4 and nVidia drivers?

Java, flash....... etc

You get the idea.

I don't mind doing a little work, but I don't want it to be a project to just get my system running and stable before I set about breaking it myself!!!

Thanks,
-OG-

---

### Post by obocho on 2008-04-25
I am also wating for the answer of this question : ) 

Actually, I have checked a few forums and mainly everybody says that 64bit Hardy rocks. 

However, I still have a little doubt! 

Thanks in advance guys...

---

### Post by gogogo111 on 2008-04-25
As I am on 64-bit Hardy right now, I can tell you that it rocks. Its fast, stable, and I was even playing WoW in Wine.

Its great, go for it.

---

### Post by ravenon on 2008-04-25
I have been using 64 bit since Edgy. Admittedly, Edgy and Fiesty tested my patience and determination. Gutsy far less so. Now with Hardy, I have had no problems at all.

---

### Post by kklimonda on 2008-04-25
Well, most applications that can be compiled from source work just fine. The only problem i've encountered so far is Flash support. Don't know if it's only me but flashplugin-nonfree from repository is not stable enough to use it with Firefox.
There is VirtualBox for amd64 so no problem here (vmware also provides amd64 binaries), haven't tested Java as i don't really need it.
Haven't got any problems with nvidia drivers so far using Quadro 140M (nvidia also provides amd64 version of their driver).

---

### Post by faridx82 on 2008-04-25
dont be afraid to try 64 bit version. it it much easier than running linux 10 years ago.

---

### Post by crjackson on 2008-04-25
It works just fine, just install it and if you have any issues I'm sure we can resolve them quickly.  Be sure to back up any critical data before you begin.

---

### Post by OldGaf on 2008-04-25
OK...... I will give it a shot...... once I determain that flash and Java will be OK. This is my "main" PC and I want everything to work...

So.... whats the deal with some people using 32 bit Java / Flash?
I would need to also run 32 bit FF I assume..... tho I don't think that would be a big deal.....

So.... is that the way to go if the 64 bit verions kack on my box?

---

### Post by potrzebie on 2008-04-26
32-bit flash works just fine in your 64-bit browser. After your fresh hardy install, choose flashplugin-nonfree in synaptic and it will install Adobe's 32-bit official plugin and the pluginwrapper you'll need to run it in your browser automatically (that used to be the kind-of-hard part, but ubuntu devs got it woked out a month or two ago) Sometimes, if the browser is running all the time like mine is, you'll find that flash has crashed or something (youtube embeds, etc, are suddenly just gray boxes). I just quit firefox and restart it (set "show my windows and tabs from last time" in the "when firefox starts" section of the preferences) and everything is back, plus flash is running again. That's almost the only annoyance, and it's minor, IMO.

Java I don't use, but it seems to be there and is working (I just checked an [essential java app]("http://www.douglasadams.com/creations/infocomjava.html") and it is working), I didn't install it specifically but if I recall it is installed as part of the ubuntu restricted extras.

And virtualbox definitely works, as kklimonda already stated, and is in the universe repository.

---

### Post by Neo Adventist on 2008-04-26
Step One: Install brand-new Hardy Heron 64!

Step Two: Establish Network Connection

Step Three: "sudo apt-get install icedtea-gcjwebplugin"

Step Four: "sudo apt-get install flashplugin-nonfree"

Step Five: "sudo apt-get install ubuntu-restricted-extras"

That's basically how I got my machine to work. Your mileage may vary. :popcorn:

---

### Post by hodge24 on 2008-04-26
With regards to Java, I have the 64 bit JRE installed (from Sun's website), and I'm using it to run 64 Bit Eclipse IDE with no problems at all.

---

### Post by ptn107 on 2008-04-26
I've been running 64-bit since Feisty.  I have never had a single problem with flash, Nvidia [or X] drivers, or wireless since Gutsy-64.  And Hardy-64 installed and runs flawlessly.  My answer is yes, though each users experience is going to differ (substantially in some cases).

---

### Post by Formica45 on 2008-04-26
Installed Hardy 64 and everything is good, i.e. flash and java work just fine. There is no reason not to go 64.

---

### Post by Milleman on 2008-04-26
> **Neo Adventist said:**
> Step One: Install brand-new Hardy Heron 64!

Step Two: Establish Network Connection

Step Three: "sudo apt-get install icedtea-gcjwebplugin"

Step Four: "sudo apt-get install flashplugin-nonfree"

Step Five: "sudo apt-get install ubuntu-restricted-extras"

That's basically how I got my machine to work. Your mileage may vary. :popcorn:


Thats sound great! But... How do I do to make the Sun Java 6 Web-plugin to work in Firefox? I don't really like the icedtea-gcjwebplugin, since Java layouts doesn't look 100% the same as with Sun.

---

### Post by OldGaf on 2008-04-26
So what is the word on nVidia drivers..... manual, repo, envy......?

---

### Post by old_geekster on 2008-04-26
> **OldGaf said:**
> So what is the word on nVidia drivers..... manual, repo, envy......?

I am using a XFX 7900GTX video card (See my sig.).  Envyng is the version that works with Hardy.  I installed 169.12 drivers.  There is even a .deb version, for those faint of heart, on Alberto's website.  It is working perfectly.  Compiz has never worked this good on any other Ubuntu version.  I have been using it since Edgy.

---

### Post by kutjara on 2008-04-26
I'm running Hardy 64 on my HP Pavilion laptop, and it's great. My desktop is Gnome, however, so that may have something to do with it.

I tried Kubuntu Hardy 64 during beta and wasn't all that impressed. Some of that was due to the fact that I'm more familiar with Gnome menus and layout, but a lot had to do with the fact that KDE 4 really isn't that polished yet. Setting up the desktop so it looked the way I liked took a lot of messing around. The menubar applets actively seemed to be fighting me half the time.

Now, I know KDE 4 is an extensive re-engineering of KDE and is intended to be a solid foundation for great things to come. For that reason, I eagerly await the upcoming releases of the desktop. For now, however, a bit too much of the "scaffolding" is showing for it to become my preferred work environment.

---

### Post by Wynne G Oldman on 2008-04-26
> **OldGaf said:**
> So what is the word on nVidia drivers..... manual, repo, envy......?Nvidia drivers ain't a problem. After you've installed Hardy 64, after a short time you will see the "Hardware Drivers" icon pop up in the top panel. Just click on it and enable the proprietry Nvidia driver and reboot and your 3D driver is installed. You can also install envy from the repo's if you really want to, if you enable the 2 x that are unchecked by default (but I find that there's no real need). My top tip is to go to Synaptic and install "Ubuntu Restricted Extras" then go to the Medibuntu website and follow the instructions carefully to the bottom of the page, cutting and pasting the commands in to Terminal. This will give you everything you need to enable Ubuntu to use Flash, play (and copy) encrypted DVD's, rip to MP3 with Sound Juicer etc.

---

### Post by OldGaf on 2008-04-26
> **Wynne G Oldman said:**
> Nvidia drivers ain't a problem. After you've installed Hardy 64, after a short time you will see the "Hardware Drivers" icon pop up in the top panel. Just click on it and enable the proprietry Nvidia driver and reboot and your 3D driver is installed. You can also install envy from the repo's if you really want to, if you enable the 2 x that are unchecked by default (but I find that there's no real need). My top tip is to go to Synaptic and install "Ubuntu Restricted Extras" then go to the Medibuntu website and follow the instructions carefully to the bottom of the page, cutting and pasting the commands in to Terminal. This will give you everything you need to enable Ubuntu to use Flash, play (and copy) encrypted DVD's, rip to MP3 with Sound Juicer etc.

Sounds good.... from an OldGaf to an Oldman....... thank you!

---

### Post by OldGaf on 2008-04-26
Is there any diff. between the envy and repo drivers for nVidia?

---

### Post by Milleman on 2008-04-26
> **hodge24 said:**
> With regards to Java, I have the 64 bit JRE installed (from Sun's website), and I'm using it to run 64 Bit Eclipse IDE with no problems at all.

Is that the 64 bit Java package? If so, the webplugin isn't included. Actually, I find it rather strange that Sun yet haven't made a 64 bit version of the Java Web Plugin.

Anyone here that had any luck with installing the 32 bit Sun Java 6 Package that INCLUDES a Web Plugin, together with the 64 bit Firefox 3...?

Also... I seem to be having problems with Hibernate on the 64 bit 8.04 Hardy. Well, it didn't work on the previous versions either.

My Nvidia 8600GT worked like a charm without any particular work. Just enabled the Restricted Drivers when the yellow balloon pops up, reboot and done!

---

### Post by donovan1983 on 2008-04-27
The 64-bit version of Kubuntu seems to work just fine. The only exception is flaky Atheros wireless network adapter drivers that are completely useless, as opposed to the 32-bit version which sometimes worked (although often not). No big deal since I just have an ethernet cable going to my iBook which is connected to my wireless network. After installing the kubuntu-restricted-extras package I had working Flash (haven't tested Java) in Konquerer. The NVIDIA drivers installed just fine from the Restricted Drivers Manager app.

While the 64-bit version of Windows Vista is noticably slower than the 32-bit version, I can't say I notice any performance difference between the 64-bit and 32-bit versions of Ubuntu at least for normal desktop use. I just figure I might as well run an OS that more fully takes advantage of my hardware.

---

### Post by edantes on 2008-04-27
In case anyone needs further assurance, I have been running Ubuntu AMD-64 starting with Gutsy.  Just finished a very successful transition to Hardy with a fresh install.  I had two small problems:

1. Restricted ATI driver for my IGP (X1200) was not offered automatically.  However, installing fglrx driver from the repositories was painless and worked perfectly.  In the Ubuntu partner repository they currently has Catalysis 8.3.  There is a newer version (8.4) recently available from AMD/ATI, but the creation of the .deb files failed here.

2. GoogleEarth 4.3 installed from the Medibuntu missed a dependency for package lib32nss-mdns.  It works after I manually installed the package.  Folk at Medibuntu are fixing this anyway.

Everything else went swimmingly so far.  Flash for Firefox, codecs, Java 6, Acrobat reader, Atheros wifi.  Even the 64bit Java plugin worked for all applets I tried up to now. Not the NONEXISTENT 64bit plugin from Sun (shame, shame, shame!!!), of course.

There was a marked improvement since my Feisty installation, which needed tweaking for some 32-bit apps to work.  My humble congratulation to all the people that built the necessary 64bit packages from 32bit apps in Medibuntu.

64bit will be mainstream soon because memory above 3G and Ubuntu is ready.

---

### Post by mynamesforrest on 2008-04-27
8.04 64bit here.  Running Virtual box just fine, although VB only supports 32bit OS's.

It's solid, it's stable and it's the linux release that has finally persuaded me to ditch Windows as my primary OS.

---

### Post by samwyse on 2008-04-27
My bank requires the Sun Java plugin, so I run Mepis on Virtualbox for that. It's not often I need it, so I don't really care. The rest works fine.

---

### Post by owenll on 2008-04-27
Everything works fine here on Hardy 64x. Problems with plugins etc with older versions seem to have been solved by the developers. I just upgraded when Hardy was Beta and found that everything worked. Still running well. :)

---

### Post by SnakeHips on 2008-04-27
Xubuntu 8.04
Linux desk 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
nvidia driver 169.12 from repos

No probs to speak of with java or flash in FF3 added from repos

Wine seems to give me minor nags at the mo ,still looking into it.

All in all the transition from 32bit to 64bit proved pretty uneventful for me.

---

### Post by OldGaf on 2008-04-27
Well..... have had it installed for about 24 hours now (though I work evenings so not too much time on it yet) and I have hit my first (and old) problem..... when the system is idle, xorg starts sucking up the cpu. I have not let it go long enough to hang the system yet, but I left it running with top running when I left for work. I will call home in an hour or so to see if it hung.

Meanwhile, has there ever been a definitive fix for this problem? This is the reason I left Kubuntu and went to Debian.

---

### Post by jespdj on 2008-04-28
> **OldGaf said:**
> So, my question is.... is 64 bit K/Ubuntu realy ready... as in I don't need to tweak this, that and the other thing to make it work?

Are there any applications that I will not be able to use.... VirtualBox for example is a must....

What about KDE4 and nVidia drivers?

Java, flash....... etc
Is 64-bit Ubuntu ready for mainstream? If you ask me, **yes it is**, with Hardy even more so than with any previous version.

I'm running 64-bit Hardy on my laptop and it works great. Everything works out-of-the-box and only minor tweaking was necessary. VirtualBox runs on a 64-bit host OS without any problems. (It does, however, only support 32-bit host OSes at the moment, as far as I know).

I don't know anything about KDE4 because I use GNOME.

nVidia drivers are the same as in 32-bit Ubuntu. In 64-bit Hardy, installing Flash is just as easy as in 32-bit Hardy:
```
sudo apt-get flashplugin-nonfree
```
This will automatically install nspluginwrapper and other stuff to make 32-bit Adobe Flash work in 64-bit Firefox.

---

### Post by Laibcoms on 2008-04-28
Using Ubuntu64 myself.  As others have said, less problems with 8.04 than previous Ubuntu64 releases.  It's only getting better and better!!

---

### Post by Kilz on 2008-04-28
The java issue is the main concern for a lot of 64bit users. But there are options
OpenJDK , which is (I think) based on icedtea is not sun java. It is avilable for the 64bit browser with the icedtea-gcjwebplugin. Its good and works on a lot of sites. For a lot of people this is a solution.
But if icedtea-gcjwebplugin doesnt work for you there are other options. Some banks require Sun Java. In that case you can install [a 32bit firefox/java/flash setup in a few minutes.]("http://ubuntuforums.org/showthread.php?p=1174435") This gives the best of both worlds, 64bit power when you need it 99% of the time. Then the browser for the few sites that you need compatibility for.

---

### Post by stmiller on 2008-04-28
Yes 64bit works great! I've been a 64bit Linux user starting with the first Mandrake 64bit version back in the day....

Currently using Kubuntu KDE4 8.04 64bit and it's great.

---

### Post by jespdj on 2008-04-29
> **Kilz said:**
> The java issue is the main concern for a lot of 64bit users. But there are options
OpenJDK , which is (I think) based on icedtea is not sun java. It is avilable for the 64bit browser with the icedtea-gcjwebplugin. Its good and works on a lot of sites. For a lot of people this is a solution.
[OpenJDK](http://openjdk.java.net/) *is* Sun Java, with the last proprietary parts replaced by open source parts. It's actually the other way around; [IcedTea](http://en.wikipedia.org/wiki/IcedTea) is based on OpenJDK.

The problem with Sun Java is that there isn't a 64-bit Java plug-in included. OpenJDK does contain a 64-bit Java plug-in, and it works mostly, but I've also encountered some websites where it doesn't work (properly).

---

### Post by Milleman on 2008-04-29
> **Kilz said:**
> The java issue is the main concern for a lot of 64bit users. But there are options
OpenJDK , which is (I think) based on icedtea is not sun java. It is avilable for the 64bit browser with the icedtea-gcjwebplugin. Its good and works on a lot of sites. For a lot of people this is a solution.
But if icedtea-gcjwebplugin doesnt work for you there are other options. Some banks require Sun Java. In that case you can install [a 32bit firefox/java/flash setup in a few minutes.]("http://ubuntuforums.org/showthread.php?p=1174435") This gives the best of both worlds, 64bit power when you need it 99% of the time. Then the browser for the few sites that you need compatibility for.

Hmm... That script is only for Firefox 2. Hardy is running Firefox 3 though.
Is there any info/rumors around from Sun, telling when they will release a 64 bit Java Web plugin?
Anyone? :)

---

### Post by Kilz on 2008-04-29
> **Milleman said:**
> Hmm... That script is only for Firefox 2. Hardy is running Firefox 3 though.
Is there any info/rumors around from Sun, telling when they will release a 64 bit Java Web plugin?
Anyone? :)

Are you suggesting that you run so many sites that require Sun java and you must have Firefox 3 (still in development). That no other browser will do? If so , I invite you to dig right in and help! Create a 32bit firefox 3 package that blends in, doesnt crash, finds its plugins, and then host it for everyone.  :D

---

### Post by Milleman on 2008-04-29
> **Kilz said:**
> Are you suggesting that you run so many sites that require Sun java and you must have Firefox 3 (still in development). That no other browser will do? If so , I invite you to dig right in and help! Create a 32bit firefox 3 package that blends in, doesnt crash, finds its plugins, and then host it for everyone.  :D

:D Well... I use Java applications. The layout doesn't exactly look the same in Icetea, as it do with the Sun Java Plugin. And Firefox? Being spoiled with v3, it feels little bit as step backward to use v2 again. But... You're probably right. Better to use a tested version. Your tribute is great. Until Sun releases the 64 bit Web Plugin, that's the way to go. :) 

Anyway... Like Microsoft Steve Ballmer recently announced:
-Vista is a work in progress. If people wants XP, we'll give them XP!
:lolflag:

Cheers mate!

---

### Post by OldGaf on 2008-05-30
Well.... I started this thread just over a month ago now so time for an update.

So far, so good. I moved from FF3 back to FF2-32 to get java working. I finally had to get rid of my beloved SuperKaramba as it causes my system to hang (this is NOT just a Hardy / 64 bit issue). I have yet to install Vbox (will tomorrow I think) but other then that it is going well.

I must say tho, that I do not see much of a speed improvement, but I did change OS's at the same time so don't have a good perspective.

In any event, I am giving 64 bit Kubuntu the thumbs up!

And what a nice way to spend my 200th post!

---

### Post by Sef on 2008-05-30
> Is there any info/rumors around from Sun, telling when they will release a 64 bit Java Web plugin?
Anyone?

A 64-bit java is coming.  Click on the Java on 64-Bit Systems link below for some more information.

---

