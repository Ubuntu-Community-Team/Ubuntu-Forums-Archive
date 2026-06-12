---
title: "Flash video big grey box x86 64 bit 8.04 with  Firefox 3.0.1"
date: 2008-09-02
forum: x86 64-bit Users
---

### Post by Trebacz on 2008-09-02
My ability to play YouTube videos disappeared. I just got a grey box in plash of the flash animation. I'm thinking it was due to an upgrade in the Firefox browser, because it was working on this system awhile ago. I found a fix that suggested copying the libflashplayer.so file from

/usr/lib/flashplugin-nonfree/ to /usr/lib/firefox-3.0.1/

I'm guessing for whatever reason this version of Firefox wasn't looking for the flash file in the correct directory.

I did this and restarted Firefox and I can play videos again. If someone could tell me why this works -it would be appreciated. I posted here in hopes that someone with the same problem would benefit from my luck.

---

### Post by philinux on 2008-09-03
If i read you correctly it was probably closing and restarting firefox that jump started flash. This happens to me regularly.

If you look in about:Plugins

You'll see this.

**Shockwave Flash**

 File name: npwrapper.libflashplayer.so

Which lives in /var/lib/flashplugin-nonfree/

---

### Post by MaindotC on 2008-09-23
This isn't working for me.  I copied the file to /usr/lib/firefox-3.0.1/ and restarted firefox - still getting a grey box :(  It initially shows the video for a split second, almost as if it's TRYING to play it, but then grey box.

what does /var/lib/flashplugin-nonfree have to do with /usr/lib/firefox-3.0.1 ?

Edit: Fudge now it's working!  Wtf all I did was refresh the page - before I closed and opened FF and it didn't work after that but refreshing the page somehow jiggled it.  Amazing.  Anyway, aside from removing/purging FF and all related content/plugins/extras, which produced the same result with the grey box, and then disabling the Comics screenlet (again, I doubt that's related but have to be specific), I followed OP's directions and after refreshing the page it now works.

---

### Post by Kilz on 2008-09-23
> **Trebacz said:**
> My ability to play YouTube videos disappeared. I just got a grey box in plash of the flash animation. I'm thinking it was due to an upgrade in the Firefox browser, because it was working on this system awhile ago. I found a fix that suggested copying the libflashplayer.so file from

/usr/lib/flashplugin-nonfree/ to /usr/lib/firefox-3.0.1/

I'm guessing for whatever reason this version of Firefox wasn't looking for the flash file in the correct directory.

I did this and restarted Firefox and I can play videos again. If someone could tell me why this works -it would be appreciated. I posted here in hopes that someone with the same problem would benefit from my luck.

With the 64bit browser its an issue with the nspluginwrapper than has no known fix. The problem happens when you have multiple flash enabled websites open at once in multiple tabs or windows.
Simple solution, only open one tab at a time.

---

### Post by MaindotC on 2008-09-23
Aha!!!  Kilz to the rescue again!  LoL that's perfectly fine with me - now I can use my seesmic and 12seconds, just at separate times.  Thanks kilz!

---

### Post by tuxxy on 2008-09-23
Try using totem for youtube, iv yet to had a crash when not using a browser.

---

### Post by MaindotC on 2008-09-24
Even with only 1 window open I'm getting a grey box for [Seesmic](http://www.seesmic.com).  Does this work for anyone?  All the other sites like youtube work fine - sometimes even with two youtube tabs open.

---

### Post by Kilz on 2008-09-25
> **strAlan said:**
> Even with only 1 window open I'm getting a grey box for [url=http://www.seesmic.com]Seesmic[/url[.  Does this work for anyone?  All the other sites like youtube work fine - sometimes even with two youtube tabs open.

Works for me, but I'm using flash 10 beta. I also dont recommend it because you will have to install about 10 32bit libs manually.

---

### Post by MaindotC on 2008-10-03
I got a WUSB600N wireless adapter which is way faster than anything else and for some reason I'm having a lot less problems w/ Flash.  Pretty much everything working except Seesmic.  I haven't had a chance to go through that tutorial you mentioned but one of these days I will.

---

### Post by lyoshenka on 2008-10-16
I have the same problem. It seems to be a bug with flash or nspluginwrapper. Apparently, flash crashes and then you get the grey box instead of the video. There is a sort-of fix in the new ndiswrapper that restarts flash every time it crashes. It's not pretty, but it works. 

Check out this site: [https://bugs.launchpad.net/nspluginwrapper/+bug/246450](https://bugs.launchpad.net/nspluginwrapper/+bug/246450)

---

