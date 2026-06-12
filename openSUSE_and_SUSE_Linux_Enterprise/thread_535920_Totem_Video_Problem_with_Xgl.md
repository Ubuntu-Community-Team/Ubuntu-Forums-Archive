---
title: "Totem Video Problem with Xgl"
date: 2007-08-27
forum: openSUSE and SUSE Linux Enterprise
---

### Post by theonlyrealperson on 2007-08-27
I have a weird problem - only because usually it's the opposite.

I have an IBM T42p laptop with the horrid ATI Radeon 7500 card. Beryl and Compiz run ok, as long as they aren't running with too much else. 

On OpenSuse though, I can't watch videos in Totem without "Desktop Effects" being ON! It results in a major slow-down of the video makes it very choppy.

When I turn the Desktop effects off, All I get is sound and a black screen. The screen isn't totally black - you can tell the difference between the widescreen bars and the video area - but black all the same.

I've reinstalled Totem and its codecs, but to no avail. Anyone have an idea? :confused:

---

### Post by theonlyrealperson on 2007-08-28
I downloaded MPlayer and SMplayer and noticed that the video output was "xv" instead of x11. I changed it to "x11" and the video works just fine now with xgl on. 

Anyone happen to know how to change it in Totem? I can't figure it out.

---

### Post by NiceGuy on 2007-09-11
If you are using the gstreamer backend then press alt+F2 and type

```
gstreamer-properties
```

Go to the video tab and change it to X Window System (No Xv)

If you are using the xine backend the version of totem-xine which ships with gutsy (I haven't tried other versions) has it's own config file, xine_config, which you need to edit. This can be found in the .gnome2/Totem/ in your home folder.

Just find where it says:
```

# video driver to use
# string, default: auto
#video.driver:auto

```

and change it to:
```

# video driver to use
# string, default: auto
video.driver:xshm

```

---

### Post by theonlyrealperson on 2007-09-11
Worked like a charm.

Thank you very much, kind sir.

---

### Post by Maybelline on 2007-12-17
> **NiceGuy said:**
> change it to:
```

# video driver to use
# string, default: auto
video.driver:xshm

```

Thanks a million.  Works like a champ for me.

---

