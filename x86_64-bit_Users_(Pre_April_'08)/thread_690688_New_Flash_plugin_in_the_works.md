---
title: "New Flash plugin in the works?"
date: 2008-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by maximilion on 2008-02-07
Installed Ubuntu yesterday, heard (read) on IRC today that a new 64-bit version is coming to a mirror near me soon ;)

So I decided to wait for it.

I read the sticky, I have a couple of questions:

1. Will the new plugin be as fast as the r48 one?
2. Which of those can be used in Opera?

Naturally, yesterday I used a) UbuFox to get Flash, when that failed I used Synaptic to get the restricted, when that failed I tried Gnash, which also didn't work. (Or maybe it was Gnash I installed via Ubufox. Unsure.)

More questions arose now :)

3. Do I really need Ubufox at all, if I follow plugin install instructions?
4. How do I completely remove any Flash/Gnash from all browsers? Just remove in Synaptic?

---

### Post by Kilz on 2008-02-07
> **maximilion said:**
> Installed Ubuntu yesterday, heard (read) on IRC today that a new 64-bit version is coming to a mirror near me soon ;)

So I decided to wait for it.

I read the sticky, I have a couple of questions:

1. Will the new plugin be as fast as the r48 one?
2. Which of those can be used in Opera?

Naturally, yesterday I used a) UbuFox to get Flash, when that failed I used Synaptic to get the restricted, when that failed I tried Gnash, which also didn't work. (Or maybe it was Gnash I installed via Ubufox. Unsure.)

More questions arose now :)

3. Do I really need Ubufox at all, if I follow plugin install instructions?
4. How do I completely remove any Flash/Gnash from all browsers? Just remove in Synaptic?

You may want to try my script, it has a sticky post in this section of the forum. It can install the r48 or r115 plugin.  It will try to remove failed attempts to install flash, but if you can try and remove them first, Synaptic is a good place to uninstall things. Im not sure about Opera, but copying the plugin to its plugin folder might work.

---

### Post by FooAtari on 2008-02-08
I made a separate thread about this, but perhaps I can just hijack this thread for a moment :)

Is there any advantage to installing 32-bit firefox over using the ndiswrapper to install the plugin for 64bit FF? Or visa versa.

---

### Post by Kilz on 2008-02-08
> **FooAtari said:**
> I made a separate thread about this, but perhaps I can just hijack this thread for a moment :)

Is there any advantage to installing 32-bit firefox over using the ndiswrapper to install the plugin for 64bit FF? Or visa versa.

Ok. first off the wrapper for flash is nspluginwrapper. The advantage of running 32bit firefox is java. There is at present no 64bit Sun Java plugin. There is icedtea and blackdown (blackdown is real old) java, but they dont work on all java sites. If you dont need java or the icedtea plugin works for your sites use the 64bit browser. But if not 32bit firefox only takes a few minutes to install. You can aslo install both if you have the room and they will not conflict.

---

### Post by FooAtari on 2008-02-08
Thanks for that.  32bit it is then, having lots of Java problems too.

Hopefully Adobe/Sun pull their fingers out of their bums soon and get things sorted...

---

### Post by maximilion on 2008-02-08
> **Kilz said:**
> Ok. first off the wrapper for flash is nspluginwrapper. The advantage of running 32bit firefox is java. There is at present no 64bit Sun Java plugin. There is icedtea and blackdown (blackdown is real old) java, but they dont work on all java sites. If you dont need java or the icedtea plugin works for your sites use the 64bit browser. But if not 32bit firefox only takes a few minutes to install. You can aslo install both if you have the room and they will not conflict.

Thanks, 32-bit it is then. I will also look here for tips for Opera, which is my by far preferred browser. (I do keep Firefox for some nice plugins like WebDev and Firebug ;))

I will try just putting the flash plugin in its plugins subdirectory.

---

### Post by Kilz on 2008-02-08
> **FooAtari said:**
> Thanks for that.  32bit it is then, having lots of Java problems too.

Hopefully Adobe/Sun put their fingers out of their bums soon and get things sorted...

Sun will, there will be a 64bit plugin when Sun Java 7 is released.

---

### Post by FooAtari on 2008-02-08
Great.  Do we know when 7 is released?

---

### Post by Kilz on 2008-02-08
> **FooAtari said:**
> Great.  Do we know when 7 is released?
Nope, its still in development and no plugin is available yet.

---

### Post by Cappy on 2008-02-08
Opera has a plugin path of
/usr/lib/opera/plugins:/usr/lib/mozilla/plugins:/usr/lib/flashplugin-nonfree

It will use firefox's flash plugin directory. No extra setup should be needed unless you use the 64-bit Opera and then there are some additional steps dealing with replacing the 64-bit operapluginwrapper with the 32-bit operapluginwrapper from the 32-bit install. There are threads on that if you really want the Opera 64-bit version.

---

### Post by maximilion on 2008-02-08
> **Cappy said:**
> Opera has a plugin path of
/usr/lib/opera/plugins:/usr/lib/mozilla/plugins:/usr/lib/flashplugin-nonfree

It will use firefox's flash plugin directory. No extra setup should be needed unless you use the 64-bit Opera and then there are some additional steps dealing with replacing the 64-bit operapluginwrapper with the 32-bit operapluginwrapper from the 32-bit install. There are threads on that if you really want the Opera 64-bit version.

Didn't get that path ;) but yeah, I decided to use 32-bit Ubuntu on my amd64 for ease of use, basically. I'm on 

Opera/9.25 (X11; Linux i686; U; en)

So if you say doing get-apt flashplugin-nonfree will update FF and Opera without any more work, I guess I'll just remove the Gnash etc and try again :)

Thanks Cappy!

---

