---
title: "running 32 bits applications on 64 bits (Drapper Drake) - problem with libgtk-1.2.so"
date: 2006-07-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by jplepc2006 on 2006-07-02
Hello,

I am trying to run a 32 bits application (xstata-se ) on an Ubuntu 6.06 distro
(amd64), and I keep getting the error message below.

root@home-desktop64:/home/jazevedo# /usr/local/stata9/xstata-se
/usr/local/stata9/xstata-se: error while loading shared libraries:
libgtk-1.2.so .0: cannot open shared object file: No such file or
directory
root@home-desktop64:/home/jazevedo#

Please note that this application comes both with and without a GUI. The non-GUI version of it (stata-se) runs perfectly well.

I've also ran strace, the output lies below. Any help will be much appreciated.

Cheers,

JP




jazevedo@home-desktop64:~$ strace /usr/local/stata9/xstata
execve("/usr/local/stata9/xstata", ["/usr/local/stata9/xstata"], [/*
31 vars */] ) = 0
[ Process PID=23977 runs in 32 bit mode. ]
uname({sys="Linux", node="home-desktop64", ...}) = 0
brk(0)                                  = 0x85a0000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1,
0) = 0x55 56c000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(0x3, 0xffffca0c)                = 0
mmap2(NULL, 53809, PROT_READ, MAP_PRIVATE, 3, 0) = 0x5556e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib32/tls/i686/sse2/cmov/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No such  file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/tls/i686/sse2/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file  or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/tls/i686/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file  or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/tls/i686/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such
file or d irectory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/tls/sse2/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file  or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/tls/sse2/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such
file or d irectory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/tls/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such
file or d irectory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/tls/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such file
or direct ory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/i686/sse2/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT
(No such fil e or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/i686/sse2/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/i686/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/i686/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such
file or direc tory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/sse2/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/sse2/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such
file or direc tory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such
file or direc tory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = 0
open("/usr/lib32/tls/i686/sse2/cmov/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/tls/i686/sse2/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT
(No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/tls/i686/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT
(No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/tls/i686/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/tls/sse2/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT
(No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/tls/sse2/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/tls/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/tls/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such
file or di rectory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/i686/sse2/cmov/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No such  file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/i686/sse2/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file  or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/i686/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file  or directory)
stat64(0xffffca20, 0xffffcaa4)          = 0
open("/usr/lib32/i686/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such
file or d irectory)
stat64(0xffffca20, 0xffffcaa4)          = 0
open("/usr/lib32/sse2/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file  or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/sse2/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such
file or d irectory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such
file or d irectory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such file
or direct ory)
stat64(0xffffca20, 0xffffcaa4)          = 0
open("/usr/lib/x86_64-linux-gnu/tls/i686/sse2/cmov/libgtk-1.2.so.0",
O_RDONLY) =  -1 ENOENT (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/tls/i686/sse2/libgtk-1.2.so.0",
O_RDONLY) = -1 E NOENT (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/tls/i686/cmov/libgtk-1.2.so.0",
O_RDONLY) = -1 E NOENT (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/tls/i686/libgtk-1.2.so.0", O_RDONLY) =
-1 ENOENT  (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/tls/sse2/cmov/libgtk-1.2.so.0",
O_RDONLY) = -1 E NOENT (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/tls/sse2/libgtk-1.2.so.0", O_RDONLY) =
-1 ENOENT  (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/tls/cmov/libgtk-1.2.so.0", O_RDONLY) =
-1 ENOENT  (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/tls/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/i686/sse2/cmov/libgtk-1.2.so.0",
O_RDONLY) = -1 ENOENT (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/i686/sse2/libgtk-1.2.so.0", O_RDONLY)
= -1 ENOEN T (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/i686/cmov/libgtk-1.2.so.0", O_RDONLY)
= -1 ENOEN T (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/i686/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No  such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/sse2/cmov/libgtk-1.2.so.0", O_RDONLY)
= -1 ENOEN T (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/sse2/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No  such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/cmov/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No  such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No such  file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/tls/i686/sse2/cmov/libgtk-1.2.so.0",
O_RDONLY) = -1 ENOENT (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/tls/i686/sse2/libgtk-1.2.so.0", O_RDONLY)
= -1 ENOEN T (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/tls/i686/cmov/libgtk-1.2.so.0", O_RDONLY)
= -1 ENOEN T (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/tls/i686/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No  such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/tls/sse2/cmov/libgtk-1.2.so.0", O_RDONLY)
= -1 ENOEN T (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/tls/sse2/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No  such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/tls/cmov/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No  such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/tls/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No such  file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/i686/sse2/cmov/libgtk-1.2.so.0", O_RDONLY)
= -1 ENOE NT (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/i686/sse2/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (N o such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/i686/cmov/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (N o such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/i686/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No suc h file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/sse2/cmov/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (N o such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/sse2/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No suc h file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/cmov/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No suc h file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT
(No such fil e or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
writev(2, [{ptrace: umoven: Input/output error
0x18ffffd9cd, 10021669952}, {ptrace: umoven: Input/output error
0x245556a52c, 10021669956}, {ptrace: umoven: Input/output error
0xf5556d94f, 10021669947}, {ptrace: umoven: Input/output error
0x1e5556d930, 10021669947}, {ptrace: umoven: Input/output error
0x1955568fd5, 5726702672}, {NULL, 0}, {NULL, 0}, {NULL, 0}, {NULL, 0},
{NULL, 0} ], 10/usr/local/stata9/xstata: error while loading shared

libraries: libgtk-1.2. so.0: cannot open shared object file: No such
file or directory

) = 139
exit_group(127)

---

### Post by Kilz on 2006-07-02
[QUOTE=jplepc2006]Hello,

I am trying to run a 32 bits application (xstata-se ) on an Ubuntu 6.06 distro
(amd64), and I keep getting the error message below.

root@home-desktop64:/home/jazevedo# /usr/local/stata9/xstata-se
/usr/local/stata9/xstata-se: error while loading shared libraries:
libgtk-1.2.so .0: cannot open shared object file: No such file or
directory
root@home-desktop64:/home/jazevedo#

Please note that this application comes both with and without a GUI. The non-GUI version of it (stata-se) runs perfectly well.

I've also ran strace, the output lies below. Any help will be much appreciated.

Cheers,

JP




jazevedo@home-desktop64:~$ strace /usr/local/stata9/xstata
execve("/usr/local/stata9/xstata", ["/usr/local/stata9/xstata"], [/*
31 vars */] ) = 0
[ Process PID=23977 runs in 32 bit mode. ]
uname({sys="Linux", node="home-desktop64", ...}) = 0
brk(0)                                  = 0x85a0000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1,
0) = 0x55 56c000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(0x3, 0xffffca0c)                = 0
mmap2(NULL, 53809, PROT_READ, MAP_PRIVATE, 3, 0) = 0x5556e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib32/tls/i686/sse2/cmov/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No such  file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/tls/i686/sse2/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file  or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/tls/i686/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file  or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/tls/i686/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such
file or d irectory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/tls/sse2/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file  or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/tls/sse2/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such
file or d irectory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/tls/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such
file or d irectory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/tls/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such file
or direct ory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/i686/sse2/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT
(No such fil e or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/i686/sse2/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/i686/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/i686/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such
file or direc tory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/sse2/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/sse2/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such
file or direc tory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such
file or direc tory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib32/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = 0
open("/usr/lib32/tls/i686/sse2/cmov/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/tls/i686/sse2/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT
(No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/tls/i686/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT
(No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/tls/i686/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/tls/sse2/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT
(No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/tls/sse2/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/tls/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/tls/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such
file or di rectory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/i686/sse2/cmov/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No such  file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/i686/sse2/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file  or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/i686/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file  or directory)
stat64(0xffffca20, 0xffffcaa4)          = 0
open("/usr/lib32/i686/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such
file or d irectory)
stat64(0xffffca20, 0xffffcaa4)          = 0
open("/usr/lib32/sse2/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No
such file  or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/sse2/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such
file or d irectory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/cmov/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such
file or d irectory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib32/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT (No such file
or direct ory)
stat64(0xffffca20, 0xffffcaa4)          = 0
open("/usr/lib/x86_64-linux-gnu/tls/i686/sse2/cmov/libgtk-1.2.so.0",
O_RDONLY) =  -1 ENOENT (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/tls/i686/sse2/libgtk-1.2.so.0",
O_RDONLY) = -1 E NOENT (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/tls/i686/cmov/libgtk-1.2.so.0",
O_RDONLY) = -1 E NOENT (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/tls/i686/libgtk-1.2.so.0", O_RDONLY) =
-1 ENOENT  (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/tls/sse2/cmov/libgtk-1.2.so.0",
O_RDONLY) = -1 E NOENT (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/tls/sse2/libgtk-1.2.so.0", O_RDONLY) =
-1 ENOENT  (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/tls/cmov/libgtk-1.2.so.0", O_RDONLY) =
-1 ENOENT  (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/tls/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/i686/sse2/cmov/libgtk-1.2.so.0",
O_RDONLY) = -1 ENOENT (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/i686/sse2/libgtk-1.2.so.0", O_RDONLY)
= -1 ENOEN T (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/i686/cmov/libgtk-1.2.so.0", O_RDONLY)
= -1 ENOEN T (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/i686/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No  such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/sse2/cmov/libgtk-1.2.so.0", O_RDONLY)
= -1 ENOEN T (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/sse2/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No  such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/cmov/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No  such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No such  file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/tls/i686/sse2/cmov/libgtk-1.2.so.0",
O_RDONLY) = -1 ENOENT (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/tls/i686/sse2/libgtk-1.2.so.0", O_RDONLY)
= -1 ENOEN T (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/tls/i686/cmov/libgtk-1.2.so.0", O_RDONLY)
= -1 ENOEN T (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/tls/i686/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No  such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/tls/sse2/cmov/libgtk-1.2.so.0", O_RDONLY)
= -1 ENOEN T (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/tls/sse2/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No  such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/tls/cmov/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No  such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/tls/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No such  file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/i686/sse2/cmov/libgtk-1.2.so.0", O_RDONLY)
= -1 ENOE NT (No such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/i686/sse2/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (N o such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/i686/cmov/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (N o such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/i686/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No suc h file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/sse2/cmov/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (N o such file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/sse2/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No suc h file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/cmov/libgtk-1.2.so.0", O_RDONLY) = -1
ENOENT (No suc h file or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libgtk-1.2.so.0", O_RDONLY) = -1 ENOENT
(No such fil e or directory)
stat64(0xffffca20, 0xffffcaa4)          = -1 ENOENT (No such file or directory)
writev(2, [{ptrace: umoven: Input/output error
0x18ffffd9cd, 10021669952}, {ptrace: umoven: Input/output error
0x245556a52c, 10021669956}, {ptrace: umoven: Input/output error
0xf5556d94f, 10021669947}, {ptrace: umoven: Input/output error
0x1e5556d930, 10021669947}, {ptrace: umoven: Input/output error
0x1955568fd5, 5726702672}, {NULL, 0}, {NULL, 0}, {NULL, 0}, {NULL, 0},
{NULL, 0} ], 10/usr/local/stata9/xstata: error while loading shared

libraries: libgtk-1.2. so.0: cannot open shared object file: No such
file or directory

) = 139
exit_group(127)[/QUOTE]

Have you tried searching for the .deb package, opening it up, and copying the lib to /usr/lib32? Installing 32bit applications on 64bit ubuntu sadly isnt automatic.

---

### Post by jplepc2006 on 2006-07-02
Hello,
Many thanks for the suggestion.
No, I have not tried to look for this library on a Ubuntu 32 instalation.
Please note that I'm a newbie, and I'm not quite sure where and how I could look for this package.
Any futher help will be much appreciated.
Cheers,
JP

---

### Post by Kilz on 2006-07-02
[QUOTE=jplepc2006]Hello,
Many thanks for the suggestion.
No, I have not tried to look for this library on a Ubuntu 32 instalation.
Please note that I'm a newbie, and I'm not quite sure where and how I could look for this package.
Any futher help will be much appreciated.
Cheers,
JP[/QUOTE]
First do a [search here, make sure to get the i386 package if the application the lib is looking for is 32bit ]("http://packages.ubuntu.com/") next install a piece of software
```
sudo apt-get install dpkg-dev
```
You will then be able to extract the contents of the deb file you downloaded wit hthe archive program after you install it.
Next inside the files you extracter is a data.tar.gz, extract it to your desktop. You will now have a /usr folder on the desktop look inside for /usr/lib, open up the terminal type in
```
cd ~/Desktop/usr/lib
``` hit enter
```
cp -r ./* /usr/lib32/
``` hit enter
The files should now be in the /usr/lib32 for 32 bit libs. Navigate with Nautilus there to make sure.

---

### Post by Arnaud_B on 2006-07-08
Hi,
No you obviously won't find any .deb package for stata (just use their website..) but you could check with them if there is a way to exchange your 32 bits license for a 64 bits license (I did a similar thing with them in the past...). stata does exist for 64 bits and it seems very stable even if the port is new. Well but if you prefer keeping the 32 bits license, it will work with a chroot or the ia32 libs... (I personally prefer a chroot but well... it's up to you)
Hope this helps,
Good luck!
A.

---

