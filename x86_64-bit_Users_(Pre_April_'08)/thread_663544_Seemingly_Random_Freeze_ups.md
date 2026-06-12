---
title: "Seemingly Random Freeze ups"
date: 2008-01-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by remu on 2008-01-10
Hey Guys,
Sorry if this topic has been brought up before, I searched and couldn't find it, so I thought I'd ask here.

My specs: Turion 64 x2 1.60 GHz, 1.50GB Ram, wireless with ndiswrapper, nvidia restricted drivers for nvidia go6150.

I dunno what else information to give. The problem I am having is that every now and then my system freezes up for a few (5-10) seconds. During that time, I can move my mouse, But nothing happens. Often happens in both firefox and swiftweasel, as well as just about everywhere else. Sometimes it's good and won't do it, other times it'll freeze up often. During the freeze up, if I click to close a window, or click in a text field to type, or scroll, it won't do it when its frozen, but when the system unfreezes, it does all those things I wanted it to do during the freeze up. I can't narrow this down to what might be causing the problem. I ran the memtest from grub and let it run over night (for about 7-8 hours) and the test showed 0 errors. I really don't know whats causing this or how to fix it. I am a new user, but I am comfortable in following instructions, and any and all help would be greatly appreciated!

Umer

EDIT: I'm using Gutsy AMD64

---

### Post by gnelson on 2008-01-10
I have exactly the same symptoms.  Turion, 2 GB RAM, NDISWrapper for Broadcom Wireless and NVidia restricted graphics driver.  Gutsy AMD64.

My system will freeze for a few seconds every now and then.

---

### Post by Kilz on 2008-01-10
Do you have desktop effects enabled, if so does disabling them help?

---

### Post by remu on 2008-01-10
I had them enabled, will disable and use it for a while and see if that makes a difference or not. If it does, is there anything we can do so that I can still use Desktop Effects and not get this problem? Or not really?

---

### Post by cotcot on 2008-01-10
My amd64 (and 32 bit installs on the same desktop) were freezing also. I installed an older nvida-driver (9643) a couple of weeks ago and since then I have not had any freeze. (before I had the nvidia driver 100. ... ; I also tried the latest 167.  .. but that causes also freezings)

---

### Post by hotbit on 2008-01-10
My system used to freeze completely. Hard reboot was necessary. What helped - I had 2 x 512 Mb Ram memory, removed one and for the last 3 days no problems :) 
However I use ATI graphics driver.
Thus, if anything else will not help, try to remove memory, as you have 1.5 G = 3x512 or 1G + 512Mb;

---

### Post by remu on 2008-01-12
I turned off the Desktop Effects, and I haven't seen the problem since. Is there something we can change so that Desktop Effects will run but not cause this problem? Or is it best to leave them turned off?

---

### Post by Kilz on 2008-01-12
> **remu said:**
> I turned off the Desktop Effects, and I haven't seen the problem since. Is there something we can change so that Desktop Effects will run but not cause this problem? Or is it best to leave them turned off?

Not that I know of, but at least you have somewhat narrowed down what the problem might be a little. This should help when looking for a solution.

---

