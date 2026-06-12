---
title: "[SOLVED] WMV video not playing on one site"
date: 2007-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by firecat53 on 2007-04-27
Hi. I'm running Feisty 64 on AMD system. I have the 64 bit firefox working flawlessly with the mplayer and flash plugins (Youtube, Google video, any wmv movies on websites I've visited) using nspluginwrapper. There's just one website I can't seem to play the videos for:  [www.king5.com](www.king5.com) (news channel here in Seattle). 

I'd be much obliged if anyone else running firefox 64 with the nspluginwrapper would care to have a go at figuring out how to play those videos.

Thanks!

Scott

Let me know if I can provide any further system information.

---

### Post by Kilz on 2007-04-27
> **firecat53 said:**
> Hi. I'm running Feisty 64 on AMD system. I have the 64 bit firefox working flawlessly with the mplayer and flash plugins (Youtube, Google video, any wmv movies on websites I've visited) using nspluginwrapper. There's just one website I can't seem to play the videos for:  [www.king5.com](www.king5.com) (news channel here in Seattle). 

I'd be much obliged if anyone else running firefox 64 with the nspluginwrapper would care to have a go at figuring out how to play those videos.

Thanks!

Scott

Let me know if I can provide any further system information.

I dont run nspluginwrapper. But I will tell you that Firefox32 shows videos from that site.

---

### Post by firecat53 on 2007-04-27
Hmmm. My Firefox32 install is doing the same behavior as my 64-bit firefox.....just shows the video window with a 'loading' icon going in circles and does nothing more. I made sure there were no competing plugins in ~/.mozilla/plugins (it's empty).  All the 32-bit plugins are in /usr/lib32/firefox32/plugins, and the nspluginwrapper plugins are in the /usr/lib/mozilla/plugins and /usr/lib/mozilla-firefox/plugins.

I can view quicktime trailers w/ no issues with either browser, and some test .wmv's worked fine w/ both.

What am I missing??

Thanks, Kilz, for all your input and help w/ 64-bit issues!! 

Scott

---

### Post by Kilz on 2007-04-27
Its possible its a problem with feisty and the newer mplayer/mplayer plugins. I run dapper. 
But lets make sure it isnt something simple. Did you do a fresh install of Feisty and the script , or was it an upgrade from Edgy? Also do all the plugins belong to you, or root on the permission tab in properties?

---

### Post by joepotter on 2007-04-27
> **firecat53 said:**
> Hi. I'm running Feisty 64 on AMD system. I have the 64 bit firefox working flawlessly with the mplayer and flash plugins (Youtube, Google video, any wmv movies on websites I've visited) using nspluginwrapper. There's just one website I can't seem to play the videos for:  [www.king5.com](www.king5.com) (news channel here in Seattle). 

I'd be much obliged if anyone else running firefox 64 with the nspluginwrapper would care to have a go at figuring out how to play those videos.

Thanks!

Scott

Let me know if I can provide any further system information.

I can report that Debian Sid 64 + Firefox 64 plays the videos just fine with nspluginwrapper.

I may try to get my Feisty install to run the 64 bit Firefox this weekend and report back; I just use 32 bit swiftfox in Ubuntu.

Edit: That should be Iceweasel 64 bit, rather than Firefox --- Debian may not distribute Firefox anymore.

---

### Post by joepotter on 2007-04-28
> **firecat53 said:**
> Hi. I'm running Feisty 64 on AMD system. I have the 64 bit firefox working flawlessly with the mplayer and flash plugins (Youtube, Google video, any wmv movies on websites I've visited) using nspluginwrapper. There's just one website I can't seem to play the videos for:  [www.king5.com](www.king5.com) (news channel here in Seattle). 

I'd be much obliged if anyone else running firefox 64 with the nspluginwrapper would care to have a go at figuring out how to play those videos.

Thanks!

Scott

Let me know if I can provide any further system information.

I watched a news video on the front page of: [www.king5.com](www.king5.com) (news channel in Seattle) in 64 bit Firefox just minutes ago. I have now watched the site with 64 bit Firefox and 64 bit Iceweasel; as well as 32 bit swiftfox running in 64 bit Feisty. (Debian 64 and Ubuntu 64 both used)

I just can not get a foul up. :-(

So, sorry but I am no help.

---

### Post by firecat53 on 2007-04-28
Joe, can you post what plugins you have installed in ~/.mozilla/plugins, /usr/lib/mozilla/plugins, and /usr/lib/mozilla-firefox/plugins?  You're using nspluginwrapper? 

It's encouraging :)

Kilz, all my plugins are root:root owned. When I tried to change it to my own username & group, things went haywire on all the other sites that did work. So I changed them back to root:root for now.  Yes, this was a fresh Feisty install, not an Edgy upgrade. I used your script (as of a couple of weeks ago) to install my firefox32. I unfortunately didn't check that site when I first installed firefox32, so now I'm not sure if it used to work and I borked something, or if there's another issue going on.

Thanks, Scott

---

### Post by Kilz on 2007-04-28
> **firecat53 said:**
> Joe, can you post what plugins you have installed in ~/.mozilla/plugins, /usr/lib/mozilla/plugins, and /usr/lib/mozilla-firefox/plugins?  You're using nspluginwrapper? 

It's encouraging :)

Kilz, all my plugins are root:root owned. When I tried to change it to my own username & group, things went haywire on all the other sites that did work. So I changed them back to root:root for now.  Yes, this was a fresh Feisty install, not an Edgy upgrade. I used your script (as of a couple of weeks ago) to install my firefox32. I unfortunately didn't check that site when I first installed firefox32, so now I'm not sure if it used to work and I borked something, or if there's another issue going on.

Thanks, Scott

I dont think Firefox32 could mess up the 64bit version. They use completely different files, including the plugins. The plugins for 64 bit are in /usr/lib/mozilla and /usr/lib/firefox/plugins. The 32bit are in /usr/lib32/firefox32/plugins. The 32bit files for mplayer-mozilla are not installed as a deb, but copied into place. Since they dont use any of the same files, its hard to see where one could effect the other.

---

### Post by firecat53 on 2007-04-28
Here are the plugins for 32-bit Firefox in /usr/lib32/firefox32/plugins/
flashplayer.xpt       mplayerplug-in-dvx.so   mplayerplug-in-rm.xpt
libflashplayer.so     mplayerplug-in-dvx.xpt  mplayerplug-in.so
libjavaplugin_oji.so  mplayerplug-in-qt.so    mplayerplug-in-wmp.so
libnpp.so             mplayerplug-in-qt.xpt   mplayerplug-in-wmp.xpt
libnullplugin.so      mplayerplug-in-rm.so    mplayerplug-in.xpt

And here are the 64 bit plugins in /usr/lib/mozilla-firefox/plugins/
flashplayer.xpt                    npwrapper.mplayerplug-in-dvx.so
mplayerplug-in-dvx.xpt       npwrapper.mplayerplug-in-qt.so
mplayerplug-in-qt.xpt          npwrapper.mplayerplug-in-rm.so
mplayerplug-in-rm.xpt         npwrapper.mplayerplug-in.so
mplayerplug-in-wmp.xpt      npwrapper.mplayerplug-in-wmp.so
mplayerplug-in.xpt           
npwrapper.libflashplayer.so

All the plugins are recognized by about:plugins in each browser, java works fine in firefox32, and quicktime trailers and sample wmv's play fine in both browsers.

It's just this one site. Both browsers do the same thing....just show the rotating 'loading' icon and that's it.

I also tried clearing my cache.

Anything else I should check?

Thanks!  Scott

---

### Post by joepotter on 2007-04-29
> **firecat53 said:**
> 
... It's just this one site. Both browsers do the same thing....just show the rotating 'loading' icon and that's it.

I also tried clearing my cache.

Anything else I should check?

Thanks!  Scott

I led you astray before. I had not checked everything.

When I go there in a fresh install of xubuntu and 64 bit Firefox, I can see videos but they are flaky. They will play and then freeze my computer. I have it set so that mplayer and w64codecs will show me the video; but then I have a frozen computer.

Can you e-mail them and ask what in the world they are doing with their videos?

---

### Post by firecat53 on 2007-07-04
Well....turned out to be an easy fix....Disable adblock plus on that page and they work fine....

<sigh>  Wish all problems were that easy :)

Scott

---

