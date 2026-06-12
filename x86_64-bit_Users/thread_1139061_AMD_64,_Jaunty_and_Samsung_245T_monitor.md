---
title: "AMD 64, Jaunty and Samsung 245T monitor"
date: 2009-04-26
forum: x86 64-bit Users
---

### Post by mholmes on 2009-04-26
Hi all,

I'm having a difficult time getting Jaunty 64-bit to drive my Samsung 245T monitor. I have it connected by HDMI cable from the ASUS M4A78 PRO mobo, which has good onboard graphics, and will happily drive two monitors; on the VGA connection I have a Samsung 21" 1600 x 1200 monitor. The 245T resolution should be 1920 x 1200, but Jaunty can only offer me 640 x 480, and the ridiculous 1920 x 540. I've tried everything I can think of, including the proprietary drivers, but nothing works. I've tried booting up with only the big monitor attached, attaching it second, and every other permutation imaginable. 

In previous Ubuntu versions, you could add monitor setup info to xorg.conf, but Jaunty just seems to ignore that. I've found a file called ./.config/monitors.xml, which seems to be the right place to specify the settings I want, but any changes I make there are simply ignored. There also used to be the option in the display configuration applet to specify the make and model of the monitor too, but that's gone in Jaunty. I appreciate that it's a good idea to do auto-detection of hardware capabilities, but when that fails -- and Jaunty seems to fail at detecting this monitor -- how can I tell it what settings it should be using?

I should add that I have virtually identical hardware on a work computer, also with two monitors, running Intrepid, and on that setup I was eventually able to make Ubuntu recognize the monitor properly, but I did it by supplying the monitor make, model and resolution, something I don't seem to be able to do any more in Jaunty.

Does anyone have any idea how to do this?

All help appreciated.
Martin

---

### Post by mholmes on 2009-04-26
Answering my own question: I had a brainwave, and realized that the problem might be connecting the monitor over HDMI. HDMI, I thought, was basically the same as DVI, but it appears that it's actually not; when I reconnected the monitor using the DVI cable instead of the HDMI, Jaunty was able to offer me the correct resolution (using the open-source driver -- I haven't installed the proprietary drivers).

My guess, from a position of pure ignorance, is that the monitor itself fails to give useful info about itself over an HDMI connection -- maybe it assumes it's being connected to a relatively dumb device such as a Blu-Ray player -- but over DVI, it assumes it's talking to a PC, and gives the correct info, enabling Jaunty to provide useful resolution options.

The heart of my question still stands, though: in Jaunty, where on earth do you go to tell the OS information about your monitors?

Cheers,
Martin

---

