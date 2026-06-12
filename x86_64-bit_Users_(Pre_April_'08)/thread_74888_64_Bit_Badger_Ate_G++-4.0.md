---
title: "64 Bit Badger Ate G++-4.0"
date: 2005-10-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by andellmoon on 2005-10-12
Hi. I have the preview install of the 64 bit badger. I did a bunch of updates earlier. Now, when I want to code, g++-4.0.2 gives me crazy errors. Below is the beginning. My Proj2.cpp is my project and line 11 is "#include <iostream>".

> In file included from /usr/include/c++/4.0.2/x86_64-linux-gnu/bits/c++config.h:35,
                 from /usr/include/c++/4.0.2/iostream:43,
                 from Proj2.cpp:11:
/usr/include/c++/4.0.2/x86_64-linux-gnu/bits/os_defines.h:39:22: error: features.h: No such file or directory
In file included from /usr/include/c++/4.0.2/x86_64-linux-gnu/bits/c++locale.h:41,
                 from /usr/include/c++/4.0.2/iosfwd:45,
                 from /usr/include/c++/4.0.2/ios:43,
                 from /usr/include/c++/4.0.2/ostream:44,
                 from /usr/include/c++/4.0.2/iostream:44,
                 from Proj2.cpp:11:
/usr/include/c++/4.0.2/cstring:51:20: error: string.h: No such file or directory
In file included from /usr/include/c++/4.0.2/x86_64-linux-gnu/bits/c++locale.h:42,
                 from /usr/include/c++/4.0.2/iosfwd:45,
                 from /usr/include/c++/4.0.2/ios:43,
                 from /usr/include/c++/4.0.2/ostream:44,
                 from /usr/include/c++/4.0.2/iostream:44,


Edit: I think I broke the badger. Nevermind... I need to fix a bunch of stuff O.o
Update: Okay! Badger is okay now. But g++ is still giving me those errors. Help, please.

---

