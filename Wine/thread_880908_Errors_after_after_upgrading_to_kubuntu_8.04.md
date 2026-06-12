---
title: "Errors after after upgrading to kubuntu 8.04"
date: 2008-08-05
forum: Wine
---

### Post by chjustc on 2008-08-05
Hi there,

I recently upgraded my kubuntu system to 8.04.1 (Hardy Heron), and one of the my data collection software under wine gives me this error every time I run it. I upgrade my wine version to 1.1.2, but the problem persists.

When I run the following command

```

wine ~/.wine/drive_c/DSWINDOW/DSWINDOW.EXE &

```

I get the error

```

err:ntdll:RtlpWaitForCriticalSection section 0x7b92ec60 "syslevel.c: Win16Mutex" wait timed out in thread 001c, blocked by 0019, retrying (60 sec)
wine: Critical section 7b92ec60 wait failed at address 0x7bc3ac50 (thread 001c), starting debugger...
Unhandled exception: wait failed on critical section 0x7b92ec60
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc3ac50
Process of pid=0017 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000c
        00000012    0
        0000000e    0
        0000000d    0
0000000f
        00000016    0
        00000015    0
        00000011    0
        00000010    0
0000001a
        0000001b    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'

```

I tried to use different OS version, such as windows XP, 2000, ME, vista, and 98. None of them solves the problem.

Previously, my kubuntu version was 7.10 (Gutsy Gibbon), and this program (called DataStream) worked fine.

I googled "err:ntdll:RtlpWaitForCriticalSection" for solution and found a few posts.
Such as this one,
[http://appdb.winehq.org/commentview.php?iAppId=74&iVersionId=315&iThreadId=13763](http://appdb.winehq.org/commentview.php?iAppId=74&iVersionId=315&iThreadId=13763)

None of these posts seems to give a good solution.

Does anyone know how to fix this? Thanks.

---

