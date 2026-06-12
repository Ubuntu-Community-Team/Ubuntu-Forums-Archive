---
title: "64bit flash, failures, successes and solutions"
date: 2009-07-22
forum: x86 64-bit Users
---

### Post by dlmarti on 2009-07-22
Sorry for the length of this post, I wanted to get all the information to (hopefully) someone who would understand it.

Couple weeks ago I got a new pc (big Xeon server dirt cheap).  I loaded the 32bit version of Juanty on it, and everything worked fine.

I order 4G of more ram (already had 2G), once installed Linux only recognized 3G of it (missing 6G).

I then installed the 64bit version of Jaunty, everything worked (flash, java, everything).

At one point I downloaded virtualbox (to try out windows 7), during the downloading of windows 7 it showed the screen for the product key.  I figured that would be a good thing to print out so I had Jaunty auto-detect my HP 1320n and print out the page.  During the detecting it installed a bunch of drivers and stuff, but I never gave it much thought.

Away I went with the Virtualbox and Windows setup, along with configuring a bunch of software (Linux stuff) I needed for work.  During a break I tried to jump on the web and play a game, but my flash no longer worked.

I spent a day debugging but to no avail, I gave up and reinstalled 64bit Jaunty and everything worked again.

After several days of everything working fine, I decided to setup the printer again, low and behold the minute I did Flash stopped working. I was like WTF?

This is the list of packages that the printer tool decided to load in order to support my printer:
libqt4-assistant.
libqt4-opengl.
libqt4-gui.
dpkg-dev.
html2text.
gettext.
intltool-debian.
po-debconf.
debhelper.
libbeecrypt6.
librpm4.4.
rpm.
alien.
postfix.
bsd-mailx.
libstdc++6-4.3-dev.
g++-4.3.
g++.
build-essential.
libsys-hostname-long-perl.
libmail-sendmail-perl.
libqt3-mt.
m4.
mailx.
ncurses-term.
pax.
lsb-core.
lsb-graphics.
lsb-cxx.
lsb-desktop.
lsb.
openprinting-ppds-postscript-hp.

I kid you not, what a cluster ......

I figured one of these was messing up my flash, but I had no clue where to start.

When I removed these files, flash started working again:
openprinting-ppds-postscript-hp ... 
lsb ... 
lsb-desktop ... 
libqt4-gui ... 
libqt4-assistant ... 

[B]Install them again, flash stops working.
Uninstall them again, flash starts working.[/B]

Your mileage may vary, but this is obviously something that someone with some knowledge needs to look into.

btw, the printer works just fine without them.

---

### Post by Yellow Pasque on 2009-07-22
Any terminal output from a "no Flash" session of Firefox?
Also, please clarify which Flash plugin you were using (64-bit or 32-bit with nspluginwrapper).

---

### Post by dlmarti on 2009-07-22
> **Temüjin said:**
> Any terminal output from a "no Flash" session of Firefox?
Also, please clarify which Flash plugin you were using (64-bit or 32-bit with nspluginwrapper).

Command line run of firefox, during a a problem indicates an Invalid code opcode.  No indication of where the invalid code is (which module/library, etc)

This is with the 64bit flash, but switching to the 32bit with the wrapper during the problem does not solve the issue.

---

### Post by condamine on 2009-09-02
I've been struggling with this as well. I am about to try the 64bit Alpha from Adobe on a Dell XPSM1330 runing 64bit Jaunty.

I've tried both synaptic offerings, both 32 bit packages. Neither worked for me. They are:

> flashplugin-installer
Adobe Flash Player plugin installer
Depends nspluginwrapper (and a whole other bunch of 32bit libs)
AND
adobe-flashplugin
Adobe Flash Player plugin version 10
(Depends on many lib32 etc)


A google search returned quite a few results and I reckon these are the best (and most recent) guides...

[[COLOR="Blue"]Installing 64bit Flash Player in Ubuntu Linux; Kevin's Life[/COLOR]]("http://blog.lckymn.com/2009/06/07/installing-64bit-flash-player-in-ubuntu-linux/")
[[COLOR="Blue"]Real 64-bit Flash on amd64; Me and U(buntu)[/COLOR]]('http://meandubuntu.wordpress.com/2008/11/18/real-64-bit-flash-on-amd64/')
The first url links to an earlier release of the 64bit alpha that may be better?

This is the link to the latest release from Adobe (impossible to find from the normal Get adobe download pages)
[[COLOR="Blue"]10.0.32.18.linux-x86_64 Apha[/COLOR]]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz")
[[COLOR="Blue"]Read about it here at Adobe labs[/COLOR]]("http://labs.adobe.com/downloads/flashplayer10.html")


I'll report back soon to let you know if it was a success or failure!

Yep worked fine for Youtube but still not working for ABC TV Iview. I don't see any huge increase in the CPU usage as reported by others.

I installed here ... [B]/usr/lib/firefox-addons/plugins
[/B]
But got a broken link with this command (wanting to be able to use the plugin with other mozilla apps)

**JoeBlogs@TUX:/usr/lib/mozilla/plugins$ sudo ln -s /usr/lib/firefox/plugins/libflashplayer.so**

---

### Post by michael37 on 2009-09-02
IMO the only trick of correctly installing 64-bit flash is getting rid of everything else.

Make sure that your /usr/lib/firefox-addons/plugins, /usr/lib/firefox/plugins, /usr/lib/mozilla-firefox/plugins and /usr/lib/mozilla/plugins contain *the one and the only* file that contains flash and that file is
```
/usr/lib/firefox-addons/plugins$ file libflashplayer.so 
libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped

```

Works for me well in both FF 3.0 and 3.5.

---

