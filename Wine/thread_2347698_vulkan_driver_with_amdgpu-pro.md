---
title: "vulkan driver with amdgpu-pro"
date: 2016-12-27
forum: Wine
---

### Post by fredwntr1 on 2016-12-27
Hi all i recently got the new doom game running on linux through wine-staging and im tryng to launch the game using vulkan instead of OpenGL but i dont think i have the vulkan driver installed right and there doesnt seem to be any tutorials on how to use vulkan on linux does anyone know how to play games with vulkan on linux with amd cards?

---

### Post by QIII on 2016-12-27
Hello!

Which release of Ubuntu are you running and what model of GPU?

---

### Post by fredwntr1 on 2016-12-27
im using 16.04.1 and its the rx 470 with the amdgpu-pro driver

---

### Post by Yellow Pasque on 2016-12-28
Some commands that may help:
```
sudo apt-get install vulkan-utils
dpkg -l amdgpu-pro-vulkan-driver*
vulkaninfo | more
```

---

### Post by jonny-tightlips on 2016-12-29
Hey, I'm having a similar issue. Apparently, it's an issue when compiling the binary. This latest driver is only a few days old and a patch should be released soon enough.

---

### Post by howefield on 2016-12-29
Moved to the "*Wine*" forum.

---

### Post by fredwntr1 on 2016-12-29
Good to know thanks

---

