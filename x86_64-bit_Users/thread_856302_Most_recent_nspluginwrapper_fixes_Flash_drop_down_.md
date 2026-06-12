---
title: "Most recent nspluginwrapper fixes Flash drop down menu issue"
date: 2008-07-11
forum: x86 64-bit Users
---

### Post by bpl07 on 2008-07-11
If you're like me, Flash covering up drop-down menus drives you crazy.  Flash 10 beta 2 fixes this issue, but nspluginwrapper didn't support the change... or at least I thought it didn't.

If you install the most recent version of [nspluginwrapper (1.1.0)]("http://gwenole.beauchesne.info/en/blog/2008/07/06/nspluginwrapper_1.1.0"), the issue is fixed.  You can either wait for ubuntu to update the repository, or try to install it yourself from source, but I can confirm that Flash finally does not cover up drop-down menus with this version of nspluginwrapper!

---

### Post by soxs on 2008-07-11
I get at error when trying to run configure...
```
cURL environment not found
```

---

### Post by bpl07 on 2008-07-11
> **soxs said:**
> I get at error when trying to run configure...
```
cURL environment not found
```

Install libcurl4-gnutls-dev in synaptic, then run configure again.

Make sure you update your links once you're finished:

> sudo nspluginwrapper -v -a -u

---

### Post by Kilz on 2008-07-11
The original poster is incorrect. I have Flash beta 2 installed and the drop down issues were fixed without the need to install a new version of nspluginwrapper.

---

### Post by bpl07 on 2008-07-11
> **Kilz said:**
> The original poster is incorrect. I have Flash beta 2 installed and the drop down issues were fixed without the need to install a new version of nspluginwrapper.

For me, it worked in opera but not firefox.  With the new nspluginwrapper, it works in both.  The [nspluginwrapper site]("http://gwenole.beauchesne.info/en/blog/2008/07/06/nspluginwrapper_1.1.0") states that the old version in the ubuntu repositories did not fully support beta 2, but the new version does.

> Here is a short list of changes since 1.0.0, details to follow:

    *
      Add support for windowless plugins (Flash Player 10 beta 2)
    *
      Add standalone plugins player (nspluginplayer)
    *
      Restart plugins viewer on error (Martin Stransky)

Windowless plugins support. Windowless plugins are now supported in Firefox 3. Only Flash Player 10 beta 2 and a modified DiamondX plugin were tested. There currently is no means to disable windowless plugins but at compile-time through the ALLOW_WINDOWLESS_PLUGINS macro in npw-viewer.c. This can change in the future if there is a need to do so. 

---

### Post by Kilz on 2008-07-11
> **bpl07 said:**
> For me, it worked in opera but not firefox.  With the new nspluginwrapper, it works in both.  The [nspluginwrapper site]("http://gwenole.beauchesne.info/en/blog/2008/07/06/nspluginwrapper_1.1.0") states that the old version in the ubuntu repositories did not fully support beta 2, but the new version does.

That report is wrong. I have the old nspluginwrapper from the repositories installed with the Flash 10 beta 2. The problem of menu's hidden behind graphics on a web page is fixed.

---

### Post by bpl07 on 2008-07-12
> **Kilz said:**
> That report is wrong. I have the old nspluginwrapper from the repositories installed with the Flash 10 beta 2. The problem of menu's hidden behind graphics on a web page is fixed.

Lucky you.  Many others have reported it not being fixed for them with the old nspluginwrapper, not just me.  I wasn't lying.

---

### Post by Kilz on 2008-07-12
> **bpl07 said:**
> Lucky you.  Many others have reported it not being fixed for them with the old nspluginwrapper, not just me.  I wasn't lying.

I dont think you are lying, I think you and others may not have generated the wrapper correctly, that it may not have been in place, or may have left the old plugin in place. There are a lot of possible problems that you could have run into.

Take a look at the screenshots, I have the old wrapper, the new plugin, and the Bears site works that had hidden drop downs with Flash 9.

---

### Post by emerson999 on 2008-07-12
The good news, worked for me from a simple apt-get, no need for a new nsplugin compile. It worked 'ok' for fixing the drop down problem for me. A bit of flicker, not as seemless as on osx, but menus are actually visible! The bad news, controls on at least one site, crunchyroll, no longer work for me.

---

### Post by soxs on 2008-07-12
> **Kilz said:**
> I dont think you are lying, I think you and others may not have generated the wrapper correctly, that it may not have been in place, or may have left the old plugin in place. There are a lot of possible problems that you could have run into.

Take a look at the screenshots, I have the old wrapper, the new plugin, and the Bears site works that had hidden drop downs with Flash 9.

Definitley not, I first purged and afterwards erased anything related to flashplugin firefoxplugins and nspluginwrapper. I get proper drop down menus in opera 9.51, but ot in FF3

---

### Post by chapterthree on 2008-07-12
Hi All,

I'm having build issues with 1.0.0 and 1.1.0 (same issue) and I can't seem to figure out how to fix it.  During make, I'm getting the following error:
```
gcc -std=c99 -m32 -o npviewer.bin npviewer-npw-viewer.o npviewer-npw-rpc.o npviewer-rpc.o npviewer-debug.o npviewer-utils.o npviewer-npruntime.o npviewer-cxxabi-compat.o -m32 -Llsb-build-i386 -lgtk-x11-2.0 -lgdk-x11-2.0 -lgobject-2.0 -ldl -lglib-2.0 -lX11 -lXt -ldl -lpthread -lgthread-2.0 -Wl,--export-dynamic -Wl,--version-script,/home/chapterthree/src/nspluginwrapper-1.1.0/src/npw-viewer.map -lsupc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/libsupc++.a when searching for -lsupc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/libsupc++.a when searching for -lsupc++
/usr/bin/ld: cannot find -lsupc++
collect2: ld returned 1 exit status
make: *** [npviewer.bin] Error 1
```

Googling isn't turning up much in the way of help.  Any ideas here?

**Update: It looks like this was failing because it was trying to build the 32-bit version.**  I changed my configure options to the following, and I was successfully able to build the code:
```
./configure --disable-biarch --enable-viewer --enable-player
```

---

### Post by Kilz on 2008-07-12
> **soxs said:**
> Definitley not, I first purged and afterwards erased anything related to flashplugin firefoxplugins and nspluginwrapper. I get proper drop down menus in opera 9.51, but ot in FF3

I dont know what went wrong for you, but now 2 people have said they have it working without having the new wrapper.

---

### Post by chapterthree on 2008-07-12
I have finally managed to get nspluginwrapper-0.9.91.5-2ubuntu2 and Flash 10.0.0 d525 to play nice together, although for me I still have the 'menu behind Flash' issue.

I must say there seems to be a wide variety of ways/places/procedures to install Flash 10 beta2, so I'm still not sure if I have things where they need to be for all of this to be happy.  I have found multiple tutorials that vary quiet a bit, and don't do a full end-to-end walkthrough (at least not for the combination of Hardy x86_64, nspluginwrapper from repo, and Flash 10 beta2).

I have managed to successfully build nspluginwrapper 1.0.0 and 1.1.0, but I was not successful in getting them to work.  On both versions I was getting the 'no appropriate viewer found' error when trying to install libflashplayer.so.

---

### Post by bpl07 on 2008-07-12
> **chapterthree said:**
> 

I have managed to successfully build nspluginwrapper 1.0.0 and 1.1.0, but I was not successful in getting them to work.  On both versions I was getting the 'no appropriate viewer found' error when trying to install libflashplayer.so.

I think you should have installed a 32-bit library to get lsupc++ working without the compile tag you mentioned.  I had to install the multilib library for gcc or g++ (can't remember which) before it would compile without the lsupc++ error.  I believe you're getting the "can't find a suitable player" error because libflashplayer.so is a 32-bit player, but you have nspluginwrapper looking for a 64-bit player because of the way you compiled it.

---

### Post by chapterthree on 2008-07-12
> **bpl07 said:**
> I think you should have installed a 32-bit library to get lsupc++ working without the compile tag you mentioned.  I had to install the multilib library for gcc or g++ (can't remember which) before it would compile without the lsupc++ error.  I believe you're getting the "can't find a suitable player" error because libflashplayer.so is a 32-bit player, but you have nspluginwrapper looking for a 64-bit player because of the way you compiled it.

Ah ha, now it is all starting to make sense.  It looks like the package I was missing on the lsupc++ issue was g++-multilib.  Once I installed that I was able to complete a build using the default configure options (which is mostly necessary for the whole ball of wax to work properly).

I'm now running nspluginwrapper-1.1.0 and Flash 10 beta2 and I am no longer experiencing the 'menu behind Flash' issue; everything appears to be working as it should.  Thank you so much for this post as this was the missing piece of the puzzle.

---

### Post by chapterthree on 2008-07-12
Doh, guess there are trade-offs.  The menu behind Flash issue is resolved, but now I'm getting the flickering on some Flash items on some pages ([http://www.nba.com](http://www.nba.com)) and Flash is not loading on some pages ([http://www.addictinggames.com/bloxors.html](http://www.addictinggames.com/bloxors.html)).

But I guess this is to be expected from using 2 beta products.  As is mentioned on the nspluginwrapper site, both issues seem to be known, and are bugs/issues in Flash, so we'll have to hold our breath until Adobe releases another beta.  In the mean time, I'm using Opera for my Flash needs when FF can't display something. :)

---

### Post by Kilz on 2008-07-13
> **chapterthree said:**
> Doh, guess there are trade-offs.  The menu behind Flash issue is resolved, but now I'm getting the flickering on some Flash items on some pages ([http://www.nba.com](http://www.nba.com)) and Flash is not loading on some pages ([http://www.addictinggames.com/bloxors.html](http://www.addictinggames.com/bloxors.html)).

But I guess this is to be expected from using 2 beta products.  As is mentioned on the nspluginwrapper site, both issues seem to be known, and are bugs/issues in Flash, so we'll have to hold our breath until Adobe releases another beta.  In the mean time, I'm using Opera for my Flash needs when FF can't display something. :)

Interesting game, I am using the Flash 2 beta and it shows for me, see screenshot. Have you tried to refresh the page. I sometimes get a white box on some pages that will go away if I refresh.

---

### Post by z0mbie on 2008-07-26
Anyone have a deb package for this?

---

### Post by steveneddy on 2008-07-27
> **chapterthree said:**
> Doh, guess there are trade-offs.  The menu behind Flash issue is resolved, but now I'm getting the flickering on some Flash items on some pages ([http://www.nba.com](http://www.nba.com)) and Flash is not loading on some pages ([http://www.addictinggames.com/bloxors.html](http://www.addictinggames.com/bloxors.html)).



You horrible people! Why did you post the link to that game?! 

I can't sleep anymore unless the block goes through the hole!

For the love of macaroni and cheese, please help me!

BTW - Flash 10 and the old nspluginwrapper works great for me on 64 bit.

And yes - this is a very cool game.

---

### Post by srf21c on 2008-10-29
Update:  A more elegant solution (which won't affect firefox) would be to set the /usr/lib/mozilla/plugins=0 line in the Opera pluginpath.ini file [as detailed here]("https://help.ubuntu.com/community/OperaBrowser#Opera Segmentation Fault and Java crash with static version problem")

If you're interested in my troubleshooting methodology, read on.

I was having no luck getting Flash to work with Opera 9.61 on my amd64 bit installation of Hardy Heron.

First tried installing flashplugin-nonfree from the repos.  No dice, I could hear the sound at [[COLOR="Red"]the Adobe flash test page[/COLOR]]("http://www.adobe.com/shockwave/welcome/"), but the box would remain white, no graphics.

So I ran : ```
sudo apt-get purge flashplugin-nonfree 
```

and tried installing Flash 10 using Kilz 10 script [[COLOR="#ff0000"]from this thread.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=772490&highlight=flash+plugin+opera+amd64") 

Still not working.  I tried running through the manual installation steps too, no progress.

So I manually downloaded the Abobe Flash 10 32bit tarball for linux (Abobe has yet to release a true 64-bit build) [[COLOR="#ff0000"]from here[/COLOR]]("http://get.adobe.com/flashplayer/")

I then manually extracted libflashplayer.so and copied it to /usr/lib/flashplugin-nonfree/libflashplayer.so.

Restarted Opera but still no luck.  So I typed ```
about:plugins 
``` into the Opera address bar and it was showing three flash plugins.  I manually removed the mozzila instances like so:

```
sudo rm /usr/lib/mozilla/plugins/flashplugin-alternative.so
sudo rm /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so 

```  restarted Opera, and boom now Flash 10 is now working.

An Napoleon Dynamite's brother would say:

Yeeeesssssssssssssssssssssssssssssss....!    :guitar:

I hope this helps some other people.

---

