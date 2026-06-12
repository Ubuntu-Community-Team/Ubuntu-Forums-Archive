---
title: "Launcher in the way during Wine gameplay"
date: 2012-07-08
forum: Wine
---

### Post by Futant on 2012-07-08
Hello, just upgraded to precise, very happy generally but have one small problem. When I play a game using Wine, the launcher appears whenever I move to the left. I'm guessing its something to do with the new launcher thing of appearing with two bumps to the left (which in itself is brilliant) as it didn't happen in 11.10. Just wondering if anyone knows a way to sort this out? Its not a massive problem, just one of those things I'd like to fix

---

### Post by Paddy Landau on 2012-07-08
I can think of a couple of things to try. First install [Compiz Config Settings Manager]("apt:compizconfig-settings-manager") (CCSM).

Now try these to see which of them you prefer.

[LIST]
[*]CCSM > Desktop > Ubuntu Unity Plugin > Behaviour > Hide Launcher > Never
[/LIST]
If you don't like that or if it doesn't work well, restore it to its default behaviour (Autohide), and do this:

[LIST]
[*]CCSM > Desktop > Ubuntu Unity Plugin > Behaviour > Reveal Trigger > Top Left Corner
[/LIST]
This one will reveal the Launcher not when you bump left, but only when you bump the top-left corner.

---

### Post by Futant on 2012-07-08
Thanks, already had ccsm, not really into the top left corner trigger but I can indeed use it whenever I want to play with Wine :) Still interested if there's a proper fix for this though?

---

### Post by thatguruguy on 2012-07-08
> **Paddy Landau said:**
> I can think of a couple of things to try. First install [Compiz Config Settings Manager]("apt:compizconfig-settings-manager") (CCSM).

Now try these to see which of them you prefer.

[LIST]
[*]CCSM > Desktop > Ubuntu Unity Plugin > Behaviour > Hide Launcher > Never
[/LIST]
If you don't like that or if it doesn't work well, restore it to its default behaviour (Autohide), and do this:

[LIST]
[*]CCSM > Desktop > Ubuntu Unity Plugin > Behaviour > Reveal Trigger > Top Left Corner
[/LIST]
This one will reveal the Launcher not when you bump left, but only when you bump the top-left corner.

Actually, these options are now available without installing CCSM. Simply right-click on your desktop, and choose "Change Desktop Background." Then, click on the "Behavior" tab. You can choose whether to auto-hide the Launcher, whether the "reveal location" is the left-hand side or the upper-left corner, and set the sensitivity from that menu.

---

### Post by Paddy Landau on 2012-07-09
> **thatguruguy said:**
> Actually, these options are now available without installing CCSM...
Cool. Thanks.

---

