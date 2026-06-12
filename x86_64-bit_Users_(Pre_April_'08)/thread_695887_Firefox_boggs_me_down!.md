---
title: "Firefox boggs me down!"
date: 2008-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by shane2peru on 2008-02-13
Ok, I found the problem of why my computer is always bogging down.  I'm about 94% it is Firefox.  Everytime it bogs down, I check my processes and Firefox is eating memory like it is candy!  What is going on with this?  This is super annoying to me.  Does anyone else have this problem or a solution?

Shane

---

### Post by moogyd on 2008-02-13
I don't know if it helps, I don't see the problem in Ubuntu but I get problems with Windows XP (on both home and work PC's).

---

### Post by shane2peru on 2008-02-13
> **moogyd said:**
> I don't know if it helps, I don't see the problem in Ubuntu but I get problems with Windows XP (on both home and work PC's).

I only have Linux installed on my system.  I didn't have this problem while using 32bit.  Just since switching over to 64bit.  There must be some file somewhere that is holding up the system.

Shane

---

### Post by Paul S on 2008-02-13
Someone else with the same complaint.  My answer:

aptitude install mozilla-firefox-adblock

Then set up filters on offending ads, and no more problem, until a new add is encountered.

HTH

---

### Post by Kilz on 2008-02-13
> **shane2peru said:**
> Ok, I found the problem of why my computer is always bogging down.  I'm about 94% it is Firefox.  Everytime it bogs down, I check my processes and Firefox is eating memory like it is candy!  What is going on with this?  This is super annoying to me.  Does anyone else have this problem or a solution?

Shane

How many tabs do you have open?

---

### Post by shane2peru on 2008-02-13
I do have a few tabs open, but it seems like if I leave Firefox open for a while (which I do often) it really starts to bog things down.  At that moment I had 2 Firefox windows open and about 4 tabs per window (so a total of about 8 tabs).  However it does this even if I have one window open without tabs and leave it open for a few hours. I didn't really have this problem with 32bit, or at least I'm about 90% sure I didn't.  

Shane

---

### Post by raafaell on 2008-02-13
Do you have flashplayer installed? is your Firefox up-to-date?

---

### Post by shane2peru on 2008-02-13
> **raafaell said:**
> Do you have flashplayer installed? is your Firefox up-to-date?

I have the flash player installed from this forum, the ndswrapper or something of that nature, installed it from the sticky in this forum.  And everything is up to date.  

Shane

---

### Post by raafaell on 2008-02-13
on my opinion, you should try uninstalling ndiswrapper, and then in Terminal do: > sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux32

and then download flashplayer 9.0 from this link: [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz")

then: > sudo mkdir /usr/local/firefox32/plugins/flash7
sudo mv -f /usr/local/firefox32/plugins/flashplayer.xpt /usr/local/firefox32/plugins/flash7/
sudo mv -f /usr/local/firefox32/plugins/libflashplayer.so /usr/local/firefox32/plugins/flash7/

The flash 9 plugin will come in a tar file. The files name install_flash_player_9_linux.tar.gz . 

So do: > cd ~/Desktop
tar -xzvf install_flash_player_9_linux.tar.gz
sudo mv -f ~/Desktop/install_flash_player_9_linux/libflashplayer.so /usr/lib32/firefox32/plugins
sudo mv -f ~/Desktop/install_flash_player_9_linux/flashplayer.xpt /usr/lib32/firefox32/plugins 

then, give a little test: > chown -R <YOURUSERNAMEHERE>:users /home/<username>/.macromedia

Then download and double click on [[COLOR="Red"]this package[/COLOR]]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb") to install it.

if you have any problem after that, do: > sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

and: > sudo apt-get install alsa-oss

To test your flashplayer, visit: [http://www.youtube.com]("http://www.youtube.com")

Good luck.

---

### Post by eks on 2008-02-13
You can also try Swiftweasel:

[http://swiftweasel.tuxfamily.org/about.php](http://swiftweasel.tuxfamily.org/about.php)

> 
Swiftweasel is an optimized build of the Mozilla Firefox web browser for Linux. With builds for both AMD and Intel processors. Swiftweasel is 100% compatible with all Firefox themes, plugins, and extensions.

It works like a charm.


eks

---

### Post by shane2peru on 2008-02-13
> **raafaell said:**
> on my opinion, you should try uninstalling ndiswrapper, and then in Terminal do: 

and then download flashplayer 9.0 from this link: [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz")

then: 

The flash 9 plugin will come in a tar file. The files name install_flash_player_9_linux.tar.gz . 

So do:  

then, give a little test: 

Then download and double click on [[COLOR="Red"]this package[/COLOR]]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb") to install it.

if you have any problem after that, do: 

and: 

To test your flashplayer, visit: [http://www.youtube.com]("http://www.youtube.com")

Good luck.

Ok, ran into this little problem at the first command:```

WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  util-linux

```
I'm not sure about doing that.  What is util-linux and what does it do? 

Thanks
Shane

---

### Post by shane2peru on 2008-02-13
> **eks said:**
> You can also try Swiftweasel:

[http://swiftweasel.tuxfamily.org/about.php](http://swiftweasel.tuxfamily.org/about.php)



It works like a charm.


eks

Ok, do to the restriction I ran into with the other fix, I downloaded and installed swiftweasel.  Now I have a problem.  It imported all my books marks, and **most** of my extensions, except a key one, **greasemonkey** and my Script to play FoxNews Videos.  I watch more Foxnews than I do Youtube.  On occasion I do visit youtube, but not often.  Can I get greasemonkey and FoxNews? if not, this is just not going to work. :)


Shane

---

### Post by Kilz on 2008-02-13
> **shane2peru said:**
> Ok, do to the restriction I ran into with the other fix, I downloaded and installed swiftweasel.  Now I have a problem.  It imported all my books marks, and **most** of my extensions, except a key one, **greasemonkey** and my Script to play FoxNews Videos.  I watch more Foxnews than I do Youtube.  On occasion I do visit youtube, but not often.  Can I get greasemonkey and FoxNews? if not, this is just not going to work. :)


Shane

Try reinstalling greasemonkey in swiftweasel.

---

### Post by shane2peru on 2008-02-13
> **Kilz said:**
> Try reinstalling greasemonkey in swiftweasel.

Ya know that sounds sooo simple, and I tried it once.  When I went to the extensions page it said, "This script is not for Linux" and there was no install button!  So I tried the command line and the Ubuntu Greasemonkey script, and apparently it is only for Firefox.  So I read your post and then went back to the Mozilla extensions page and searched Greasemonkey and sure enough there it was, and it installed!  How odd!  Thanks for making me double check that page.

Shane

---

### Post by Kilz on 2008-02-13
> **shane2peru said:**
> Ya know that sounds sooo simple, and I tried it once.  When I went to the extensions page it said, "This script is not for Linux" and there was no install button!  So I tried the command line and the Ubuntu Greasemonkey script, and apparently it is only for Firefox.  So I read your post and then went back to the Mozilla extensions page and searched Greasemonkey and sure enough there it was, and it installed!  How odd!  Thanks for making me double check that page.

Shane

No problem, thanks for the knowledge on how to make fox video work. Now if only these is a script for abc.com's full episode player.

---

### Post by imon9 on 2008-02-13
try firefox3....(from synaptic)

not all plugin are supported yet...but most memory leak sure are fixed...no more grey-out/hanging on javascript heavy site

---

### Post by shane2peru on 2008-02-13
> **Kilz said:**
> No problem, thanks for the knowledge on how to make fox video work. Now if only these is a script for abc.com's full episode player.

hmm, don't know much about ABC, I did a quick search, and it doesn't look good.  The only solution I came up with is using Firefox2 with Wine.  Not the best solution.  Did you find the link for the foxnews videos?  if not it is here:  [http://userscripts.org/scripts/show/1371](http://userscripts.org/scripts/show/1371)  After greasemonkey is installed this script will fix your Foxnews issues, it even strips the commercials!  I had forgotten they have commercials till I saw it on windows once. :lolflag:

Shane

---

### Post by shane2peru on 2008-02-13
> **imon9 said:**
> try firefox3....(from synaptic)

not all plugin are supported yet...but most memory leak sure are fixed...no more grey-out/hanging on javascript heavy site

Hey this will be a nice test.  I'm content with Swiftweasel now that I got FoxNews videos working, however I installed this Firefox3 too and will test it out!  Thanks.

Shane

---

### Post by Kilz on 2008-02-13
firefox 3 is a beta install, I bet there will be a swiftweasel of the beta within a few days.

---

