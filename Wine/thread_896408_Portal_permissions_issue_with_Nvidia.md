---
title: "Portal permissions issue with Nvidia"
date: 2008-08-21
forum: Wine
---

### Post by Paqman on 2008-08-21
I've just installed Portal and Steam through Wine. Steam runs fine, but Portal won't launch due to a permissions problem with /dev/nvidia0 and /dev/nvidiactl.

Those two files are owned by root and group 44. What confuses me is that there is no group 44 in my groups list, so I can't add my user to it. Portal launches fine if I chmod the file to give "others" read/write permission, but that's a hacky way to do it, and i'd rather not be setting files outside my home to such brad permissions.

Any ideas?

---

### Post by aoanla on 2008-08-21
I believe that nVidia drivers try to use something like the "video" group as the group for their device files.

However, your solution (to chmod things to globally rw ) is actually the most commonly recommended solution I've seen on the internet - for years, even (I remember it being recommended as a solution for the same kind of issues even as far back as the Geforce 4...).

---

### Post by kdorf on 2008-08-21
On my machine, group 44 is "video", which makes sense. You can create a group with that GID by running
```
sudo groupadd -g 44 video
```

Then add yourself to the video group.

---

### Post by Paqman on 2008-08-22
Haha, figured out that it was own mistake. I made a user called video a while back, and when I deleted the user account I must have deleted the GID 44 and left the GID 1003 group "video"

D'oh!

Nothing to see here, move along...

---

