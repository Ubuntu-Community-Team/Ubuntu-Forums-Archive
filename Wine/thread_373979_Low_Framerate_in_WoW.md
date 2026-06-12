---
title: "Low Framerate in WoW"
date: 2007-03-01
forum: Wine
---

### Post by BitTorrentBuddha on 2007-03-01
I've been playing world of warcraft on Linux for a couple months now, and the longer I play, the more difficult PVP seems to be with my low framerate, typically between 7 and 20 frames per second. I was wondering, if there are any tricks, short of disabling the OpenGL extension in regedit, which I have already done, that will increase my framerate significantly. 

I also would like to know if my framerate is suffering solely due to my specs: 2.0gHz Celeron @ 2.8gHz, 1024MB DDR2 RAM, nVidia GeForce 6200 AGP 128MB. And if it is due to my hardware, what can I upgrade to get the largest performance boost, my guess would be CPU, but please tell me if otherwise.
    
I appreciate your help and anticipate your replies.

---

### Post by Sammi on 2007-03-02
Dude, if you care about gaming then you shouldn't have bought a Celeron in the first place.

Don't really know about the how much RAM WoW needs, but I think the graphics card should be fine.

---

### Post by justin whitaker on 2007-03-02
> **BitTorrentBuddha said:**
> I've been playing world of warcraft on Linux for a couple months now, and the longer I play, the more difficult PVP seems to be with my low framerate, typically between 7 and 20 frames per second. I was wondering, if there are any tricks, short of disabling the OpenGL extension in regedit, which I have already done, that will increase my framerate significantly. 

I also would like to know if my framerate is suffering solely due to my specs: 2.0gHz Celeron @ 2.8gHz, 1024MB DDR2 RAM, nVidia GeForce 6200 AGP 128MB. And if it is due to my hardware, what can I upgrade to get the largest performance boost, my guess would be CPU, but please tell me if otherwise.
    
I appreciate your help and anticipate your replies.

Decrease your draw distance. It helps tremendously with frame rates.

---

### Post by BitTorrentBuddha on 2007-03-02
> **Sammi said:**
> Dude, if you care about gaming then you shouldn't have bought a Celeron in the first place.

Don't really know about the how much RAM WoW needs, but I think the graphics card should be fine.

Made the computer when I was 15, and didn't have a job. I didn't care about gaming at the time, and didn't have the funds to beat the value of a Celeron. But what your saying, is that a CPU upgrade will definitely be a good way to go to up my framerate?

---

### Post by Sammi on 2007-03-02
Other than doing what justin whitaker suggests and buying a whole new computer... yes. Celeron was never meant for gaming.

---

### Post by BitTorrentBuddha on 2007-03-02
Building a new computer seems like the path to take here, the one I've got right now only has a 30gb hard drive and a pretty bad motherboard. Thanks for your replies.

---

### Post by I have no job on 2007-10-25
i had same problema with a radeon 9600 pro, but i dont hink you need a new computer since im playng this game with my onboard intel card right now, i thinhk this tweak can solve the problem :
 
OpenGL Registry Edit

A common performance tweak for wine and opengl games is a registry edit. While your results may vary, many users report up to a 100% increase in framerate with no loss of stability. To make this change, do the following:

   1. Open regedit (regedit)
   2. Navigate to HKEY_CURRENT_USER\Software\Wine\
   3. Right click on the wine folder and select [NEW] then [KEY].
   4. Replace the text New Key #1 with OpenGL (case sensitive).
   5. Right click in the right panel and select [NEW] then [String Value].
   6. Replace the text New Value #1 with DisabledExtensions (case sensitive).
   7. Now right click on DisabledExtensions and select Modify
   8. A dialog box should appear. In the value field type GL_ARB_vertex_buffer_object 

Here's a screenshot of what it should look like, roughly, once you've done this: [http://appdb.winehq.org/appimage.php?iId=3746](http://appdb.winehq.org/appimage.php?iId=3746) 

and dont forget when  create the laucher put the -opengl paramenter  = like this WoW.exe -opengl 
i hope will work

---

