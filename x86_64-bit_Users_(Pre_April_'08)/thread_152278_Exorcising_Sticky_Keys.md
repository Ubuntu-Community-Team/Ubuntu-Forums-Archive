---
title: "Exorcising Sticky Keys"
date: 2006-03-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-03-29
Ubuntu-64 Breezy, nVidia diver at 1680 x 1050 on Compaq laptop.
<crossposted to 32-bit forum, because it may not be just a 64-bit issue>

I installed the nVidia driver to get Totem to play movies, which it now does very well. Previously, while trying to get movies working I had installed ogle, gxine, vlc and mplayer. So last night, this being spring break, I decided to watch a movie and try out the other players. All failed, and have been uninstalled, except gxine. So I was playing this movie with gxine and suddenly "Do you want to enable sticky keys" popped up. I said no, and continued to watch the movie. A few moments later another one popped up. And so it went for 15-20 minutes. At one point I clicked on No and another one popped up immediately. This went on for 10-15 popups before it finally went away. And afterwards another one popped up every vew minutes. Eventually I decided I didn't like gxine, particularly because there was evidently a bug with sticky keys. After all, I had not touched the keyboard once, not even to start the movie. I went to close gxine, but all I could get with the mouse was a + sign over whatever I was clicking on, and no action resulted. The keyboard was completely dead. I had to shut down the computer to escape.

Now, I have had this "Do you want to enable sticky keys" window pop up before. Normally it just goes away when I click on No. It's annoying, but it doesn't happen that often. And it has always happened on this computer, even back when I was running Hoary. The thing is, though, that it happens at random even if I don't press the shift key five times, which is supposed to be how you turn on sticky keys.

At this point I just want to get it off my computer. According to what I can find it is part of X. But the only documentation I can find tells me how to enable it and how to disable it. I need to REMOVE it forever. Or at least find some startup code that will make it unavailable even if the user presses shift five times. I can't find any documentation that tells me how to get completely rid of it. Does anyone have any ideas?

---

### Post by skylark on 2006-03-31
Maybe this has something to do with keyboard accessibility?

Try:
System -> Preferences -> Keyboard

Then press the "Accessiility" button at the bottom of the keyboard preferences panel.

Then at the top of this panel make sure "Enable keyboard accessibility features" is unchecked.

If it is already disabled then I've gone down a completely wrong track - sorry!

---

### Post by John Jason Jordan on 2006-03-31
[QUOTE=skylark]Maybe this has something to do with keyboard accessibility?
Try:
System -> Preferences -> Keyboard
Then press the "Accessiility" button at the bottom of the keyboard preferences panel.
Then at the top of this panel make sure "Enable keyboard accessibility features" is unchecked.
If it is already disabled then I've gone down a completely wrong track - sorry![/QUOTE]
I had already unchecked "Enable Sticky Keys" below, but didn't see the "Enable Keyboard Accessibility Features" above. It was checked, so I unchecked it! I hope that works!

Thanks for the tip.

---

### Post by gfca on 2006-10-05
I have the same problem... I think!
but that solution doesn't work for me!!
any suggestion?

thanks

---

