---
title: "World of Warcraft, Intrepid Ibex, Sound/FPS issues.. How to fix it!"
date: 2008-10-31
forum: Wine
---

### Post by thumper13 on 2008-10-31
Greetings fellow Azerothians...

I, much like most other people in the Ubuntu community, recently upgraded my computer from 8.04 to 8.10. I am extremely impressed with 8.10 thus far, with one exception:

MY WARCRAFT DOESN'T WORK!!! I am practically addicted to warcraft, and I had a wicked problem with the sound and video. My sound was extremely static-y, and my fps dropped from 25-30 to 6 overnight. The only thing I had changed was Ubuntu, the upgrade.

Contrary to what other information I have found, it seems that the issue isn't related to PulseAudio at all, rather the wine update that ships with Intrepid Ibex. Therefore, I will explain how to get back to a running warcraft, without removing Intrepid Ibex.

1) Open synaptic package manager.
    -Search for wine.
    -Mark for removal. (Not complete removal, just removal.)

2) Open the following web page:
    -http://wine.budgetdedicated.com/archive/index.html
    -Click on Wine 1.1.5 i386 (for 32-bit) or Wine 1.1.5 amd64 (for 64-bit)
      -I know it is not for "Intrepid Ibex" and is for Hardy Heron. This is the one that I used, and seemed to work in my case.
    -Open with GDebi.

3) GDebi will install and compile wine for you.

4) Your warcraft should now work properly.

This fix I am posting as it worked perfect for my computer: HP Pavilion a1330n: AMD 64 bit processor, BFG nVidia 8400 GS, 1 mb ram.

I just thought I'd add this, as I could find absolutely no fixes for warcraft as of yet.

Thumper
Thumperox of Rexxar.

---

### Post by Bios Element on 2008-10-31
I haven't tested this but i have to point out that there should (As in it worked for me.) be a better way. I changed my Audio settings to OSS (May work with Alsa now, Haven't tested it.), Hardware acceleration to Standard and Driver Emulation unchecked works great. I even got about 15-20+ More FPS for that. ^_^

---

### Post by wbrucem on 2008-11-01
Switching to OSS does fix the sound stuttering issue. (ALSA still sounds terrible with the other setting changes).  The problem with using OSS is that only 1 program has access to the sound driver at a time.  This means I can't use Ventrilo (voice chat) while raiding in WoW.

---

### Post by Bios Element on 2008-11-02
> **wbrucem said:**
> Switching to OSS does fix the sound stuttering issue. (ALSA still sounds terrible with the other setting changes).  The problem with using OSS is that only 1 program has access to the sound driver at a time.  This means I can't use Ventrilo (voice chat) while raiding in WoW.

Thus why you use aoss to lauch WoW via wine. My blog has some info on it as well but basically launch WoW like this.

```
aoss wine WoW.exe
```

---

### Post by tlsarles on 2008-11-02
Thanks Thumper. That made my sound much better. Video still lags, but thats life with a gf5200.

---

### Post by wbrucem on 2008-11-02
I tried using AOSS, but I still can't get both WoW and Ventrilo both active with sound.

---

### Post by hotballz87 on 2008-11-02
how would i get Hardware acceleration to Standard and Driver Emulation unchecked?

ya its prollay a real nub question, but im getting 4 fps in BT, which is no good

---

### Post by Trap3d on 2008-11-03
This works if you are using 1.1.7. if any other it still might work if you have ever installed 1.1.7.
First you'll have to get rid of your current wine so do that.
**System > Administration > Synaptic packet manager**, there find wine and check complete removal, then go to home folder (**Places > Home folder**) btw the folder is hidden so turn show hidden folders on and delete your .wine folder ([COLOR="Red"]**you might want to backup your games & apps and other stuff you have installed under wine from that folder as when you delete it [SIZE="5"]they will be lost unless backuped[/SIZE]**[/COLOR])
Then remove every single thing related to your wine in the Software sources(**System > Administration > Software sources**)
Now all you have to do is install wine from your Add/Remove apps in Applications tab and voila you should have normal sound once again tought do not upgrade it to 1.1.7 let it stay 1.0.1.

---

### Post by Amannim on 2008-11-04
Thumper13's instructions worked like a charm

Synaptic Package Manager->Search Wine->Remove Wine 1.1.7 (NOT complete)
Download 1.1.5 .deb
Install
Play
w00t

---

### Post by fireoftroy on 2008-11-10
I did the same as Amannim except after doing a base removal of 1.1.7, Synaptic came back showing 1.0.1 available for download, so I marked that one for installation.  After waiting a few minutes for it to download, it was good to go.  Wow works fine for my standards.  I'm sure 1.1.5 has some nice updates but this method was a quick fix for those short on time.

---

### Post by forest.r on 2008-11-10
Thanks a lot thumper. One solutions for my fps problem i couldn't think of was downgrading.

---

### Post by markackerman8@gmail.com on 2008-11-14
I am completely new to this game, and have seemed to install it correctly.

When I start it , I see it starting up then it bives me a black screen and doesnt let me out.  When I do get out my resolution has shot down to 800x600 or something like that.  How do I configure WoW to work with my radeon ATI notebook graphics card??

Thanks in advance

Ack

---

