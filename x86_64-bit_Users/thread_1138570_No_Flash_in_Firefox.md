---
title: "No Flash in Firefox"
date: 2009-04-26
forum: x86 64-bit Users
---

### Post by j_freeman on 2009-04-26
I'm posting this in the AMD 64 forum because I never had this problem on i386, although that was 8.10 and not 9.04 (which I'm now running).

I've read all the HOWTO's on getting Flash running on this platform. I tried Adobe's Flash 10 plugin, as well as Gnash's plugin. (I made sure to uninstall Adobe's before installing Gnash's.)

Both plugins showed up in "about:****plugins" in Firefox. The problem is that Flash apps aren't displayed in the browser. I've attached what I see when I visit [this YouTube video]("http://www.youtube.com/watch?v=Gd4_TlIKcU0").

Any ideas? All help is very much appreciated!

---

### Post by mattlach on 2009-04-26
I have this same problem.

Plugins are installed and enabled (show up on about: plugins) but don't work.

Its disappointing because I had this set up to work in 8.10 though the windows plugin wrapper, but after upgrading all I get is a white box where the flash content should have been...

---

### Post by mattlach on 2009-04-26
> **mattlach said:**
> I have this same problem.

Plugins are installed and enabled (show up on about: plugins) but don't work.

Its disappointing because I had this set up to work in 8.10 though the windows plugin wrapper, but after upgrading all I get is a white box where the flash content should have been...

Actually, I take that back.

I downloaded the scripts from the 64bit flash/java thread and executed them both and now everything just works....

---

### Post by bford16 on 2009-04-26
There seems to be a bug in the install process for the flash plugin.  I did two clean installs (of Jaunty Jackalope 9.04) this weekend, and both suffered the same problem.  Upon installing 'ubuntu-restricted-extras,' it appeared that 'flashplugin-nonfree' was installed.  However the plugin itself was NOT actually installed.  To shorten the story, I fixed the problem like this:```
sudo apt-get remove flashplugin-installer flashplugin-nonfree
```Then,```
sudo apt-get install flashplugin-installer
```This caused the flash plugin to install correctly. I cannot tell you WHY this works, but it does.

---

### Post by TheBuzzSaw on 2009-04-26
> **bford16 said:**
> There seems to be a bug in the install process for the flash plugin.  I did two clean installs (of Jaunty Jackalope 9.04) this weekend, and both suffered the same problem.  Upon installing 'ubuntu-restricted-extras,' it appeared that 'flashplugin-nonfree' was installed.  However the plugin itself was NOT actually installed.  To shorten the story, I fixed the problem like this:```
sudo apt-get remove flashplugin-installer flashplugin-nonfree
```Then,```
sudo apt-get install flashplugin-installer
```This caused the flash plugin to install correctly. I cannot tell you WHY this works, but it does.
This helped, but now I have no sound in YouTube! :(

---

