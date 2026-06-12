---
title: "Cannot Compile 32-bit hello.cc program on 64-bit Edgy"
date: 2006-11-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by UrbanFallout on 2006-11-15
Hello

I am unable to compile a simple hello world program using the 32-bit option in gcc.

Some research turned up [this thread]("http://ubuntuforums.org/showthread.php?t=286175") - to no avail. 

Here is the code for **hello.cc** that I'm trying to compile:
```
#include <iostream>
using namespace std;

int main( int argc, char* argv[] )
{
  cout <<"Hello"<<endl;
}
```

At the command line I call gcc with the 32-bit switch:

```
gcc -m32 hello.cc
```

This returns the following error:
> In file included from /usr/include/features.h:346,
                 from /usr/include/c++/3.3/x86_64-linux-gnu/bits/os_defines.h:39,
                 from /usr/include/c++/3.3/x86_64-linux-gnu/bits/c++config.h:35,
                 from /usr/include/c++/3.3/iostream:44,
                 from hello.cc:1:
/usr/include/gnu/stubs.h:7:27: gnu/stubs-32.h: No such file or directory


I have installed the following libraries / packages - but I have had no luck so far:
[LIST]
[*]a32-libs (version 1.5ubuntu5) will be installed
[*]lib32stdc++6 (version 4.1.1-13ubuntu5) will be installed
[*]libc6-dev-i386 (version 2.4-1ubuntu12) will be installed
[*]lib32ncurses
[*]g++-3.3
[/LIST]

Using g++-3.3 did not solve the problem either - although I seem to remember it solving this problem in Breezy.

Any suggestions?

Many thanks in advance
Nick

---

### Post by RFScheer on 2006-11-15
On my setup, stubs-32.h is found at:

/usr/include/i486-linux-gnu/gnu/stubs-32.h

Looks like you need to direct gcc to that dir.

---

### Post by RAOF on 2006-11-15
Do you have ia32-libs-dev installed?  Also, it's entirely possible that the 32bit libs will only be available for gcc4, since that's Edgy's default gcc.

---

### Post by UrbanFallout on 2006-11-16
Thank you for the two replies - I'll take them one at a time:

1. stubs-32.h - Yes this is indeed in the /usr/include/i486-linux-gnu/gnu/ directory. I could point the compiler too it with a -I directive, but this should be automatically dealt with! 

2. ia32-libs-dev - This is not listed in Synaptic, only ia32-lib and a few variants for java, kde, etc. Are you sure you didn;t just mean ia32-libs??

Incidentally the first suggestion results in the following error when I call:
gcc -m32 hello.cc -I /usr/include/i486-linux-gnu/

> 
/tmp/ccPAChvg.o: In function `__static_initialization_and_destruction_0(int, int)':
hello.cc:(.text+0x23): undefined reference to `std::ios_base::Init::Init()'
/tmp/ccPAChvg.o: In function `__tcf_0':
hello.cc:(.text+0x6c): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccPAChvg.o: In function `main':
hello.cc:(.text+0x8e): undefined reference to `std::cout'
hello.cc:(.text+0x93): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
hello.cc:(.text+0x9b): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
hello.cc:(.text+0xa3): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/ccPAChvg.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status


This seems to imply that the wrong (64-bit) libraries are being linked.  

Any other suggestions - apart from the obvious one of installing a chroot environment?

Thanks again

---

### Post by RAOF on 2006-11-16
> **UrbanFallout said:**
> ...
This seems to imply that the wrong (64-bit) libraries are being linked.  

Any other suggestions - apart from the obvious one of installing a chroot environment?

Thanks again

Actually, no.  That implies that **no** libraries are being linked.  You might want to try a -lstdc++ :)

---

### Post by UrbanFallout on 2006-11-17
Great thanks for pointing that out.

I now have a hello world that compiles using:

gcc -m32 hello.cc -I/usr/include/i486-linux-gnu/ -lstdc++ -ohello

Quick question though:

Surely I shouldn't need to explicitly link in the 32-bit libraries...
Is something I must just live with?

Thanks again.

---

### Post by RAOF on 2006-11-17
You will need to explicitly link in libstdc++ - you'd need to do that for a 64bit program, too.

As far as I know, you shouldn't have to explicitly add /usr/include/i486-linux-gnu to your includes directories.  I'm not sure why you do :(

---

### Post by UrbanFallout on 2006-11-19
Hmm... 

It appears the requirement for the "-I /usr/include/i486-linux-gnu/" parameter has disappeared.

I guess I needed a restart of xterminal after installing one of these packages:
# a32-libs (version 1.5ubuntu5) 
# lib32stdc++6 (version 4.1.1-13ubuntu5) 
# libc6-dev-i386 (version 2.4-1ubuntu12) 

This was probably to update some environment variable. I'm sure which package instigated this.

Apologies for getting this wrong. Hopefully this doesn't confuse anyone.

---

