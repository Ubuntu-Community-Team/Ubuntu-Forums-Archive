---
title: "Install Nvidia drivers in Wine"
date: 2008-10-24
forum: Wine
---

### Post by Heroshinator on 2008-10-24
I was wondering if it is possible to install a video card driver in wine. Just as i was typing that sentance i realized that i dont know if Wine uses hardware virtualization since im an ubuntu newbie. 

I guess when answering that question I just want to know ways such as patches and drivers to increase wine performance.

I am trying to switch to ubuntu on my desktop for a few months to see if i should use it on my college laptop when i get it. (Also considering buying a macbook pro any good thoughts on that)

---

### Post by hikaricore on 2008-10-24
You can't install drivers under WINE.

Well I mean you can probably try but it won't do anything at all aside from wasting a small amount of drive space.

If you wish to install or update your nvidia drivers you will need to do it through the package manager or with a binary installer for Linux from nvidia's website.

---

### Post by asdfoo on 2008-10-24
> **Heroshinator said:**
> I was wondering if it is possible to install a video card driver in wine. Just as i was typing that sentance i realized that i dont know if Wine uses hardware virtualization since im an ubuntu newbie. 

I guess when answering that question I just want to know ways such as patches and drivers to increase wine performance.

I am trying to switch to ubuntu on my desktop for a few months to see if i should use it on my college laptop when i get it. (Also considering buying a macbook pro any good thoughts on that)

Installing envyng-core and envyng-gtk using synaptic is probably the easiest way.  It won't work in Wine.

---

### Post by jacksaff on 2008-10-24
Wine doesn't deal with hardware directly. If your windows program makes calls that linux can handle then wine passes them on to the kernel. If the program wants to do something that linux can't do then wine translates the call into something that linux can dealwith first. In the case of windows games using directX for video, wine translates directX calls into open gl ones that the linux kernel knows how to deal with. You can't install hardware drivers in wine. 
You can sometimes use a windows dll with wine which you might want to do if the dll has a function not yet in wine or if the wine version is buggy. This means you're using MS code though, and you may need a license to do so.

---

