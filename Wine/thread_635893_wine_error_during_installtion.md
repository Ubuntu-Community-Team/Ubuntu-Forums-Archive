---
title: "wine error during installtion"
date: 2007-12-09
forum: Wine
---

### Post by kouya77 on 2007-12-09
Hi all,
Met some problems when trying to install WC3. Here's the code

user@PC00:~/Desktop/Warcraft_III$ ls
autoplay.exe  install.exe  setup.mpq  War3.ico
autorun.inf   movies       support    War3.mpq
directx       Razor1911    trailers   Warcraft III Manual.pdf
user@PC00:~/Desktop/Warcraft_III$ wine install.exe
[B]Warning: could not find DOS drive for current working directory '/home/user/Desktop/Warcraft_III', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\install.exe": Module not found[/B]

Can someone enlighten me on what this means? Help will be greatly appreciated. Thanks!

---

### Post by cogadh on 2007-12-09
It means that Wine was expecting a CD drive or something associated with the directory you are running the install from in Wine's drive configuration, but didn't find one. Is there a particular reason you are not running the install off of the CD?

---

