---
title: "VLC fixed the flicker, now I have a stutter?"
date: 2009-01-08
forum: x86 64-bit Users
---

### Post by Hjaltlander on 2009-01-08
Hi all,

I wonder if anyone can help me?

I have reinstalled Ubuntu 8.10, got rid of windows eventually.

When I installed VLC, originaly I had a terrible flicker, which I solved my selecting X11 output in the video properties.

Now it plays mostly well, except every now and then I get a stutter in the video, it will pause or jump ever so slightly, although the sound seems to carry on with no problem?

Anyone have any ideas?

If you need any more info just ask and I will try to help, but I am a n00b

Hjaltlander

---

### Post by martino2k8 on 2009-01-09
I'm assuming you have an ATI card, hence why the flicker problems. X11 isn't GPU accelerated like xv (-- in mplayer; or am I wrong) and hence why you get stutter problems since it can't keep up. A solution would be to turn off advanced desktop effects, so that'd be KWin or Compiz, when watching a video and setting the driver back to what you had before. This should hopefully fix the problem, even though it may not be a perfect solution.

---

### Post by Hjaltlander on 2009-01-09
Hi there, 

Thanks for your reply, I do have an ATI card, a 4850 to be precise. I had had no luck with Mplayer before, that is why I was using VLC (hang over from windows)

But today I have been looking at Mplayer again, and it seems to be running better then VLC so maybe I will just go with that.

Thanks again

---

### Post by CJ56 on 2009-01-09
I found something similar on my setup - having been a longtime fan of VLC - but now use Totem-xine. 

It's not quite as feature-friendly as VLC but it plays just as well and (to date) no stuttering...

---

### Post by Hjaltlander on 2009-01-09
Ok so I have decided to use Mplayer, so I have uninstalled VLC, and Mplayer works without stuttering, the problem I now have, is it appears not to want to play in full screen?

If I right click an .avi file, and select play with Mplayer, it opens up as a small window, and starts playing. If I hit the maximise window thing in the top right corner, it opens the window full screen, but the actual video stays the original size.

Any ideas?

---

### Post by CJ56 on 2009-01-09
Have you right-clicked on the screen as it's playing - ?

You should get a whole menu list of options, with, towards the bottom, resizing the screen, including fullscreen...

---

### Post by Hjaltlander on 2009-01-09
Yes, Just tried that, still the same, the window goes fullscreen, but the actual video image stays the original size, in the center.

Bit strange, well at least there is no flicker or stutter.

---

### Post by martino2k8 on 2009-01-09
I have a 4850 too, so my assumption was good.

As far as your MPlayer issue goes you have it most likely set on x11, which will not cause flickering but you will loose some hardware acceleration as well as the ability to resize. As I mentioned earlier, a good solution is to turn off desktop effects (Compiz or KWin, depending on which one you use) completely and set your video driver in MPlayer to xv (mplayer -vo xv).

Hopefully ATI will fix this issue in their drivers, as well as texture tearing.

---

