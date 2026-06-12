---
title: "ATI Video Driver Guide"
date: 2008-05-02
forum: x86 64-bit Users
---

### Post by Yellow Pasque on 2008-05-02
[SIZE="4"]Temüjin's Radeon Driver Guide[/SIZE]

_**AGP**_

**Radeon 7k - X850-series (R4x0 GPU or older)**At this time (5/1/08), AMD/ATI still does not have support in place for AGP cards in their Catalyst drivers. Your card should automatically work with the open-source ati/radeon driver. See [http://wiki.x.org/wiki/radeon](http://wiki.x.org/wiki/radeon) for details on multi-monitor setups and TV-out, etc.

**Radeon X1k-series (R5x0 GPU)** You can use the ati driver supplied with Ubuntu or the radeonhd driver.

**Radeon HD 2k,3k (R6x0 GPU)** You'll have to use the radeonhd driver.

_**PCI-e**_

**X-series (R4x0 GPU):** Use the open-source "radeon" driver supplied by Ubuntu unless 3D performance/desktop effects are important for you or you're having issues with multi-monitor/TV-out. In that case, use Ubuntu's proprietary ATI driver.

**Radeon X1k (R5x0/RS6x0 GPU):** You have a lot of choice. If 3D acceleration isn't a concern for you, you can either use the open-source ati/radeon driver supplied by Ubuntu or the open-source radeonhd driver. If you want 3D performance and/or desktop effects, use Ubuntu's proprietary ATI driver.

**Radeon HD 2k & 3k owners:** See if Ubuntu's proprietary ATI driver works. If not, follow Method 2 of the ATI Catalyst Install Guide at the end of this post.

[COLOR="RoyalBlue"]
radeonhd Driver[/COLOR]: This open-source driver supports 2D functions and acceleration on modern ATI video cards (X1k, Radeon HD 2k, 3k). An old  version is available in the Ubuntu repo for easy installation, but the very latest cards and IGP's may require the driver to be built and installed from source following this guide: [http://www.phoronix.com/scan.php?page=article&item=843&num=1](http://www.phoronix.com/scan.php?page=article&item=843&num=1)

[COLOR="Red"]Catalyst Install Guide[/COLOR]: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by inphektion on 2008-05-02
Thanks.  after i went to hardy my comp with the radeon hd card booted into failsafe X which is better than before when it would just crash if the driver messed up and I'd have to book from CD to replace a basic x11 conf file.  I installed the latest from phoronix under hardy and back to looking nice again except still no compiz, composite, etc so also no awn which stinks.  If anyone knows when the 3D stuff will start working in radeonHD please keep me posted.

---

### Post by jocko on 2008-05-02
> **Temüjin said:**
> _**AGP**_

**Radeon 7k - X850-series (R4x0 GPU or older)**At this time (5/1/08), [COLOR=Red]AMD/ATI still does not have support in place for AGP cards in their Catalyst drivers[/COLOR]. Your card should automatically work with the open-source ati/radeon driver. See [http://wiki.x.org/wiki/radeon](http://wiki.x.org/wiki/radeon) for details on multi-monitor setups and TV-out, etc.

That's misinformation!
This is the truth:
Older than Radeon 9500 --> Open source is the only thing that works (on current Xorg releases).
Radeon 9500 and newer Radeons: Choose between fglrx or ati/radeon. They both work with their own problems. I use fglrx (v. 8.37.6 in gutsy) on my radeon 9600 Pro (AGP), and it works pretty well. I haven't upgraded to hardy yet, in part because the new driver base (which is used in the catalyst linux driver) is still too buggy for my taste, [COLOR=Red]but it does work[/COLOR].

---

### Post by ASULutzy on 2008-05-02
Look, obviously I'm all about open source and love my Ubuntu install and whenever possible I try to use open source stuff.

But to say that people who are using the newest of the new ATI cards should use radeon open source drivers is kind of silly isn't it? Who would drop a couple hundred bucks on a card and then install drivers that don't support 3d acceleration?

With that said, is there any estimate on when the open source drivers will be able to support 3d?

---

### Post by Yellow Pasque on 2008-05-02
jocko, this guide was made with users installing or upgrading to Hardy in mind. I'm aware of the old 8.37 driver.

ASULutzy, people using the very latest ATI cards may not have their PCI ID match up with Ubuntu's outdated (Catalyst 8-3) proprietary driver, so they would have no choice.

> With that said, is there any estimate on when the open source drivers will be able to support 3d? 
From what the radeonhd developers have said, it should be some time in 2008. Good news on Phoronix today:

> The RadeonHD DRM isn't yet in a usable state to end-users, but Matthias Hopf has pushed his latest RadeonHD work into his personal git tree. DRM is now able to initialize on an RS690 GPU, but DRI isn't working yet. Nor does Matthias's code work with 2D acceleration currently. However, he does hope to have this code working within a few weeks. The git URL and his message can be read on the RadeonHD mailing list. Luc Verhaegen has also made a very interesting RadeonHD enhancement without DRM, which could be available for public showing soon.

---

### Post by jocko on 2008-05-02
> **Temüjin said:**
> jocko, this guide was made with users installing or upgrading to Hardy in mind. I'm aware of the old 8.37 driver.

You claimed that the catalyst driver in hardy doesn't support agp cards, but that's wrong.
I have tried hardy with the catalyst driver on this computer, with a radeon 9600 pro agp card, and it does work. So I just wanted to point out that the information you give is at least partially wrong.
However, xvideo overlay with the catalyst driver is pretty broken and dual display support is much worse than with the old 8.37 driver in gutsy, but that's independent of which card you have, be it pcie or agp. Still overall the catalyst driver is superior to the open source ati/radeon driver (at least in my hands) in many ways (it's actually capable of tvout support in other resolutions than 800x600)...

---

### Post by Yellow Pasque on 2008-05-02
> You claimed that the catalyst driver in hardy doesn't support agp cards, but that's wrong.
Ah, I'll fix it up later tonight. Thanks

---

