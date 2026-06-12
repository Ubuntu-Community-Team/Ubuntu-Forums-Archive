---
title: "g++ Problems"
date: 2005-11-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by KenF on 2005-11-12
I'm new to the forums.
My first linux install was Slackware ... with the 1.2.8 linux kernel, so I'm not new to linux.   I've also used plain Debian for a while ... so apt-get isn't new to me.

This is my first Ubuntu install (AMD64 Ubuntu 5.10).  My problem:  the g++ install seems to be missing some (not all) of the normal header files.  For example, a compile of a simple Hello World gives the following errors (I'm including a partial list ... the full list goes on for 89K.

Any ideas?

Thanks,

Ken

#include <iostream>
int main(int argc,char* argv[]) {
  std::cout << "Hello World!\n";
}

ken@newbox:~$ g++ testit.cc
In file included from /usr/include/c++/4.0.2/x86_64-linux-gnu/bits/c++config.h:35,
                 from /usr/include/c++/4.0.2/iostream:43,
                 from testit.cc:1:
/usr/include/c++/4.0.2/x86_64-linux-gnu/bits/os_defines.h:39:22: error: features.h: No such file or directory
In file included from /usr/include/c++/4.0.2/x86_64-linux-gnu/bits/c++locale.h:41,
                 from /usr/include/c++/4.0.2/iosfwd:45,
                 from /usr/include/c++/4.0.2/ios:43,
                 from /usr/include/c++/4.0.2/ostream:44,
                 from /usr/include/c++/4.0.2/iostream:44,
                 from testit.cc:1:
/usr/include/c++/4.0.2/cstring:51:20: error: string.h: No such file or directory
In file included from /usr/include/c++/4.0.2/x86_64-linux-gnu/bits/c++locale.h:42,
                 from /usr/include/c++/4.0.2/iosfwd:45,
                 from /usr/include/c++/4.0.2/ios:43,
                 from /usr/include/c++/4.0.2/ostream:44,
                 from /usr/include/c++/4.0.2/iostream:44,
<SNIP OUT REST OF 89K>

---

### Post by fabs0028 on 2005-11-12
Hello,
you need the developpement packages to compile it.
Just do it in a terminal with synaptict turned off :

sudo apt-get install libc6-dev libstdc++6-4.0-dev libstdc++6-dev

i think it would resvole the problem.
Maye a simpler solution would be to 

sudo apt-get install build-essential

Good luck

---

### Post by KenF on 2005-11-12
Thanks!
Installing build-essential did the trick.

Ken

---

