---
title: "Sound not workign and desktop flashing on WoW"
date: 2008-07-04
forum: Wine
---

### Post by FrankBro on 2008-07-04
I recently got Wow to work ( the graphic part lol ). Now my only problem is, there is absolutly no sound. I tryed everything at [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) such as adding 
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
to the wtf file and switching from ALSA to OSS with no result. I also tryed the method used in the guide there [https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting#No%20Sound%20or%20other%20unrelated%20issues](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting#No%20Sound%20or%20other%20unrelated%20issues) and there [http://wow4wine.wetpaint.com/page/Studdering+Sound%2FNo+sound?t=anon](http://wow4wine.wetpaint.com/page/Studdering+Sound%2FNo+sound?t=anon) with no result.
 Can anybody point me another guide or thing to check concerning sound plz ? 

Also, my ubuntu desktop keep flashing, at different place on the screen, i can see the desktop, but the game is running fine, i tried unchecking "Allow window manager to control the windows" and "Allow window manager to decorate the windows" and got it to work. I just wondered what those 2 options were doing and if they should stay unchecked ( can it cause crash, etc.) 

Thx a lot

---

### Post by FrankBro on 2008-07-04
Well got the desktop flashing thing to work yea but still no luck with sound, every sound work on ubuntu except on thing and i dont know if it might have a relation with it. I can't play any songs from my windows partition, keep saying i dont have the codecs, no luck with amarock either. However, i can listen videos on youtube, break, etc.
Would that show any sign of problem ?

---

### Post by FrankBro on 2008-07-04
After a couple test, got it to work so ill explain it for everyone. After looking around on the web, i found that ALSA isnt always installed on all linux distro ( wasnt on my ubuntu 8.04 ) so i just installed an app called GNOME alsa mixer in the add/rem progs thing. Now it works perfectly, i hope ill be able to help ppl. :)

---

