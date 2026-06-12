---
title: "flashplayer slow under full screen"
date: 2008-04-30
forum: x86 64-bit Users
---

### Post by lamborghiniwang on 2008-04-30
Hardy 64bit on a Thinkpad T61p (Core2Duo T7300 with Nvidia Quadro FX 570M video card) the property Nvidia driver (v169.12) and flashplugin-nonfree(9.0.124) is installed from the repo, it runs fine except under full-screen mode, the video is slow and choppy. Neither enable/disable hardware acceleration or enable/disable desktop effects would solve this problem.

  Anyone is experiencing the same problem?

---

### Post by aluizio98 on 2008-05-06
I have the same problem with Ubuntu 8.04 on Pentium 4, 512MB. I´ve read that if you install flash player r48 the videos will run much better in full screen. I´ll try tonight.

---

### Post by Artemis3 on 2008-05-06
This occurs with all current linux versions. Thank adobe for its wonderful programming...

---

### Post by lamborghiniwang on 2008-05-06
As for youtube, I just found out the Totem 2.22.1 that comes with Hardy support search/play youtube video. 
All you have to do is to enable the plugin at Edit->Preferences->Plugins->Youtube browser, and then you can search youtube video in the sidebar of Totem. It players the youtube video much faster than the flashplayer from Adobe.

---

### Post by lamborghiniwang on 2008-05-12
Well, there is another problem with flashplayer+FF3, it seems the flashplayer plugin crashes very often under this combination, not just for youtube videos. Sometimes I am just browsing some site with a lot of flash (e.g., [http://www.nba.com](http://www.nba.com)), and suddently all the flash parts start to become gray boxes, and the only way to solve this is to restart FF3. Flashplayer in opera has the same problem, but crashes less often and usually can be solved by re-open a new tab.
  I assume this bug has to do with both FF3 and flashplay-nonfree

---

### Post by philinux on 2008-05-12
I know it's not  perfect solution but i use flashblock addon. It replaces the flash with an F and then when you mouse over it, it changes into a play button.

You can whitelist sites too. Upshot, no crashes, less time to load. I only whitelist sites that dont crash my machine.

---

### Post by olivierp on 2008-05-12
Keep in mind you are:
- running a 64bit OS
- a 64bit browser
- using nspluginwrapper for running a 32bit plugin (flash). So don't complain too much on Adobe's coding :-)

- There's a "to be released" pluginwrapper here [http://gwenole.beauchesne.info/en/blog/2007/12/25/nspluginwrapper_and_new_flash_player](http://gwenole.beauchesne.info/en/blog/2007/12/25/nspluginwrapper_and_new_flash_player) for Flash 9.0.115, and maybe above.

- If you want to test prevîous releases of Flash plugins, you can get a complete archive of 9.x plugins for all supported OSs here [http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1)

- To test these versions, extract the one you want, and, to avoid wreaking too much havoc with your installs, MANUALLY perform the install actions found in /var/lib/dpkg/info/flashplugin-nonfree.postinst

---

### Post by enchantedsky on 2008-05-14
> **olivierp said:**
> Keep in mind you are:
- running a 64bit OS
- a 64bit browser
- using nspluginwrapper for running a 32bit plugin (flash). So don't complain too much on Adobe's coding :-)

What you're saying is not true because I have tested numerous versions of Ubuntu, in 64-bit *and* 32-bit, and they all have problems with 32-bit Adobe Flash for Linux. When Youtube videos are maximized, the video is choppy. And sometimes in Firefox 3, a grey box is shown instead of a video, as a poster above mentioned. A lot of bugs are due to Adobe's poor programming in flashplugin-nonfree(9.0.124). 

I'm actually going to meet with a representative of Adobe tomorrow, and I'm going to tell him about the problems of Flash player for Linux. If Adobe doesn't want to do anything about it, then we should all embrace a *good* open-source version in the future when it comes out.

---

### Post by aluizio98 on 2008-05-16
I installed Adobe Flash Player r48 and it runs much much better than the latest 9.0.115 in full screen. You can change to r48 without regret !!!

---

### Post by mysoogal on 2009-05-10
> **aluizio98 said:**
> I installed Adobe Flash Player r48 and it runs much much better than the latest 9.0.115 in full screen. You can change to r48 without regret !!!

where can you download this Adobe Flash Player r48 version ?:confused:


i installed install_flash_player_10_linux.deb

and video is slow in full screen, wish i didnt update !

---

### Post by Yellow Pasque on 2009-05-10
> **mysoogal said:**
> where can you download this Adobe Flash Player r48 version ?:confused:


i installed install_flash_player_10_linux.deb

and video is slow in full screen, wish i didnt update !
Adobe offers old versions here: [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)
Unfortunately, you can't just get the specific one you want.

When you say that you installed Flash10, did you install the 64-bit version or some 32-bit version?
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by mysoogal on 2009-05-10
> **Temüjin said:**
> Adobe offers old versions here: [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)
Unfortunately, you can't just get the specific one you want.

When you say that you installed Flash10, did you install the 64-bit version or some 32-bit version?
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

i really need to install the old version before i was asked to update, it  was something like 3 mb new version. im on 32 version


when i installed new flash player 10.0.22.87 update videos become slow in full screen and seem to skip frames and very slow.

anyway to check which flash player version i had installed before this nnew version ?

is there 10.0.22.37 something ? i believe it was something like that i installed before and it worked great in full screen

---

### Post by mysoogal on 2009-05-10
how to install install_flash_player_9r48_linux.tar.gz

im use deb to install from normally, but not sure how this thing needs to be installed

---

### Post by m3alnemer on 2009-05-11
untar it first

```
untar install_flash_player_9r48_linux.tar.gz
```

to install it:
say you have it on Desktop
```
cd ~/Desktop
```

```
sudo chmod +x nameoffile.bin
```

then run it

```
./nameoffile.bin
```

where nameoffile is the name of the extracted file.

Hopefully this well work

---

### Post by mysoogal on 2009-05-11
> **m3alnemer said:**
> untar it first

```
untar install_flash_player_9r48_linux.tar.gz
```

to install it:
say you have it on Desktop
```
cd ~/Desktop
```

```
sudo chmod +x nameoffile.bin
```

then run it

```
./nameoffile.bin
```

where nameoffile is the name of the extracted file.

Hopefully this well work

thanks, it was much simpler, just extracting the files to desktop and clicking on the install and run in terminal, from here easy to install :KS

it seems the new flash player 10 version really is bad on Eee pc. 

the videos seem to play normally now, hope they fix things on the next flash player 11 ? im wondering why doesnt totem player ! pickup ! flv files ? like it does for divx avi ? when i visit [http://filebase.to](http://filebase.to) and view video from there i dont need to install divx web player, since there is no divx web player, anyway for linux, was just wondering why not make totem the default web player in firefox to player flv video :confused:

---

