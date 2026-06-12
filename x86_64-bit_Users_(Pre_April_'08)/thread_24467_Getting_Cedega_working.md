---
title: "Getting Cedega working?"
date: 2005-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by WMCoolmon on 2005-04-07
I've been trying to get Cedega working on my AMD64 with the linuxgamers script, however, it gives me this:
> Compiling ...




--------- Error log - file /home/steven/.WineCVS/sources/cvscedega/ErrorLog : ---------
make[1]: Entering directory `/home/steven/.WineCVS/sources/cvscedega/winex/unicode'
gcc -MMD -c  -I. -I. -I../include -I../include  -g -O2 -Wall -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -fPIC -D__WINE__ -D_REENTRANT -I/usr/X11R6/include -o casemap.o casemap.c
In file included from ../include/winnt.h:10,
                 from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from casemap.c:4:
../include/basetsd.h:148:3: #error Unknown CPU architecture!
In file included from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from casemap.c:4:
../include/winnt.h:1030:2: #error You need to define a CONTEXT for your CPU
In file included from ../include/windef.h:16,
                 from ../include/wine/unicode.h:10,
                 from casemap.c:4:
../include/winnt.h:1033: error: syntax error before '*' token
../include/winnt.h:1033: warning: type defaults to `int' in declaration of `PCONTEXT'
../include/winnt.h:1033: warning: data definition has no type or storage class
../include/winnt.h:2068: error: syntax error before "PCONTEXT"
../include/winnt.h:2068: warning: no semicolon at end of struct or union
../include/winnt.h:2069: warning: type defaults to `int' in declaration of `EXCEPTION_POINTERS'
../include/winnt.h:2069: warning: type defaults to `int' in declaration of `PEXCEPTION_POINTERS'
../include/winnt.h:2069: warning: data definition has no type or storage class
../include/winnt.h:2081: error: syntax error before "PCONTEXT"
../include/winnt.h:2093: error: syntax error before "ExceptionInfo"
../include/winnt.h:2096: error: syntax error before "epointers"
In file included from ../include/winnls.h:5,
                 from ../include/wine/unicode.h:11,
                 from casemap.c:4:
../include/winbase.h:121: error: syntax error before "LPCONTEXT"
../include/winbase.h:121: warning: type defaults to `int' in declaration of `LPCONTEXT'
../include/winbase.h:121: warning: data definition has no type or storage class
../include/winbase.h:123: error: syntax error before "LPEXCEPTION_POINTERS"
../include/winbase.h:123: warning: type defaults to `int' in declaration of `LPEXCEPTION_POINTERS'
../include/winbase.h:123: warning: data definition has no type or storage class
../include/winbase.h:1362: error: syntax error before "CONTEXT"
../include/winbase.h:1499: warning: type defaults to `int' in declaration of `CONTEXT'
../include/winbase.h:1499: error: syntax error before '*' token
make[1]: *** [casemap.o] Error 1
make[1]: Leaving directory `/home/steven/.WineCVS/sources/cvscedega/winex/unicode'
make: *** [unicode/libwine_unicode.so] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


Is there some way to work around this?

---

