---
title: "Any wireless PCMCIA or USB that works?"
date: 2008-07-07
forum: x86 64-bit Users
---

### Post by kenfeyl on 2008-07-07
My integrated wireless recently died on Ubuntu and Windows, so it's a hardware problem. In the meantime I need an alternative, and I've tried out two USB wifi sticks only to find that 64-bit Ubuntu is miles behind 32-bit in terms of compatibility with these sticks. My current buy is a D-Link WUA-2430. Neither D-Link nor Atheros publishes a 64-bit driver for this device, so ndiswrapper is out. There also does not appear to be a native driver, since MadWifi doesn't support USB chipsets. The same disappointment happened with my last buy, a WG111v3 (which published only Vista64 drivers). Both vendors seem to be leaning on 64-bit Windows' compatibility with 32-bit device drivers. Sadly, ndiswrapper provides no such luxury. Sucks for us. The depressing thing is that I had done my homework both times and found multiple posts saying "I got this stick working with Ubuntu!" The people fail to mention their architecture, and that their solutions are almost always for 32-bit Ubuntu.

Now I would like to query the community for help. I need a USB stick or PCMCIA card that WORKS in amd64. It doesn't have to work out of the box; I'm willing to install it using a how-to guide (but am unable to do much beyond that, please). Please provide the brand and model number. Does anyone have such a device working on an amd64 system?

P.S. I saw a previous, similar thread on USB sticks that work out of the box, but there was no real conclusion on a stick that works.

---

### Post by kenfeyl on 2008-07-08
Oh my gosh. I'm almost in tears here. I got the WUSB54GC from Linksys today and the thing works out of the box in AMD64 Hardy! I was so thrilled I almost wept when I saw the little green circles over the networking icon. I didn't even have to do a thing -- all the drivers were there. Apparently we x64'ers need to stick to Ralink drivers. Wow. Just wow.

---

