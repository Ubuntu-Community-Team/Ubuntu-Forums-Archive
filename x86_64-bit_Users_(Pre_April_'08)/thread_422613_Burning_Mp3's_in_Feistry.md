---
title: "Burning Mp3's in Feistry"
date: 2007-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by ghandi69_ on 2007-04-25
Ok, I use K3B usally to burn music cd's to listen to in my car.  However, since I've install feisty 64, it says it is missing the plugin to do so.  I have .mp3's playing fine in amarok, and I downloaded a whole bunch of gs streamer packages based on directions from the edgy guide, but no luck. Is this a 64bit issue that I'm possibly missing??

---

### Post by juanhunglow on 2007-04-25
> **ghandi69_ said:**
> Ok, I use K3B usally to burn music cd's to listen to in my car.  However, since I've install feisty 64, it says it is missing the plugin to do so.  I have .mp3's playing fine in amarok, and I downloaded a whole bunch of gs streamer packages based on directions from the edgy guide, but no luck. Is this a 64bit issue that I'm possibly missing??

I don't burn mp3's but I do notice a warning that comes up when I open k3b about no mp3 support and something about installing MAD files.  Do you get that message?

---

### Post by ghandi69_ on 2007-04-25
> **juanhunglow said:**
> I don't burn mp3's but I do notice a warning that comes up when I open k3b about no mp3 support and something about installing MAD files.  Do you get that message?

Yes.. yes I do.. I tried installig everything "mad" i could find in the packet manager.

Also of note, serpentine works for mp3, but I just think its kind of a pain to use.

---

### Post by PJSingh5000 on 2007-04-28
Try installing libk3b2-mp3 using Adept Manager to remove the error/missing plugin message.

---

### Post by nemarona on 2007-04-29
With the advent of Feisty, support for mp3, Flash, Java, etc, has been bundled into the ubuntu-restricted-extras package. Sadly this package doesn't include libk3b2-mp3, which is what (as PJSingh5000 rightly pointed out) we need here. I believe this might be related to k3b being a KDE application.

Devs, what about a future "kubuntu-restricted-extras" package that includes libk3b2-mp3?

---

### Post by dptxp on 2007-04-30
Can not say about MP3 encoding, but enable ALL SOFTWARE (I forget tht words) on right and top of add/remove (open that first). Then select the gstreamer plugins in audio/video , I use the first two- I think the bad and ugly.

Playback of mp3 and many video formats get enabled.

---

### Post by Kilz on 2007-04-30
> **nemarona said:**
> With the advent of Feisty, support for mp3, Flash, Java, etc, has been bundled into the ubuntu-restricted-extras package. Sadly this package doesn't include libk3b2-mp3, which is what (as PJSingh5000 rightly pointed out) we need here. I believe this might be related to k3b being a KDE application.

Devs, what about a future "kubuntu-restricted-extras" package that includes libk3b2-mp3?

I took a look at the Ubuntu packages site,[ it lists a libk3b2-mp3 in the universe]("http://packages.ubuntu.com/feisty/libs/libk3b2-mp3"), are you sure you have that repo enabled?

---

### Post by PJSingh5000 on 2007-05-01
Kilz, I do have universe enabled.

---

### Post by Kilz on 2007-05-01
> **PJSingh5000 said:**
> Kilz, I do have universe enabled.

Thats strange, because we can see, with the link I provided above, it should be there.  Have you tried just downloading the deb file, clicking on it, and letting gdebi install it?

---

### Post by John.Michael.Kane on 2007-05-01
I can vouch for libk3b2-mp3 being in the current repos as well.

Those having issue post your sources.list.

---

