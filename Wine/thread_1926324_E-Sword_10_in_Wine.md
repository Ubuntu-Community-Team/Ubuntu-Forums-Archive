---
title: "E-Sword 10 in Wine"
date: 2012-02-16
forum: Wine
---

### Post by darkeale on 2012-02-16
Hi,

Has anyone had any luck installing E-Sword 10 in wine?  It installs ok but if I try to change commentaries it crashes, and when running in terminal there are hundreds of err and fixme messages, too many to list.  Do I need some extra dll files or something to go with it?

Thanks,
Alex

---

### Post by nothingspecial on 2012-02-16
*Thread moved to **Wine**.*

---

### Post by forrestcupp on 2012-02-17
Yeah, I gave instructions on how to get it working [right here](http://ubuntuforums.org/showpost.php?p=11673552&postcount=2). Though, I think you'll need to remove your installation of e-Sword, follow my instructions, and then install it again.

When I followed these directions, everything in e-Sword worked perfectly, including searching, dictionaries, and commentaries. It does run kind of slow, though.

If you're not bound to commercial e-Sword modules that you have already purchased, you might want to check out [theWord](http://www.theword.net), though. It works in Wine more smoothly than e-Sword, and I like it better. I was always a big e-Sword supporter, but I recently found out about theWord.

---

### Post by darkeale on 2012-04-24
Ok, thanks.  I tried this an everything seems to work except the module downloader.  Do you have it working?  Also, in Winetricks those 5 extra ddls are shown as "cached".  Does this mean they are installed?

Thanks,
Alex

---

### Post by forrestcupp on 2012-04-24
> **darkeale said:**
> Ok, thanks.  I tried this an everything seems to work except the module downloader.  Do you have it working?  No, that's the one thing I never got working. Everything else worked like a charm for me. I didn't really need it, though, because I just copied all of the module files over from my Windows installation of e-Sword. But if you don't have that available, [BibleSupport.com](http://www.biblesupport.com/e-sword-downloads/) has a lot of e-Sword module installers that you can download. Hopefully you won't have any problem running them with Wine.

I've since switched over to theWord, which runs perfectly with Wine without any workarounds, and I like it a lot better, too. It has tons of great free and commercial modules.

> **darkeale said:**
> Also, in Winetricks those 5 extra ddls are shown as "cached".  Does this mean they are installed?
I think that "cached" means that the installer for that dll is saved to your computer, but it doesn't necessarily mean that it is installed. If the box is checked, then it is installed. I have a few things that are cached, but the box is unchecked. That just means that it doesn't have to download it to install it.

---

### Post by darkeale on 2012-04-24
Ok, I might try the word.  The list of modules looks great.  I'm trying Xiphos as well, but it can't connect to the repo to download modules for some reason!

---

