---
title: "Flash 10... shoot still broken?"
date: 2008-06-07
forum: x86 64-bit Users
---

### Post by Sir Rodness on 2008-06-07
Well...
I'm new to linux (decided to go x64) and I've been really enjoying it over the last few months. Fantastic fun messing with the interface and playing with compiz. Though there was one thing that really bugged me. Flash 9 on websites would cover drop down menus I used (NBA.com for instance). Something to do with param name="wmode" and value="transparent" that apparently only affects the linux version of flash. It was recently rumored to me that there was a release of flash 10, though in beta, apparently fixed this issue. So all excited I hunted down the release and followed the instructions to clear out my copy of flash 9 and replaced it with the new flash 10. Install went flawless and I'm now using flash 10. However my menus on nba.com are still covered like they were with version 9. :( 
Well guess I'll wait for the final release and see how that goes. Anyone have better luck then I did?

---

### Post by Kilz on 2008-06-07
> **Sir Rodness said:**
> Well...
I'm new to linux (decided to go x64) and I've been really enjoying it over the last few months. Fantastic fun messing with the interface and playing with compiz. Though there was one thing that really bugged me. Flash 9 on websites would cover drop down menus I used (NBA.com for instance). Something to do with param name="wmode" and value="transparent" that apparently only affects the linux version of flash. It was recently rumored to me that there was a release of flash 10, though in beta, apparently fixed this issue. So all excited I hunted down the release and followed the instructions to clear out my copy of flash 9 and replaced it with the new flash 10. Install went flawless and I'm now using flash 10. However my menus on nba.com are still covered like they were with version 9. :( 
Well guess I'll wait for the final release and see how that goes. Anyone have better luck then I did?

Nope, the menu's on mlb.com are the same way. Best to voice our opinions to adobe. perhaps it will be fixed then.

---

### Post by bpl07 on 2008-06-07
There's a bug posted on the adobe website that many have been using as a petition to fix this issue.  [http://bugs.adobe.com/jira/browse/FP-80]("http://bugs.adobe.com/jira/browse/FP-80")  It's a very annoying problem that should be easy to fix.

---

### Post by DelSol on 2008-06-08
i've got the same issues with flash. this is annoying to the death. i had that issue already for a while, i cant even remember any linux distribution that worked without covering the tabs.

---

### Post by bpl07 on 2008-06-08
The problem is fixed on the linux side, adobe just needs to fix their end.  Something to do with wmode and transparency, google it and you'll learn more.

---

### Post by bpl07 on 2008-07-02
Anyone tried the [new beta released today]("http://labs.adobe.com/downloads/flashplayer10.html")?

According to this [launchpad post]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/49613/comments/77") it's been fixed, but I haven't taken the time to try it out yet.

---

### Post by cariboo on 2008-07-03
There still isn't a 64bit release though, you still have to use nspluginwrapper to make it work.

Jim

---

### Post by soxs on 2008-07-03
> **bpl07 said:**
> Anyone tried the [new beta released today]("http://labs.adobe.com/downloads/flashplayer10.html")?

According to this [launchpad post]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/49613/comments/77") it's been fixed, but I haven't taken the time to try it out yet.

At least the nvidia page works now (apart from the damn flickering in opera :-S)

---

### Post by bpl07 on 2008-07-03
Actually it's still not fixed for me.  I followed kilz's install method and my browser confirms that I'm using flash 10.0.0 d525 (10 beta 2) but flash still covers up html on all the websites it used to.

soxs: how did you get it to work on your system?  Is your system 64-bit?

---

### Post by soxs on 2008-07-03
> **bpl07 said:**
> Actually it's still not fixed for me.  I followed kilz's install method and my browser confirms that I'm using flash 10.0.0 d525 (10 beta 2) but flash still covers up html on all the websites it used to.

soxs: how did you get it to work on your system?  Is your system 64-bit?
```
sudo apt-get purge nspluginwrapper flashplugin-nonfree
sudo rm -Rvf /usr/lib/nspluginwrapper
```
now search in 
```
/usr/lib/firefox/plugins
```
and
```
/var/lib/flashplugin-nonfree
```
for
```
libflashplayer.so
```
and
```
npwrapper.libflashplayer.so
```

So now ervything is cleaned up.

copy the libflashplayer from the tar file to ```
/usr/lib/firefox/plugins
```
```
sudo apt-get install nspluginwrapper
sudo nspluginwrapper -i /usr/lib/firefox/plugins/libflashplayer.so
```
As some webpages still require version 9.xxx
```
sudo apt-get install flashplayer-nonfree
``` (this works, as it does not use the same dir as for 10 beta 2 flaslib, at least it does on x86_64 bit with opera)

---

### Post by bpl07 on 2008-07-03
That's basically the steps I followed too, except I put libflashplayer.so in the firefox-addons/plugins folder instead of the firefox/plugins folder.  There's a symbolic link in the firefox/plugins folder to the npwrapper though, and everything says I'm using Flash 10, so I think I have it installed correctly.

Flash works in most places, but it still covers up drop down menus on webpages, like [nba.com]("http://www.nba.com").  Flash actually isn't working in opera at the moment (I usually use swiftweasel or firefox), so maybe I did something wrong, but all the files seem to be in place.  

Flash sucks.

---

### Post by soxs on 2008-07-03
> **bpl07 said:**
> That's basically the steps I followed too, except I put libflashplayer.so in the firefox-addons/plugins folder instead of the firefox/plugins folder.  There's a symbolic link in the firefox/plugins folder to the npwrapper though, and everything says I'm using Flash 10, so I think I have it installed correctly.

Flash works in most places, but it still covers up drop down menus on webpages, like [nba.com]("http://www.nba.com").  Flash actually isn't working in opera at the moment (I usually use swiftweasel or firefox), so maybe I did something wrong, but all the files seem to be in place.  

Flash sucks.
I'm using opera 9.50 final and the dropdown menu works, didn't test firefox so far... and I am not keen on going back to ff

---

### Post by bpl07 on 2008-07-04
> **soxs said:**
> I'm using opera 9.50 final and the dropdown menu works, didn't test firefox so far... and I am not keen on going back to ff

Update:  I noticed the plugin for opera uses the /usr/lib/mozilla/plugins folder for the plugin.  I copied libflashplayer.so to this folder and also to the /usr/lib/firefox/plugins folder (like soxs) and now drop down menus work in opera 9.51.  However, they still don't work in firefox or swiftweasel.  Very weird, but I'm happy that something is starting to be fixed.

---

### Post by studyhard888 on 2008-07-04
> **Sir Rodness said:**
> Well...
I'm new to linux (decided to go x64) and I've been really enjoying it over the last few months. Fantastic fun messing with the interface and playing with compiz. Though there was one thing that really bugged me. Flash 9 on websites would cover drop down menus I used (NBA.com for instance). Something to do with param name="wmode" and value="transparent" that apparently only affects the linux version of flash. It was recently rumored to me that there was a release of flash 10, though in beta, apparently fixed this issue. So all excited I hunted down the release and followed the instructions to clear out my copy of flash 9 and replaced it with the new flash 10. Install went flawless and I'm now using flash 10. However my menus on nba.com are still covered like they were with version 9. :( 
Well guess I'll wait for the final release and see how that goes. Anyone have better luck then I did?

Why do you use the X86 ubuntu ? the compatibility of X86 is better than X64 ? i am using X86 for two mouths ,flawless.

---

### Post by fudje on 2008-07-11
> **studyhard888 said:**
> Why do you use the X86 ubuntu ? the compatibility of X86 is better than X64 ? i am using X86 for two mouths ,flawless.

x64 (in my case amd64 specifically) is 64-bit, i386 is not.  Guess which one runs better on 64-bit hardware?

I understand at the moment, however, the problem lies in nspluginwrapper.  Which is still an old version in Ubuntu for some reason (0.9.91.5-2ubuntu2) -- 1.0 has since been released, don't know whether this fixes it or not.

---

### Post by bpl07 on 2008-07-11
> **fudje said:**
> 
I understand at the moment, however, the problem lies in nspluginwrapper.  Which is still an old version in Ubuntu for some reason (0.9.91.5-2ubuntu2) -- 1.0 has since been released, don't know whether this fixes it or not.

Just installed the most recent stable version of nspluginwrapper (1.0.0), doesn't fix the issue.  The release notes list compatibility with beta 1 only, but the next release may have support for flash 10 beta 2.

After that, I installed the unstable release of nspluginwrapper (1.1.0), which fixes he issue.  Flash doesn't cover up drop down menus anymore!

---

### Post by Kilz on 2008-07-11
> **studyhard888 said:**
> Why do you use the X86 ubuntu ? the compatibility of X86 is better than X64 ? i am using X86 for two mouths ,flawless.

Saying you have had no issues with x86 does not mean other will not. Have you ever taken a serious look at the rest of the forum? If you compare the number of issues in this one section vs the rest of the forum that deals with x86 the 64bit version has less. 
I personally have not had one problem with 64bit, does that mean no one else will?

> **bpl07 said:**
> Just installed the most recent stable version of nspluginwrapper (1.0.0), doesn't fix the issue.  The release notes list compatibility with beta 1 only, but the next release may have support for flash 10 beta 2.

After that, I installed the unstable release of nspluginwrapper (1.1.0), which fixes he issue.  Flash doesn't cover up drop down menus anymore!

I am running Flash beta 2 and the old nspluginwrapper. The hidden drop down menus are fixed for me.

---

### Post by mhenriday on 2008-07-12
> **Kilz said:**
> ... 
I personally have not had one problem with 64bit, does that mean no one else will? ...

**Kilz**, you're a lucky - and no doubt, very knowledgeable - man ! But then, you're probably running an audio card that doesn't give rise to quite as many difficulties as the** Creative SoundBlaster X-Fi**. I have the latter installed on my 64-bit **AMD X2** setup, which led to no few difficulties getting the sound to work on **Ubuntu** prior to my discovering **NullHead**, **Temüjin**, *et al*'s wonderful [_*thread*_]("http://ubuntuforums.org/showthread.php?t=571656"), which provided instructions allowing me to get the card to function almost as well on **Hardy** as it does on the **Windows** side of my triple-boot machine. At least until yesterday, when I installed the latest version of the non-free flashplugin (10.0.1.218+10.0.0525ubuntu1~hardy1) ! I suddenly lost all sound on websites like **YouTube**, whereas playing from my own audio files with the **VLC Mediaplayer** was not affected. Unlike some people, I'm not experiencing any **Firefox** (as a matter of fact, [**_Swiftweasel_**]("http://swiftweasel.tuxfamily.org/"), which browser I prefer) crashes after the installation, but being forced to leave my favourite OS for **Windows** to play a video clip is a pain ! I'd be most grateful for any suggestions which might help me to get things working again on my 64-bit system without installing a 32-bit workaround....

Henri

---

### Post by Kilz on 2008-07-12
> **mhenriday said:**
> **Kilz**, you're a lucky - and no doubt, very knowledgeable - man ! But then, you're probably running an audio card that doesn't give rise to quite as many difficulties as the** Creative SoundBlaster X-Fi**. I have the latter installed on my 64-bit **AMD X2** setup, which led to no few difficulties getting the sound to work on **Ubuntu** prior to my discovering **NullHead**, **Temüjin**, *et al*'s wonderful [_*thread*_]("http://ubuntuforums.org/showthread.php?t=571656"), which provided instructions allowing me to get the card to function almost as well on **Hardy** as it does on the **Windows** side of my triple-boot machine. At least until yesterday, when I installed the latest version of the non-free flashplugin (10.0.1.218+10.0.0525ubuntu1~hardy1) ! I suddenly lost all sound on websites like **YouTube**, whereas playing from my own audio files with the **VLC Mediaplayer** was not affected. Unlike some people, I'm not experiencing any **Firefox** (as a matter of fact, [**_Swiftweasel_**]("http://swiftweasel.tuxfamily.org/"), which browser I prefer) crashes after the installation, but being forced to leave my favourite OS for **Windows** to play a video clip is a pain ! I'd be most grateful for any suggestions which might help me to get things working again on my 64-bit system without installing a 32-bit workaround....

Henri

you could try the new beta plugin, see the flash sticky.

---

### Post by bpl07 on 2008-07-12
> **Kilz said:**
> you could try the new beta plugin, see the flash sticky.

> At least until yesterday, when I installed the latest version of the non-free flashplugin (10.0.1.218+10.0.0525ubuntu1~hardy1) 

I believe 10.0.1.218 is flash 10 beta 1, and 10.0.0525 is flash 10 beta 2.

---

### Post by kbozen on 2008-07-13
the last ubuntu update (with backports) solved the problem; it updated:

- firefox-3.0
(3.0.1+build1+nobinonly-0ubuntu0.8.04.1) hardy-proposed

- flashplugin-nonfree
(10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124 .0ubuntu2) hardy-backports

---

### Post by Sir Rodness on 2008-07-14
I just downloaded the latest flash beta to try out on my girlfriends 32 bit Ubuntu computer (yes I've convinced her to give up her windows ways and she's loving it, go figure.) and although its not as clean as the windows version the menu problem seems to have actually been fixed. Looking forward to installing it on my 64bit version to see if the results are the same(crossing fingers). But it's nice to see that Adobe is actually listening. :guitar:

---

### Post by steveneddy on 2008-07-17
Flash 10 is in the repos. Just enable the backports.

---

### Post by manca on 2008-07-19
I updated my Hardy x64 yesterday and it installed Flashplugin-nonfree 10.0.0.1.218 but in firefox (it's updated to 3.0.1), in plugins it still shows that i am using  Shockwave Flash 9.0 r124, why?

Do I have to copy a version 10 lib to list of plugins, what should i do?

---

### Post by Sir Rodness on 2008-07-19
> **Sir Rodness said:**
> I just downloaded the latest flash beta to try out on my girlfriends 32 bit Ubuntu computer (yes I've convinced her to give up her windows ways and she's loving it, go figure.) and although its not as clean as the windows version the menu problem seems to have actually been fixed. Looking forward to installing it on my 64bit version to see if the results are the same(crossing fingers). But it's nice to see that Adobe is actually listening. :guitar:

Well...looks like its only remedied in 32bit(at least for me), guess that's a start. I tried it out in 64bit and the issue remains. Never thought something so simple would annoy the hell out of me. Here's hoping the final release has something to offer us 64bit pioneers.

---

### Post by IanW on 2008-07-20
> **manca said:**
> I updated my Hardy x64 yesterday and it installed Flashplugin-nonfree 10.0.0.1.218 but in firefox (it's updated to 3.0.1), in plugins it still shows that i am using  Shockwave Flash 9.0 r124, why?

AFAIK Due to the Flash10 being buggy, the devs wanted to remove it from _all_ x64 installs & the only way to do it was to offer a Flash9 with a higher version number than the v10.
If you look at flashplugin-nonfree in Synaptic the version number reads as follows:-

Version: 10.0.1.218+10.0.0.525ubuntu1~hardy1+_really9.0.124.0ubuntu2_

---

### Post by Kilz on 2008-07-20
> **IanW said:**
> AFAIK Due to the Flash10 being buggy, the devs wanted to remove it from _all_ x64 installs & the only way to do it was to offer a Flash9 with a higher version number than the v10.
If you look at flashplugin-nonfree in Synaptic the version number reads as follows:-

Version: 10.0.1.218+10.0.0.525ubuntu1~hardy1+_really9.0.124.0ubuntu2_

Flash 10 is far from buggy, I think its far more stable that the current Flash 9 plugin.

---

### Post by manca on 2008-07-22
well what should I do then? How do I install flash 10?

---

### Post by viciouslime on 2008-07-22
Go to system, administration, software sources, then on the updates tab, tick "unsupported updates". press close and ubuntu will download a list of the latest updates. The new updates available icon will appear in the top right by the clock, click on it, press update and flash 10 will be installed :)

---

### Post by bpl07 on 2008-07-22
> **manca said:**
> well what should I do then? How do I install flash 10?

If you do what vicouslime suggested, you'll end up with flash 9 (note the comments a few posts above about it being really flash 9)

You can download the [intrepid deb file here]("http://packages.ubuntu.com/intrepid/flashplugin-nonfree")

---

### Post by manca on 2008-07-27
Yeah, what vicouslime posted is what I have in synaptics, it's actually 9.0 version....

Will that interpid deb package replace the current version or I'll have to manually remove it?

---

### Post by matthewboh on 2008-07-27
I having the same problem - I went ahead and got the updated unsupported packages, but it didnt fix the problem.  Im on an updated box that went from 7.10 to 8.04, but flash had never worked  before the update either.

---

