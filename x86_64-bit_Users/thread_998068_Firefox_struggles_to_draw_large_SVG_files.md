---
title: "Firefox struggles to draw large SVG files"
date: 2008-11-30
forum: x86 64-bit Users
---

### Post by Ben Webber on 2008-11-30
First of all, as my first post, I want to make clear how appreciative I am of this community (which has helped me innumerable times before).

I was recently attempting to load a particularly large SVG file from Wikimedia Commons ([**_file is here_**]("http://upload.wikimedia.org/wikipedia/commons/7/77/Unix_history-simple.svg")). Firefox slowed to an absolute crawl while attempting to draw it, an almost Windows-crash-like crawl if that is imaginable. I was able to [FONT="Courier New"]**xkill**[/FONT] Firefox and attempted to duplicate the problem. Again, Firefox struggled to draw the SVG file.

Saving it to my computer, the SVG file loads fine in F-Spot, GIMP, and Inkscape. Opening the saved file in Firefox causes Firefox to grey-out and slow to a halt, but the rest of the system is relatively responsive.

I am not sure if this is an issue with Firefox 3.0.4 in particular, or the 64-bit version of Firefox.

I am currently running Intrepid 64-bit edition on a Thinkpad T61 with 2 GB of RAM, a 2.5 GHz Intel Core 2 Duo processor, and a 256MB NVIDIA Quadro FX 570M. Compiz is enabled.

---

### Post by cariboo on 2008-12-01
I would suggest creating a new Firefox profile to see if that makes a difference. I just clicked the link and the page loaded with no problem at all. To create a new Firefox profile press Alt-F2 and type:

```
firefox -ProfileManager
```


Jim

---

### Post by Ben Webber on 2008-12-01
Unfortunately running the Profile Manager and creating a new profile didn't seem to alleviate the problem. Nor did removing and reinstalling Firefox.

---

### Post by insane_alien on 2008-12-01
opens fine here, on lesser specs and with compiz on as well.

it was a bit jittery when scrolling but otherwise fine. on my main machine and even on my laptop it was smooth as normal.

---

### Post by tghe-retford on 2008-12-01
> **Ben Webber said:**
> I was recently attempting to load a particularly large SVG file from Wikimedia Commons ([**_file is here_**]("http://upload.wikimedia.org/wikipedia/commons/7/77/Unix_history-simple.svg")). Firefox slowed to an absolute crawl while attempting to draw it, an almost Windows-crash-like crawl if that is imaginable. I was able to [FONT="Courier New"]**xkill**[/FONT] Firefox and attempted to duplicate the problem. Again, Firefox struggled to draw the SVG file.
Yep, it completely stalled on my computer as well, even the Gnome panel stalled whilst Firefox wouldn't respond. It finally sprung back to life after about half a minute, but moving the scrollbars anywhere would cause Firefox to stall for another few seconds.

Using a Intel Core 2 Quad Q6600 at 2.4GHz, 2GB of RAM and a Zotac 8800GT AMP Edition graphics card using the NVidia 177.80-0ubuntu3 package with Compiz enabled.

---

### Post by Ben Webber on 2008-12-02
> **tghe-retford said:**
> Yep, it completely stalled on my computer as well, even the Gnome panel stalled whilst Firefox wouldn't respond. It finally sprung back to life after about half a minute, but moving the scrollbars anywhere would cause Firefox to stall for another few seconds.

I had the same experience. If I left it for a while, it would eventually load but stall again upon scrolling. I assume you're running Intrepid or Hardy 64-bit?

Are any else of you guys running 64-bit versions of Ubuntu? It seems to me it may be due to a bug in the 64-bit version of Firefox.

---

### Post by philinux on 2008-12-02
Completely kills my machine dead. Had to force quit firefox.
I'm running 32bit intrepid.

Although FF in safe mode did a bit better.

---

### Post by peacewithall on 2008-12-03
I've noticed this on many websites such as myspace, I clicked the link in the OP and sure enough, firefox practically stops working, I experience greying out and pausing. My machine is quite fast, AMD quad core 2.4Ghz, and I am running 64 bit Intrepid.

This problem is so annoying to the point of booting into windows (in which it works very smooth), not very impressed with Ubuntu the last two releases, the inability to simply browse a website is terrible IMO.

---

### Post by philinux on 2008-12-03
Jaunty 64bit testing.

The problem website loaded in a flash without any problem, however scrolling is a bit slow.

---

### Post by Ben Webber on 2008-12-05
Jaunty would still use the same Firefox package, though. I am very puzzled as to why it is experienced on some machines and not others. The problem could lie in addons or plugins installed.

I have:

[LIST]
[*]Adblock Plus,
[*]Better Gmail 2,
[*]DownThemAll!,
[*]Gmail Notifier,
[*]Google Notebook,
[*]Sage,
[*]Stop-or-Reload Button,
[*]TabMix,
[*]Ubiquity,
[*]Ubuntu Firefox Modifications,
[*]as well as flashplugin-nonfree.
[/LIST]

Should this be reported in the Firefox Bugzilla? It is difficult to determine the exact conditions of the bug since it has been experienced on both 32-bit and 64-bit operating systems.

---

### Post by philinux on 2008-12-05
When I installed Jaunty 64 bit i copied my .mozilla folder from Intrepid 32 bit. So for comparisons sake it's good. Jaunty does a much better job. Why no idea. Could be xulrunner being a newer version. etc.

These are my addons. They were enabled when i did the Jaunty test.

---

