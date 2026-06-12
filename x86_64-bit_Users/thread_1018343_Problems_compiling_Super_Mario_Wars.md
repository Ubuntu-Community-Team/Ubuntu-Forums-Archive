---
title: "Problems compiling Super Mario Wars"
date: 2008-12-22
forum: x86 64-bit Users
---

### Post by go_beep_yourself on 2008-12-22
I get these errors when running make. Can anyone compile this?
[http://www.fileden.com/files/2007/9/11/1425938/smw-1.7-src.zip](http://www.fileden.com/files/2007/9/11/1425938/smw-1.7-src.zip)
I had to run chmod +x configure and dos2unix configure to get it to run.

[PHP]_src/global.cpp:258: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:258: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:258: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:258: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:258: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:258: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:258: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:258: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:258: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:258: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:262: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:262: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:262: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:262: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:262: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:262: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:262: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:262: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:262: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:262: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:262: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:265: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:265: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:265: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:265: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:265: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:265: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:265: warning: deprecated conversion from string constant to ‘char*’
_src/global.cpp:265: warning: deprecated conversion from string constant to ‘char*’
g++  -DLINUXFUNC -DPREFIXPATH=\"/usr/share/smw\" -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -Wall -I. -DPNG_SAVE_FORMAT -o build/map.o -c _src/map.cpp
g++  -DLINUXFUNC -DPREFIXPATH=\"/usr/share/smw\" -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -Wall -I. -DPNG_SAVE_FORMAT -o build/movingplatform.o -c _src/movingplatform.cpp
_src/MapList.cpp: In member function ‘void MapList::WriteMapSummaryCache()’:
_src/MapList.cpp:467: warning: format not a string literal and no format arguments
g++  -DLINUXFUNC -DPREFIXPATH=\"/usr/share/smw\" -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -Wall -I. -DPNG_SAVE_FORMAT -o build/path.o -c _src/path.cpp
_src/movingplatform.cpp: In member function ‘void MovingPlatform::collide(CPlayer*)’:
_src/movingplatform.cpp:809: warning: suggest parentheses around && within ||
_src/movingplatform.cpp: In member function ‘void MovingPlatform::collide(IO_MovingObject*)’:
_src/movingplatform.cpp:1195: warning: suggest parentheses around && within ||
_src/path.cpp: In function ‘const std::string convertPath(const std::string&)’:
_src/path.cpp:81: error: ‘strcpy’ was not declared in this scope
_src/path.cpp:89: error: ‘strcat’ was not declared in this scope
make: *** [build/path.o] Error 1
make: *** Waiting for unfinished jobs....[/PHP]

---

