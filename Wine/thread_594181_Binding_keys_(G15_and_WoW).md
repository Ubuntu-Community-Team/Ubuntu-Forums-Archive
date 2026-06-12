---
title: "Binding keys (G15 and WoW)"
date: 2007-10-27
forum: Wine
---

### Post by shailiha on 2007-10-27
Heya.

The reason I'm not putting this in the WoW thread is because its more about the G15 keyboard than WoW.

I've recently got everything working fine for me, except two things.

1) When running WoW under Wine I can't bind the § button to any action, it only responds if I type it in a chatbox. Anyone know why this is and/or how to fix it?

2) The 18 extra buttons on the G15 keyboard I have configured in windows like so (a small example): G1 = ctrl+alt+F1, G2 = ctrl+alt+F2 etc etc, which easily made them bindable in WoW or any other game really that allows keybindings. Is there any way to do the same under linux? I've read all I can on google and on here about g15tools, but I just can't find any information that helps me.
I have G15daemon running without problem.

---

### Post by szaqlon on 2008-06-23
I would love to have an answer to that. That is exactly the way I use those keys. This topic seems to have everyone stumped.

---

### Post by hoozey on 2008-07-16
I am trying this using xbindkeys and xbindkeys-config. It works somewhat, but whenever I hit a G key, it toggles the numlock key, sending my character into autorun(very annoying). What's weird is it doesn't actually turn numlock on or off (the light stays on). It seems to send the numlock keypress only to WoW and not to Ubuntu. I may just have to unbind numlock from autorun in WoW as a workaround, but I'm still messing around with this...I'll report back if I make any progress.

---

### Post by hoozey on 2008-07-16
I now have it everything mostly working. Some combinations don't seem to work in WoW this way, such as Ctrl-Shift-F1 (this is only through xbindkeys, Ctrl-Shift-F1 is a valid key combo for WoW). So I ended up just using Ctrl-F1 through F10  and Ctrl-Alt-1 through 8. 

One thing that doesn't work is casting on key up events. In other words, spells are cast as soon as I hit the button, instead of as soon as I release the button, which is the preferred way. I need to figure out how to make xbindkeys hold a key combo down instead of just hitting it and releasing immediately.

I also had to unbind numlock (see previous post). This was okay for me though since I use the fwd mouse button for autorun.



So basically all I did was follow the ubuntu G15 guide here: [https://help.ubuntu.com/community/LogitechG15](https://help.ubuntu.com/community/LogitechG15)

and then use xbindkeys to map the G keys to key combinations.

---

### Post by Spydr4590 on 2008-07-18
Thanks Hoozey. I'll have to give this a try.

---

### Post by ckrodle on 2010-06-17
I've been trying to do this myself, but I'm running into problems.
I've installed the g15daemon, and xbindkeys.

However, when I run xbindkeys-config, I'll select the "Get Key" button and whenever I press a G button the xbindkeys-config just locks up and goes gray. 

Has anybody successfully ran this in 10.04. If so, please help me out.

---

### Post by WoWer on 2010-08-07
I am having a similar problem. When I click Get Key it automatically closes the window back to the terminal. I am very new to linux and I am trying to setup for Gaming on WoW. If anyone knows of a fix it would be greatly appreciated. Also for further information I do have keyboard model set to G15 with G15daemon

---

