---
title: "Please reccomend a video card for x86-64 Feisty"
date: 2007-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by jnutter on 2007-04-25
Nobody seems have an answer as to how to get my on board Via K8M890 video functioning properly with X86-64 Feisty, so let's try a different idea...

Can anyone tell me what video card they have used that worked properly with an x86-84 Feisty install on an AMD based machine? Bonus points if you have used that card with an MSI motherboard with the Via K8M890 chip set and an AMD 62 X2 series CPU. 

It would be even better if you could recommend a PCI express card that costs under $100 and supported wide screen modes like 1440x900 because I have this [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2974576&CatId=170](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2974576&CatId=170) monitor, although any suggestions would be appreciated.

Thanks

John Nutter

---

### Post by krylko on 2007-04-25
Hi, welcome to 64-bit Ubuntu :)

I am using MSI GF 6600 (128MB) with proprietary drivers. Everything works fine, once you set it up. If you are going to play with Beryl/Compiz, you will have to have some patience. Otherwise, if you do not need full 3d acceleration, stick with the free drivers (enabled by default). My motherboard is Foxconn and the chipset is SiS. The processor is AMD Athlon 64 2800+. As far as the graphic card goes, everything works fine, but I had some trouble setting it up and it was my fault (I know this sounds stupid but I forgot to switch the monitor driver from default PnP to mine and could not - obviously - raise refresh rate to more than 60Hz and resolution to more than 640x480 until I switched - ancient HP Pavillion M70 and it was on the list :)).

Very nice release indeed, especially at the hardware point. I am pretty sure that you should have no problems if you choose any current NVIDIA card. As for ATI, I am not familiar with their drivers' situation. Somebody help him there?:confused: 

I saw a decent XFX GF 7600 selling at Sams club for under $100. You gotta be a member though, and hopefully there are Sam's clubs in your area. That card is more than enough for Linux use, unless you want something high-end for Cedega compatible titles.

---

### Post by Enverex on 2007-04-25
In short get the best PCI-E nVidia card that you can afford or are willing to shell out for. That's the safest and generally best option in Linux.

---

### Post by silverpig on 2007-04-25
> **Enverex said:**
> In short get the best PCI-E nVidia card that you can afford or are willing to shell out for. That's the safest and generally best option in Linux.

I second this option. Take a look at the 7300GS.

---

### Post by jnutter on 2007-04-25
Thanks for the suggestions! 

I've got one of these coming in the mail. 

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2746205&CatId=1560](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2746205&CatId=1560)

I don't have any 3D plans at the moment, so I think this will be OK for now.  It fits my budget.

---

### Post by ronocdh on 2007-04-26
> **Enverex said:**
> In short get the best PCI-E nVidia card that you can afford or are willing to shell out for. That's the safest and generally best option in Linux.
Can't be better said. If you like Linux, don't buy ATI! Check my sig, you'll know how much I mean it. ;)

If Dell does release open hardware laptops, I'm really thinking of buying one. I love my MBP, but I **love** open hardware!

---

### Post by kiaran on 2007-04-26
Might want to stay away from the 8800 series from Nvidia. I've got one and it's given me lots of grief.

If you're willing to trudge through the mess getting it installed, the performance is killer though:guitar:

---

### Post by Enverex on 2007-04-26
> **jnutter said:**
> Thanks for the suggestions! 

I've got one of these coming in the mail. 

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2746205&CatId=1560](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2746205&CatId=1560)

I don't have any 3D plans at the moment, so I think this will be OK for now.  It fits my budget.

That video card should work great as far as drivers go in Linux, but the card itself is very very low end. The "TurboCache" cards basically steal your system RAM which in itself is alot slower than normal video RAM and means you have less system RAM to use. The 7100 series itself is basically "super budget".

Although it depends what you intend to do with it, I assume you're not intending on gaming at all in which case it should be fine.

---

### Post by k@pl@n on 2007-04-26
> **kiaran said:**
> Might want to stay away from the 8800 series from Nvidia. I've got one and it's given me lots of grief.

If you're willing to trudge through the mess getting it installed, the performance is killer though:guitar:

well nvidia release a new driver for 8xx series .   

 im going to buy a 8600gt sonic but i have doubts about of aiglx run or not :confused: 

  will u give me more detail of your expreriences about your(8800) card.  my distro feisty amd 64.

  thx.

---

### Post by marcio.mutti on 2007-04-26
Just be sure to go for nVidia. ATI drivers stink.
Last year I changed my video card from x1600 to GF6800 just to get rid of the trouble it was forcing me into.

---

### Post by diskotek on 2007-04-26
i wish i could change my ATI...

---

### Post by Enverex on 2007-04-26
> **diskotek said:**
> i wish i could change my ATI...

I'm sure most ATi users feel the same. My semi-old laptop has a Mobility Radeon 9000 in it. With the open source 'radeon" driver the 3D is "ok" but 2D rendering (window redraw etc) is unbearably slow, like it's drawing it with an etch'a'scetch. :(

---

### Post by k@pl@n on 2007-04-26
i want to ask a quetion too. is there any performance difference on XGL or aiglx  via 64 bit ubuntu ?

---

### Post by NullHead on 2007-04-26
> **k@pl@n said:**
> i want to ask a quetion too. is there any performance difference on XGL or aiglx  via 64 bit ubuntu ?

I'm interested too is there a difference?

---

### Post by Mongoose on 2007-04-26
AIGLX is the only way to go imho, so I guess it's a trick question.  ;)

I use beryl, and it's quiet stable for months with AIGLX... also you can just switch to metacity or whathaveyou and then load up games.  I use my OpenGL modelers and tools with beryl running however, and there is not a noticable difference in rendering / heat / etc even with a lot of shaders.  BTW there will be a PLE version of Maya 8.5 out soon.  It would be nice if Linux got native PLE...  =)

---

### Post by jnutter on 2007-04-30
Thanks for the suggestion on getting the nVidia card. It showed up today. I followed some other posts and reconfigured xorg.conf and then did some hand editing to make the video card auto detect my monitor. Now everything is working the way I expected. 1440x900 resolution comes up and everything looks normal again. 

If anybody else finds this thread and is looking for a way to make their on-board K8M890 work right - forget it and get and nVidia based card :)

---

### Post by kuja on 2007-04-30
> **k@pl@n said:**
> well nvidia release a new driver for 8xx series .   

 im going to buy a 8600gt sonic but i have doubts about of aiglx run or not :confused: 

  will u give me more detail of your expreriences about your(8800) card.  my distro feisty amd 64.

  thx.

I was reading reviews on the 8600s the other day. It seems people were really disappointed with their performance. Supposedly they don't give near as much bang for their buck as the 8800s.

---

### Post by smartbei on 2007-05-01
I have the same chipset, but with an intel corde 2 duo. I am using a geforce 6200TC with no problems. I had a lot of trouble getting the integrated video working, though that was in dapper 32bit and it never worked quite right.

---

### Post by jespdj on 2007-05-02
> **Mongoose said:**
> AIGLX is the only way to go imho, so I guess it's a trick question.  ;)
And the ATI drivers do not support AIGLX (according to the [Compiz documentation](http://compiz.org/ATI)), so you need XGL instead of AIGLX if you're using an ATI card. In order to get Compiz working on an ATI card you need to do some tricks (see [Xgl wiki page](https://help.ubuntu.com/community/CompositeManager/Xgl)) because the ATI driver does not support the Composite extension for X windows. I've got it working now on my ATI X1600 but it's not ideal; 3D acceleration doesn't work for applications, just for the desktop itself. :( ATI Linux drivers are crap! :mad:

I'm going to replace my ATI X1600 with an nVidia 8600GTS soon. The only thing is that the 8600GTS is brand new (introduced two weeks ago or so?) so I wonder if nVidia's Linux drivers for it are useable...
> **kuja said:**
> I was reading reviews on the 8600s the other day. It seems people were really disappointed with their performance. Supposedly they don't give near as much bang for their buck as the 8800s.
Still I'm going for an 8600 and not an 8800 because the 8800 uses much less power (about 50W vs. 100W) and I want a quiet and system that doesn't use too much power. MSI has a [passively cooled 8600GTS](http://global.msi.com.tw/index.php?func=proddesc&prod_no=1197&maincat_no=130&cat2_no=136) - that's what I'm going to get.

---

### Post by jespdj on 2007-05-02
.

---

### Post by FoolishGhoul on 2007-05-02
I was looking at that card too, wonder how it compares to a Radeon X 1950 XT...?

Also is this just too new for Linux support to be available yet?

---

### Post by Coucouf on 2007-05-02
You should get an ATI card not of the latest generation.

I have 2 boxes with a Radeon 9700 (x86) and a Radeon X800XL (x86-64) and they both work perfectly with the open source 'radeon' driver.
3D direct rendering works well and 2D video playback is neat too.
Desktop effects work nearly out of the box (I did just set the driver to 'radeon' in the xorg.conf file and enabled the desktop effets from the gnome system menu).

Dual screen also works perfectly with the 'mergedfb' option. Even desktop effects on dual screen work (with the rightest part of the desktop not beeing refreshed as expected I must say) !

Even if the 3D performance may not be as good as the latest boards, being able to use the open source driver is definitely a good thing. :)
I would advise you to get a X800-something card which you can find for really cheap now !

---

### Post by Tanker Bob on 2007-05-02
I've got an EVGA GeForce 8800 GTS w/640MB and PCI-E x16 interface.  It runs Beryl at around 16,200 frames/sec according to glxgear (not a benchmark program) with the NVIDIA 9755 driver--absolutely awesome.  NVIDIA's Linux support is great, far above ATI or anyone else.  The 8800 GTS is coupled with an E6600 Core 2 Duo CPU overclocked to 2.94 GHz for a screaming system.  Can't say enough good things about the 8800 GTS.

---

### Post by ronacc on 2007-05-02
to the OP  I went through the same grief a few months ago with a k9vgm and ened up with the same solution (in my case an nx7300le) . I'll never buy anything with via graphics again. I knew that for flashy graphics I should go with Nvidia but I didn't need more than a basic desktop on that box boy did I say some bad words when I discovered that the built in via graphics on that board wern't even up to that.

---

