---
title: "Static program stop to start"
date: 2009-10-30
forum: x86 64-bit Users
---

### Post by ios77 on 2009-10-30
In my 64 bit Ubuntu 9.10 (Linux ubu 2.6.31-14-generic) everything goes well, but two day ago all the static program stop to start!!!
If I try to start one like googleearth for example it doesn't start:
```
os77@ubu:~/Software/google-earth$ ./googleearth
exec: 50: ./googleearth-bin: not found
ios77@ubu:~/Software/google-earth$ 

```

```
ios77@ubu:~/Software/google-earth$ strace ./googleearth
execve("./googleearth", ["./googleearth"], [/* 38 vars */]) = 0
brk(0)                                  = 0xe15000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fe5977ab000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fe5977a9000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=59643, ...}) = 0
mmap(NULL, 59643, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fe59779a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libc.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320\353\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1490312, ...}) = 0
mmap(NULL, 3598344, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fe59721f000
mprotect(0x7fe597385000, 2093056, PROT_NONE) = 0
mmap(0x7fe597584000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x165000) = 0x7fe597584000
mmap(0x7fe597589000, 18440, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fe597589000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fe597799000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fe597798000
arch_prctl(ARCH_SET_FS, 0x7fe5977986f0) = 0
mprotect(0x7fe597584000, 16384, PROT_READ) = 0
mprotect(0x617000, 4096, PROT_READ)     = 0
mprotect(0x7fe5977ac000, 4096, PROT_READ) = 0
munmap(0x7fe59779a000, 59643)           = 0
getpid()                                = 3720
rt_sigaction(SIGCHLD, {SIG_DFL, [CHLD], SA_RESTORER|SA_RESTART, 0x7fe597252530}, {SIG_DFL, [], 0}, 8) = 0
geteuid()                               = 1000
brk(0)                                  = 0xe15000
brk(0xe36000)                           = 0xe36000
getppid()                               = 3719
stat("/home/ios77/Software/google-earth", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat(".", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("./googleearth", O_RDONLY)         = 3
fcntl(3, F_DUPFD, 10)                   = 10
close(3)                                = 0
fcntl(10, F_SETFD, FD_CLOEXEC)          = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGINT, {0x40812f, ~[RTMIN RT_1], SA_RESTORER, 0x7fe597252530}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL, ~[RTMIN RT_1], SA_RESTORER, 0x7fe597252530}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL, ~[RTMIN RT_1], SA_RESTORER, 0x7fe597252530}, NULL, 8) = 0
read(10, "#!/bin/sh\n#\n# Google Earth start"..., 8192) = 1326
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7fe5977987c0) = 3721
close(4)                                = 0
read(3, ".\n", 128)                     = 2
read(3, "", 128)                        = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
close(3)                                = 0
wait4(4294967295, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 3721
stat("./googleearth-bin", {st_mode=S_IFREG|0755, st_size=301804, ...}) = 0
geteuid()                               = 1000
chdir("/home/ios77/Software/google-earth") = 0
execve("./googleearth-bin", ["./googleearth-bin", "-style=cleanlooks"], [/* 39 vars */]) = -1 ENOENT (No such file or directory)
write(2, "exec: 50: ", 10exec: 50: )              = 10
write(2, "./googleearth-bin: not found", 28./googleearth-bin: not found) = 28
write(2, "\n", 1
)                       = 1
exit_group(2)                           = 
```

And this happend for avery program not installed with deb system.
Please HELP!!

---

### Post by bedtime_with_the_bear on 2009-10-30
> **ios77 said:**
> 
chdir("/home/ios77/Software/google-earth") = 0
execve("./googleearth-bin", ["./googleearth-bin", "-style=cleanlooks"], [/* 39 vars */]) = -1 ENOENT (No such file or directory)
write(2, "exec: 50: ", 10exec: 50: )              = 10
write(2, "./googleearth-bin: not found", 28./googleearth-bin: not found) = 28
write(2, "\n", 1
)                       = 1
exit_group(2)                           = [/code]And this happend for avery program not installed with deb system.
Please HELP!!

I think the ENOENT error means that there is a problem wither with the googleearth-bin file, or with the program that interprets or executes it.

Does Google Earth require Wine on Linux? I've never used it on Linux, but at the start, Google would use the Windows binaries with Wine for the Linux versions.

What is the result of the following:

file /home/ios77/Software/google-earth/googleearth-bin

If it says something like "PE32 executable for MS Windows (console) Intel 80386 32-bit", then you need to install Wine.

---

### Post by ios77 on 2009-10-30
```
ios77@ubu:~$ file /home/ios77/Software/google-earth/googleearth-bin
/home/ios77/Software/google-earth/googleearth-bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.0, stripped
```

no it run without wine or emulation. And this happen with other programs like MoioSms and Cisco Packet Tracer.
After an update of Ubuntu One packets everything is restored. Strange, very very strange. I close the thread but I really don't have understand what is happened to my system.

---

