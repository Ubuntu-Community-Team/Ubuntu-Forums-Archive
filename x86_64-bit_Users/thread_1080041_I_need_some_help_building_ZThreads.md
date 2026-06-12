---
title: "I need some help building ZThreads"
date: 2009-02-25
forum: x86 64-bit Users
---

### Post by fontenot_1031 on 2009-02-25
Hi, I'm trying to build the ZThreads library. I've already made one change to the source to allow one of the files to be built but I'm getting similar errors on other files when I try to build it. For example this is the current error I'm getting:
```
MutexImpl.h: In member function 'void ZThread::MutexImpl<List, Behavior>::acquire()':
MutexImpl.h:156: error: there are no arguments to 'ownerAcquired' that depend on a template parameter, so a declaration of 'ownerAcquired' must be available
MutexImpl.h:156: error: (if you use '-fpermissive', G++ will accept your code, but allowing the use of an undeclared name is deprecated)
MutexImpl.h:167: error: there are no arguments to 'waiterArrived' that depend on a template parameter, so a declaration of 'waiterArrived' must be available
MutexImpl.h:176: error: there are no arguments to 'waiterDeparted' that depend on a template parameter, so a declaration of 'waiterDeparted' must be available
MutexImpl.h:195: error: there are no arguments to 'ownerAcquired' that depend on a template parameter, so a declaration of 'ownerAcquired' must be available
MutexImpl.h: In member function 'bool ZThread::MutexImpl<List, Behavior>::tryAcquire(long unsigned int)':
MutexImpl.h:239: error: there are no arguments to 'ownerAcquired' that depend on a template parameter, so a declaration of 'ownerAcquired' must be available
MutexImpl.h:256: error: there are no arguments to 'waiterArrived' that depend on a template parameter, so a declaration of 'waiterArrived' must be available
MutexImpl.h:265: error: there are no arguments to 'waiterDeparted' that depend on a template parameter, so a declaration of 'waiterDeparted' must be available
MutexImpl.h:287: error: there are no arguments to 'ownerAcquired' that depend on a template parameter, so a declaration of 'ownerAcquired' must be available
MutexImpl.h: In member function 'void ZThread::MutexImpl<List, Behavior>::release()':
MutexImpl.h:329: error: there are no arguments to 'ownerReleased' that depend on a template parameter, so a declaration of 'ownerReleased' must be available
make[3]: *** [Mutex.lo] Error 1
make[3]: Leaving directory `/home/david/Desktop/ZThread-2.3.2/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/david/Desktop/ZThread-2.3.2/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/david/Desktop/ZThread-2.3.2/src'
make: *** [all-recursive] Error 1

```

The error I mentioned before in Guard.h was similar to these (in asking for g++ to use -fpermissive). If the -fpermissive thing might be the case does anyone know how I could tell make to build with that parameter?

---

