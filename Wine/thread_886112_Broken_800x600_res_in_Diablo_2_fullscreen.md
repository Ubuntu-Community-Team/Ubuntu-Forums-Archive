---
title: "Broken 800x600 res in Diablo 2 fullscreen"
date: 2008-08-10
forum: Wine
---

### Post by Vaphell on 2008-08-10
i copied my win D2 installation and it pretty much works BUT...
running it in fullscreen produces this odd resolution where picture is stretched up vertically causing bottom of the picture below screen edge. Approximately 1/6th of the game screen is out of sight, health/mana orbs, belt etc.
I have gf6200, direct rendering, compiz and whatnot work.
My monitor: sm730bf LCD, native resolution 1280x1024 (aspect ratio 5:4)

I tried once to tweak my xorg.conf. Currently the are no resolutions listed (xorg autodetection works apparently) so i added some modelines for 640x480, 800x600 and 1280x1024. They had to be bad, because xserver crashed and after i had only 640x480 and 800x600 resolutions (vesa mode?) - ubuntu got almost unusable with ridiculuously big fonts. But that's not the point... Out of curiosity i ran d2 and this time fullscreen was perfect.
Do nvidia drivers use some bad parameters in 800x600 fullscreen required by d2? If so, is there any way to give proper ones?

---

