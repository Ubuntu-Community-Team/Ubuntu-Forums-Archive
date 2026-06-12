---
title: "[SOLVED] How do you make runescape run in firefox 64?"
date: 2007-07-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-07-04
Okay - I installed 64 bit ubuntu on the kids computer.  I installed the flash plug-in. It works.  I installed sunjava for 64bit.  I installed the blackdawn 1.4 jre from the synaptic engine.

It loads the pages, starts to run, the BAM! the browser closes for no reason that I know of.  

How do I make this work in the 64bit browser?

---

### Post by ubuntu.daemon on 2007-07-04
pssst sorry to tell you but there is no flash for 64bit, there aer workarounds but it takes a bit, for your kids oh btw you only need one java, id go with the 
sun-jre6-bin
sun-jre6-plugin
sun-jre6-
you can uninstall the blackdown
oh sorry short solution
install a 32bit firefox, reinstall java and the flash-nonfree from synaptic
and should work fine:popcorn:

---

### Post by crjackson on 2007-07-04
> **ubuntu.daemon said:**
> pssst sorry to tell you but there is no flash for 64bit, there aer workarounds but it takes a bit, for your kids oh btw you only need one java, id go with the 
sun-jre6-bin
sun-jre6-plugin
sun-jre6-
you can uninstall the blackdown
oh sorry short solution
install a 32bit firefox, reinstall java and the flash-nonfree from synaptic
and should work fine:popcorn:

Well, flash isn't the problem.  I used a script made by Kilz and it works perfectly.  Java is the problem.  I'm sure there is a solution somewhere.  sun-jre was installed first but didn't seem to do the trick.

---

### Post by ubuntu.daemon on 2007-07-04
you did make sure to install the java after you installed the browser right??  uninstall all the java then try just the jre-java6 you need the jre-java6-plugin for browsers so make sure you get at least that

---

### Post by mig5 on 2007-07-05
> **crjackson said:**
> I installed sunjava for 64bit.  I installed the blackdawn 1.4 jre from the synaptic engine.

It loads the pages, starts to run, the BAM! the browser closes for no reason that I know of.  

On 32bit feisty blackdown java and sun java seem to conflict.  This could also be a problem on 64 bit.  Make sure that you don't have both of them installed at the same time.  Once you uninstall one, reinstall the other, just to make sure.
As a side note I'd like to say that for me blackdown java is slower, but it gives me sound in runescape, whereas sun java is faster but no sound.
Here is a howto to install 32 bit firefox and 32 bit plugins on AMD 64: [http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)

---

### Post by crjackson on 2007-07-05
> **mig5 said:**
> On 32bit feisty blackdown java and sun java seem to conflict.  This could also be a problem on 64 bit.  Make sure that you don't have both of them installed at the same time.  Once you uninstall one, reinstall the other, just to make sure.
As a side note I'd like to say that for me blackdown java is slower, but it gives me sound in runescape, whereas sun java is faster but no sound.
Here is a howto to install 32 bit firefox and 32 bit plugins on AMD 64: [http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)

I removed the blackdown java and re-installed the sun java.  Of course this only took me back to my original situation.

I installed 32bit swift fox and all the plugins and it plays runescape fine.  I was just hoping for a solution that wouldn't require an install of the 32bit browser.  I guess it's just not possible.  Since 64bin sun java is installed, I can't understand why it doesn't work, unless the 64bit java is broken.

---

### Post by mig5 on 2007-07-06
I would suggest that you try Opera web browser, as it handles java differently, without a plugin, instead you have to tell it where java is installed.  BUT, it's 32 bit.

You could try 64 bit konqueror, according to here: [http://lists.slug.org.au/archives/slug/2007/06/msg00096.html](http://lists.slug.org.au/archives/slug/2007/06/msg00096.html) , it works with runescape, with 64 bit java.  Konqueror, like Opera, doesn't use a plugin for java.  However the Konqueror in the repositories depends on a lot of KDE stuff.  According to here: [http://ubuntuforums.org/showthread.php?t=195328](http://ubuntuforums.org/showthread.php?t=195328) , Konqueror does work OK on Ubuntu with Gnome.  If you are using Kubuntu then you should already have Konqueror installed.

You could also try Epiphany 64 bit web browser (specially designed for gnome).  However, it uses the mozilla libraries, so if Firefox crashes then it will probably do so to.

---

### Post by Kilz on 2007-07-06
> **mig5 said:**
> I would suggest that you try Opera web browser, as it handles java differently, without a plugin, instead you have to tell it where java is installed.  BUT, it's 32 bit.

You could try 64 bit konqueror, according to here: [http://lists.slug.org.au/archives/slug/2007/06/msg00096.html](http://lists.slug.org.au/archives/slug/2007/06/msg00096.html) , it works with runescape, with 64 bit java.  Konqueror, like Opera, doesn't use a plugin for java.  However the Konqueror in the repositories depends on a lot of KDE stuff.  According to here: [http://ubuntuforums.org/showthread.php?t=195328](http://ubuntuforums.org/showthread.php?t=195328) , Konqueror does work OK on Ubuntu with Gnome.  If you are using Kubuntu then you should already have Konqueror installed.

You could also try Epiphany 64 bit web browser (specially designed for gnome).  However, it uses the mozilla libraries, so if Firefox crashes then it will probably do so to.

If the browwser plugin is the jgc plugin then it is a security risk as it runs without a security manager, regardless of the browser that uses it. To my knowlage there is only that 64bit java plugin avilable.

---

### Post by crjackson on 2007-07-06
> **If the browwser plugin is the jgc plugin then it is a security risk as it runs without a security manager, regardless of the browser that uses it. To my knowlage there is only that 64bit java plugin avilable**

@kilz

what is the jgc plugin and where can I get it for testing?  I'm not concerned about the security risk for this computer right now, I would just like to see for myself if this would eliminate the java issue w/runescape.

---

### Post by mig5 on 2007-07-06
> **Kilz said:**
> If the browwser plugin is the jgc plugin then it is a security risk as it runs without a security manager, regardless of the browser that uses it. To my knowlage there is only that 64bit java plugin avilable.

Like I said Konqueror and Opera don't use a plugin, instead they ask for where java jre is installed, like this:

[CENTER][IMG]http://i16.tinypic.com/689jg9k.png[/IMG][/CENTER]

Is the security risk in the java install itself and not the plugin?

---

### Post by Tur Third on 2007-07-12
Hi, I now have Runescape running (with sound) on x86-64. However I think it is only working with 32 bit. I am on Ubunutu 6.06

I did the following:

I tried installing the package for Blackdown JRE 1.4 and Runescape works with firefox 1.5 but without sound.

I then installed  firefox 2.0 and Sun JRE 1.5 (following their instructions). This also worked (a bit slower logging in), but again no sound.

I then thought that the sound problem could be due to not having a music synthisiser on my sound card (most pc's don't) therefore I could not play midis. So I installed the pacakge for 'timidity++'.

The sound still did not work on both versions, but I could now play midis.

Finally I followed the instructions here, getting timidity++ to load up as a sound server on boot.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty/AddOnApplications#How_to_install_MIDI_sound_server_.28Timidity.2B.2B.29]("http://ubuntuguide.org/wiki/Ubuntu:Feisty/AddOnApplications#How_to_install_MIDI_sound_server_.28Timidity.2B.2B.29")

I rebooted and sound now works in both versions however the version with 1.4 crashes when I log in, however firefox 2.0 with 1.5 is fine. (I think that is the 32 bit version).

---

### Post by Tur Third on 2007-07-12
argh! just tried to play it, and the sound has stopped working. Also I note I have JRE 1.6. I will see whether I can get it working again....

---

### Post by crjackson on 2007-07-12
I installed the 32bit browser / plugins and that was it.  I gave up on 64bit browser w/Java

---

### Post by Tur Third on 2007-07-14
I am using 32 bit too, but with Firefox 2 it does not always work. It either all works or seems to either hang or there are very long lags when logging in. It might just be to do with when the runescape servers are busy. With Firefox 1.5 (installed with 6.06) the whole browser crashes when I log in! Sound also seems a bit hit and miss.

Haven't really tested playing the game, just logging in so far!

---

### Post by crjackson on 2007-07-14
> **Tur Third said:**
> I am using 32 bit too, but with Firefox 2 it does not always work. It either all works or seems to either hang or there are very long lags when logging in. It might just be to do with when the runescape servers are busy. With Firefox 1.5 (installed with 6.06) the whole browser crashes when I log in! Sound also seems a bit hit and miss.

Haven't really tested playing the game, just logging in so far!

It works every time here.

---

### Post by Tur Third on 2007-07-17
A summary of where I am with this now. I am wondering whether you need a more powerful pc to play this game. Think my cpu is only 2300. However this is not the case in windows.

Using Firefox 2 and Sun Java JRE1.6
======================
Neither installed using a package. Instead downloaded and installed per software websites.

Current Problems
==========
intermittant - high CPU usage
intermittant - Keyboard does not respond, or becomes very slow (no problems with mouse). 
intermittant - cursor keys scroll the firefox window rather than change the view.

With keyboard problems switching to another application and using the keyboard or typing something in the search field in firefox sometimes fixes the problem.

WorldMap usually does not open, and errors appear on Java console stating problems with memory stack. If map does open intermittant problems are made worse. It should be noted opening the map in windows can take a long time.

Music and sound affects are OK. 
Logging in seems ok now, previous problem was that keyboard intermittantly did not respond when logging in, strangely installing alsamixergui and unplugging USB webcam seemed to fix.

Taking out Firefox plugins, did not seem to have much affect.

I get the impression that it works but is just not that reliable.

---

### Post by mig5 on 2007-07-17
> **Tur Third said:**
> intermittant - high CPU usage

Firefox sends the CPU usage really high on my comp aswell when I start using runescape.  So does Opera.  Maybe swiftfox could lower the usage a bit, but I think its to do with the way firefox uses the plugin or a problem with the plugin/java install itself.  Seeing as all those browsers use the same engine (gecko), i doubt you will see much improvement swapping from one to the other.

---

### Post by jazz452 on 2008-01-07
Just do what your told and install konqueror browser it has always worked on 64 bit ubuntu.If i have no runescape then i have no ubuntu kids would not allow it

---

