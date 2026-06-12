---
title: "Gutsy 64bit w/Flash and Java"
date: 2007-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by timzak on 2007-11-01
Is there an updated howto on how to install Flash and Java on Gutsy 64bit?  I tried some howto's but got confused between all the separate instructions for different versions of Ubuntu.

I just need Flash and Java to work.  Is the version of Firefox that comes with Gutsy 64, 64 bit?  I'm getting the impression I need the 32bit version of Firefox to use Flash and Java.  Does this still hold true in Gutsy 64?

Thanks.

---

### Post by parann0yed on 2007-11-01
Sorry I don't have an answer.  I too am having problems with java/flash in the 64bit version of 7.10.  I'll be monitoring any answers to this post.  But I believe this is a bug and has probably already been submitted.

---

### Post by LoneWolfJack on 2007-11-01
You can definitely get flash to work with FF64. Use Synaptic to install the flash-nonfree package.

As for Java, there is no Java64 available from sun yet, but some people claim that they had some luck with the blackdown package. If you already have it installed, try removing it first.

If none of that works, you may use the FF32 installer script by Kiltz, which worked very well for me.

---

### Post by moma on 2007-11-01
I am running 64bits Ubuntu 7.10 with 100% success'fully.
Flash and Java browser-plugins works just fine.

* The 64bits  Java is based on GNU's GCJ Java.
See: [http://gcc.gnu.org/java](http://gcc.gnu.org/java)  and  [http://freshmeat.net/projects/gcjwebplugin](http://freshmeat.net/projects/gcjwebplugin)
-----

* The first Flash implementation i tried was based on Pluginwrapper and standard 32 bits Flash from Adobe. This setting works pretty well. 
See: [http://freshmeat.net/projects/nspluginwrapper](http://freshmeat.net/projects/nspluginwrapper)

But I did not like to use the pluginwrapper so I choosed GNU's pure 64 bits Gnash Flash.
-----

* GNU's 64bits Gnash Flash.
I installed Gnash Flash and it can play most of the Flash 9 videos and images well.
See: [http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/)
----- ----- ----- -----

[COLOR="DarkRed"]All in all, do this:[/COLOR]

1) Install 64 bits Ubuntu 7.10 as instructed in this guide importancia: [http://www.futuredesktop.org](http://www.futuredesktop.org)


2) Install the Java and Flash plugins + multimedia-codeces via **Automatix** as instructed in step **7)**   [ all steps  7a - 7d ]

3) The GCJ Java-plugin has some errors,  fix it as instructed in step **9b)**. Follow [the link...]("http://www.futuredesktop.org/java-plugin-64-bits-ubuntu.html")

4) If you want to try GNU's 64bits Gnash Flash (I run Gnash now), do this 

$[COLOR="SeaGreen"] sudo apt-get install mozilla-plugin-gnash gnash[/COLOR]

and switch to Gnash instead of Flash-plugin wrapper
$ [COLOR="SeaGreen"]sudo update-alternatives --config mozilla-flashplugin[/COLOR]

From the menu that appears, select: /usr/lib/gnash/libgnashplugin.so

EDIT: In addition, I had to do:
$[COLOR="SeaGreen"] sudo ln -sf /etc/alternatives/mozilla-flashplugin  /usr/lib/firefox/plugins/flashplugin-alternative.so[/COLOR]
(Note: it overwrites the existing link. Study:  [COLOR="SeaGreen"]ls -l /usr/lib/firefox/plugins/ [/COLOR] before you run ln -sf)

Restart Firefox.
Browse to Youtube.com and test  the Flash-plugin. Right-mouse click on the video-window to see whether it runs Gnash or Adobe's Flash. The popup-menu will reveal it.

5) Install Flashblock and improve your browsing speed: [https://addons.mozilla.org/en-US/firefox/search?q=flash&status=4](https://addons.mozilla.org/en-US/firefox/search?q=flash&status=4)

6) [64 bits Automatix...]("http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.10_.28Gutsy_AMD64.29") can also set up Skype.
--------------------

Blog page: [http://linux1.no/node/2954](http://linux1.no/node/2954)

---

### Post by timzak on 2007-11-01
Thank you for the replies so far.  Am I better off switching to 32 bit Firefox?  I don't care if FF is 32 or 64 bit, as long as it is able to run Flash and Java.

I am a bit surprised that there isn't more exposure on this topic.  Flash and Java are practically required for seamless web browsing these days, and with the exposure that Gutsy has received since its release, you'd think there'd be a dedicated sticky for getting Flash and Java working in Gutsy 64 bit.

Regarding Automatix, I am very leery about using that.  I'd like to be able to take care of this through Synaptic, Add/Remove, or the command line.

I already tried installing Flash non-free, but it didn't work on the website I tested it on ([www.rush.com](www.rush.com)).  I'll try uninstalling and reinstalling this evening.

Thanks again for the help.  Please, if there are any other suggestions, post them.

---

### Post by Kilz on 2007-11-01
> **moma said:**
> I am running 64bits Ubuntu 7.10 with 100% success'fully.
Flash and Java browser-plugins works just fine.

* The 64bits  Java is based on GNU's GCJ Java.
See: [http://gcc.gnu.org/java](http://gcc.gnu.org/java)  and  [http://freshmeat.net/projects/gcjwebplugin](http://freshmeat.net/projects/gcjwebplugin)
-----

* The first Flash implementation i tried was based on Pluginwrapper and standard 32 bits Flash from Adobe. This setting works pretty well. 
See: [http://freshmeat.net/projects/nspluginwrapper](http://freshmeat.net/projects/nspluginwrapper)

But I did not like to use the pluginwrapper so I choosed GNU's pure 64 bits Gnash Flash.
-----

* GNU's 64bits Gnash Flash.
I installed Gnash Flash and it can play most of the Flash 9 videos and images well.
See: [http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/)
----- ----- ----- -----

[COLOR="DarkRed"]All in all, do this:[/COLOR]

1) Install 64 bits Ubuntu 7.10 as instructed in this guide importancia: [http://www.futuredesktop.org](http://www.futuredesktop.org)


2) Install the Java and Flash plugins + multimedia-codeces via **Automatix** as instructed in step **7)**   [ all steps  7a - 7d ]

3) The GCJ Java-plugin has some errors,  fix it as instructed in step **9b)**. Follow [the link...]("http://www.futuredesktop.org/java-plugin-64-bits-ubuntu.html")

4) If you want to try GNU's 64bits Gnash Flash (I run Gnash now), do this 

$[COLOR="SeaGreen"] sudo apt-get install mozilla-plugin-gnash gnash[/COLOR]

and switch to Gnash instead of Flash-plugin wrapper
$ [COLOR="SeaGreen"]sudo update-alternatives --config mozilla-flashplugin[/COLOR]

From the menu that appears, select: /usr/lib/gnash/libgnashplugin.so

EDIT: In addition, I had to do:
$[COLOR="SeaGreen"] sudo ln -sf /etc/alternatives/mozilla-flashplugin  /usr/lib/firefox/plugins/flashplugin-alternative.so[/COLOR]
(Note: it overwrites the existing link. Study:  [COLOR="SeaGreen"]ls -l /usr/lib/firefox/plugins/ [/COLOR] before you run ln -sf)

Restart Firefox.
Browse to Youtube.com and test  the Flash-plugin. Right-mouse click on the video-window to see whether it runs Gnash or Adobe's Flash. The popup-menu will reveal it.

5) Install Flashblock and improve your browsing speed: [https://addons.mozilla.org/en-US/firefox/search?q=flash&status=4](https://addons.mozilla.org/en-US/firefox/search?q=flash&status=4)

6) [64 bits Automatix...]("http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.10_.28Gutsy_AMD64.29") can also set up Skype.
--------------------

Blog page: [http://linux1.no/node/2954](http://linux1.no/node/2954)

Automatix is not necessary for installing anything in Ubuntu. In fact it is known to be bad for Ubuntu according to the [Ubuntu Technical Board]("http://mjg59.livejournal.com/77440.html"). ```
sudo apt-get install flash-nonfree
``` will install flash
Do a search for icedtea plugin in synaptic for a java plugin that is ok on most sites I use.

If the original poster needs sites that the icedtea plugin wont wok, there are links to howtos for 32bit firefox in the stickies. IMHO avoid Automatix at all costs.

---

### Post by OldTimeTech on 2007-11-01
On the Ubuntu Technical Board thing....if you really read it, this was the writers opinion and not the boards!

Also if you look back aways in Community Cafe, there was an announcement made that Automatix was now going to be helping Ubuntu and Ubuntu mods/devs/whoever had agreed to this.

---

### Post by moma on 2007-11-01
> **timzak said:**
> I already tried installing Flash non-free, but it didn't work on the website I tested it on ([www.rush.com](www.rush.com)).

You are right. 
[http://www.rush.com/v4.html](http://www.rush.com/v4.html) does not work with Gnash.

---

### Post by Kilz on 2007-11-01
> **OldTimeTech said:**
> On the Ubuntu Technical Board thing....if you really read it, this was the writers opinion and not the boards!

Also if you look back aways in Community Cafe, there was an announcement made that Automatix was now going to be helping Ubuntu and Ubuntu mods/devs/whoever had agreed to this.

That may be, but he is a member of that board. 
Automatix at one time (Horry - breezy) did some good, maybe, but as Ubuntu has advanced it is no longer necessary. People install it because they have always installed it. Everything needed by most users can be installed, and installing one package to install another that is available from apt or synaptic is foolish imho.
I have seen and helped numerous people over the time I have been here where Automatix messed over their install. Could some people not have problems? Yes. But the people who have the greatest problems imho are newbies who are clueless when Automatix messes up. When that happens to a new user, sometimes they blame Ubuntu and say goodbye.
imho new users should learn how to install applications the regular normal way and gain valuable knowledge. They should avoid Automatix.

---

### Post by timzak on 2007-11-02
Thanks for your help everyone.  I now have both 32bit and 64bit Firefox working on my system.  I haven't tested extensively, but it seems that everything I need to work is working on both versions!  I undid all the changes I made initially, basically getting my browser to a freshly installed state, then installed 32bit Firefox with Kilz' script, then reinstalled Flash non-free (for 64bit FF) and now it seems most, if not all websites work properly with both versions.  I'm sure as I do more extensive surfing I'll come across some issues on the 64bit side, but a big thank you to everyone and Kilz especially.  

Kilz, you should give some basic instructions for your script for newbies.  I figured it out just by downloading and double-clicking to see what happens.  But initially, I didn't know what I was supposed to do to run the script.  You provide a link, but no instructions (if you did and I didn't see them, I apologize).

Regards.

---

