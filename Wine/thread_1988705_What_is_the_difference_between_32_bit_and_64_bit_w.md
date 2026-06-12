---
title: "What is the difference between 32 bit and 64 bit wine?"
date: 2012-05-28
forum: Wine
---

### Post by venom104 on 2012-05-28
Okay here is my story. I wanted to play Diablo 3, so I had to compile it with some patches to get it to install correctly. It worked absolutely fine (I had installed the 32 bit version). I was having some issues with OSS4 (and alsa) so I went back to alsa, and installed esound and pulseaudio. My sound now works. I could not for the live of me change the oss4wine.drv driver to the winealsa.drv, so I decided to install the 64 bit version of wine from the repos. Now when I did this, Diablo 3's FPS would drop to almost nothing if I was battling stuff with a lot of objects on the screen. 

Now I thought it might be an issue involving the lack of patches, but I also remembered that I installed the 32 bit version of wine before. So instead of compiling wine again (takes FOREVER), I installed the 32 bit version from the repos (and since D3 was already installed), it worked GREAT!

I tried setting the affenty to one/two cores on the 64 bit version and that did not help. I did not have to mess with anything on the 32 bit version of wine to get it to work well.

So why does D3 work well in the 32 bit version of wine, and not well in the 64 bit version?

---

