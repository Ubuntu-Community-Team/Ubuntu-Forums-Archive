---
title: "[SOLVED] Help! My audio stopped working!"
date: 2008-12-25
forum: x86 64-bit Users
---

### Post by Laysan_A on 2008-12-25
Hi, I'm using Intrepid (see my general specs. below).

I had everything basically set-up okay, then my audio suddenly stopped working and I haven't a clue what to do...I am very new to linux.

I had been playing an mp3 in amarok for some hours. I shut amarok down then tried to watch a video with mplayer and received a message that it couldn't open/initialize audio device. There is no sound in games either. The sound works fine in windows.

Yesterday I followed some instructions about adding repositories and unsupported backports from this guide [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) I also installed a few of the programs he recommended. 

I don't know if any of this is relevent. The sound stopped working hours later.

I just updated the MB bios - didn't seem to help.

Thanks! :)


Well!
All fixed!

I opened prboom and noticed that I could barely hear the sound of slamming doors...hmmm. I closed it and opened my video file again - same result. I went down the list again of my video players and opened it in totem. If I listened carefully I could hear a few sounds. I opened the mixer and started playing with the sliders and voila, normal sound! The operation of the sliders had changed from how it was originally. I went back to mplayer and looked at the sound driver selection again. It was using pulse, but there was a selection for alsa, and I thought, well I'll just try it, and voila again, sound. Amarok works again, too. :) :)

---

