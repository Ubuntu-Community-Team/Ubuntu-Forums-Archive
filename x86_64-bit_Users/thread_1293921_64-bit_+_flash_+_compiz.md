---
title: "64-bit + flash + compiz"
date: 2009-10-17
forum: x86 64-bit Users
---

### Post by linbetwin on 2009-10-17
Hello,

I just installed the latest daily-live .iso (x86_64)
installed ATI proprietary driver when prompted by "Hardware Drivers"
rebooted, compiz was activated
installed ubuntu-restricted-extras.

Flash videos work fine (I watched Conan on NBC and a clip on southparkstudios)
EXCEPT on YouTube!

- If I find a YouTube video embedded on a website, I can't play it. I can only right-click and choose "Play on YouTube".
- On the YouTube site, the video plays fine but I can't pause, maximize or access any other controls.
- Opening Adobe Flash Properties only shows "Enable hardware acceleration", no matter what icon you click on.

I thought this is because I'm using 64-bit Ubuntu, but I disabled compiz and YouTube started working fine.

Any ideas what's causing this? Is it compiz or flash? Why only on YouTube?
Any solutions?
Thanks.

---

### Post by QIII on 2009-10-17
Do you have swfdec or gnash installed?  I can't remember if they were when I made my last clean install of the beta.  I always head for the terminal when I install Ubuntu and uninstall swfdec and gnash.

---

### Post by linbetwin on 2009-10-18
swfdec and gnash are not installed.

---

### Post by linbetwin on 2009-10-18
Now it seems to work on YouTube, too. I don't know for how long. The Fullscreen and Play/Pause buttons work. And all I did was turn Desktop Effects off and back on.

---

### Post by 00ber n00b on 2009-10-19
> **linbetwin said:**
> Now it seems to work on YouTube, too. I don't know for how long. The Fullscreen and Play/Pause buttons work. And all I did was turn Desktop Effects off and back on.

I'm having the same problem.  I deinstalled/reinstalled flash and restricted extras.  It plays for a while and is very  choppy.  Then it goes back to not playing at all.

---

### Post by 00ber n00b on 2009-10-19
Something to do with Karmic?!?

---

### Post by 00ber n00b on 2009-10-20
First I ensured I had a 64 bit system, check.  Then I ensured I had a 64 bit OS, check. Then I ensured I had a 64 bit browser, check.  Then I installed the 64 bit adobe flash player(alpha stage of course). I can now play embedded youtube videos, unlike before, but they are choppy.  It seems the only problem I'm having thus far is with youtube.

---

### Post by bigbroantonio on 2009-10-30
Same problem here.  Flash works okay, but on some youtube videos (yes, only some) I can't control anything (playback, fullscreen etc).

For example, if I want to watch 
[http://www.youtube.com/watch?v=gRsM_rU_80g&feature=fvst ]("http://www.youtube.com/watch?v=gRsM_rU_80g&feature=fvst")
I can't control anything.

On the other hand, if I want to watch 
[http://www.youtube.com/watch?v=9FdcS83kCZ0&feature=related]("http://www.youtube.com/watch?v=9FdcS83kCZ0&feature=related") 
everythig works okay.

Disabling the compiz eyecandy effects (system>preferences>appearance) there is no problem on any video.

I'm running 64bit Karmic (9.10) freshly installed this morning.  No other software has been installed other than flash, using this script:

```
#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com
# Super minor updates by jason.melton[at]gmail[dot]com
# Updates by Alejandro Cuervo 3[at]cuervo[dot]net
# more very minor updates by damien[at]groovey[dot]com
# Released under GPL

echo "Closing Firefox"
sudo killall -9 firefox

echo "Downloading and instaling Getlibs for required libraries"
wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
sudo dpkg -i getlibs-all.deb

echo "Removing previous installs of flash:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10"
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar zxvf install_flash_player_10_linux.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so that firefox can see them."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Done :-)"
echo "You may re-start Firefox now"
```

I got the code from [here]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html#comment-150888") and edited the wget link to the most recent adobe release.

Any ideas?

---

### Post by raesene on 2009-10-30
> **bigbroantonio said:**
> Same problem here.  Flash works okay, but on some youtube videos (yes, only some) I can't control anything (playback, fullscreen etc).

For example, if I want to watch 
[http://www.youtube.com/watch?v=gRsM_rU_80g&feature=fvst ]("http://www.youtube.com/watch?v=gRsM_rU_80g&feature=fvst")
I can't control anything.

On the other hand, if I want to watch 
[http://www.youtube.com/watch?v=9FdcS83kCZ0&feature=related](http://www.youtube.com/watch?v=9FdcS83kCZ0&feature=related) 
everythig works okay.



Can't immediately help, just to say I've got the exact same problem as well (those two youtube vids are a good example).   Upgrade from Jaunty to Karmic just after release, 64-bit...

---

### Post by cenzorrll on 2009-10-30
i had the same problems here, installed the flash plugin through synaptic.

the only way i've found to solve it is to just turn compiz off (no desktop effects)

---

### Post by litecomp on 2009-10-30
Same problem here. The only solution, by now, is switch off COMPIZ effects. Any solution?

[URL="http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1259102"]
[/URL]

---

### Post by gamblor01 on 2009-10-30
Same problem for me too.  I had to turn off all compiz effects and then restart X (either logout of gnome or just ctrl+alt+backspace).  Once I did that, everything started working.  I have since enabled compiz again and it's still working -- so I'm not sure how long it will take before things go awry.


about:plugins shows the following

```

**Shockwave Flash**

 File name:  npwrapper.libflashplayer.so Shockwave Flash 10.0 r32

MIME                               Type            Description  Suffixes   Enabled
application/x-shockwave-flash     Shockwave        Flash        swf        Yes
application/futuresplash          FutureSplash     Player       spl        Yes

```
I am currently running 9.04 64-bit with the 2.6.28-16.generic kernel.  Not sure when this started...

---

### Post by jhawk on 2009-10-31
Ubuntu 64 and flash work fine for me but I downloaded the real flash beta 64 bit aka libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz.

However, in Google Chromium I do have erratic moments, but firefox works like a champ with or without compiz.

[http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

Hope this helps.

jhawk

---

### Post by MidBSD on 2009-10-31
> **bigbroantonio said:**
> Same problem here.  Flash works okay, but on some youtube videos (yes, only some) I can't control anything (playback, fullscreen etc).

For example, if I want to watch 
[http://www.youtube.com/watch?v=gRsM_rU_80g&feature=fvst ]("http://www.youtube.com/watch?v=gRsM_rU_80g&feature=fvst")
I can't control anything.

On the other hand, if I want to watch 
[http://www.youtube.com/watch?v=9FdcS83kCZ0&feature=related]("http://www.youtube.com/watch?v=9FdcS83kCZ0&feature=related") 
everythig works okay.

Any ideas?


I have some more info on this.

It looks as if the plugin itself itself isn't inconsistent with the way it works for each of these videos but rather how each of these videos is played-back (perhaps different Youtube players).

If you click on the blank screen and then press the tab key, you'll see a yellow box surrounding certain flash elements.

Once it's on the Play button, if you click Enter, it'll start playing fine.

If you go to a video that plays straight off the bat (e.g. your second link) and hover over the volume icon or the resize screen icon and wait for the slider to extend up, you'll also note that you're no longer able to control the playback slider.

I'm guessing that it's got something to do with what version of the Youtube player is loaded but this is just conjecture.

---

### Post by bigbroantonio on 2009-10-31
> **jhawk said:**
> Ubuntu 64 and flash work fine for me but I downloaded the real flash beta 64 bit aka libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz.

However, in Google Chromium I do have erratic moments, but firefox works like a champ with or without compiz.

[http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

Hope this helps.

jhawk

If you check out the code I used to install you'll see that the code that installs flash fetches the installer (using wget) from [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)

which is the "real" flash player prerelease.

OMG, I just noticed a SERIOUS error in the change I made in the code I posted earlier... I'll be back if I have anything...

---

### Post by absinthe on 2009-10-31
I've been fixing this by downloading the alpha plugin from here:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

and extracting it in ~/.mozilla/plugins/

If that folder does not exist, create it.

Also make sure you remove the package flashplugin-nonfree or whatever it is through Synpatic first as we don't want conflicting issues.

This works flawlessly for me on every different distro of Linux right now.

---

### Post by bigbroantonio on 2009-10-31
:pOkay, I got it working on my machine.:p

The error I had made was that , when editing the code, I only changed the file that was fetched with wget, but the next line (which extracts the contents using "tar") did so from the PREVIOUS downloaded file (which wasn't the prerelease).

Here's the fixed code, which works perfectly on my x64 9.10 Ubuntu Karmic Koala:
```
#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com
# Super minor updates by jason.melton[at]gmail[dot]com
# Updates by Alejandro Cuervo 3[at]cuervo[dot]net
# more very minor updates by damien[at]groovey[dot]com
# and one more update by Antonio Cassano bigbroantonio[at]yahoo[dot]it
# Released under GPL

echo "Closing Firefox"
sudo killall -9 firefox

echo "Downloading and instaling Getlibs for required libraries"
wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
sudo dpkg -i getlibs-all.deb

echo "Removing previous installs of flash:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10"
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so that firefox can see them."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Done :-)"
echo "You may re-start Firefox now"
```

It will install the most recent release (pre) from adobe and install it on your system.

Hope this helps...

---

### Post by sleemanj on 2009-10-31
> **bigbroantonio said:**
> 

It will install the most recent release (pre) from adobe and install it on your system.

Hope this helps...

Script above is broken, this link is 404'd.

[http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)

---

### Post by bigbroantonio on 2009-10-31
> **sleemanj said:**
> Script above is broken, this link is 404'd.

[http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)

Well, it worked for me not so long ago... but yes, the link is now 404'd.

It's thus just a matter of finding the **getlibs.all.deb** from elsewhere.  I uploaded a copy I just googled, but I can't be sure that it works.

I suppose, until the boundlesssupremany site is back again, one could download from here (if it's allowed - sorry if it isn't, moderator) and run:

**sudo dpkg -i getlibs-all.deb**

from terminal (in the file's directory)

and then just run the rest of the script from  line 17 onwards.

Right?

---

### Post by bigbroantonio on 2009-10-31
At this point, it should work with the following script:

```
#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com
# Super minor updates by jason.melton[at]gmail[dot]com
# Updates by Alejandro Cuervo 3[at]cuervo[dot]net
# more very minor updates by damien[at]groovey[dot]com
# and one more update by Antonio Cassano bigbroantonio[at]yahoo[dot]it
# Released under GPL

echo "Closing Firefox"
sudo killall -9 firefox

echo "Downloading and instaling Getlibs for required libraries"
wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb
sudo dpkg -i getlibs-all.deb

echo "Removing previous installs of flash:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10"
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so that firefox can see them."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Done :-)"
echo "You may re-start Firefox now"
```

This should work.  Let me know.

---

### Post by zob on 2009-10-31
Thanks a lot bigbroantonio. The script solved my problem with flash, 64bit and compiz on 9.10.

---

### Post by psychok9 on 2009-10-31
Why you install the 32-bit wrapper if, after, you download 64-bit native flash plugin? Why you broke the link for the wrapper? Isn't more simple download & use 64-bit native plugin at the moment?
I don't understand the script.
Thanks

---

### Post by markola on 2009-10-31
I have the same problem but have found that flash in opera operates better than the supported browser firefox... weird!

---

### Post by DodgeV83 on 2009-10-31
> **bigbroantonio said:**
> At this point, it should work with the following script:

```
#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com
# Super minor updates by jason.melton[at]gmail[dot]com
# Updates by Alejandro Cuervo 3[at]cuervo[dot]net
# more very minor updates by damien[at]groovey[dot]com
# and one more update by Antonio Cassano bigbroantonio[at]yahoo[dot]it
# Released under GPL

echo "Closing Firefox"
sudo killall -9 firefox

echo "Downloading and instaling Getlibs for required libraries"
wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb
sudo dpkg -i getlibs-all.deb

echo "Removing previous installs of flash:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10"
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so that firefox can see them."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Done :-)"
echo "You may re-start Firefox now"
```

This should work.  Let me know.

With the normal flash from synaptic, hulu and southparkstudios.com work, but I can't go full screen.  With the x64 alpha version of flash, everything works on all videos (including buttons with compiz running), but Hulu and some other websites just crash the browser.

Does this script get hulu working with the x64 flash?  Try this link and let me know:

[http://www.hulu.com/watch/105441/community-introduction-to-statistics](http://www.hulu.com/watch/105441/community-introduction-to-statistics)

---

### Post by mcpish on 2009-10-31
> **bigbroantonio said:**
> :pOkay, I got it working on my machine.:p

The error I had made was that , when editing the code, I only changed the file that was fetched with wget, but the next line (which extracts the contents using "tar") did so from the PREVIOUS downloaded file (which wasn't the prerelease).



Thank you very much, I was pulling out my hair trying to get Flash/youtube to work in x64 9.10   

Your script worked perfect.  Excellent!

---

### Post by Yellow Pasque on 2009-11-01
That script is weird. It gets the 64-bit plugin and then tries to wrap it with nspluginwrapper.

---

### Post by bigbroantonio on 2009-11-01
> **Temüjin said:**
> That script is weird. It gets the 64-bit plugin and then tries to wrap it with nspluginwrapper.

Yes, you're right.

As I said earlier, though, I actually just grabbed the script from another site - all I did was edit in so that it grabs the most recent x64 flash installer from adobe and the getlibs from a site that actually is working at the moment ([http://www.boundlesssupremacy.com/Ca...etlibs-all.deb](http://www.boundlesssupremacy.com/Ca...etlibs-all.deb) is not working).

I can't see any reasons for the nspluginwrapper, so I suppose changes can be made...

I'll check a few things out and be back....

---

### Post by DodgeV83 on 2009-11-01
> **bigbroantonio said:**
> Yes, you're right.

As I said earlier, though, I actually just grabbed the script from another site - all I did was edit in so that it grabs the most recent x64 flash installer from adobe and the getlibs from a site that actually is working at the moment ([http://www.boundlesssupremacy.com/Ca...etlibs-all.deb](http://www.boundlesssupremacy.com/Ca...etlibs-all.deb) is not working).

I can't see any reasons for the nspluginwrapper, so I suppose changes can be made...

I'll check a few things out and be back....

Can you watch full screen Hulu?

[http://www.hulu.com/watch/105441/community-introduction-to-statistics](http://www.hulu.com/watch/105441/community-introduction-to-statistics)

---

### Post by bigbroantonio on 2009-11-01
> **DodgeV83 said:**
> Can you watch full screen Hulu?

[http://www.hulu.com/watch/105441/community-introduction-to-statistics](http://www.hulu.com/watch/105441/community-introduction-to-statistics)

I, personally, can't, because I'm outside the US, and hulu won't stream out of the US.

Are you having problems with hulu?

---

### Post by ruffneck on 2009-11-01
I have the same issue as well, it's been that way before upgrading from Jaunty to Koala.

---

### Post by bigbroantonio on 2009-11-01
> **ruffneck said:**
> I have the same issue as well, it's been that way before upgrading from Jaunty to Koala.

Couldn't it just be that the swf is not working right?

What about on other browsers/os - anyone having issues with hulu?

---

### Post by jwvraets on 2009-11-01
I had the same problem - a choice between having YouTube videos or Compiz. Sadly I removed Compiz. Hopefully a solution is found and I can have both but this works for now since YouTube is more important to me than Compiz effects

---

### Post by bigbroantonio on 2009-11-02
> **jwvraets said:**
> I had the same problem - a choice between having YouTube videos or Compiz. Sadly I removed Compiz. Hopefully a solution is found and I can have both but this works for now since YouTube is more important to me than Compiz effects

Have you tried the script I posted earlier?

---

### Post by P.KO on 2009-11-02
Hi bigbroantonio,

Like others have noticed earlier, your script is installing 32 bits libraries and a wrapper for 32 bit. So I would be a little more careful with your script especially when you don't understand the script yourself. ;)

> As I said earlier, though, I actually just grabbed the script from another site - all I did was edit in so that it grabs the most recent x64 flash installer from adobe and the getlibs from a site that actually is working at the moment ([http://www.boundlesssupremacy.com/Ca...etlibs-all.deb](http://www.boundlesssupremacy.com/Ca...etlibs-all.deb) is not working).

Actually you only need to download [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") and then unpack it.

Then you only need to place the unpacked file libflashplayer.so in /usr/lib/mozilla/plugins.

---

### Post by kehon on 2009-11-02
thank you very much that fixed it. glad I kept reading before I tried the script

---

### Post by JoseRijo on 2009-11-02
I've had some issues with 64-bit flash on my new 9.10 install.  If I put libflashplayer.so in /usr/lib/mozilla/plugins, I get "javascript not responding" errors and a white screen where the flash should be.  But if I use ~/.mozilla/plugins/ then everything seems to work great.

---

### Post by bigbroantonio on 2009-11-02
> **P.KO said:**
> Hi bigbroantonio,

Like others have noticed earlier, your script is installing 32 bits libraries and a wrapper for 32 bit. So I would be a little more careful with your script especially when you don't understand the script yourself. ;)



Actually you only need to download [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") and then unpack it.

Then you only need to place the unpacked file libflashplayer.so in /usr/lib/mozilla/plugins.

Yes, I agree.  As I said earlier, it's not "my" script.  It's just something suggested from elsewhere that, as I said, I had to check up on - funny enough it works for me and a few others, though!  I'm sorry if it broke anything for anyone.:(

I love ubuntu, but I still think it's such a shame that some minor things (like installing flash) could be so "dangerous".

---

### Post by ruffneck on 2009-11-04
> **P.KO said:**
> Actually you only need to download [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") and then unpack it.

Then you only need to place the unpacked file libflashplayer.so in /usr/lib/mozilla/plugins.

I've tried this and it actually crashes the browser for me. This happening to anyone else?

---

### Post by JoseRijo on 2009-11-04
> **ruffneck said:**
> I've tried this and it actually crashes the browser for me. This happening to anyone else?

Did you see my post?  Did you try to put it in your ~/.mozilla/plugins/ directory instead?

---

### Post by nixed242 on 2009-11-05
> **DodgeV83 said:**
> With the normal flash from synaptic, hulu and southparkstudios.com work, but I can't go full screen.  With the x64 alpha version of flash, everything works on all videos (including buttons with compiz running), but Hulu and some other websites just crash the browser.

Does this script get hulu working with the x64 flash?  Try this link and let me know:

[http://www.hulu.com/watch/105441/community-introduction-to-statistics](http://www.hulu.com/watch/105441/community-introduction-to-statistics)

Has anyone tried installing the 64 bit Flash and disabling Compiz to see if that keeps Hulu from Crashing Firefox? 

I played around with Compiz last night and turned off a few of the settings such as zoom and the mouse plug-in which tracks the pointer's movements. It may have been my imagination, but Hulu's buttons seemed more responsive after turning them off. 

Compiz is buggy, and so is flash. I had to turn Wobbly Windows off. It was the only way I could properly play a DVD in Totem Fullscreen and not having it crash on Exit.

Found this workaround in another thread. Don't know if it'll work for everyone:

> 
As long as you have the right mouse button held down, the Flash object correctly detects the left mouse button. Of course, right-clicking usually brings up some kind of context menu so you will need to left-click out of that menu first.

---

### Post by ruffneck on 2009-11-05
> **JoseRijo said:**
> Did you see my post?  Did you try to put it in your ~/.mozilla/plugins/ directory instead?



Hi JoseRijo. I did try that as well but FF 3.5x crashes. Inthe Chromium browser, an error states that the plugin has crashed.

---

### Post by hayim on 2009-11-08
> **JoseRijo said:**
> Did you see my post?  Did you try to put it in your ~/.mozilla/plugins/ directory instead?

Hey thanks man this worked for me!

Flash, hulu, youtube all playing again.

One day I hope we'll be able to laugh about this without also crying..
[http://xkcd.com/619/](http://xkcd.com/619/)

---

