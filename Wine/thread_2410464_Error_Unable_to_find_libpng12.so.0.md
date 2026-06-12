---
title: "Error: Unable to find libpng12.so.0"
date: 2019-01-15
forum: Wine
---

### Post by iridi on 2019-01-15
I'm trying to install [Paint Tool SAI ver.2 ]("https://www.systemax.jp/en/sai/devdept.html")(64-bit) and it spits out a ton of errors. One in particular I also got when trying to install something unrelated so I want to try to figure it out before troubleshooting the rest. Here:
```
000d:err:wincodecs:PngEncoder_CreateInstance Failed writing PNG because unable to find libpng12.so.0
```
I followed the instructions [given here]("https://ubuntu-mate.community/t/wine-on-18-04-unable-to-find-libpng12-so-0/17967") and installed libpng12 & did ```
sudo ln -s /lib/i386-linux-gnu/libpng12.so.0  /usr/lib/libpng12.so.0
sudo ln -s /lib/x86_64-linux-gnu/libpng12.so.0  /usr/lib64/libpng12.so.0
``` which resulted in these 2 errors:
```
ln: failed to create symbolic link '/usr/lib/libpng12.so.0': File exists
ln: failed to create symbolic link '/usr/lib64/libpng12.so.0': No such file or directory
```

Ultimately it didn't fix the original error. Can someone help me figure out what these errors mean and what I need to do instead?

**Ubuntu 18.04.1 LTS & Wine 4.0-rc5**

---

