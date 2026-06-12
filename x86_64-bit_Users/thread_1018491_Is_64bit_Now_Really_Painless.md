---
title: "Is 64bit Now Really Painless?"
date: 2008-12-22
forum: x86 64-bit Users
---

### Post by joey-elijah on 2008-12-22
Aside from a few niche apps not having yet been compiled for 64 bit, with the release of Java 64 and flash 64 is there now no real reason not to 64 if you have the hardware?

For example i used 64bit Ubuntu Hardy earlier this year and, after a while, got fed up of certain applications not installing and the whole trying to get flash to work just got annoying.

Does everything else "essential" work in 64bit? 

Does Compiz?

---

### Post by CJ56 on 2008-12-22
Without a doubt

I have an AMD64x2 plus 4Gb RAM with all the basics - Firefox, Thunderbird, OpenOffice, Totem-xine etc - 

Flash 10 works like a charm, no problems yet with Java, I use FrostWire for P2P, all codecs work, movies & DVDs play perfectly, Nvidia drivers (GeForce 7300GT) work better than in 32-bit, Compiz-Fusion is absolutely fine, what more could one want?

Plus, even at my very lowly level (no big-ticket number-crunching apps here) there's a snappiness, a crispness about the 64-bit system that's hard to define, but you'll know it when you see it. 

In other words, you'll kick yourself if you don't use it... :cool:

---

### Post by NickD-NLUG on 2008-12-22
> **CJ56 said:**
> Without a doubt

I have an AMD64x2 plus 4Gb RAM with all the basics - Firefox, Thunderbird, OpenOffice, Totem-xine etc - 

Flash 10 works like a charm, no problems yet with Java, I use FrostWire for P2P, all codecs work, movies & DVDs play perfectly, Nvidia drivers (GeForce 7300GT) work better than in 32-bit, Compiz-Fusion is absolutely fine, what more could one want?

Plus, even at my very lowly level (no big-ticket number-crunching apps here) there's a snappiness, a crispness about the 64-bit system that's hard to define, but you'll know it when you see it. 

In other words, you'll kick yourself if you don't use it... :cool:

I'm missing the crispness you describe, have some niggles, especially around the graphics side... Compiz did work until the latest kernel upgrade.  What nvidia driver are you using?  I've got an "GeForce 8500 GT (rev a1)".

---

### Post by ushimitsudoki on 2008-12-22
Yes - and it's been that way for a while. Compiz works fine. Flash is fine - far far less problems now even though the 64-bit is still in alpha.

Give it a whirl. I've been on 64-bit since Gutsy and it was *never* bad, but it's pretty darn smooth now.

---

### Post by jespdj on 2008-12-22
Flash wasn't really a problem, even before the 64-bit version of Flash was released. The 32-bit version worked without any problem with nspluginwrapper (which was automatically installed since 64-bit Ubuntu 7.10). I think many people hear before they install 64-bit Ubuntu that getting Flash to work is difficult, and then they try to do all kinds of difficult things while it really isn't necessary - just install flashplugin-nonfree and it works.

For Java, there was already a 64-bit plugin based on IcedTea Java, which worked for most Java applets on the web (but unfortunately not everything).

I've been running 64-bit Ubuntu since Feisty (7.04) and it works just as well as the 32-bit version.

So, I can't think of any reason to not run the 64-bit version if you have a 64-bit capable processor.

The only 32-bit programs I run are Skype and Google Earth, which are easy to install on 64-bit from the [Medibuntu](http://medibuntu.org/) repository.

---

### Post by Arup on 2008-12-22
It was never painful to begin with, I have been on x64 since its early days. Granted there were some glitches like Flash etc. but nothing major and now everything has been sorted out.

---

### Post by Nepherte on 2008-12-22
> **Arup said:**
> It was never painful to begin with, I have been on x64 since its early days. Granted there were some glitches like Flash etc. but nothing major and now everything has been sorted out.
I can only agree.

---

### Post by whosmatt on 2008-12-23
> Flash wasn't really a problem, even before the 64-bit version of Flash was released. The 32-bit version worked without any problem with nspluginwrapper (which was automatically installed since 64-bit Ubuntu 7.10). 

I have to disagree with this one - nspluginwrapper often stopped working, requiring a browser restart.  

The 64 bit binary from Adobe works great, though.  For me, that was the last real hurdle to get over.  I don't like that flash is pretty much ubiquitous, but the fact remains that it is.

Now I'm just waiting for linux native (64 bit of course) Steam to hit.....

---

### Post by stchman on 2008-12-23
> **joey-elijah said:**
> Aside from a few niche apps not having yet been compiled for 64 bit, with the release of Java 64 and flash 64 is there now no real reason not to 64 if you have the hardware?

For example i used 64bit Ubuntu Hardy earlier this year and, after a while, got fed up of certain applications not installing and the whole trying to get flash to work just got annoying.

Does everything else "essential" work in 64bit? 

Does Compiz?

I have 1 laptop and 2 desktops running 64 bit Hardy with no issues.  I did upgrade to Flash 10 Alpha and it works very well(better than Flash 9).  I don't really visit too many Java websites so Icedtea browser plugin works well for me.

I recommend you do it.  I would say 99%+ of the stuff in the repos have a 64 bit version so no worry.

---

### Post by teddks on 2008-12-23
I don't see what everyone is getting excited about. Adobe Flash is still non-free software, and it'll break again in the future, and they won't care. It invades your privacy and can compromise your network.

[GNU Gnash](apt://mozilla-plugin-gnash) is free software, and has always worked (perfectly might I add) on my amd64 boxen. I've also used OpenJDK's plugin ([icedtea6-plugin, click here to install](apt://icedtea6-plugin)) for Java for some time, again perfectly.

Free software is typically portable. Another benefit. :)

---

### Post by tomdkat on 2008-12-23
> **teddks said:**
> I don't see what everyone is getting excited about. Adobe Flash is still non-free software, and it'll break again in the future, and they won't care. It invades your privacy and can compromise your network.I'm excited about the fact it (64-bit beta from Adobe) works better than any other Flash solution I've tried!  :)

> [GNU Gnash](apt://mozilla-plugin-gnash) is free software, and has always worked (perfectly might I add) on my amd64 boxen. I've also used OpenJDK's plugin ([icedtea6-plugin, click here to install](apt://icedtea6-plugin)) for Java for some time, again perfectly.
You're lucky.  There are Flash sites that NOW function for me using the Adobe 64-bit plugin that either didn't work or didn't fully work with Gnash.

I've had hit/miss success with Icedtea but I have yet to try the 64-bit JRE browser plugin from Sun.

I've never considered running 64-bit Linux "painful" but some things were certainly annoying.

Peace...

---

### Post by TBomBM3879 on 2008-12-23
Flash is as of now a very painless install for 64bit, i haven't had any major problems with any other programs.

The only thing I've required at any point so far is 32bit openAL libraries

---

### Post by teddks on 2008-12-23
> **tomdkat said:**
> I'm excited about the fact it (64-bit beta from Adobe) works better than any other Flash solution I've tried!  :)

If by "works better" you mean [invades privacy](http://www.ghacks.net/2007/05/04/flash-cookies-explained/) and [compromises your security](http://www.gnucitizen.org/blog/flash-upnp-attack-faq/), then sure it does.

---

### Post by tomdkat on 2008-12-23
> **teddks said:**
> If by "works better" you mean [invades privacy](http://www.ghacks.net/2007/05/04/flash-cookies-explained/) and [compromises your security](http://www.gnucitizen.org/blog/flash-upnp-attack-faq/), then sure it does.Nope, by "works better" I mean actually displaying the Flash content and not hanging or crashing the browser as I try to navigate some Flash sites.  You know, that kind of basic stuff.  :)

Peace...

---

### Post by teddks on 2008-12-23
> **tomdkat said:**
> Nope, by "works better" I mean actually displaying the Flash content and not hanging or crashing the browser as I try to navigate some Flash sites.  You know, that kind of basic stuff.  :)

Peace...

Well, if you prefer the "oooh shiny" web experience to privacy and security, sure. But to most others, I think "not being tracked online" and "not getting your network ripped open" are a bit higher on the list (even if they don't act it).

---

### Post by jerome1232 on 2008-12-23
> **teddks said:**
> If by "works better" you mean [invades privacy](http://www.ghacks.net/2007/05/04/flash-cookies-explained/) and [compromises your security](http://www.gnucitizen.org/blog/flash-upnp-attack-faq/), then sure it does.

Actually out of curriosity I opened up my router config and noticed 6 ports being forwarded to my Wifes computer via upnp. It's not running any programs that might require several ports open.

upnp is turned off now.

---

### Post by jcm4 on 2008-12-23
Works perfectly for me, though I've never used 32-bit.

---

### Post by tomdkat on 2008-12-23
> **teddks said:**
> Well, if you prefer the "oooh shiny" web experience to privacy and security, sure. But to most others, I think "not being tracked online" and "not getting your network ripped open" are a bit higher on the list (even if they don't act it).Actually, I'm not a huge fan of Flash at all.  In some cases, I think it's totally abused (but that's another topic of discussion).  The fact of the matter is, when there were times when I needed to view Flash content, I found the open source Flash solutions would sometimes work and sometimes not.  I think my best Flash experience was using a 32-bit plugin in Opera and even that was only 90% functional.  With the 64-bit native plugin from Adobe, the "problem" Flash content started working.

Having a working Flash plugin is of higher priority to some than to others.  It's just been my experience that the Adobe 64-bit native plugin has been the only solution yet which solves this issue and well.  To many, this would make migrating to a 64-bit Linux environment more attractive since those hesitant to migrate probably won't want to "fight" getting Flash working as they would want.

For the record, I've been running 64-bit Ubuntu since 7.04 and that was the first Ubuntu release I installed on the 64-bit AMD64 3200+ based machine I had just purchased.  I've been surfing just fine without a fully functional Flash environment so it's obvious it hasn't been a priority for me. :)

Peace...

---

### Post by tomdkat on 2008-12-23
> **jerome1232 said:**
> Actually out of curriosity I opened up my router config and noticed 6 ports being forwarded to my Wifes computer via upnp. It's not running any programs that might require several ports open.
Is your wife running Windows?

Peace...

---

### Post by jerome1232 on 2008-12-23
> **tomdkat said:**
> Is your wife running Windows?

Yes, that particular one runs xp.

---

### Post by bcurry on 2008-12-23
> **jerome1232 said:**
> Yes, that particular one runs xp.

LOL!  That particular Wife or that particular computer?

:)

---

### Post by jerome1232 on 2008-12-23
> **bcurry said:**
> LOL!  That particular Wife or that particular computer?

:)

LOL, computer... my sides are hurting from laughing now.

---

### Post by TBomBM3879 on 2008-12-23
> **teddks said:**
> If by "works better" you mean [invades privacy](http://www.ghacks.net/2007/05/04/flash-cookies-explained/) and [compromises your security](http://www.gnucitizen.org/blog/flash-upnp-attack-faq/), then sure it does.


Interesting how I've never had my security compromised by ANY of Adobe's products.

Maybe I'm just lucky.

---

### Post by joey-elijah on 2008-12-27
well awesome! Will install it in a few days. I've never had an issue (aside from an olde scanner) with Vista 64, but had encountered issues with Ubuntu Hardy 64 a while back.

Regardless of the ubiquitous-ness of Flash, for the majority of people who like to "experience" the web (iPlayer, YouTube) stable flash is expected. They're not too concerend if it wants validation or reports back on which OS they're using. 

My sticking point last time was the lack of AdobeAir for 64 (or any workarounds). With the actual release of Air and flash 64 this isn't an issue now as FINALLY you can just force install it. 

I noticed earlier how much i miss Ubuntu :( Had been using hardy 64 then ibex 32 for months then after some absolute mess up which needed a re-install so installed Vista 64 again (i really hate having to reinstall my OS cos it's quicker to sort whatever problem that way btw, but i appreciate Ubuntu is a quick and painless installation process) 

Actually, probably should ask in a dedicated thread, but is there a "system restore" equivilent in Ubuntu? I tweak, learn etc and sometimes break stuff. being able to "undo" changes on the fly by restoring would be ace.

---

### Post by Swerve1000 on 2008-12-27
Anyone using a Lexmark 1100 series all in one printer?

Also is anyone using Skype with with success, I'm making the jump to 64 in the new year.

*trembles with apprehension **

---

### Post by Master Chief on 2008-12-27
It depends on what brand/type of hardware you have, and don't take the amd64 (Ubuntu 8.10) route when you have a Canon color laser like me (Canon LBP5000) because that is still a pain in the lower back ;)

---

### Post by ubuntu27 on 2008-12-27
> **teddks said:**
> If by "works better" you mean [invades privacy](http://www.ghacks.net/2007/05/04/flash-cookies-explained/) and [compromises your security](http://www.gnucitizen.org/blog/flash-upnp-attack-faq/), then sure it does.

Hey, thanks for the links! I didn't know about Adobe Flash's Cookie.
Another good reason to use [Gnash]("http://www.gnu.org/software/gnash/") or [Swfdec]("http://swfdec.freedesktop.org/").

Now I wish [Open Source Flash Development]("http://osflash.org/") will be successful also.

---

