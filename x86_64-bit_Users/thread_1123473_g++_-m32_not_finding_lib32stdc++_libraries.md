---
title: "g++ -m32 not finding lib32stdc++ libraries?"
date: 2009-04-12
forum: x86 64-bit Users
---

### Post by akos.maroy on 2009-04-12
I'm trying to do 32-bit C++ development on a 64 bit box, but the linker does not seem to find the std C++ libraries, even though I have lib32stdc++ installed:

```
$ g++ -m32 -o hello hello.cpp 
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libstdc++.a when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status

```

the source code is simple:

```
$ cat hello.cpp 
#include <iostream>

int main(int argc, char **argv) {
    std::cout << "Hello, World!" << std::endl;

    return 0;
}

```

and I do have lib32stdc++6 installed:

```
$ dpkg -L lib32stdc++6
/.
/usr
/usr/share
/usr/share/doc
/usr/lib32
/usr/lib32/libstdc++.so.6.0.10
/usr/share/doc/lib32stdc++6
/usr/lib32/libstdc++.so.6

```

what am I doing wrong?

---

### Post by Slim Odds on 2009-04-12
> **akos.maroy said:**
> I'm trying to do 32-bit C++ development on a 64 bit box, but the linker does not seem to find the std C++ libraries, even though I have lib32stdc++ installed:

```
$ g++ -m32 -o hello hello.cpp 
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/[COLOR=Red]libstdc++.so[/COLOR] when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libstdc++.a when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status
and I do have lib32stdc++6 installed:

[code]$ dpkg -L lib32stdc++6
/.
/usr
/usr/share
/usr/share/doc
/usr/lib32
/usr/lib32/libstdc++.so.6.0.10
/usr/share/doc/lib32stdc++6
/usr/lib32/libstdc++.so.6

```what am I doing wrong?

It appears that the package is missing a symbolic link for the libstdc++.so that the linker is looking for.

Try this:```
ln -s /usr/lib32/libstdc++.so.6 /usr/lib32/libstdc++.so
```

---

### Post by akos.maroy on 2009-04-13
> **Slim Odds said:**
> It appears that the package is missing a symbolic link for the libstdc++.so that the linker is looking for.

Try this:```
ln -s /usr/lib32/libstdc++.so.6 /usr/lib32/libstdc++.so
```

thanks - this makes it work. but shouldn't I file a bug report because of this? where would I do that?

---

### Post by Yellow Pasque on 2009-04-15
> **akos.maroy said:**
> thanks - this makes it work. but shouldn't I file a bug report because of this? where would I do that?
You may have already figured this out by now, but the link you were missing is part of the g++-multilib package. You should install this package if you haven't already (it's essential if you're using -m32 with g++).
```
sudo apt-get install g++-multilib
```
Hopefully, you didnt file a bug report (on launchpad.com for future reference).

---

### Post by akos.maroy on 2009-04-15
> **Temüjin said:**
> You may have already figured this out by now, but the link you were missing is part of the g++-multilib package. You should install this package if you haven't already (it's essential if you're using -m32 with g++).
```
sudo apt-get install g++-multilib
```
Hopefully, you didnt file a bug report (on launchpad.com for future reference).

I installed g++-multilib of course, before anything else - and my symlink wasn't there.

I guess this qualifies as a proper bug then...

---

