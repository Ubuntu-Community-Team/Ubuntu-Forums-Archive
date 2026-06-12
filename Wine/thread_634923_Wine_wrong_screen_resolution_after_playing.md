---
title: "Wine: wrong screen resolution after playing"
date: 2007-12-08
forum: Wine
---

### Post by Neo40 on 2007-12-08
Hi,

My normal screen resolution on my laptop is 1280x800. When I use wine to play a game (like Civ IV), and I go back to my desktop, the resolution is 1024x768 instead my native resolution. How can I fix this?

Thank you!

---

### Post by cogadh on 2007-12-08
What version of Wine are you using? This problem is generally corrected in the most current version, 0.9.50. If you are using the current version and it is still happening, then I would recommend you either run the game in a Wine virtual desktop window or in a seperate X server from your normal desktop.

---

### Post by dethredic on 2007-12-08
This happens to me as well. My normal resolution is 1280x 1024, but after playing it is set to 1600x1400. I have the most recent version of WIine

---

### Post by Neo40 on 2007-12-08
> **cogadh said:**
> What version of Wine are you using? This problem is generally corrected in the most current version, 0.9.50. If you are using the current version and it is still happening, then I would recommend you either run the game in a Wine virtual desktop window or in a seperate X server from your normal desktop.

I'm using the latest version (0.9.50). How can I set wine in virtual desktop? How can I start a separate X server?

---

### Post by Marrshu on 2007-12-08
to run Wine in a virtual desktop, go to a terminal and type in "winecfg" 

On the Graphics tab, check "Enable a Virtual Desktop" then specify the res you want in the boxes below.

---

### Post by cogadh on 2007-12-08
> **Neo40 said:**
> How can I start a separate X server?
Create and use a launch script. Click on the "Stuff I've learned about Wine" link in my sig and go to the "Advanced Stuff" section, it is explained in step-by-step detail there.

---

