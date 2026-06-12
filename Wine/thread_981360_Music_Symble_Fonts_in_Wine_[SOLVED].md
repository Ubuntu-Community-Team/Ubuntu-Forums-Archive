---
title: "Music Symble Fonts in Wine [SOLVED]"
date: 2008-11-13
forum: Wine
---

### Post by t1m on 2008-11-13
This post is a solution to a problem I recently solved, I hope it's helpful.

I had a problem when running Wine programs--some of the fonts would be music symbols. I had puzzled about it for quite some time, but recently I was forced to fix it so that I could use a program. I couldn't see any musical fonts in my .fonts directory (~/.fonts; for newbies: ~ is shorthand for the /home/<**yourusername**> folder). Then I looked in the Wine fonts dir (~/.wine/drive_c/windows/Fonts), and found them.

The solution? I just closed the program I was trying to use, installed msttcorefonts, and voila! Piece of cake. (You can install msttcorefonts via Synaptic or apt-get or whatever.)

Hooray! :popcorn:

Note: You may be able to just delete the music symble fonts in ~/wine/drive_c/windows/Fonts, I haven't tried that, though.

---

