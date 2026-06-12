---
title: "Karmic inverting video color"
date: 2009-11-07
forum: x86 64-bit Users
---

### Post by a2z on 2009-11-07
Good day everyone,

I have several disks where I burned avi and wmv videos from my windows machine.
They all worked great until now. I find somehow the colors are being inverted. 
I originally thought it was a bad burn. But when I checked other disks it turns out the same. I assume this might be a bug. But not sure. 
I know all the videos worked good from intrepid to jaunty and my previously (brief) experience with karmic bata before I did a clean install of jaunty again.

After giving karmic some time to have the bugs worked out, I did the upgrade to karmic via update manager. 
Can anyone suggest a remedy?

Thanks to all,

a2z

---

### Post by a2z on 2009-11-09
I first noticed a video problem while trying to load my avi and wmv files into Cinelerra. Cinelerra would show the file in the media folder but wouldn't do anything else with the file.
I also checked my dvd disks again on windows without a problem. 
And I also was able to load an avi I made with blender from my hard drive into cinelerra. And it functioned normally.
I coppied the files from cdrom to hd. Perhaps karmic is having trouble reading from there. It is lightscribe cdrom.
As I stated before, I have not had trouble with earlier versions ubuntu. And no "cdrom"- video trouble with karmic beta.
I hope this helps iron out this problem if it's with karmic..

Thanks again,

a2z

---

### Post by arvana on 2009-11-12
Try this:

```
xvattr -a XV_HUE -v 0
```

---

### Post by epicflux on 2009-11-16
adjust hue in totem: [http://ubuntuforums.org/showthread.php?t=1312298](http://ubuntuforums.org/showthread.php?t=1312298)

---

