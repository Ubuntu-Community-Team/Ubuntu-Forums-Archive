---
title: "flash for 64"
date: 2006-07-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by loserboy on 2006-07-09
I know theres threads about this already, but thats the problem.... theres like 5 dif ways people are saying to get flash to work on 64, so im just asking what is the *best* way to do it?

also i have automatix installed everything it has but i still can load alot of flash

---

### Post by Teroedni on 2006-07-09
Well for my use the simplest was to do this
[http://doc.gwos.org/index.php/AMD64_Firefox32](http://doc.gwos.org/index.php/AMD64_Firefox32)

---

### Post by a-musing amazon on 2006-07-09
> **loserboy said:**
> I know theres threads about this already, but thats the problem.... theres like 5 dif ways people are saying to get flash to work on 64, so im just asking what is the *best* way to do it?

also i have automatix installed everything it has but i still can load alot of flash

Which way you do it depends a bit on what you want to do and to achieve.

I suspect that Automatix wont work because it assume that you are using a 32-bit installation.

1) Flash Player itself is a closed-source application and it sonly avaialble in 32-bit. Its also only Flash 7 whereas the Windows versions are more up to date. There is no way to get a Flash 8 or 9 player working except perhaps through wine (running the Windows version). However Flash 7 does still work for most sites, e.g. on my friends myspace movies.

2) There are a couple of open-source applications/projects out there that have been compiled in 64-bit Linux. If you are fanatical about open-source then you can use these. Unfortunately they are not as compatible as the official flash-player and can at worst crash or freeze your Browser on some flash sites, in other instances they just fail to work properly.

3) You can use a 32-bit browser (Firefox, Epiphany, etc.). This is then compatible with any 32-bit plugin. You can't install the 32-bit browser through Synaptic or Gdebi if oyu are running 64-bit, you will have to force-install on the command line. 

4) You can use nspluginwrapper. This is an app that allows a 32-bit plugin such as Flash Player to run in your standard-issue 64-bit browser. With the latest versions of nspluginwraper this seems to work OK (its what I use). However the instructions with nspluginwrapper are not as clear as they might be for Dapper, however there is a useful thread on doing it this way on the forum.

---

### Post by jvictor on 2006-07-09
> I suspect that Automatix wont work because it assume that you are using a 32-bit installation

The 64 bit automatix installs some workaround.. but its not as seamless as the original flash

Edit
----
Can try **flock** from [www.flock.com](www.flock.com)

---

### Post by Endow on 2006-07-09
Man I had the exact same problem and there is no simpler solution that installing SwiftFox.

Not only did it solve my falhs problem (you just need to install flash like your noramally would after installing swiftfox) but it also makes for a faster browser.

SwiftFox all the way:)

---

### Post by Kilz on 2006-07-09
> **Teroedni said:**
> Well for my use the simplest was to do this
[http://doc.gwos.org/index.php/AMD64_Firefox32](http://doc.gwos.org/index.php/AMD64_Firefox32)

I have a [updated howto]("http://www.ubuntuforums.org/showthread.php?p=1174435") you might want to look at. It has a few fixes that are not in that version. It also has a few more plugins.

---

### Post by John.Michael.Kane on 2006-07-09
Isn't Gnash a viable option for those who need to use flash with out the use of 32bit-lib's?

---

### Post by Kilz on 2006-07-09
> **SD-Plissken said:**
> Isn't Gnash a viable option for those who need to use flash with out the use of 32bit-lib's?
[From what I have read]("http://software.newsforge.com/article.pl?sid=06/06/20/1855200&from=rss") gnash is available, but still needs some work. There are a few howto's out (I have one) that alow people to use the 32bit mcaromedia plugin. Id love to be able to kiss macromedia goodby, as soon as gnash is close, my howto will use it.

---

### Post by loserboy on 2006-07-09
ok kilz im goona giveyours a shot and see what happens, thanks

Edit: well that seemed to work, thanks alot, can i just use add/remove to get rid of firefox64?

---

### Post by loserboy on 2006-07-09
one thing i didnt understand   > It will ask you to close all browsers, and then what location it wants you to install to. Type in "/usr/local/firefox32/".

it never gave me this option so i installed to default (.mozilla i think)

---

### Post by Kilz on 2006-07-09
> **loserboy said:**
> one thing i didnt understand   

it never gave me this option so i installed to default (.mozilla i think)

```
sudo linux32 ./install_flash_player_7_linux/flashplayer-installer
```
Sorry forgot the sudo

---

### Post by loserboy on 2006-07-10
oh heh i guess i should have noticed that..... i guess i was in copy and paste mode  lol

but uh do i need to reinstall...everything seems to work...except maybe it overwrote some firefox64?

---

### Post by Kilz on 2006-07-10
> **loserboy said:**
> oh heh i guess i should have noticed that..... i guess i was in copy and paste mode  lol

but uh do i need to reinstall...everything seems to work...except maybe it overwrote some firefox64?

Nope, firefox64 should still be installed. Unless you change the launchers in the application menu with the alacarte menu editor you can launch it there. Thats why the howto has you create a launcher.
Did you try the mplayer plugin install?

---

### Post by An3Azz on 2006-07-10
> **Endow said:**
> Man I had the exact same problem and there is no simpler solution that installing SwiftFox.

Not only did it solve my falhs problem (you just need to install flash like your noramally would after installing swiftfox) but it also makes for a faster browser.

SwiftFox all the way:)

What you are saying is, that if I install SwiftFox I can use normal 32-bit flash without any troubles? Just install them both, as if I were installing on a 32bit system?

---

### Post by Endow on 2006-07-10
Exactly.Trust me you will have no problems.I had the same issue and it was solved:)


After [http://getswiftfox.com/](http://getswiftfox.com/)

go here ... [http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

---

### Post by An3Azz on 2006-07-10
> **Endow said:**
> Exactly.Trust me you will have no problems.I had the same issue and it was solved:)


After [http://getswiftfox.com/](http://getswiftfox.com/)

go here ... [http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

n00bquestion number 1, how do I install it? Swiftfox, I know how to install flash

EDIT, nevermind, found a script :D Problem solved for now

---

### Post by loserboy on 2006-07-10
I haven't done the java or the mplayer yet, i'll do that tonight after work

---

### Post by An3Azz on 2006-07-10
F**in Aye!!! IT works, god damn man I'll defenetly buy you a beer anytime.

---

### Post by Endow on 2006-07-10
You can thank me by spreading the word....:D ...there are thousands of 64bit users out there doing all sort of complicated things when they could make things a lot more simple....oh the righteousness!!!!!\\:D/ :lol:

---

### Post by Kilz on 2006-07-10
> **Endow said:**
> You can thank me by spreading the word....:D ...there are thousands of 64bit users out there doing all sort of complicated things when they could make things a lot more simple....oh the righteousness!!!!!\\:D/ :lol:
I like swiftfox, and I'm seriously concidering using it as a base for my howto. It has good support for flash. But some of the other plugins are just as hard to setup

---

### Post by Endow on 2006-07-10
Such as...?Well it's true I don't use that much plugins myself - as long as I can stream audio/viedo wherever I go and get to see 99% of the pages as they were first invisioned I'm ok.

---

### Post by Kilz on 2006-07-10
> **Endow said:**
> Such as...?Well it's true I don't use that much plugins myself - as long as I can stream audio/viedo wherever I go and get to see 99% of the pages as they were first invisioned I'm ok.
I downloaded swiftfox for a test. I started it. [Went to this page (java)]("http://www.java.com/en/download/installed.jsp?detect=jre&try=1"), [this one (flash)]("http://today.reuters.com/tv/videoChannel.aspx?storyId=54fe3cf8857963d224380b11125e31a7c55f9756") and [this one (mplayer)]("http://www.apple.com/trailers/independent/conversationswithotherwomen/trailer/").
Not one of them shows the plugin installed. It tries to auto download it, says it failed, and gives a manual plugin link. Isnt it suposed to be automatic?
If not, I already have the plugins installed.  But maybe doesnt detect them?

---

### Post by An3Azz on 2006-07-10
> **Kilz said:**
> I downloaded swiftfox for a test. I started it. [Went to this page (java)]("http://www.java.com/en/download/installed.jsp?detect=jre&try=1"), [this one (flash)]("http://today.reuters.com/tv/videoChannel.aspx?storyId=54fe3cf8857963d224380b11125e31a7c55f9756") and [this one (mplayer)]("http://www.apple.com/trailers/independent/conversationswithotherwomen/trailer/").
Not one of them shows the plugin installed. It tries to auto download it, says it failed, and gives a manual plugin link. Isnt it suposed to be automatic?
If not, I already have the plugins installed.  But maybe doesnt detect them?

Was automatic for me, if you start swiftfox with the swiftfox command, instead of run-mozilla.sh or whatever it's called :D

---

### Post by Endow on 2006-07-10
> **Kilz said:**
> I downloaded swiftfox for a test. I started it. [Went to this page (java)]("http://www.java.com/en/download/installed.jsp?detect=jre&try=1"), [this one (flash)]("http://today.reuters.com/tv/videoChannel.aspx?storyId=54fe3cf8857963d224380b11125e31a7c55f9756") and [this one (mplayer)]("http://www.apple.com/trailers/independent/conversationswithotherwomen/trailer/").
Not one of them shows the plugin installed. It tries to auto download it, says it failed, and gives a manual plugin link. Isnt it suposed to be automatic?
If not, I already have the plugins installed.  But maybe doesnt detect them?

Hmm...I remember that with Flash at least I only installed swiftfox and then went to the flash site and installed the linux version...

---

### Post by Kilz on 2006-07-10
> **Endow said:**
> Hmm...I remember that with Flash at least I only installed swiftfox and then went to the flash site and installed the linux version...
Thanks, at least I know it isnt something broken, or a bad download. Swiftfox just it isnt automatic on all plugins.

---

### Post by joakim2 on 2006-07-14
> **Kilz said:**
> I downloaded swiftfox for a test. I started it. [Went to this page (java)]("http://www.java.com/en/download/installed.jsp?detect=jre&try=1"), [this one (flash)]("http://today.reuters.com/tv/videoChannel.aspx?storyId=54fe3cf8857963d224380b11125e31a7c55f9756") and [this one (mplayer)]("http://www.apple.com/trailers/independent/conversationswithotherwomen/trailer/").
Not one of them shows the plugin installed. It tries to auto download it, says it failed, and gives a manual plugin link. Isnt it suposed to be automatic?
If not, I already have the plugins installed.  But maybe doesnt detect them?

FYI, I found what was missing. You need to create ~/.mozilla/plugins manually. After that all the plugins installed from the browser for me. Woohoo.

---

### Post by loserboy on 2006-07-14
Kilz!..  you mean I followed your howto to install 32bit firefox and now you're gonna switch to swiftfox?   you traitor....   :)  jk

lemme know what works better, if swift then maybe you can help me undo the firefox and install swift

---

### Post by Kilz on 2006-07-14
> **loserboy said:**
> Kilz!..  you mean I followed your howto to install 32bit firefox and now you're gonna switch to swiftfox?   you traitor....   :)  jk

lemme know what works better, if swift then maybe you can help me undo the firefox and install swift
No, I personaly havent switched. But Im considering adding instructions and/or scripts to install it. Swiftfox is just an optimised Firefox. Im thinking it may be hard to write the scripts though considering the many versions it has (one for each of a dozen processors).
I am also looking at the speed diffrences between the two. I didnt see that big a difference if any between the latest version of swiftfox and firefox 1.5.0.4. Some people use it because it has easy plugin setup. But with the new install scripts I have, its a matter of downloading it and entering 2 commands in a terminal to install firefox.

---

### Post by loserboy on 2006-07-14
oh i see.... well keep up the good work.
my prblem right now is that I'm having to be very selective about what I install because i'm running out of space till i either remove windows or buy another hd....

---

### Post by hajk on 2006-07-16
As an alternative to installing 32-bit Firefox, you might also consider installing 32-bit Opera 9 (you need the i386 deb-package with *statically linked libs* on the Opera download site). Afterwards, you can just download and the 32-bit Flash player from Macromedia and install it to the /usr/lib/opera/plugins directory. I've done that myself, and it works like a charm. 

Mind you, SWF/mozilla-plugin also runs reasonably well on my 64-bit Firefox, sufficient at least to do my banking online with the bank using flash on their login page (haven't experienced any strange transactions yet ;) ).

---

### Post by modestmelody on 2006-07-16
I have had flash working for quite sometime using Swifterfox and then today suddenly I've lost the ability to do so.  I am trying to install the official installer, since I am using a 32bit driver, but it keeps coming back that my platform isn't supported.  HOw can I force the install?  Or, better, why would I suddenly lose flash?  I downloaded swiftfox again and it still doesn't work.

---

### Post by opusmortis on 2006-08-03
I hope this isn't too weird of a spot to place this question... but I did the howto on mplayer and when I went to check to see if everything was working after installing it, it didn't. When I try and play any of the trailers, it buffers to 99% and stops there. Any clue how I can fix this?

btw. Thanks for all the howtos Kilz :-D All the others are working great!

---

### Post by Kilz on 2006-08-03
> **opusmortis said:**
> I hope this isn't too weird of a spot to place this question... but I did the howto on mplayer and when I went to check to see if everything was working after installing it, it didn't. When I try and play any of the trailers, it buffers to 99% and stops there. Any clue how I can fix this?

btw. Thanks for all the howtos Kilz :-D All the others are working great!

My sugestion is to make sure you have 32bit mplayer , and codecs installed. [There is a howto for that]("http://www.ubuntuforums.org/showthread.php?t=188974"). If that dosent work you might want to try the complete install script that installes firefox,flash,java, and mplayer to make sure everything is setup right.

---

