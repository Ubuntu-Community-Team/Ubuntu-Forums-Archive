---
title: "&quot;Frames to render ahead&quot; option in nvidia for wine?"
date: 2011-08-05
forum: Wine
---

### Post by len1444 on 2011-08-05
Hello, I have only been using ubuntu for a little while, but am already getting comfortable. :popcorn:

Anyway, my inquiry pertains to the "Max Frames to Render ahead" option in nvidia control panel. (in windows, not linux) I'm sure there must be a way to tweak this option in linux but can't find anything related. (tried searching the forums, google, and got nothing)

Basically what the option does is specify how many frames the application may prerender, so it can get loaded later. If set to a high value, mouse lag can sometimes appear. This is the problem I have,(the specific game is oblivion) and I wish to rectify it by finding this option somewhere in linux.

Regards,

Leo

---

### Post by Iloru on 2011-12-02
I'd like to know this, as well.  I've been trying to tweak Skyrim so that there is less lag/stuttering and one of the tweaks that worked well when I had Windows was to set "Frames to Render Ahead" to 1.  The nvidia-settings panel doesn't have this feature, unfortunately.  :(

---

### Post by Dlambert on 2011-12-02
If you manually go into the config file, it should be either Sampling/multisampleing= X, or draw distance/view-distance.

---

### Post by Iloru on 2011-12-02
Thank you!  I'll have to give it a try to see how it goes.  :)

---

### Post by Iloru on 2011-12-02
Ok, I tried changing the multisampling value in the game's config file and it definitely didn't do the equivalent of the "Frames to Render Ahead" setting on the Windows Nvidia control panel. If I was supposed to change an Nvidia config file, could you give me an idea of where I might find it? I have never seen such a file on my system.

*edit* - In case I misunderstood and was supposed to edit a wine config, where might I find it?  Would it be a regedit or something else?

---

### Post by Dlambert on 2011-12-02
No, the skyrim config.

---

