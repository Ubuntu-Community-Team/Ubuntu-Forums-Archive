---
title: "Firefox 3.5"
date: 2009-07-11
forum: x86 64-bit Users
---

### Post by HavocXphere on 2009-07-11
[RANT - skip to last paragraph for actual question]

Firefox is starting to annoy the hell out of me.

Installing & configuring FF3.5 on windows = 15 minutes
Installing & configuring FF3.5 on ubuntu = 1.5 hours and counting

First I tried the whole Shiretoko thing. Incompatible with the ubuntu modification add-on and funky blue icon and branding.:rolleyes: That worked OK until it got stuck installing add-ons. It continually claimed it needed to restart (it doesn't).

So I uninstalled that and grabbed the version of the mozilla site. Not being a .deb, I extracted it to somewhere and added shortcuts & icons by hand. It knew about *some* of my addons. The rest I added by hand. It also suggest I upgraded ubiquity to 0.5 which worked great.

Next: Flash. Some site pointed me to the adobe website which detected my OS as linux and provided a download link. Great...only firefox doesn't know what to do with the .deb, so I point it to gdebi-gtk manually. gdebi-gtk goes blank and freezes. So I kill that process and try it from a terminal. That at least tells me that the problem is that I can't install 32bit flash on a 64bit system. Off to adobe labs to grab the 64-bit alpha which is a tar.gz containing a .so file. Ubuntu doesn't know what to do with it and neither do I. Some googling reveals that its the extension that firefox plugins use.

One of the ubuntu wiki suggested that one must first remove all the other gnash etc versions installed which I did.

Not knowing the location, I check where the FF3.0.11 version gets the plugins from. Doesn't help since the correct .so file is already there and FF3.5 doesn't know about it. Go back to FF3.5 which claims that its now incompatible with the ubiquity 0.5 it just suggested I install.:confused: So that got downgraded to 1.9 again.

Some hunting on google reveals that firefox can show the location of plugins with plugins:about after some changes in about:config. But I don't have any in FF3.5 so thats no help.

Is it just me or is the area where ubuntu and firefox meet completely and utterly fubar? Maybe its better to run FF in WINE...

So where would I put this .so file so that FF3.5 detects it? There seem to be a gazillion places for this and none I've tried so far worked. I've tried/looked in:
InstallLocation/plugins
~/.mozilla
/usr/lib/firefox-3.0.11/plugins
/usr/lib/firefox-addons/plugins
/usr/lib64/firefox-3.0.11/plugins (The lib64 seem to be linked)
/usr/lib64/firefox-addons/plugins
/usr/lib64/mozilla/plugins
/usr/lib64/mozilla-firefox/plugins
/usr/lib/mozilla-firefox/plugins
/usr/lib/mozilla/plugins
~/.mozilla/plugins (Created. As suggested by a site)

---

### Post by Moop on 2009-07-11
Put the .so file in /home/.mozilla/plugins  You can just create the plugins folder if it's not there.

---

### Post by HavocXphere on 2009-07-11
> **Moop said:**
> Put the .so file in /home/.mozilla/plugins  You can just create the plugins folder if it's not there.
Tried that already. Doesn't work.:frown:

---

### Post by seamuso on 2009-07-12
Anyone can correct me if I'm wrong, but it's my understanding that FF 3.0x and Shiretoko were both compiled as 64bit apps specifically for the x86_64 versions. The 64bit flash plugin was written for a 64bit browser, not a 32bit.

The version of Firefox that you download from mozilla is a 32bit app, not 64bit.

When I run the 3.5 I just downloaded from mozilla, my 64bit flash plug-in doesn't show up. When I drop in a 32 bit version of the plug-in (both in ~/.mozilla/plugins ), it is recognized (shows up in tools -> addons -> plugins).

You can download the 32bit .tar.gz file, extract it, drop the .so to where it needs to be in ~/.mozilla/plugins and it should work .. I'm watching a hulu video with the listed setup ...

---

### Post by mandarke on 2009-07-12
why is firefox 3.5 not in the repositories yet?

---

### Post by HavocXphere on 2009-07-12
> **seamuso said:**
> Anyone can correct me if I'm wrong, but it's my understanding that FF 3.0x and Shiretoko were both compiled as 64bit apps specifically for the x86_64 versions. The 64bit flash plugin was written for a 64bit browser, not a 32bit.
That does make sense.:D

> **seamuso said:**
> When I run the 3.5 I just downloaded from mozilla, my 64bit flash plug-in doesn't show up. When I drop in a 32 bit version of the plug-in (both in ~/.mozilla/plugins ), it is recognized (shows up in tools -> addons -> plugins).
I'll try that a bit later when I'm in front of the PC. I totally forgot about the 32 bit plugin after gdebi said its not compatible, but your line of thought makes sense.

Thanks for the help.

@mandarke: It is (kinda), but the end result is that Shiretoko branded thing so most people grab it directly from the mozilla website. Mozilla apparently doesn't allow firefox branding to be applied to other (non-mozilla) builds.

---

### Post by mandarke on 2009-07-12
> **HavocXphere said:**
> @mandarke: It is (kinda), but the end result is that Shiretoko branded thing so most people grab it directly from the mozilla website. Mozilla apparently doesn't allow firefox branding to be applied to other (non-mozilla) builds.

i'm not seeing it under apt-get or synaptic using the official software sources.

---

### Post by Moop on 2009-07-12
You can get Firefox 3.5 from this ppa. You can either add the ppa to your software sources and use Synaptic or download and install it from the ppa. 

[https://launchpad.net/~fta/+archive/ppa]("https://launchpad.net/%7Efta/+archive/ppa")

---

### Post by HavocXphere on 2009-07-12
Seamuso was right. The x86 version is detected & youtube works. Thanks.

> **mandarke said:**
> i'm not seeing it under apt-get or synaptic using the official software sources.
Have you enabled the universe & multiverse repos? Its listed as firefox-3.5 I think.

---

### Post by philinux on 2009-07-12
> **mandarke said:**
> why is firefox 3.5 not in the repositories yet?

It's been there for jonks as FF3.5 beta, universe repo, now 3.5 release candidate I think.

[edit] sudo apt-get install firefox-3.5

---

### Post by mandarke on 2009-07-13
> **HavocXphere said:**
> Have you enabled the universe & multiverse repos? Its listed as firefox-3.5 I think.

yes, i have. but it's never showed up when i do apt-get update/upgrade via terminal.

---

### Post by e.m.fields on 2009-10-18
> **HavocXphere said:**
> 

So where would I put this .so file so that FF3.5 detects it? There seem to be a gazillion places for this and none I've tried so far worked. ...

[COLOR="Red"]**@ HavocXphere:**[/COLOR]
Did you find your solution the Flash problem yet? This has been my first annoying experience with Ubuntu and Firefox to date, but a significant one. 

ANSWER:

**/home/USER/.mozilla/plugins is the correct directory.**

You will need to purge all the previous versions of firefox & flash plugins to make sure you got it clean, otherwise FF goes looking for your plugin and finds the 32-bit version & crashes. There were a couple I was missing until I followed the instructions at the following thread: 

[http://ubuntuforums.org/showthread.php?t=1081964&highlight=flash+crashes]("http://ubuntuforums.org/showthread.php?t=1081964&highlight=flash+crashes")

Hope this solves it for you.
-fields

---

### Post by AaronLS on 2009-10-22
> **Moop said:**
> You can get Firefox 3.5 from this ppa. You can either add the ppa to your software sources and use Synaptic or download and install it from the ppa. 

[https://launchpad.net/~fta/+archive/ppa]("https://launchpad.net/%7Efta/+archive/ppa")

So I add the above URL to the Synaptic Package Manager->Settings->Repositories->Third-Part Software Tab?

---

### Post by drdos2006 on 2009-10-24
Here is what I did
Installing Adobe FlashPlayer 10 in Ubuntu 9.04 64 bit

Downloaded  libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
Extracted into /usr/lib/mozilla/plugins/

Executed from /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/firefox-addons/plugins/
plus
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

Run Firefox, all OK.
regards

---

