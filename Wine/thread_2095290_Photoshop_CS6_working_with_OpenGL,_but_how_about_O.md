---
title: "Photoshop CS6 working with OpenGL, but how about OpenCL?"
date: 2012-12-16
forum: Wine
---

### Post by nainainai on 2012-12-16
I'm using Adobe Photoshop CS6 on 12.10 nicely but with two problems:

1) The lasso and similar tools fail to start the selection several times, like the focus was not on the PS window. Is this fixable?

2) I was able to enable OpenGL by adding this DWORD on regedit:
```
[HKEY_CURRENT_USER\Software\Adobe\Photoshop\CS60.0]
"AllowOldGPUS"=dword:00000001
```

any idea on how I can enable OpenCL too? 
I tried to load all the libs but none works:
```
LD_PRELOAD="libGL.so.1 libOpenCL.so.1 libOpenCL.so libOpenCL.so.1.0 libOpenCL.so.1.0.0" env ......
```

3) this is not a problem but a question, can I enable copy, paste, drag and drop to both ends? right now if I copy a image on firefox I can't paste it on PS

Thanks

---

### Post by nainainai on 2012-12-20
nothing? :rolleyes:

---

