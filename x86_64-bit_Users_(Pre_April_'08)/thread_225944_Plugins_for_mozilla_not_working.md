---
title: "Plugins for mozilla not working"
date: 2006-07-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by spacepirates on 2006-07-30
I've gone through maybe three howtos and tutorials on the forums to try and get these plugins working, but one site still refuses to work. ([www.bestofgooglevideo.com)](www.bestofgooglevideo.com)). I've tried automatix, easyubuntu, and the  "Tutorial - How to Install ALL those Required Plugins in Mozilla Firefox (Web Browser)" tutorial. 

help?

---

### Post by Kilz on 2006-07-30
> **spacepirates said:**
> I've gone through maybe three howtos and tutorials on the forums to try and get these plugins working, but one site still refuses to work. ([www.bestofgooglevideo.com)](www.bestofgooglevideo.com)). I've tried automatix, easyubuntu, and the  "Tutorial - How to Install ALL those Required Plugins in Mozilla Firefox (Web Browser)" tutorial. 

help?

Go to my howto, the link is in my signature. Download one of the firefox with flash scripts, follow the instructions in the readme file. Click on the firefox32 it will place on your desktop.

---

### Post by spacepirates on 2006-07-30
followed the HowTo exactly without errors, still no luck with [www.bestofgooglevideo.com](www.bestofgooglevideo.com) . I like how the HowTo sets it up for beginners, espeically with how to use firefox downloads.

still open to suggestions on how to get the plugins to work properly.

---

### Post by Kilz on 2006-07-30
> **spacepirates said:**
> followed the HowTo exactly without errors, still no luck with [www.bestofgooglevideo.com](www.bestofgooglevideo.com) . I like how the HowTo sets it up for beginners, espeically with how to use firefox downloads.

still open to suggestions on how to get the plugins to work properly.

I didnt suggest to follow the howto, I suggested to download and run one of the automated setup scripts on that page. This will install all current packages. The automated scripts were all updated yesterday. The howto is a month or so old since its last update.

---

### Post by spacepirates on 2006-07-31
Installed the scripts without errors, [www.bestofgooglevideo.com](www.bestofgooglevideo.com) still does not work. any ideas?

---

### Post by Kilz on 2006-07-31
> **spacepirates said:**
> Installed the scripts without errors, [www.bestofgooglevideo.com](www.bestofgooglevideo.com) still does not work. any ideas?

I dont know why it isnt working for you. It is for me, and Im running the same script. By the way, what script of the 3 did you install.

---

### Post by spacepirates on 2006-07-31
"This script installs Firefox32 Flash Java, and Mplayer plugin." that one.

I don't know why it wouldn't be working either, maybe another program is causing problems? I have maybe 10 different audio/video applicaitons, and i was thinking one of them might cause mplayer to error.

let me know what you think, or if you need any more information.

---

### Post by Kilz on 2006-07-31
> **spacepirates said:**
> "This script installs Firefox32 Flash Java, and Mplayer plugin." that one.

I don't know why it wouldn't be working either, maybe another program is causing problems? I have maybe 10 different audio/video applicaitons, and i was thinking one of them might cause mplayer to error.

let me know what you think, or if you need any more information.

The google site uses macromedia flash plugin, not mplayer. Go to /usr/local/firefox32/plugins and make sure that flashplayer.xpt and libflashplayer.so are there. Also make sure they are owned by your username , with the users group.

---

### Post by spacepirates on 2006-07-31
you sir, win.

thank you, the site works now. i am just confused as to why all the other plugins work and not flash. it makes me wonder what else could not be working...

but thank you once again.

---

### Post by Kilz on 2006-07-31
> **spacepirates said:**
> you sir, win.

thank you, the site works now. i am just confused as to why all the other plugins work and not flash. it makes me wonder what else could not be working...

but thank you once again.

We all win when things work :) 
But Im a little confused, are you saying that the site works now, but flash doesnt? or that flash is now working and so is the site?
If you did get flash working, what exactly did you fix?

---

### Post by RenZO on 2006-07-31
Probably chmod...

---

### Post by spacepirates on 2006-07-31
flash works. i had thought it was working before, but i suppose i was mistaken. all the HowTos had sites to check if flash and java were working, and they always were, just not on this site. (i found another site that wasn't working either, so it wasn't site-specific)

I used "sudo nautilus" to go into usr/local/firefox32/plugins and modify the permissions of the two flash files from "root" and "users" to my account information. Mplayer still isn't permissioned specifically to me, so i'm going to do that to see if that improves anything.

as a random side question, know of anyway to permanantly be root? as in, no more 'sudo anything' commands? it would just make life easier in situations like this...

thanks once again!

---

### Post by Kilz on 2006-08-01
> **spacepirates said:**
> flash works. i had thought it was working before, but i suppose i was mistaken. all the HowTos had sites to check if flash and java were working, and they always were, just not on this site. (i found another site that wasn't working either, so it wasn't site-specific)

I used "sudo nautilus" to go into usr/local/firefox32/plugins and modify the permissions of the two flash files from "root" and "users" to my account information. Mplayer still isn't permissioned specifically to me, so i'm going to do that to see if that improves anything.

as a random side question, know of anyway to permanantly be root? as in, no more 'sudo anything' commands? it would just make life easier in situations like this...

thanks once again!

I dont recommend even trying to add a root account to Ubuntu. Use gksudo nautilus. I used the Alacarte menu editor to add gksudo nautilus to my system Administration menu to make it easier for me.
What site is giving you problems with mplayer?

---

### Post by spacepirates on 2006-08-01
[http://www.apple.com/trailers/wb/teenagemutantninjaturtles/tmnt_small.html](http://www.apple.com/trailers/wb/teenagemutantninjaturtles/tmnt_small.html)

the movie works... it is very choppy, i blame my interent connection for that though. When it first starts playing i get three mplayer boxes. a video, a control panel, and an error box stating "Couldn't resolve name for AF_INEG: images.apple.com".

that is the only problem with mplayer so far.

is there a way to pause mplayer and let it load the movie before playing, as to avoid skipping?

gksudo nautilus? what is the command i enter in alacarte to create a working link?

---

### Post by Kilz on 2006-08-01
> **spacepirates said:**
> [http://www.apple.com/trailers/wb/teenagemutantninjaturtles/tmnt_small.html](http://www.apple.com/trailers/wb/teenagemutantninjaturtles/tmnt_small.html)

the movie works... it is very choppy, i blame my interent connection for that though. When it first starts playing i get three mplayer boxes. a video, a control panel, and an error box stating "Couldn't resolve name for AF_INEG: images.apple.com".

that is the only problem with mplayer so far.

is there a way to pause mplayer and let it load the movie before playing, as to avoid skipping?

gksudo nautilus? what is the command i enter in alacarte to create a working link?

I wish I knew a way to pause it and let it load, Ill look into it. The command to enter is 
```
gksudo nautilus
``` In the link command. :D  Once you have it set, all you have to do is click on it, enter a password in the box that pops up, and nautilus opens in root mode. I think it should be something they add to all menu's.

---

