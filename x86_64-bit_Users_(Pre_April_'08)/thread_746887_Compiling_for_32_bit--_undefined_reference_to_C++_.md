---
title: "Compiling for 32 bit-- undefined reference to C++ operators"
date: 2008-04-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by stair314 on 2008-04-06
I'm running 64 bit Ubuntu 7.10 with an Intel CPU. I'm trying to compile some code into a 32 bit binary, but I get all sorts of errors that look like I am missing some essential part of C++, ie, undefined reference to `operator new[](unsigned int)'

I followed the directions on this help page:
[https://help.ubuntu.com/community/InstallingCompilers#head-cfc6b98a82e8d1de090a662317d0a08da7d2b4c7](https://help.ubuntu.com/community/InstallingCompilers#head-cfc6b98a82e8d1de090a662317d0a08da7d2b4c7)

I have g++ version 4.1, so I installed g++-multilib as well as lib32stdc++6. I also installed all sorts of stuff not mentioned on that page, like ia32-libs. I still get the undefined references. Do I need to install something else, or do I need to edit my paths to expose the 32 bit libraries somehow?

Any help is greatly appreciated.

---

### Post by stair314 on 2008-04-06
Well, hey, fixed it myself. If anyone else runs into this problem, it turned out I had missed a -m32 on one of my object files so it was trying to link 32 bit and 64 bit object files.

---

