---
title: "Firefox 3 &amp; Ubuntu 7.10 64 bits =&gt; no video plugins"
date: 2008-07-15
forum: x86 64-bit Users
---

### Post by jemdos on 2008-07-15
Greetings from Sunny Spain 8)

I've recently installed firefox v3 on my ubuntu 7.10 box, following the instructions I found on [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion) and a couple of places more. 

It's set up on /opt/firefox. A simbolic link from there redirects to the /usr/lib/firefox/plugins folder, where I basically have two plugins: flash and mplayer.

Good news are that the flash player works, but the bad news are the mplayer plugin (or other video plugins I tried) don't. They worked great with firefox 2, but simply don't even load on firefox 3 (they do not appear under about:plugins) :confused:

It looks like something is preventing those video plugins from loading to firefox, but I do not what. I've googled around and I haven't seen anything that works to me. 

Please help me. I've run out of ideas (although that's quite easy in my case). Thanks for reading this.

---

### Post by Cappy on 2008-07-15
That guide installs the 32-bit firefox. The mplayer and other media plugins (other than flash) are 64-bit and won't work in a 32-bit browser. I don't know where to install 64-bit Firefox 3, I haven't done that yet.

---

### Post by stchman on 2008-07-15
> **jemdos said:**
> Greetings from Sunny Spain 8)

I've recently installed firefox v3 on my ubuntu 7.10 box, following the instructions I found on [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion) and a couple of places more. 

It's set up on /opt/firefox. A simbolic link from there redirects to the /usr/lib/firefox/plugins folder, where I basically have two plugins: flash and mplayer.

Good news are that the flash player works, but the bad news are the mplayer plugin (or other video plugins I tried) don't. They worked great with firefox 2, but simply don't even load on firefox 3 (they do not appear under about:plugins) :confused:

It looks like something is preventing those video plugins from loading to firefox, but I do not what. I've googled around and I haven't seen anything that works to me. 

Please help me. I've run out of ideas (although that's quite easy in my case). Thanks for reading this.

All you have to do to install Firefox 3 in Gutsy is to:

1.  Make sure the Universe repositoty is enabled.
2.  Install Firefox using the following command:

```
sudo apt-get install firefox-3.0
```

The tutorial you followed was to install Firefox 3.0 from Mozilla website using the precompiled binary.

---

### Post by jemdos on 2008-07-16
Greetings from Sunny Spain 8)

First of all, thanks a lot for taking the time & patience to teach a newbie like me... that always will be a newbie, after all. 8/

I had to realize it was the 32/64 bits plugin stuff that prevented the video to work properly on firefox 3, I was just badly biased because flash did work. 8(

And getting the "firefox-3.0" from the universe repository is not an option because it is still is an alpha version!

---

