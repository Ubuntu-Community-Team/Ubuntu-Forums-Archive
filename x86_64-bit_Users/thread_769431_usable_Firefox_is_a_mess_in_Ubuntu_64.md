---
title: "usable Firefox is a mess in Ubuntu 64"
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by gersoid on 2008-04-26
Why the hell can't we just have an official Ubuntu package that allows users who've installed amd64 to use firefox32 plus ALL the 32 bit plugins (flash, Sun java, acrobat...) in one go. Frankly it is a mess right now.

I know there are a couple of sites detailing how to set up 32 bit firefox, and associated 32 bit plugins, and I have followed them carefully (I've been running linux for 4 years now, am not a windows newbie); I got flash OK, but I still don't have working java applets in 8.04 although the identical setup with 7.10 worked OK. I want Sun java, it won't start apps properly; I have no idea why; now I'm looking at simply reinstalling the whole of Ubuntu (or maybe some other distro) in 32 bit. I simply don't have time to waste a day tracking down the problem. Seems disappointing, given that practically every Intel/AMD chip sold over the last 18 months, including the dual core in my Dell laptop, is 64 bit.

I'm not doing down the firefox32 install guides, its just that in my particular case they didn't work. Maybe I'm thick; maybe I mistyped. I don't feel I should have to be typing in "ln" commands in bash when trying to set up the most widely used plugins in the most widely used GPL browser, in a brand new distribution aimed at new-to-linux users. This was OK for Linux 4 years ago, it's terrible now. Having a proper package that sets this all up and checks it is simply better for all; it eliminates most of the uncertainty, certainly saves vast amounts of user time and aggravation. 

I am sure I will be shouted down by the 64 bit purists (I have read the ubuntu [bug]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/28479") list...) but ultimately a distribution where the most-used browser plugins seem not to work in many cases, and seem to be unsupported officially, will simply fly for the vast majority of new users, who will drift back to Vista (where despite our quibbling, most of this kind of stuff "just works") or to 32 bit distros. (I know Vista is 32 bit as well, before you all yell, I also know that ultimately the fault lies with Sun/Adobe who can't/won't recompile in 64 bit, but this is life, work around it....)

Folks, please just create a package that contains Firefox32, plus working flash, Sun Java, Java applets, Adobe reader (another flame war started I fear but it's simply more reliable than the GPL pdf viewers). These all exist as 32 bit packages, it would be good to get some official support. By all means make me click on a dialog box stating I am ok with non-free apps but make it simpler, please.

---

### Post by old_geekster on 2008-04-26
I am using FF3b5 and I have Sun Java working.  Try this "ia32-sun-java6-bin".  I also installed "ia32-libs".  This is the shared libraries for use on AMD64 and ia64 systems.  Both are in "Synaptic".  I have had no problems with any websites to date.

---

### Post by thekat on 2008-04-26
It is frustrating sometimes.. and I do this stuff for a living..


There are a lot of threads to install 32-bit apps on 64 bit , believe
me I went through this frustration on Gutsy-64 and decided that since
it had only 2 Gig of RAM - 32-bit was the way to go.. It has been
rock solid

Ubuntu 64 *has* come a long way even from Gutsy.. 
The new box my sig is new and Gutsy or 32bit Hardy won't run on it so my 
8 GIG of RAM is wasted.


For Flash
```

sudo apt-get install flashplugin-nonfree

```
(I test this on Youtube)

For Java plugin
```

sudo apt-get install  icedtea-gcjwebplugin

```
I use this site to test
[http://radar.weather.gov/radar.php?rid=tlx&product=N0R&overlay=11101111&loop=no]("http://radar.weather.gov/radar.php?rid=tlx&product=N0R&overlay=11101111&loop=no")
- Under the Reflectivity - Composite 
- Click on  Loop

the old Geezer is using Frostwire which does require 32-bit java
```

sudo apt-get install  ia32-sun-java6-bin 

```
to use the 32 bit java
```

sudo update-alternatives --config java

```
Chose the 32-bit java

Hang in there

tk

---

### Post by gersoid on 2008-04-26
Thanks for the prompt responses, folks. Unfortunately I'd done the ia32-sun-java6/ia32 thing already, to no avail. 

i did however install the icedtea java, and used the 

update-alternatives --config java

to switch to use it. I do now get the weather map to run in firefox32 (looks like its pissing down in oklahoma city!)....however I still cannot get it to load the java app I need (logitech/slimserver "softsqueeze" mp3 streamer client). This app runs fine on my wife's XP laptop (grrr) and on my previous 7.04 install so I suspect it needs Sun java.

As I've said, the Java fault may well be mine; a mistype somewhere when installing  manually using sudo commands, and you're stuffed for future as you can't easily undo.

The Flash has always worked fine on firefox32.

After all this, and although I am grateful for your time, doesn't this reinforce the requirement - WHY ISN'T THIS ALL PACKAGED ALREADY?

---

### Post by thekat on 2008-04-27
> **gersoid said:**
> 
After all this, and although I am grateful for your time, doesn't this reinforce the requirement - WHY ISN'T THIS ALL PACKAGED ALREADY?

You would think the developers would sure consider this option..

I tried Gutsy-64 but had some issues with Flash and Java...
There were (and still are) workarounds via a user posted script but
it sure would be nice if this *was* an option.. 

For the record, Hardy-64 is the best version IMHO so far as to what
I need it for.. 

I do a lot of support for different OS's like ClarkConnect, Ubuntu-Server and OpenBSD and Solaris.. so I built this box with the intention of doing most all my work in the virtual environment instead of having a bunch of PCs scattered all over my office.. :)

oops.. sorry went off topic.. :)

---

### Post by philinux on 2008-04-27
I'm running the default Hardy clean install on new pc, whatever that includes and it's running really well. Desktop effects cube. Not one crash FF or system.

Am I just lucky.

---

### Post by Julius on 2008-04-27
> **philinux said:**
> I'm running the default Hardy clean install on new pc, whatever that includes and it's running really well. Desktop effects cube. Not one crash FF or system.

Am I just lucky.

I haven't had any crashes, and overall I think the system is more responsive than all my other ubuntu installs (been using ubuntu since 2004), although to be honest this is a new computer and this is my first ubuntu install on this computer so I have nothing to compare with (on this specs, that is).

But sometimes the systems (especially firefox) slows down and it wont let me do anything, sometimes the window turns gray. It recovers just fine, but it is annoying.

---

