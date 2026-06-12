---
title: "adobe flash plugin 10 works bad on ubuntu 8.10 64 bit"
date: 2009-01-21
forum: x86 64-bit Users
---

### Post by Wanas on 2009-01-21
I am always using ubuntu 32 bit and adobe flash plugin works great 9 and 10,
but when I installed ubuntu iterpid 64 bit and installed adobe flash plugin 10 when the firefox told me to install missing plugins and after the install it works bad always a white screen and nothing loading.

What is the best way to fix this?
and is the other flash players plugins good too like (gnash) ?

---

### Post by utnubuuser on 2009-01-21
Hi -- Try using the flash-plugin from synaptic.  --Uninstall the from the add-ons/tools section of Firefox, then re-install through synaptic.  
I'm suggesting this because I've read plenty of posts regarding probs with flash in 64.
Some people had problems with flash (32 ans 64 bit users) if they installed through Firefox rather than through synaptic.
"flash-plugin non-free"

---

### Post by philinux on 2009-01-21
Uninstall any flash you have. Go to adobe [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) and download the tar.gz for linux. 
Extract the archive. In the ~/.mozilla folder create a folder called plugins. 
Copy the libflashplayer.so file from your desktop to this new folder. Restart FF.

---

### Post by stmiller on 2009-01-21
Yeah you'll have to manually remove the old 32bit flash, and install the 64bit one from adobe manually.

64bit flash with 64bit firefox works great for me.

---

### Post by stchman on 2009-01-21
> **Wanas said:**
> I am always using ubuntu 32 bit and adobe flash plugin works great 9 and 10,
but when I installed ubuntu iterpid 64 bit and installed adobe flash plugin 10 when the firefox told me to install missing plugins and after the install it works bad always a white screen and nothing loading.

What is the best way to fix this?
and is the other flash players plugins good too like (gnash) ?

Try using the Flash 10 64 bit.  I will assume you installed the flashplugin-nonfree package.

```
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
sudo apt-get autoremove flashplugin-nonfree
tar -C ~/mozilla/plugins -xvzf ~/libfla*
rm -f ~/libfla*
```

This will uninstall the 32 bit flashplugin and install the 64 bit Flash 10 plugin.  I use this on my 64 bit Hardy boxes.

---

### Post by Arup on 2009-01-21
I just added the libflashplayer.so to usr/lib/mozila/plugins after extracting it from the tar and both FF and Opera works great with Flash. I make sure not to install any other version or have nsplugin installed.

---

### Post by lamborghiniwang on 2009-01-22
I am seeing huge lags when moving mouse cursor around while watching Youtube video in full screen mode. Wondering if anybody else is having the same issue. The full screen flash video plays fine if I do not move my mouse.

64-bit Intrepid on a Thinkpad T61p(Nvidia Quadro FX 570M), 64-bit flashplayer 10, both 177.82 and 180.22 driver are affected.

Anyone?

---

### Post by wfp on 2009-01-22
Same here but really never noticed until you mentioned it, i guess i never move my mouse around when i am watching videos in full screen. The flash in 32-bit worked  better for me. But the 64bit flash from adobe is still beta.

---

### Post by lamborghiniwang on 2009-01-22
Just found the following bug report on this issue: 

[#286673]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/286673")

---

### Post by mrpurple on 2009-01-22
for what i see flash 10 in 64 bit is make working too much the cpu.
With one flash application in my firefox is working constantly over the 50% when there are two tabs with flash application is going over 80 % and this makes me in my portable very noisy because of the internal fan.
with the 32 version before 10 this wasn't happen.

[IMG]http://farm4.static.flickr.com/3331/3219178754_a33fc204ed.jpg[/IMG]

---

### Post by jaminux on 2009-01-22
I had problems with this when I re-installed. I started off downloading the Flash Plugin through Firefox and nothing showed but a gray screen where the flash should be.

I fixed the problem along with a few others by installing the package ubuntu-restricted-extras.

---

### Post by dcstar on 2009-01-25
This thread may be helpful:

[http://ubuntuforums.org/showthread.php?t=772490&highlight=intrepid](http://ubuntuforums.org/showthread.php?t=772490&highlight=intrepid)

---

### Post by kevmitch on 2009-01-25
The debian sid package worked for me in Intrepid: [http://packages.debian.org/sid/amd64/flashplugin-nonfree/download](http://packages.debian.org/sid/amd64/flashplugin-nonfree/download). It seems that Debian has been quicker on the uptake of the native 64-bit version. As far as I could tell the version in the Intrepid repositories is still using the notoriously unstable nspluginwrapper.


Kevin

---

### Post by amazing mustard on 2009-01-25
The 64-bit prerelease ( november 2008 ) worked perfect on Ubuntu 8.10 AMD64. No flash troubles for me anymore :)

Download [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz)

Follow the instructions on [http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

It takes like 2 minutes max.

---

### Post by lamborghiniwang on 2009-01-27
Tried both the Debian Sid package and the 64-bit beta downloaded directly from Adobe, both have huge lags if I move the mouse around while watching full screen Youtube video.
Upgrade to the latest Nvidia 180.25 driver doesn't solve the problem.

---

### Post by portis on 2009-01-28
It's weird. I'm using 64bit Jaunty development branch. I noticed an upgrade of flashplugin-nonfree which was based on adobe's native 64bit plugin. And then it was turned back to the nspluginwrapper.

> **kevmitch said:**
> The debian sid package worked for me in Intrepid: [http://packages.debian.org/sid/amd64/flashplugin-nonfree/download](http://packages.debian.org/sid/amd64/flashplugin-nonfree/download). It seems that Debian has been quicker on the uptake of the native 64-bit version. As far as I could tell the version in the Intrepid repositories is still using the notoriously unstable nspluginwrapper.


Kevin

---

### Post by Anubis on 2009-02-05
No problems what so ever from my system, since the plugin came out. Firefox no longer crashes, ever!

---

### Post by funky_uncle on 2009-02-05
> **philinux said:**
> Uninstall any flash you have. Go to adobe [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) and download the tar.gz for linux. 
Extract the archive. In the ~/.mozilla folder create a folder called plugins. 
Copy the libflashplayer.so file from your desktop to this new folder. Restart FF.It works with Firefox, but in Opera I can only get sound.

I found a file called pluginpath.ini in /.opera:
[I]&#65279;Opera Preferences version 2.1
; Do not edit this file while Opera is running
; This file is stored in UTF-8 encoding

[Paths]
/usr/lib/opera/plugins=1
/usr/lib/mozilla/plugins=1
/usr/lib/flashplugin-nonfree=1[/I]

So it appears Opera will try to use whatever plugins you have installed for Firefox.

---

### Post by Wanas on 2009-03-22
> **mrpurple said:**
> for what i see flash 10 in 64 bit is make working too much the cpu.
With one flash application in my firefox is working constantly over the 50% when there are two tabs with flash application is going over 80 % and this makes me in my portable very noisy because of the internal fan.
with the 32 version before 10 this wasn't happen.

[IMG]http://farm4.static.flickr.com/3331/3219178754_a33fc204ed.jpg[/IMG]

Non of the above solutions solver the cpu issue, I have tried all of them but when I open a flash media the cpu works too much and the flash works very slow in some flash videos.

---

