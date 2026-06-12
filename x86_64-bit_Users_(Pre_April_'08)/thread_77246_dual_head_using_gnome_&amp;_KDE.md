---
title: "dual head using gnome &amp; KDE"
date: 2005-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by luckyaba on 2005-10-16
I have 2 pci express nvidida 6600 gt's sli'd together but the driver doesn't support that. So i was think of installing two monitors( one on each card) but i was also wondering if there was a way to set it up so that one monitor has KDE running on it while the other has gnome? Is there a way to do this?

maybe a howto?

i can get the monitors and everything setup i am just not sure about the 2 desktop parts.

---

### Post by Rounan on 2005-10-16
The short answer: It probably could be done, but you don't want to bother.

The long answer:

I've never seen this done, but what you'd have to do for what you describe is start two instances of the X server, one for each monitor, and run kdm and gdm seperately on each display. That would probably require some fairly serious rc-script editing to do automatically every boot.

Then, you'd either have to use seperate keyboards/mice to drive each display, or work out some fancy symlinking script to disengage inputs from one Xserver and engage into the other. And I'm not sure how the server would react to the device it's using suddenly disappearing.

Then you'd have to work out how to tell programs you're launching which display to use. The cleanest way would probably be to have two seperate users. With two seperate home directories. But you could probably also re-set the $DISPLAY variable in your input-changing script.

So far, we've doubled the hardware on your desk, doubled the amount of data in RAM, and doubled the size of your home directory, as well as adding a whole lot of complication. And that's before we try to get kmail and evolution to share your email, gaim and kopete to share your IM connections.... etc.

Though it may be that someone has come up with a way to do this, what I'm getting at is that it's probably a lot of hassle for very little gain. Gnome apps will launch and work in KDE just fine, and vice-versa. If you really want two completely seperate desktop environments simultaneously, it would actually be easier to install them on two seperate machines and buy a KVM switch.

---

### Post by luckyaba on 2005-10-16
wow... thanks for the explanation. It sounds like an awesome idea but when you put it that way i think im gonna stick with just the twinview.... lol

---

