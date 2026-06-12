---
title: "New User: Graphics card issue (Limited graphics mode)"
date: 2008-03-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by PremiumPete83 on 2008-03-11
I just installed Ubuntu for the first time on a second partition and am currently dual booting with Vista.  I'm having a problem with my GeForce 7900GS Nvidia card.  Every time I boot up it says it can't recognize hardware and it reverts back to limited mode.  Now I notice it doesn't recognize my monitor (Dell 1503FP digital) or my graphics card properly.  

Under Vista it is fine but I do get a warning that it's down clocked so the card isn't damaged because it is underpowered a little.  Would this cause the issue?

I used Envy to install the restricted drivers to no avail..

---

### Post by warp99 on 2008-03-11
Well your first problem was that you used envy and didn't have to because Ubuntu already has a restricted devices manager under System &#8594; Administration:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

The first thing to do is back out of the mess that envy may have made:

Open up a terminal and do the following:

```
 sudo dpkg-reconfigure xserver-xorg
```

Reconfigure the driver to fit your graphics card and display, once finished press ctrl-alt backspace to reload the xserver. You may have to use the open version of the driver named "nv" instead of the "nvidia" driver if there is a problem until you can troubleshoot to install the restricted driver.

If you can't get the restricted driver installed do the following:

```
cat /etc/X11/xorg.conf > ~/Desktop/xorg.txt
```

and cut/paste the contents of the xorg.txt file on this thread so I can review it. ;)

---

### Post by PremiumPete83 on 2008-03-11
Yeah, I think I see the issue.  The box came with a post manufacturer video card and the power cord isn't plugged into the back of the card as it needs extra juice.  I'm assuming this is why the nvidia driver isn't picking up the card.  I'll do the steps above the get rid of the current driver to get up and running and run to the pc store to get the right power cable split.

Thanks.

---

### Post by warp99 on 2008-03-11
> **PremiumPete83 said:**
> Yeah, I think I see the issue.  The box came with a post manufacturer video card and the power cord isn't plugged into the back of the card as it needs extra juice.  I'm assuming this is why the nvidia driver isn't picking up the card.  I'll do the steps above the get rid of the current driver to get up and running and run to the pc store to get the right power cable split.

Thanks.

That's the **exact** same thing that happen to me when I was trying to get my nvidia card running, but the extra power port was on the inside. :)

---

### Post by PremiumPete83 on 2008-03-11
Yeah, this is on the back of the card.  I think I'm going to need a new power supply.. :/

---

