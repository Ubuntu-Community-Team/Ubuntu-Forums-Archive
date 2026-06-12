---
title: "native shared library crashes if C++ exceptions are used on Ubuntu Wine build"
date: 2020-05-22
forum: Wine
---

### Post by markok3-14 on 2020-05-22
This problem appears only on Ubuntu 20.04 with Wine 5.0 installed from Ubuntu repository. If I build Wine 5.0 myself or install Wine 4.0.4 from Wine repository, then there is no problem, so I assume the problem is in Ubuntu 20.04 build of Wine.

I have written a shared library for our application using Winelib project, which calls native Linux API. C++ is used. Crash happens on first C++ exception thrown.
App which shows the problem:

```
         
#include <stdexcept>
#include <stdio.h>

int main() {
    printf("start\n");
    try {
        throw std::runtime_error("desc");
    } catch (std::exception &ex) {
        printf("in catch\n");
    }
    printf("end\n");
}

```
built with:
       ```

    g++ -c -fPIC t.cpp
    /home/mkk/wine-git_64/tools/winegcc/wineg++ -B/home/mkk/wine-git_64/tools/winebuild -o tt t.o

```
run as:
```

   wine tt.exe.so

```
Prints 'start', then crashes.
Any idea how to solve this problem?

---

### Post by mastablasta on 2020-05-22
if this issues is only present on Ubuntu repo build, it is clearly ubuntu packaging issue of sorts. i would report it on launchpad.

---

