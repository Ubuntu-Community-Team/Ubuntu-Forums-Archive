---
title: "Flash on amd64-a solution in sight.."
date: 2005-09-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by kb_ganesh on 2005-09-09
Contrary to popular belief, flash on AMD64 is not unimplemented... No, gplflash wasn't updated.
In the shadows, another plugin was developped:
[http://www.schleef.org/swfdec/](http://www.schleef.org/swfdec/)

It executes most of content on the web and is very stable.
YES. :D

--courtesy lokee..taken from lq.org ( [exact post](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=294498) )

---

### Post by hod139 on 2005-09-09
Nice find, and thanks for posting.

---

### Post by Corbelius on 2005-09-09
[QUOTE=kb_ganesh]Contrary to popular belief, flash on AMD64 is not unimplemented... No, gplflash wasn't updated.
In the shadows, another plugin was developped:
[http://www.schleef.org/swfdec/](http://www.schleef.org/swfdec/)

It executes most of content on the web and is very stable.
YES. :D

--courtesy lokee..taken from lq.org ( [exact post](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=294498) )[/QUOTE]

It's better GPLFlash, the animation work, with swfdec no, example: [http://bretonnia.m4d.it/](http://bretonnia.m4d.it/)

---

### Post by thundertoad on 2005-09-09
Um, sort of a stupid question here
but how do you install this ... I wasnt quite successfull in figuring out how to install it

any wiki's . how to's or instructions would be much appreciated.

thanks.
(great find btw)
ThunderToad

---

### Post by kb_ganesh on 2005-09-09
i too havent been successful yet in installing yet..just wanted to share the link..i have successfully run make and make install but not able to open any flash file yet..still they open in totem which complains about codecs..

and regarding the plugin for FF, the readme file says that i have to modify the MOZ_PLUGIN_PATH environment variable which i am not sure how to do..if someone can shed light on this, i would be very thankful..

---

### Post by dmn_clown on 2005-09-09
The easiest way for an Ubuntu user to install swfdec would be 

> sudo apt-get install libswfdec 

For updated packages try the breezy repositories.

To compile the plugin from source you need the mozilla development headers installed.  (Available in the repositories).

---

### Post by nrayever on 2005-09-09
damn!!! this sounds good!! let's give a shot!! any question i will reply here!! thanks for this plugin!!

---

### Post by h17m4n on 2005-09-09
If you got the time and space, chroot 32-bit Firefox+Flash.

---

### Post by nrayever on 2005-09-10
[QUOTE=h17m4n]If you got the time and space, chroot 32-bit Firefox+Flash.[/QUOTE]

i tried it once, and i just make a mess on my os!! maybe i'm too stupid for chroot 32-bit. was that howto updated or something like that??

nrayever

---

### Post by h17m4n on 2005-09-10
It really wasn't the hardest thing I've got done and I've been using this for less than 2 weeks. The hardest thing so far is trying to install IE6 on chroot(and setting up ndiswrapper too).

---

### Post by nrayever on 2005-09-10
give a try with crossover, work really fine!! and maybe in some step of the howto i got lost..... but it didn't worked for me. :-? :-s

---

### Post by kb_ganesh on 2005-09-10
[QUOTE=dmn_clown]The easiest way for an Ubuntu user to install swfdec would be 

sudo apt-get install swfdec

For updated packages try the breezy repositories.

To compile the plugin from source you need the mozilla development headers installed.  (Available in the repositories).[/QUOTE]
 i dint know that..tried it just now..as always, it went off well..

but still, FF is not opening flash files..what must i do??

---

### Post by NickB on 2005-09-11
[QUOTE=dmn_clown]To compile the plugin from source you need the mozilla development headers installed.  (Available in the repositories).[/QUOTE]

Unfortunately that would require a nearly complete upgrade to breezy of X and everything that depends on it, since the development packages do not seem to be available in hoary.

Nick

---

### Post by Ribs on 2005-09-12
[QUOTE=kb_ganesh]FF is not opening flash files..what must i do??[/QUOTE]
Hi,

You've only got the library installed there. You need to grab the plugin, which in a seperate package. Doing this in should work (only tested in Breezy! I don't know about Hoary):
```
apt-get install swf-player
```
Remember to quit and restart firefox before viewing flash pages.

P.S. Although this software isn't finished yet, it's showing potential. Don't forget to e-mail the author (in this case; ds at schleef dot org) and tell him how much you like this software, and would love to see it grow. Trust me, a little love can go a long way, it takes you two minutes, and will make the developers day, which is always a good thing, right? :smile:

---

### Post by kb_ganesh on 2005-09-15
thanks for the help!! (sorry for being so late)

EDIT:
i got it installed from synaptic..and no more does any website show the "plugin missing" message..

but till now, i havent been able to view a single flash file on any website i have been to so far..can someone who is using this plugin tell me a website where the plugin has worked for them so that i can check it out?

---

### Post by DancingSun on 2005-09-16
[QUOTE=kb_ganesh]thanks for the help!! (sorry for being so late)

EDIT:
i got it installed from synaptic..and no more does any website show the "plugin missing" message..

but till now, i havent been able to view a single flash file on any website i have been to so far..can someone who is using this plugin tell me a website where the plugin has worked for them so that i can check it out?[/QUOTE]
If you see an ad banner that you cannot right click on, it's probably a flash-based banner.  But I've noticed some banners are stuck at the first "frame", they don't get animated.  Clicking on these ad banners also don't take you to their websites.  As well, this flash plug-in does not play any of the recorded flash "tutorials" that I found.

---

### Post by mblakele on 2007-04-20
If you really want to try swfdec-0.4.3, but can't compile it, you can try the debian experimental packages. Each page has a link to the amd64 debs.

[LIST]
[*][http://packages.debian.org/unstable/libs/libswfdec0.4]("http://packages.debian.org/unstable/libs/libswfdec0.4")
[*][http://packages.debian.org/unstable/utils/swfdec-mozilla]("http://packages.debian.org/unstable/utils/swfdec-mozilla")
[/LIST]

**NOTE**:This is somewhat risky, since the debian packages may not interact well with the ubuntu packages. For example, I already had the ubuntu universe build of libswfdec0.3 installed, and had to remove it before video would work.

---

### Post by BIGtrouble77 on 2007-04-20
mblakele, why would you bring to life a 2 year old thread?  It's not relevant anymore.

---

