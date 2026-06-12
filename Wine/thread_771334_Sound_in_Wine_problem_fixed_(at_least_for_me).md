---
title: "Sound in Wine problem fixed (at least for me)"
date: 2008-04-27
forum: Wine
---

### Post by papabean on 2008-04-27
Just in case this can help someone else:

After upgrading to Hardy, I no longer had sound in Wine.  I tried a couple of the suggestions I had found on the forums:  using *padsp* to use the OSS sound option in winecfg and selecting ESound since PulseAudio is supposed to be a drop-in replacement for ESound.  Neither of these worked.

Something I had noticed when I launched *winecfg* that I hadn't seen before were errors about the fake windows directory not being acessible.  Strange since Wine worked fine before.  This led me to believe that something strange had happened to my Wine configuration.

I backed up ~/.wine/drive_c to another location and removed the .wine folder.  When I ran *winecfg* this time, the .wine directory was recreated, no errors were reported and I was able to select either the ALSA or ESound drivers in the Audio configuration and hear the test sound.

So, if you're having problems with sound in Wine after upgrading to Hardy, it might be a stale Wine configuration.

---

### Post by cogadh on 2008-04-27
You might want to try running "wineprefixcreate" after you upgrade Wine. That will re-register any customizations you have made to your Wine directory and may prevent the problem you encountered.

---

### Post by papabean on 2008-04-27
Thank you very much for this tip.  I'll try that in the future before nuking my preferences should I encounter any oddness with Wine.

---

