---
title: "cout and printf not defined??"
date: 2009-10-29
forum: x86 64-bit Users
---

### Post by DPCarbone on 2009-10-29
I've nearly successfully setup 9.10 on my 3,1 MBP and thus far everything has worked EXCEPT g++.  I am a CS major and am in a class which uses a little robot called the Scribbler.  The instructors have created their own unique set of libraries and etc for use with the Scribbler, and under 9.04 i was able to compile the code necessary to get it to work.  however, since the move to 9.10 everytime i try to compile i get errors stating that both printf and cout are undefined, along with stderr and cerr, etc.  the lot.  I have NO idea what could be causing this, all of the files have #include <iostream> and are using namespace std, which has pretty much exhausted my debug knowledge on this issue.

Any help would be greatly appreciated.

---

### Post by wirate on 2009-10-30
i dont know much but give this a try

#include <stdio.h>

---

### Post by ahmdsamir on 2009-10-30
I have the same problem with printf, what's going on ?

```
home/ahmed/develop/trunk/Base/extern/mitk/src/Core/IGT/IGTTrackingDevices/mitkClaronInterfaceStub.cpp:25: error: ‘printf’ was not declared in this scope
/home/ahmed/develop/trunk/Base/extern/mitk/src/Core/IGT/IGTTrackingDevices/mitkClaronInterfaceStub.cpp: In member function ‘void mitk::ClaronInterface::Initialize(std::string, std::string)’:

```

---

