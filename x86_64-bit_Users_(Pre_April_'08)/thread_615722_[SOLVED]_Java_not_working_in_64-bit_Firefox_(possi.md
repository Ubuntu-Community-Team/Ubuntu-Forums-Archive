---
title: "[SOLVED] Java not working in 64-bit Firefox (possibly not at all)"
date: 2007-11-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Darksouled on 2007-11-17
Hi!

I just recenty converted myself to use Ubuntu after sticking to Windows the last 13 years, and I gotta admit that I love everything Linux has to offer compared to Windows, even with my absolute beginner skill.



However, nothing is ever as easy as it first seems. However much I have tried, I can't get Java to work in Firefox 2.

First I installed the icedtea-plugin as recommended when I tried to view a Java applet, but that didn't work. In fact, it didn't even recognize my install at all and still recommended that I installed the icedtea. 

Ok, so I ignored that, removed the icedtea-plugin and installed Sun java7 via the Synaptic Package Manager. Great, now it would surely work!? Nay! Went back into the PM and marked a whole bunch of different JRE-packages and plugins, but the Java applet (along with others) didn't show any signs of life. At least Firefox didn't recommend the icedtea plugin anymore.

Switched between the different JRE's with "update-alternatives --config java", but no luck. Tried in pure desperation to remove everything and try one at a time, but the Java applets were still dead as a graveyard.


So, with no more ideas on what to try, I wonder if any of you have had the same problem and are willing to share the (preferrably) dumbed down solution on how I may fix it.


As mentioned, I'm using the 64-bit version of Firefox and (obviously) the 64-bit Ubuntu. And by the way, haven't tried using Java on an applet outside of Firefox.

---

### Post by rsambuca on 2007-11-17
There is no Sun java web browser plugin for the 64 bit OS (Java works for applications, but no web browser plugin).  Some people have been having limited success with the Icedtea java, but it doesn't seem to work on all sites.

If you really want java for your browser, the easiest method is to install the 32bit browser and then you can easily install the 32bit flash and java plugins.  There is a simple script written by community member Kilz that does it all for you, so you just click on it and answer the questions.  You can get the info from the [first post of this thread]("http://www.ubuntuforums.org/showthread.php?t=202537").

---

### Post by Darksouled on 2007-11-17
Thanks a billion! It works like a dream now! :D

Had actually been sweeping through that thread, but somehow managed to stamp it as irrelevant. Couldn' actuallyt have been easier. Again, thanks! :)

---

### Post by dralokyn on 2007-11-17
there's a solution for being able to use 64-bit firefox and 64-bit java on your 64-bit machine. why skimp? this is what works for me, and most other people.

first, reinstall 64-bit firefox.

there are three flavors of java generally available through synaptic; sun, blackdown, and iced-tea. remove the sun-java and icedtea-java packages by marking for complete removal. there should be at least three packages for each version. now click on the 'status' button on the bottom left panel of synaptic, and then click on 'Not Installed (residual config)' and see if you've got any java stuff there. if so, remove it all completely. if you don't already have blackdown java installed, which is listed as j2re-java, install it.

now you have to make sure you remove all references to the removed installs, and make sure the new install is referenced. go to the directories:
/etc/alternatives
/usr/lib/mozilla/plugins
/home/USERNAME/.mozilla/plugins (if this directory doesn't exist, go ahead and create it now)
and remove any remaining symbolic links for the removed java flavors, as well as any for libjavaplugin_oji.so. now, we make sure we have the correct links for blackdown java.
```

sudo ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so /etc/alternatives/
sudo ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so /usr/lib/mozilla/plugins
sudo ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so /home/dralokyn/.mozilla/plugins
```restart your browser, and everything should work fine, and you don't have to use the 32-bit software on your 64-bit machine.

---

### Post by rsambuca on 2007-11-18
> **dralokyn said:**
> there's a solution for being able to use 64-bit firefox and 64-bit java on your 64-bit machine. why skimp? this is what works for me, and most other people.

first, reinstall 64-bit firefox.

there are three flavors of java generally available through synaptic; sun, blackdown, and iced-tea. remove the sun-java and icedtea-java packages by marking for complete removal. there should be at least three packages for each version. now click on the 'status' button on the bottom left panel of synaptic, and then click on 'Not Installed (residual config)' and see if you've got any java stuff there. if so, remove it all completely. if you don't already have blackdown java installed, which is listed as j2re-java, install it.

now you have to make sure you remove all references to the removed installs, and make sure the new install is referenced. go to the directories:
/etc/alternatives
/usr/lib/mozilla/plugins
/home/USERNAME/.mozilla/plugins (if this directory doesn't exist, go ahead and create it now)
and remove any remaining symbolic links for the removed java flavors, as well as any for libjavaplugin_oji.so. now, we make sure we have the correct links for blackdown java.
```

sudo ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so /etc/alternatives/
sudo ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so /usr/lib/mozilla/plugins
sudo ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so /home/dralokyn/.mozilla/plugins
```restart your browser, and everything should work fine, and you don't have to use the 32-bit software on your 64-bit machine.Yes, that works, but it is very insecure and will run any malicious scripts on your machine.  If you run blackdown, you have to be very careful what sites you visit.

---

### Post by Darksouled on 2007-11-18
Thanks! Always good to know the opportunities, but would the overall performance gain of using 64-bit apps justify the security issues rsambuca is mentioning?

---

### Post by Kilz on 2007-11-18
> **Darksouled said:**
> Thanks! Always good to know the opportunities, but would the overall performance gain of using 64-bit apps justify the security issues rsambuca is mentioning?

The simple answer is NO. A browser, with a plugin is not a number crunching application like an encoder or a 3d modeling application. A encoder or a 3d modeling application get a large performance increase because of that. Browsers will get a slight improvement.
Secondly security is more important than anything. Just ask someone running windows about that.

---

### Post by dralokyn on 2007-11-18
well, that's good to know. i haven't run into any issues so far, but i also visit a limited range of sites. *consternation*

---

### Post by dralokyn on 2007-11-19
> **Kilz said:**
> Secondly security is more important than anything. Just ask someone running windows about that.

i happened across swiftweasel today, and tried it, and when i go to sites with java, i am asked to allow or disallow individual scripts. i'd imagine that negates the security concerns.

---

### Post by Darksouled on 2007-11-19
Yeah, that would be so true, Kilz. It's not often Firefox consumes 100% of the CPU, although heavy flash apps like games etc _might_ be tough to swallow for lesser computers. Draoklyn, can you tell the difference in such apps, 64 vs 32?

And speaking of security, it's just so nice to know that I won't be having any more security centers screaming about security issues and virus definitions every other day. And just to know that I won't be bothered with malware, spyware and other treats on a "regular" basis in Ubuntu is priceless.

---

### Post by dralokyn on 2007-11-19
i've noticed a difference, mostly in script-heavy sites that i visit on a regular basis. for average browsing, such as livejournal, craigslist, etc., i don't notice much difference because you can't get much faster than instant loading. for other sites, such as kongregate (lots of flash games) or google maps, i find a huge difference.

---

### Post by Kilz on 2007-11-19
> **dralokyn said:**
> i happened across swiftweasel today, and tried it, and when i go to sites with java, i am asked to allow or disallow individual scripts. i'd imagine that negates the security concerns.

I dont know if I would trust myself to choose what to run on limited information. Do you get to view the code?

---

### Post by dralokyn on 2007-11-19
> **Kilz said:**
> I dont know if I would trust myself to choose what to run on limited information. Do you get to view the code?

when i go to a site that has an embedded applet, i get this message:

[http://games.asobrain.com/play2/toulouse/playnorank.php](http://games.asobrain.com/play2/toulouse/playnorank.php) wants to load an applet.
GNU Classpath's security implementation is not complete.
HOSTILE APPLETS WILL STEAL AND/OR DESTROY YOUR DATA!
Click "Cancel" if you do not trust the source of this applet.
Click "Trust Applet" to load and run this applet now.
Click "Trust Applet and Add To Whitelist" to always load and run this applet from now on, without asking.
The whitelist is a list of the URLs from which you trust applets.
Your whitelist file is " /home/dralokyn/.gcjwebplugin/whitelist.txt ".

while this isn't full code, it does tell you the origin of the applet. also, since i am expecting an applet at this site, i know it is ok. if i wanted to, i could probably get the code from the direct url of the applet. i'm not an expert on that, however.

---

### Post by Darksouled on 2007-11-25
> **dralokyn said:**
> when i go to a site that has an embedded applet, i get this message:

[http://games.asobrain.com/play2/toulouse/playnorank.php](http://games.asobrain.com/play2/toulouse/playnorank.php) wants to load an applet.
GNU Classpath's security implementation is not complete.
HOSTILE APPLETS WILL STEAL AND/OR DESTROY YOUR DATA!
Click "Cancel" if you do not trust the source of this applet.
Click "Trust Applet" to load and run this applet now.
Click "Trust Applet and Add To Whitelist" to always load and run this applet from now on, without asking.
The whitelist is a list of the URLs from which you trust applets.
Your whitelist file is " /home/dralokyn/.gcjwebplugin/whitelist.txt ".

while this isn't full code, it does tell you the origin of the applet. also, since i am expecting an applet at this site, i know it is ok. if i wanted to, i could probably get the code from the direct url of the applet. i'm not an expert on that, however.

Nice, it seems safe enough. Can't recall NOT knowing whether or not to expect an applet at sites I've been visiting, so the whitelisting thing might be a good thing really.

---

### Post by Kilz on 2007-11-25
> **dralokyn said:**
> when i go to a site that has an embedded applet, i get this message:

[http://games.asobrain.com/play2/toulouse/playnorank.php](http://games.asobrain.com/play2/toulouse/playnorank.php) wants to load an applet.
GNU Classpath's security implementation is not complete.
HOSTILE APPLETS WILL STEAL AND/OR DESTROY YOUR DATA!
Click "Cancel" if you do not trust the source of this applet.
Click "Trust Applet" to load and run this applet now.
Click "Trust Applet and Add To Whitelist" to always load and run this applet from now on, without asking.
The whitelist is a list of the URLs from which you trust applets.
Your whitelist file is " /home/dralokyn/.gcjwebplugin/whitelist.txt ".

while this isn't full code, it does tell you the origin of the applet. also, since i am expecting an applet at this site, i know it is ok. if i wanted to, i could probably get the code from the direct url of the applet. i'm not an expert on that, however.

So if you go to a site expecting an applet and one is listed you will allow it? Ever hear of someone hacking a site and installing malicious code? The security that is inportant isnt the warning , but the limiting of some features to execute commands on the local machine. Im not 100% sure the blackdown or icedtea has this, sun's java does. I would have to be real 100% cretin of the sites safety before I would use blackdown or icedtea. Otherwise you could be installing a rootkit or getting your hard drive formated.

---

### Post by Master One on 2007-11-29
So what's the conclusion of this thread?

Either run icedtea, which is not working properly at all, or run blackdown, which is working but insecure?

That does not look like a satisfying result.

P.S. Has it been confirmed, that using the blackdown plugin in Firefox is any more insecure than the sun-java plugin?

---

### Post by Kilz on 2007-11-29
> **Master One said:**
> So what's the conclusion of this thread?

Either run icedtea, which is not working properly at all, or run blackdown, which is working but insecure?

That does not look like a satisfying result.

P.S. Has it been confirmed, that using the blackdown plugin in Firefox is any more insecure than the sun-java plugin?

Yes, from what I have read, the sun plugin actually restricts some functions that Blackdown and icedtea do not. Sun is also a newer plugin with enhanced features and security. The new icedtea and blackdown only warn you a applet is present in the page and offer the ability to stop it loading.
IMHO if you need java (some people dont) and want security install a 32bit browser and the 32bit sun plugin.

---

### Post by Darksouled on 2007-11-29
> **Kilz said:**
> Yes, from what I have read, the sun plugin actually restricts some functions that Blackdown and icedtea do not. Sun is also a newer plugin with enhanced features and security. The new icedtea and blackdown only warn you a applet is present in the page and offer the ability to stop it loading.
IMHO if you need java (some people dont) and want security install a 32bit browser and the 32bit sun plugin.

Amen! 

Thanks for the help everyone. :)

---

