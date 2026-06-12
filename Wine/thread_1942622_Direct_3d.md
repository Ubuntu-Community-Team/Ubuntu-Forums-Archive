---
title: "Direct 3d"
date: 2012-03-17
forum: Wine
---

### Post by srharri9 on 2012-03-17
How do I get Direct 3d installed?  I'm completely lost :(

I am running Ubuntu 10.10, but I have little experience so far.

What other kinds of information do I need to provide for help in this matter?

---

### Post by Toz on 2012-03-18
If you are talking about installing direct3d in wine, then (from a terminal window):
```
winetricks d3dx9
```

Why do you need to install Direct 3D? What are you trying to do?

---

### Post by srharri9 on 2012-03-18
I'm trying to get a game to run properly.  However, I now see that I've had direct3d installed all along. So, I guess my issues are coming from some other source.

Thanks for the help.

---

### Post by Toz on 2012-03-18
Which game are you trying to install and what are the issues you are facing?

---

### Post by srharri9 on 2012-03-19
I'm trying to play Star Trek Online.  The Hud and menus work, and I can see other player's names.  However, it's like somebody turned off all the lights and I'm flying around in the dark.  I can just make out the outlines of ships, and I can see some running lights, but for the most part, it's pretty dark.  I've posted this question on the STO forums, but nobody's replied yet.

---

### Post by forrestcupp on 2012-03-19
If you're on Ubuntu 10.10, I suspect you need to uninstall STO, [install the Wine PPA for Ubuntu](http://www.winehq.org/download/ubuntu), and get the latest version of wine. Then try installing STO again. STO has a gold rating on Wine 1.4 without any workarounds.

---

### Post by srharri9 on 2012-03-19
@forrestcupp

I will try that as soon as I get a minute!  That sounds like it'll be extremely easy.  Thanks for the suggestion.  I'll let you know how it goes.

---

