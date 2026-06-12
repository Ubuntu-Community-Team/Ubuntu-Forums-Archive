---
title: "[SOLVED] F-spot not opening."
date: 2008-05-26
forum: x86 64-bit Users
---

### Post by Sef on 2008-05-26
F-spot does not open.  It may be related to this [thread]("http://ubuntuforums.org/showthread.php?t=808052").


Here is the output from the terminal:

> sef@jokat1:~$ f-spot
Stacktrace:

  at FSpot.Global..cctor () <0xffffffff>
  at FSpot.Global..cctor () <0x0000d>
  at (wrapper runtime-invoke) FSpot.Defines.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at FSpot.Driver.Main (string[]) <0xffffffff>
  at FSpot.Driver.Main (string[]) <0x00144>
  at (wrapper runtime-invoke) FSpot.Driver.runtime_invoke_int_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	f-spot [0x51bb67]
	f-spot [0x43dacd]
	/lib/libpthread.so.0 [0x7f97d43527d0]
	/lib/libc.so.6(memcpy+0x60) [0x7f97d3dddd50]
	f-spot(mono_breakpoint_clean_code+0x1b) [0x42725b]
	f-spot [0x43f78d]
	f-spot [0x44005e]
	[0x40ac915b]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0x7f97d50337a0 (LWP 11974)]
[New Thread 0x410a7950 (LWP 11976)]
[New Thread 0x41e9d950 (LWP 11975)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0x00007f97d3e31da2 in select () from /lib/libc.so.6
  3 Thread 0x41e9d950 (LWP 11975)  0x00007f97d4351e81 in nanosleep ()
   from /lib/libpthread.so.0
  2 Thread 0x410a7950 (LWP 11976)  0x00007f97d434eb99 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  1 Thread 0x7f97d50337a0 (LWP 11974)  0x00007f97d3e31da2 in select ()
   from /lib/libc.so.6

Thread 3 (Thread 0x41e9d950 (LWP 11975)):
#0  0x00007f97d4351e81 in nanosleep () from /lib/libpthread.so.0
#1  0x00000000004b8f4f in ?? ()
#2  0x00007f97d434a3f7 in start_thread () from /lib/libpthread.so.0
#3  0x00007f97d3e38b2d in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x410a7950 (LWP 11976)):
#0  0x00007f97d434eb99 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000004bb585 in ?? ()
#2  0x00000000004bdb37 in ?? ()
#3  0x00000000004cbc03 in ?? ()
#4  0x000000000046b3c1 in ?? ()
#5  0x00000000004855c3 in ?? ()
#6  0x00000000004cb287 in ?? ()
#7  0x00000000004e07d2 in ?? ()
#8  0x00007f97d434a3f7 in start_thread () from /lib/libpthread.so.0
#9  0x00007f97d3e38b2d in clone () from /lib/libc.so.6
#10 0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7f97d50337a0 (LWP 11974)):
#0  0x00007f97d3e31da2 in select () from /lib/libc.so.6
#1  0x00007f97d47ce9bc in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#2  0x00007f97d47ced98 in g_spawn_command_line_sync ()
   from /usr/lib/libglib-2.0.so.0
#3  0x000000000051bbf9 in ?? ()
#4  0x000000000043dacd in ?? ()
#5  <signal handler called>
#6  0x00007f97d3dddd50 in memcpy () from /lib/libc.so.6
#7  0x000000000042725b in mono_breakpoint_clean_code ()
#8  0x000000000043f78d in ?? ()
#9  0x000000000044005e in ?? ()
#10 0x0000000040ac915b in ?? ()
#11 0x0000000000000000 in ?? ()
#0  0x00007f97d3e31da2 in select () from /lib/libc.so.6


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted
sef@jokat1:~$ 

Any ideas as to what to do?

---

### Post by rajeev1204 on 2008-05-27
did u install the hardy - proposed updates? it fixed it for me.

---

### Post by Sef on 2008-05-27
Thank you that worked for me too.:)

---

