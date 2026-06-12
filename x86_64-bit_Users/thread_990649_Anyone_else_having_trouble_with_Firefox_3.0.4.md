---
title: "Anyone else having trouble with Firefox 3.0.4?"
date: 2008-11-22
forum: x86 64-bit Users
---

### Post by wetling on 2008-11-22
I think it has just been since FF updated to 3.0.4 that it randomly crashes.  Well...maybe not 100% randomly.  It seems to crash either when I open a new tab or when I restart after a crash.  The thing is, it doesn't crash every time.  

For example, I open a new tab, type a URL, and hit Enter and the browser crashes.  So I re-open it and it crashes again so I open it again and this time it loads and all the tabs are there.  Other times I can go to that same URL without any trouble.

Thoughts?

---

### Post by Spr0k3t on 2008-11-23
> **wetling said:**
> I think it has just been since FF updated to 3.0.4 that it randomly crashes.  Well...maybe not 100% randomly.  It seems to crash either when I open a new tab or when I restart after a crash.  The thing is, it doesn't crash every time.  

For example, I open a new tab, type a URL, and hit Enter and the browser crashes.  So I re-open it and it crashes again so I open it again and this time it loads and all the tabs are there.  Other times I can go to that same URL without any trouble.

I had some issues when FF was updated to 3.0.4 as well.  There were some random crashes similar to what you experienced.  I believe I have resolved the issue by doing a few things.

First, back up your bookmarks or use a sync service like foxmarks.  Next, start firefox in safe mode ($ firefox -safe-mode) and remove any add-ons and reset everything to defaults.  Go into your ~/ and rename .mozilla/   Start firefox up one more time.  Everything should be good from there.  Reimport your bookmarks, and go reinstall your add-ons.  You may have to make some changes to your config outside of that.  It's been solid as a rock here since I did just that.  I thought just renaming the ~/.mozilla/ directory would clear things up, but I had to make those other steps for stability to return.

If you can figure out what the ultimate cause is of the random crashing, post away.

---

### Post by jespdj on 2008-11-23
Nope, no problems with Firefox 3.0.4. I've never had Firefox crash on my computer.

Maybe this has to do with plugins that you are using. Which Flash are you using, and do you have any other plugins?

---

### Post by steveneddy on 2008-11-23
I agree that it is either a plugin issue, like Flash, or one of your add ons conflicting.

What web sites is it crashing on?

---

### Post by BigJohnA on 2008-11-23
I have not had any crashes, but it always runs full screen and nothing I have done seems to change that. Additionally, it seems to be slower, read it hangs a lot more, than the previous version did.

---

### Post by Spr0k3t on 2008-11-24
> **BigJohnA said:**
> I have not had any crashes, but it always runs full screen and nothing I have done seems to change that. Additionally, it seems to be slower, read it hangs a lot more, than the previous version did.

Always runs fullscreen?  I'm confused by that one.  Fullscreen as in a maximized window or fullscreen as in F11 type?

BTW, I'm a local of Kansas City in case you need a second set of eyes to help figure it out.

---

### Post by Yellow Pasque on 2008-11-24
Try starting FF from the terminal to see if it gives any clues as to why it's crashing.

---

### Post by BigJohnA on 2008-11-24
I don't really want to hijack this post....

There is no other way to describe it, the menu bar is at the very top of the screen, and the status bar (both in Firefox) is at the very bottom. Resize will not work, unmaximize will not work. It is not full screen like one would acheive with F11.

---

### Post by Thelasko on 2008-11-24
[QUOTE=wetling]Anyone else having trouble with Firefox 3.0.4?[/QUOTE]

Yeah, I've actually had this issue on my XP-64 machine.  I think it's Flash related, but I'm not sure.  If I'm listening to Flash audio I notice it starts to crackle right before it does this.  I'll open a tab and it will crash.  It's very difficult to get it to start up again without restarting my machine.

My Ubuntu 8.04 64-bit machine doesn't seem to have this issue.

---

### Post by CJ56 on 2008-11-24
Sorry to butt in but can I just second BigJohnA's post? 

FF 3.0.4 does exactly the same with me - it was working fine & then started to act up; also with some slight flickering effects when moving back or forwards a page -

At present I've just bottled out of the issue by using Epiphany (which I like, anyway) but I'd be interested to see if anyone has any theories...

EDIT: I've just uninstalled the latest version of DownLoad Helper. This seems to have done the trick; the semi-fullscreen thing has stopped happening - this might work for BigJohnA

---

### Post by wetling on 2008-11-24
Spr0k3t, I'll give that a try.

I don't remember what version of Flash I was using before, but I'm currently using the alpha release of Flash 10 x64.  The problem started before I upgraded, but has continued since.

My only other plugin is the VMware remote console.

---

### Post by corbett.jim on 2008-11-24
Hi, I have Ubuntu 8.04 and when the Firefox 3.0.4 update came along as part of the automatic updates via Ubuntu, I allowed the update to proceed (2 days ago). Ever since then, I am experiencing the problem described in this thread. Random hangups on the system, when I try to open a new tab or enter a website ID such as [www.yahoo.com](www.yahoo.com). I was not sure where I could report this. Thank you.

---

### Post by BLTicklemonster on 2008-11-24
The only problem I have with Firefox 3 crashing is on windows computers. It will not stay running long on any windows machine I have here at the house. I am trying to find version 2.* to put back on them, but haven't had any luck yet.

---

### Post by Mayfairy on 2008-11-27
I just upgraded FF to 3.0.4 from Ubuntu repository and had it crashing on me. Tried a few times and the same thing happened. 
Then I tried creating a new session instead of restoring my old pages (I have like 10 pages always open in tabs) and started reopening them. When I opened the third tab and loaded WoW official forums on it I got another crash. 

Googled for this topic and read through the replies. As someone said he had disabled the DownloadHelper I looked through my addons and stuff. The closest thing I found was DownThemAll! addon which I disabled. Not too big a disappointment since I can use wget instead. Anyways, it worked. FF hasn't crashed on me, yet. 

The error I got after the crash was:

> firefox: cairo-image-surface.c:456: cairo_image_surface_get_format: Assertion `((image_surface->format) <= CAIRO_FORMAT_A1)' failed.
Google didn't return any pages with that line. I think I've had the same problem before.

---

### Post by MedellinManDem on 2008-11-27
I have a problem on all of my Ubuntu systems running 8.10 with firefox. Namely that everytime I restart it it lags with this ugly mish-mash of the previous screen/tabs. That's the best way I can explain it tbh. I imagine it's something to do with my NVIDIA 8600GT being too slow for 8.10 or something equally as ridiculous.

Open Office Word Processor does it as well.

---

### Post by wetling on 2008-12-17
I wasn't able to resolve the issue until I reinstalled Ubuntu.

---

### Post by psypher on 2008-12-18
Sounds like you have the same issue I have: [http://ubuntuforums.org/showthread.php?t=1011649&highlight=browser+crash](http://ubuntuforums.org/showthread.php?t=1011649&highlight=browser+crash)

I've found that it's not just firefox but all browsers that crash. I have tried safe mode, new profile, re-install ff, all plugings disabled, uninstall java, uninstall flash and a heavy system stress test. Nothing works. FF will still randomly crash. I realy realy realy don't want to do a re-install. it has taken me weeks and a whole bunch of bandwidth I cannot afford to fully install and setup my pc so that I can do my work. And the fact that I believe an update broke this I'm extremely tentative to reinstall. it's just not feasible. this kind of thing really makes me annoyed and reminds me of days when I ran M$ and my PC broke after an update. I hope someone has some insight

---

### Post by swatsbiz on 2008-12-18
Just installed 3.0.5 update for FF, does that fix any problems?

---

### Post by wetling on 2008-12-18
I think the main thing 3.0.5 fixed was a serious security vulnerability.

---

### Post by rootk1t on 2009-01-04
I have the same problem on Kubuntu 8.04 **i386** with FF 3.0.5.

I can't even start firefox, and I have there the passwords and users for my sites I visit, and I am not able to recover them :(

---

