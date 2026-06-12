---
title: "[SOLVED] WoW crashes after resetting UI"
date: 2008-08-15
forum: Wine
---

### Post by JMuffin on 2008-08-15
I recently started playing WoW again and when I logged in there was a little message that said I had an open GM ticket. The games help section says it is a known issue and that the way to get rid of it is to reset your UI. I followed Blizzard's instructions to do this and started the game again. The screen went black and I could hear the audio for the opening animation and then I received a very long error and the game crashed. I have since removed the game from my hard drive and completely reinstalled it. I am still getting the same (or very similar) error and the game crashes. the complete error is as follows:

==============================================================================
World of WarCraft (build 8606)

Exe:      C:\Program Files\World of Warcraft\Wow.exe
Time:     Aug 15, 2008  6:38:45.717 AM
User:     jmuff
Computer: jmuff-desktop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:00751747

The instruction at "0x00751747" referenced memory at "0xE0D48A37".
The memory could not be "read".


WoWBuild: 8606
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=48330006  EBX=0033FA20  ECX=C0088A17  EDX=5AAE3C00  ESI=00E2200C
EDI=D9710B02  EBP=008CE4DC  ESP=0033C77C  EIP=00751747  FLG=00210202
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 18/18 threads...

--- Thread ID: 58 ---
7EFC4D8B 7AAFF868 0001:00053D8B c:\windows\system32\ntdll.dll
7EFC5062 7AAFF898 0001:00054062 c:\windows\system32\ntdll.dll
7EE95BA2 7AAFF9E8 0001:00064BA2 c:\windows\system32\KERNEL32.dll
7EE95D9C 7AAFFA08 0001:00064D9C c:\windows\system32\KERNEL32.dll
0083544E 7AAFFA38 0001:0043444E C:\Program Files\World of Warcraft\Wow.exe
7EFC6D0E 7AAFFA48 0001:00055D0E c:\windows\system32\ntdll.dll
7EFC73A2 7AAFFAE8 0001:000563A2 c:\windows\system32\ntdll.dll
7EFC75BC 7AB003D8 0001:000565BC c:\windows\system32\ntdll.dll
B7E364FB 7AB004C8 0000:00000000 <unknown>

--- Thread ID: 57 ---
7EFC4D8B 7B9CB63C 0001:00053D8B c:\windows\system32\ntdll.dll
7EFC5062 7B9CB66C 0001:00054062 c:\windows\system32\ntdll.dll
7EE95BA2 7B9CB7BC 0001:00064BA2 c:\windows\system32\KERNEL32.dll
7D507AFE 7B9CB7EC 0001:00026AFE c:\windows\system32\winex11.drv
7EB6A4CE 7B9CB99C 0001:000794CE c:\windows\system32\user32.dll
7EB6A52F 7B9CB9BC 0001:0007952F c:\windows\system32\user32.dll
006771C8 7B9CBA30 0001:002761C8 C:\Program Files\World of Warcraft\Wow.exe
0075FDD4 7B9CBA48 0001:0035EDD4 C:\Program Files\World of Warcraft\Wow.exe
7EFC73A2 7B9CBAE8 0001:000563A2 c:\windows\system32\ntdll.dll
7EFC75BC 7B9CC3D8 0001:000565BC c:\windows\system32\ntdll.dll
B7E364FB 7B9CC4C8 0000:00000000 <unknown>

--- Thread ID: 56 ---
7EFC4D8B 7BCDC868 0001:00053D8B c:\windows\system32\ntdll.dll
7EFC5062 7BCDC898 0001:00054062 c:\windows\system32\ntdll.dll
7EE95BA2 7BCDC9E8 0001:00064BA2 c:\windows\system32\KERNEL32.dll
7EE95D9C 7BCDCA08 0001:00064D9C c:\windows\system32\KERNEL32.dll
0083544E 7BCDCA38 0001:0043444E C:\Program Files\World of Warcraft\Wow.exe
7EFC6D0E 7BCDCA48 0001:00055D0E c:\windows\system32\ntdll.dll
7EFC73A2 7BCDCAE8 0001:000563A2 c:\windows\system32\ntdll.dll
7EFC75BC 7BCDD3D8 0001:000565BC c:\windows\system32\ntdll.dll
B7E364FB 7BCDD4C8 0000:00000000 <unknown>

--- Thread ID: 52 ---
7EFC4D8B 7BDED988 0001:00053D8B c:\windows\system32\ntdll.dll
7EFC5062 7BDED9B8 0001:00054062 c:\windows\system32\ntdll.dll
7EFC50BC 7BDED9D8 0001:000540BC c:\windows\system32\ntdll.dll
7EFC9B50 7BDEDA38 0001:00058B50 c:\windows\system32\ntdll.dll
7EFC6D0E 7BDEDA48 0001:00055D0E c:\windows\system32\ntdll.dll
7EFC73A2 7BDEDAE8 0001:000563A2 c:\windows\system32\ntdll.dll
7EFC75BC 7BDEE3D8 0001:000565BC c:\windows\system32\ntdll.dll
B7E364FB 7BDEE4C8 0000:00000000 <unknown>

--- Thread ID: 51 ---
7EFC4D8B 7BEFE63C 0001:00053D8B c:\windows\system32\ntdll.dll
7EFC5062 7BEFE66C 0001:00054062 c:\windows\system32\ntdll.dll
7EE95BA2 7BEFE7BC 0001:00064BA2 c:\windows\system32\KERNEL32.dll
7D507AFE 7BEFE7EC 0001:00026AFE c:\windows\system32\winex11.drv
7EB6A4CE 7BEFE99C 0001:000794CE c:\windows\system32\user32.dll
7EB6A52F 7BEFE9BC 0001:0007952F c:\windows\system32\user32.dll
006771C8 7BEFEA30 0001:002761C8 C:\Program Files\World of Warcraft\Wow.exe
0075FDD4 7BEFEA48 0001:0035EDD4 C:\Program Files\World of Warcraft\Wow.exe
7EFC73A2 7BEFEAE8 0001:000563A2 c:\windows\system32\ntdll.dll
7EFC75BC 7BEFF3D8 0001:000565BC c:\windows\system32\ntdll.dll
B7E364FB 7BEFF4C8 0000:00000000 <unknown>

--- Thread ID: 50 ---
7EFC4D8B 7C2F3614 0001:00053D8B c:\windows\system32\ntdll.dll
7EFC5062 7C2F3644 0001:00054062 c:\windows\system32\ntdll.dll
7EE95BA2 7C2F3794 0001:00064BA2 c:\windows\system32\KERNEL32.dll
7EE95CFA 7C2F37B4 0001:00064CFA c:\windows\system32\KERNEL32.dll
00425ACB 7C2F3A0C 0001:00024ACB C:\Program Files\World of Warcraft\Wow.exe
00425328 7C2F3A1C 0001:00024328 C:\Program Files\World of Warcraft\Wow.exe
00645617 7C2F3A38 0001:00244617 C:\Program Files\World of Warcraft\Wow.exe
7EFC6D0E 7C2F3A48 0001:00055D0E c:\windows\system32\ntdll.dll
7EFC73A2 7C2F3AE8 0001:000563A2 c:\windows\system32\ntdll.dll
7EFC75BC 7C2F43D8 0001:000565BC c:\windows\system32\ntdll.dll
B7E364FB 7C2F44C8 0000:00000000 <unknown>

--- Thread ID: 49 ---
7EFC4D8B 7C404848 0001:00053D8B c:\windows\system32\ntdll.dll
7EFC5062 7C404878 0001:00054062 c:\windows\system32\ntdll.dll
7EE95BA2 7C4049C8 0001:00064BA2 c:\windows\system32\KERNEL32.dll
7EE95D9C 7C4049E8 0001:00064D9C c:\windows\system32\KERNEL32.dll
00649400 7C4049F8 0001:00248400 C:\Program Files\World of Warcraft\Wow.exe
00425215 7C404A10 0001:00024215 C:\Program Files\World of Warcraft\Wow.exe
00425351 7C404A1C 0001:00024351 C:\Program Files\World of Warcraft\Wow.exe
00645617 7C404A38 0001:00244617 C:\Program Files\World of Warcraft\Wow.exe
7EFC6D0E 7C404A48 0001:00055D0E c:\windows\system32\ntdll.dll
7EFC73A2 7C404AE8 0001:000563A2 c:\windows\system32\ntdll.dll
7EFC75BC 7C4053D8 0001:000565BC c:\windows\system32\ntdll.dll
B7E364FB 7C4054C8 0000:00000000 <unknown>

--- Thread ID: 48 ---
7EE97DE4 7C5159FC 0001:00066DE4 c:\windows\system32\KERNEL32.dll
7EE97E35 7C515A1C 0001:00066E35 c:\windows\system32\KERNEL32.dll
007FDB00 7C515A38 0001:003FCB00 C:\Program Files\World of Warcraft\Wow.exe
7EFC6D0E 7C515A48 0001:00055D0E c:\windows\system32\ntdll.dll
7EFC73A2 7C515AE8 0001:000563A2 c:\windows\system32\ntdll.dll
7EFC75BC 7C5163D8 0001:000565BC c:\windows\system32\ntdll.dll
B7E364FB 7C5164C8 0000:00000000 <unknown>

--- Thread ID: 47 ---
7EE97DE4 7C6269FC 0001:00066DE4 c:\windows\system32\KERNEL32.dll
7EE97E35 7C626A1C 0001:00066E35 c:\windows\system32\KERNEL32.dll
007FDB00 7C626A38 0001:003FCB00 C:\Program Files\World of Warcraft\Wow.exe
7EFC6D0E 7C626A48 0001:00055D0E c:\windows\system32\ntdll.dll
7EFC73A2 7C626AE8 0001:000563A2 c:\windows\system32\ntdll.dll
7EFC75BC 7C6273D8 0001:000565BC c:\windows\system32\ntdll.dll
B7E364FB 7C6274C8 0000:00000000 <unknown>

--- Thread ID: 46 ---
7D4149EF 7CA6AA38 0001:000039EF c:\windows\system32\wineoss.drv
7EFC6D0E 7CA6AA48 0001:00055D0E c:\windows\system32\ntdll.dll
7EFC73A2 7CA6AAE8 0001:000563A2 c:\windows\system32\ntdll.dll
7EFC75BC 7CA6B3D8 0001:000565BC c:\windows\system32\ntdll.dll
B7E364FB 7CA6B4C8 0000:00000000 <unknown>

--- Thread ID: 45 ---
7EE97DE4 7C7379FC 0001:00066DE4 c:\windows\system32\KERNEL32.dll
7EE97E35 7C737A1C 0001:00066E35 c:\windows\system32\KERNEL32.dll
007FDB00 7C737A38 0001:003FCB00 C:\Program Files\World of Warcraft\Wow.exe
7EFC6D0E 7C737A48 0001:00055D0E c:\windows\system32\ntdll.dll
7EFC73A2 7C737AE8 0001:000563A2 c:\windows\system32\ntdll.dll
7EFC75BC 7C7383D8 0001:000565BC c:\windows\system32\ntdll.dll
B7E364FB 7C7384C8 0000:00000000 <unknown>

--- Thread ID: 44 ---
7EE97DE4 7C8489FC 0001:00066DE4 c:\windows\system32\KERNEL32.dll
7EE97E35 7C848A1C 0001:00066E35 c:\windows\system32\KERNEL32.dll
007FDB00 7C848A38 0001:003FCB00 C:\Program Files\World of Warcraft\Wow.exe
7EFC6D0E 7C848A48 0001:00055D0E c:\windows\system32\ntdll.dll
7EFC73A2 7C848AE8 0001:000563A2 c:\windows\system32\ntdll.dll
7EFC75BC 7C8493D8 0001:000565BC c:\windows\system32\ntdll.dll
B7E364FB 7C8494C8 0000:00000000 <unknown>

--- Thread ID: 42 ---
7EC56805 7C959A38 0001:00025805 c:\windows\system32\winmm.dll
7EFC6D0E 7C959A48 0001:00055D0E c:\windows\system32\ntdll.dll
7EFC73A2 7C959AE8 0001:000563A2 c:\windows\system32\ntdll.dll
7EFC75BC 7C95A3D8 0001:000565BC c:\windows\system32\ntdll.dll
B7E364FB 7C95A4C8 0000:00000000 <unknown>

--- Thread ID: 40 ---
7EFC4D8B 7CBC5854 0001:00053D8B c:\windows\system32\ntdll.dll
7EFC5062 7CBC5884 0001:00054062 c:\windows\system32\ntdll.dll
7EE95BA2 7CBC59D4 0001:00064BA2 c:\windows\system32\KERNEL32.dll
7EE95D9C 7CBC59F4 0001:00064D9C c:\windows\system32\KERNEL32.dll
00649400 7CBC5A04 0001:00248400 C:\Program Files\World of Warcraft\Wow.exe
00709102 7CBC5A1C 0001:00308102 C:\Program Files\World of Warcraft\Wow.exe
00645617 7CBC5A38 0001:00244617 C:\Program Files\World of Warcraft\Wow.exe
7EFC6D0E 7CBC5A48 0001:00055D0E c:\windows\system32\ntdll.dll
7EFC73A2 7CBC5AE8 0001:000563A2 c:\windows\system32\ntdll.dll
7EFC75BC 7CBC63D8 0001:000565BC c:\windows\system32\ntdll.dll
B7E364FB 7CBC64C8 0000:00000000 <unknown>

--- Thread ID: 39 ---
7EE97DE4 7CCD65D0 0001:00066DE4 c:\windows\system32\KERNEL32.dll
7EE97E35 7CCD65F0 0001:00066E35 c:\windows\system32\KERNEL32.dll
00749C3D 7CCD65FC 0001:00348C3D C:\Program Files\World of Warcraft\Wow.exe
004584BD 7CCD6A1C 0001:000574BD C:\Program Files\World of Warcraft\Wow.exe
00645617 7CCD6A38 0001:00244617 C:\Program Files\World of Warcraft\Wow.exe
7EFC6D0E 7CCD6A48 0001:00055D0E c:\windows\system32\ntdll.dll
7EFC73A2 7CCD6AE8 0001:000563A2 c:\windows\system32\ntdll.dll
7EFC75BC 7CCD73D8 0001:000565BC c:\windows\system32\ntdll.dll
B7E364FB 7CCD74C8 0000:00000000 <unknown>

--- Thread ID: 38 ---
7EFC4D8B 7CE4B82C 0001:00053D8B c:\windows\system32\ntdll.dll
7EFC5062 7CE4B85C 0001:00054062 c:\windows\system32\ntdll.dll
7EE95BA2 7CE4B9AC 0001:00064BA2 c:\windows\system32\KERNEL32.dll
7EE95D9C 7CE4B9CC 0001:00064D9C c:\windows\system32\KERNEL32.dll

--- Thread ID: 37 ---
7EE97DE4 7CF5C9B4 0001:00066DE4 c:\windows\system32\KERNEL32.dll
7EE97E35 7CF5C9D4 0001:00066E35 c:\windows\system32\KERNEL32.dll
0065EF34 7CF5CA30 0001:0025DF34 C:\Program Files\World of Warcraft\Wow.exe
0075FDD4 7CF5CA48 0001:0035EDD4 C:\Program Files\World of Warcraft\Wow.exe
7EFC73A2 7CF5CAE8 0001:000563A2 c:\windows\system32\ntdll.dll
7EFC75BC 7CF5D3D8 0001:000565BC c:\windows\system32\ntdll.dll
B7E364FB 7CF5D4C8 0000:00000000 <unknown>

--- Thread ID: 36 [Current Thread] ---
00751747 008CE4DC 0001:00350747 C:\Program Files\World of Warcraft\Wow.exe

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 18/18 threads...

--- Thread ID: 58 ---
7EFC4D8B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7AAFF8D0,0x00000004,0x00000000) (sync.c,987)
7EFC5062 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7AAFF8D0,0x00000000,0x00000000) (sync.c,1025)
7EE95BA2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7AAFFA10,0x00000000,0xFFFFFFFF) (sync.c,192)
7EE95D9C KERNEL32.dll WaitForSingleObject+60 (0x00002224,0xFFFFFFFF,0x093E5424,0x007FDC2B) (sync.c,130)
0083544E Wow.exe      <unknown symbol>+0 (0x093E5424,0x00802057,0x7AAFFAE8,0x7EFC73A2)
7EFC6D0E ntdll.dll    call_thread_entry_point+14 (0x00802057,0x093E5424,0x10012A03,0x00000000)
7EFC73A2 ntdll.dll    call_thread_func+66 (0x7AAFFB1C,0x00000000,0x00000000,0x00000000) (thread.c,386)
7EFC75BC ntdll.dll    start_thread+396 (0x7FF94FB8,0x7AB00490,0x7AB00490,0x7AB00490) (thread.c,453)
B7E364FB              start_thread+203 (0x7AB00B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 57 ---
7EFC4D8B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000003,0x7B9CB6A4,0x00000004,0x00000000) (sync.c,987)
7EFC5062 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x7B9CB6A4,0x00000000,0x00000000) (sync.c,1025)
7EE95BA2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000003,0x7B9CB820,0x00000000,0xFFFFFFFF) (sync.c,192)
7D507AFE winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+126 (0x00000003,0x7B9CB820,0xFFFFFFFF,0x00000000) (event.c,372)
7EB6A4CE user32.dll   MsgWaitForMultipleObjectsEx+238 (0x00000002,0x7B9CB9E4,0xFFFFFFFF,0x00000000) (message.c,3237)
7EB6A52F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x7B9CB9E4,0x00000000,0xFFFFFFFF) (message.c,3251)
006771C8 Wow.exe      <unknown symbol>+0 (0x012F91B8,0x7EFC6D0E,0x012F91B8,0x0075FD55)
0075FDD4 Wow.exe      <unknown symbol>+0 (0x0075FD55,0x012F91B8,0x10012A03,0x00000000)
7EFC73A2 ntdll.dll    call_thread_func+66 (0x7B9CBB1C,0x00000000,0x00000000,0x00000000) (thread.c,386)
7EFC75BC ntdll.dll    start_thread+396 (0x7FF98FB8,0x7B9CC490,0x7B9CC490,0x7B9CC490) (thread.c,453)
B7E364FB              start_thread+203 (0x7B9CCB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 56 ---
7EFC4D8B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7BCDC8D0,0x00000004,0x00000000) (sync.c,987)
7EFC5062 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7BCDC8D0,0x00000000,0x00000000) (sync.c,1025)
7EE95BA2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7BCDCA10,0x00000000,0xFFFFFFFF) (sync.c,192)
7EE95D9C KERNEL32.dll WaitForSingleObject+60 (0x000021F4,0xFFFFFFFF,0x074FCC24,0x007FDC2B) (sync.c,130)
0083544E Wow.exe      <unknown symbol>+0 (0x074FCC24,0x00802057,0x7BCDCAE8,0x7EFC73A2)
7EFC6D0E ntdll.dll    call_thread_entry_point+14 (0x00802057,0x074FCC24,0x10012A03,0x00000000)
7EFC73A2 ntdll.dll    call_thread_func+66 (0x7BCDCB1C,0x00000000,0x00000000,0x00000000) (thread.c,386)
7EFC75BC ntdll.dll    start_thread+396 (0x7FF9CFB8,0x7BCDD490,0x7BCDD490,0x7BCDD490) (thread.c,453)
B7E364FB              start_thread+203 (0x7BCDDB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 52 ---
7EFC4D8B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7BDED9E0,0x00000004,0x7BDEDA20) (sync.c,987)
7EFC5062 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7BDED9E0,0x00000000,0x00000000) (sync.c,1025)
7EFC50BC ntdll.dll    NtWaitForSingleObject+60 (0x000021D8,0x00000000,0x7BDEDA20,0x7EFE185A) (sync.c,1035)
7EFC9B50 ntdll.dll    worker_thread_proc+304 (0x00000000,0x7EFC9A20,0x7BDEDAE8,0x7EFC73A2) (threadpool.c,125)
7EFC6D0E ntdll.dll    call_thread_entry_point+14 (0x7EFC9A20,0x00000000,0x10012A03,0x00000000)
7EFC73A2 ntdll.dll    call_thread_func+66 (0x7BDEDB1C,0x00000000,0x00000000,0x00000000) (thread.c,386)
7EFC75BC ntdll.dll    start_thread+396 (0x7FFA0FB8,0x7BDEE490,0x7BDEE490,0x7BDEE490) (thread.c,453)
B7E364FB              start_thread+203 (0x7BDEEB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 51 ---
7EFC4D8B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000003,0x7BEFE6A4,0x00000004,0x00000000) (sync.c,987)
7EFC5062 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x7BEFE6A4,0x00000000,0x00000000) (sync.c,1025)
7EE95BA2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000003,0x7BEFE820,0x00000000,0xFFFFFFFF) (sync.c,192)
7D507AFE winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+126 (0x00000003,0x7BEFE820,0xFFFFFFFF,0x00000000) (event.c,372)
7EB6A4CE user32.dll   MsgWaitForMultipleObjectsEx+238 (0x00000002,0x7BEFE9E4,0xFFFFFFFF,0x00000000) (message.c,3237)
7EB6A52F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x7BEFE9E4,0x00000000,0xFFFFFFFF) (message.c,3251)
006771C8 Wow.exe      <unknown symbol>+0 (0x012F8D40,0x7EFC6D0E,0x012F8D40,0x0075FD55)
0075FDD4 Wow.exe      <unknown symbol>+0 (0x0075FD55,0x012F8D40,0x10012A03,0x00000000)
7EFC73A2 ntdll.dll    call_thread_func+66 (0x7BEFEB1C,0x00000000,0x00000000,0x00000000) (thread.c,386)
7EFC75BC ntdll.dll    start_thread+396 (0x7FFA4FB8,0x7BEFF490,0x7BEFF490,0x7BEFF490) (thread.c,453)
B7E364FB              start_thread+203 (0x7BEFFB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 50 ---
7EFC4D8B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7C2F367C,0x00000004,0x7C2F377C) (sync.c,987)
7EFC5062 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7C2F367C,0x00000000,0x00000000) (sync.c,1025)
7EE95BA2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7C2F38D8,0x00000000,0x000001F4) (sync.c,192)
7EE95CFA KERNEL32.dll WaitForMultipleObjects+58 (0x00000001,0x7C2F38D8,0x00000000,0x000001F4) (sync.c,150)
00425ACB Wow.exe      <unknown symbol>+0 (0x00425360,0x0042536B,0x7C2F3A38,0x00645617)
00425328 Wow.exe      <unknown symbol>+0 (0x06A30008,0x006455E0,0x06A1F188,0x7EFE4444)
00645617 Wow.exe      <unknown symbol>+0 (0x000021B4,0x006455E0,0x7C2F3AE8,0x7EFC73A2)
7EFC6D0E ntdll.dll    call_thread_entry_point+14 (0x006455E0,0x06A1F188,0x10012A03,0x00000000)
7EFC73A2 ntdll.dll    call_thread_func+66 (0x7C2F3B1C,0x00000000,0x00000000,0x00000000) (thread.c,386)
7EFC75BC ntdll.dll    start_thread+396 (0x7FFA8FB8,0x7C2F4490,0x7C2F4490,0x7C2F4490) (thread.c,453)
B7E364FB              start_thread+203 (0x7C2F4B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 49 ---
7EFC4D8B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7C4048B0,0x00000004,0x7C4049B0) (sync.c,987)
7EFC5062 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7C4048B0,0x00000000,0x00000000) (sync.c,1025)
7EE95BA2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7C4049F0,0x00000000,0x000003E8) (sync.c,192)
7EE95D9C KERNEL32.dll WaitForSingleObject+60 (0x00002124,0x000003E8,0x7C404A10,0x00425215) (sync.c,130)
00649400 Wow.exe      <unknown symbol>+0 (0x000003E8,0x06A30018,0x00425340,0x00000031)
00425215 Wow.exe      <unknown symbol>+0 (0x00000000,0x7C404A38,0x00645617,0x06A30018)
00425351 Wow.exe      <unknown symbol>+0 (0x06A30018,0x006455E0,0x06A1F188,0x7EFE4444)
00645617 Wow.exe      <unknown symbol>+0 (0x000021B0,0x006455E0,0x7C404AE8,0x7EFC73A2)
7EFC6D0E ntdll.dll    call_thread_entry_point+14 (0x006455E0,0x06A1F188,0x10012A03,0x00000000)
7EFC73A2 ntdll.dll    call_thread_func+66 (0x7C404B1C,0x00000000,0x00000000,0x00000000) (thread.c,386)
7EFC75BC ntdll.dll    start_thread+396 (0x7FFACFB8,0x7C405490,0x7C405490,0x7C405490) (thread.c,453)
B7E364FB              start_thread+203 (0x7C405B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 48 ---
7EE97DE4 KERNEL32.dll SleepEx+68 (0x0000000A,0x00000000,0x7C515A24,0x007F36E8) (sync.c,109)
7EE97E35 KERNEL32.dll Sleep+37 (0x0000000A,0x008020C5,0x0000000A,0x062D7FA8) (sync.c,99)
007FDB00 Wow.exe      <unknown symbol>+0 (0x062D7FA8,0x00802057,0x7C515AE8,0x7EFC73A2)
7EFC6D0E ntdll.dll    call_thread_entry_point+14 (0x00802057,0x062D7FA8,0x10012A03,0x00000000)
7EFC73A2 ntdll.dll    call_thread_func+66 (0x7C515B1C,0x00000000,0x00000000,0x00000000) (thread.c,386)
7EFC75BC ntdll.dll    start_thread+396 (0x7FFB0FB8,0x7C516490,0x7C516490,0x7C516490) (thread.c,453)
B7E364FB              start_thread+203 (0x7C516B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 47 ---
7EE97DE4 KERNEL32.dll SleepEx+68 (0x0000000A,0x00000000,0x00000000,0x00000002) (sync.c,109)
7EE97E35 KERNEL32.dll Sleep+37 (0x0000000A,0x008020C5,0x0000000A,0x06327288) (sync.c,99)
007FDB00 Wow.exe      <unknown symbol>+0 (0x06327288,0x00802057,0x7C626AE8,0x7EFC73A2)
7EFC6D0E ntdll.dll    call_thread_entry_point+14 (0x00802057,0x06327288,0x10012A03,0x00000000)
7EFC73A2 ntdll.dll    call_thread_func+66 (0x7C626B1C,0x00000000,0x00000000,0x00000000) (thread.c,386)
7EFC75BC ntdll.dll    start_thread+396 (0x7FFB4FB8,0x7C627490,0x7C627490,0x7C627490) (thread.c,453)
B7E364FB              start_thread+203 (0x7C627B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 46 ---
7D4149EF wineoss.drv  wodPlayer+191 (0x00000000,0x7D414930,0x7CA6AAE8,0x7EFC73A2) (audio.c,1899)
7EFC6D0E ntdll.dll    call_thread_entry_point+14 (0x7D414930,0x00000000,0x10012A03,0x00000000)
7EFC73A2 ntdll.dll    call_thread_func+66 (0x7CA6AB1C,0x00000000,0x00000000,0x00000000) (thread.c,386)
7EFC75BC ntdll.dll    start_thread+396 (0x7FFC4FB8,0x7CA6B490,0x7CA6B490,0x7CA6B490) (thread.c,453)
B7E364FB              start_thread+203 (0x7CA6BB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 45 ---
7EE97DE4 KERNEL32.dll SleepEx+68 (0x0000000A,0x00000000,0x7C737A24,0x007F36E8) (sync.c,109)
7EE97E35 KERNEL32.dll Sleep+37 (0x0000000A,0x008020C5,0x0000000A,0x062E7FA8) (sync.c,99)
007FDB00 Wow.exe      <unknown symbol>+0 (0x062E7FA8,0x00802057,0x7C737AE8,0x7EFC73A2)
7EFC6D0E ntdll.dll    call_thread_entry_point+14 (0x00802057,0x062E7FA8,0x10012A03,0x00000000)
7EFC73A2 ntdll.dll    call_thread_func+66 (0x7C737B1C,0x00000000,0x00000000,0x00000000) (thread.c,386)
7EFC75BC ntdll.dll    start_thread+396 (0x7FFB8FB8,0x7C738490,0x7C738490,0x7C738490) (thread.c,453)
B7E364FB              start_thread+203 (0x7C738B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 44 ---
7EE97DE4 KERNEL32.dll SleepEx+68 (0x0000000A,0x00000000,0x00000000,0x00000002) (sync.c,109)
7EE97E35 KERNEL32.dll Sleep+37 (0x0000000A,0x008020C5,0x0000000A,0x061A8288) (sync.c,99)
007FDB00 Wow.exe      <unknown symbol>+0 (0x061A8288,0x00802057,0x7C848AE8,0x7EFC73A2)
7EFC6D0E ntdll.dll    call_thread_entry_point+14 (0x00802057,0x061A8288,0x10012A03,0x00000000)
7EFC73A2 ntdll.dll    call_thread_func+66 (0x7C848B1C,0x00000000,0x00000000,0x00000000) (thread.c,386)
7EFC75BC ntdll.dll    start_thread+396 (0x7FFBCFB8,0x7C849490,0x7C849490,0x7C849490) (thread.c,453)
B7E364FB              start_thread+203 (0x7C849B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 42 ---
7EC56805 winmm.dll    TIME_MMSysTimeThread+549 (0x00000000,0x7EC565E0,0x7C959AE8,0x7EFC73A2) (time.c,222)
7EFC6D0E ntdll.dll    call_thread_entry_point+14 (0x7EC565E0,0x00000000,0x10012A03,0x00000000)
7EFC73A2 ntdll.dll    call_thread_func+66 (0x7C959B1C,0x00000000,0x00000000,0x00000000) (thread.c,386)
7EFC75BC ntdll.dll    start_thread+396 (0x7FFC0FB8,0x7C95A490,0x7C95A490,0x7C95A490) (thread.c,453)
B7E364FB              start_thread+203 (0x7C95AB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 40 ---
7EFC4D8B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7CBC58BC,0x00000004,0x00000000) (sync.c,987)
7EFC5062 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7CBC58BC,0x00000000,0x00000000) (sync.c,1025)
7EE95BA2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7CBC59FC,0x00000000,0xFFFFFFFF) (sync.c,192)
7EE95D9C KERNEL32.dll WaitForSingleObject+60 (0x00002088,0xFFFFFFFF,0x7CBC5A1C,0x00709102) (sync.c,130)
00649400 Wow.exe      <unknown symbol>+0 (0xFFFFFFFF,0x00000028,0x00E1E060,0x007090A0)
00709102 Wow.exe      <unknown symbol>+0 (0x00E1E060,0x006455E0,0x02554B48,0x7EFE4444)
00645617 Wow.exe      <unknown symbol>+0 (0x000020E0,0x006455E0,0x7CBC5AE8,0x7EFC73A2)
7EFC6D0E ntdll.dll    call_thread_entry_point+14 (0x006455E0,0x02554B48,0x10012A03,0x00000000)
7EFC73A2 ntdll.dll    call_thread_func+66 (0x7CBC5B1C,0x00000000,0x00000000,0x00000000) (thread.c,386)
7EFC75BC ntdll.dll    start_thread+396 (0x7FFC8FB8,0x7CBC6490,0x7CBC6490,0x7CBC6490) (thread.c,453)
B7E364FB              start_thread+203 (0x7CBC6B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 39 ---
7EE97DE4 KERNEL32.dll SleepEx+68 (0x00000001,0x00000000,0x00000000,0x00000000) (sync.c,109)
7EE97E35 KERNEL32.dll Sleep+37 (0x00000001,0x7CCD6A1C,0x004584BD,0x00000001) (sync.c,99)
00749C3D Wow.exe      <unknown symbol>+0 (0x00000001,0x00000000,0x004582E0,0x00000027)
004584BD Wow.exe      <unknown symbol>+0 (0x00000000,0x006455E0,0x025531A8,0x7EFE4444)
00645617 Wow.exe      <unknown symbol>+0 (0x000020DC,0x006455E0,0x7CCD6AE8,0x7EFC73A2)
7EFC6D0E ntdll.dll    call_thread_entry_point+14 (0x006455E0,0x025531A8,0x10012A03,0x00000000)
7EFC73A2 ntdll.dll    call_thread_func+66 (0x7CCD6B1C,0x00000000,0x00000000,0x00000000) (thread.c,386)
7EFC75BC ntdll.dll    start_thread+396 (0x7FFCCFB8,0x7CCD7490,0x7CCD7490,0x7CCD7490) (thread.c,453)
B7E364FB              start_thread+203 (0x7CCD7B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 38 ---
7EFC4D8B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7CE4B894,0x00000004,0x00000000) (sync.c,987)
7EFC5062 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7CE4B894,0x00000000,0x00000000) (sync.c,1025)
7EE95BA2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7CE4B9D4,0x00000000,0xFFFFFFFF) (sync.c,192)
7EE95D9C KERNEL32.dll WaitForSingleObject+60 (0x000020C0,0xFFFFFFFF,0x7EFE4444,0x7EE97E10) (sync.c,130)

--- Thread ID: 37 ---
7EE97DE4 KERNEL32.dll SleepEx+68 (0x00000064,0x00000000,0x7CF5C9D4,0x7EE5F557) (sync.c,109)
7EE97E35 KERNEL32.dll Sleep+37 (0x00000064,0x7EE97E10,0x7EFE4444,0x01200BD8) (sync.c,99)
0065EF34 Wow.exe      <unknown symbol>+0 (0x01200C10,0x7EFC6D0E,0x01200C10,0x01200C10)
0075FDD4 Wow.exe      <unknown symbol>+0 (0x0075FD55,0x01200C10,0x10012A03,0x00000000)
7EFC73A2 ntdll.dll    call_thread_func+66 (0x7CF5CB1C,0x00000000,0x00000000,0x00000000) (thread.c,386)
7EFC75BC ntdll.dll    start_thread+396 (0x7FFD4FB8,0x7CF5D490,0x7CF5D490,0x7CF5D490) (thread.c,453)
B7E364FB              start_thread+203 (0x7CF5DB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 36 [Current Thread] ---
00751747 Wow.exe      <unknown symbol>+0 (0x4F70614D,0x772E6A62,0x00007866,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00400000 - 0x00EC8000  C:\Program Files\World of Warcraft\Wow.exe
0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll
0x797F0000 - 0x7982B000  c:\windows\system32\dbghelp.dll
0x7CA70000 - 0x7CAB6000  c:\windows\system32\dsound.dll
0x7D320000 - 0x7D32C000  c:\windows\system32\psapi.dll
0x7D360000 - 0x7D38F000  c:\windows\system32\uxtheme.dll
0x7D3E0000 - 0x7D3E8000  c:\windows\system32\midimap.dll
0x7D3F0000 - 0x7D3FF000  c:\windows\system32\msacm32.drv
0x7D410000 - 0x7D43A000  c:\windows\system32\wineoss.drv
0x7D4E0000 - 0x7D55E000  c:\windows\system32\winex11.drv
0x7D680000 - 0x7D6D2000  c:\windows\system32\rpcrt4.dll
0x7D6E0000 - 0x7D776000  c:\windows\system32\ole32.dll
0x7D780000 - 0x7D79C000  c:\windows\system32\msacm32.dll
0x7D7D0000 - 0x7D7DE000  c:\windows\system32\iphlpapi.dll
0x7D7F0000 - 0x7D80A000  c:\windows\system32\ws2_32.dll
0x7D810000 - 0x7D8C9000  c:\windows\system32\comctl32.dll
0x7D8E0000 - 0x7D9D5000  c:\windows\system32\shell32.dll
0x7D9E0000 - 0x7DA2E000  c:\windows\system32\shlwapi.dll
0x7DA30000 - 0x7DA4F000  c:\windows\system32\mpr.dll
0x7DA60000 - 0x7DA9C000  c:\windows\system32\wininet.dll
0x7DAA0000 - 0x7DABA000  c:\windows\system32\imm32.dll
0x7DAC0000 - 0x7DACE000  c:\windows\system32\lz32.dll
0x7DAD0000 - 0x7DAE7000  c:\windows\system32\version.dll
0x7DB00000 - 0x7DBE9000  c:\windows\system32\wined3d.dll
0x7DBF0000 - 0x7DC19000  c:\windows\system32\d3d9.dll
0x7E980000 - 0x7E9ED000  c:\windows\system32\opengl32.dll
0x7EA00000 - 0x7EA3F000  c:\windows\system32\advapi32.dll
0x7EA50000 - 0x7EADA000  c:\windows\system32\gdi32.dll
0x7EAF0000 - 0x7EC20000  c:\windows\system32\user32.dll
0x7EC30000 - 0x7ECAE000  c:\windows\system32\winmm.dll
0x7EE30000 - 0x7EF37000  c:\windows\system32\KERNEL32.dll
0x7EF70000 - 0x7F000000  c:\windows\system32\ntdll.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 00751747)

00751747: 8B 5C 81 08  F6 C3 01 8D  44 81 04 75  04 85 DB 75  .\......D..u...u


Stack: 1024 bytes starting at (ESP = 0033C77C)

* = addr                                         **                       *   
0033C770: DC E4 8C 00  3C 17 75 00  DC E4 8C 00  00 00 00 00  ....<.u.........
0033C780: C4 C7 33 00  20 FA 33 00  00 00 00 00  D2 19 75 00  ..3. .3.......u.
0033C790: DC E4 8C 00  D8 C7 33 00  F9 0E 71 00  DC E4 8C 00  ......3...q.....
0033C7A0: 20 FA 33 00  00 00 00 00  A0 00 00 00  28 C8 33 00   .3.........(.3.
0033C7B0: 00 00 00 00  F0 31 00 00  08 9E 3F 09  08 DE AA 08  .....1....?.....
0033C7C0: 00 17 3E 09  30 FB 33 00  85 15 71 00  08 DE AA 08  ..>.0.3...q.....
0033C7D0: 08 9E 3F 09  08 D0 AB 08  00 00 80 3F  00 00 00 00  ..?........?....
0033C7E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 80 3F  ...............?
0033C7F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C800: 00 00 80 3F  00 00 00 00  00 00 00 00  00 00 00 00  ...?............
0033C810: 00 00 00 00  00 00 80 3F  08 DE AA 08  60 E0 E1 00  .......?....`...
0033C820: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C830: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C840: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C850: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C860: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C870: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C880: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C890: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C8A0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C8B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C8C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C8D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C8E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C8F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C900: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C910: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C920: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C930: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C940: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C950: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C960: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C970: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C980: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C990: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C9A0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C9B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C9C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C9D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C9E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033C9F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CA00: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CA10: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CA20: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CA30: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CA40: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CA50: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CA60: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CA70: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CA80: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CA90: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CAA0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CAB0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CAC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CAD0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CAE0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CAF0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CB00: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CB10: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CB20: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CB30: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CB40: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CB50: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CB60: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033CB70: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0x3
Number of Processors:   2
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        15
Processor Revision:     19202

Percent memory used:    21
Total physical memory:  2124390400
Free Memory:            1670930432
Page file:              4047691776
Total virtual memory:   2147352575

The only thing that changed between the game working and crashing is that I deleted the Cache, WTF, and Interface folders from the WoW folder as per Blizzard's instructions for resetting the UI. Any help would be greatly appreciated. Thanks!

---

### Post by Mahinva on 2008-08-15
When you first installed the game, did you include **SET gxApi "opengl"** in your Config.wtf?  If you have completely deleted your config.wtf file, it may not have been able to fill back up depending on how quick the game crashes. If your Config.wtf file is empty, you can borrow my settings that I'll include at the end of this post.

Now, if your Config.wtf file does have information in it, include **SET gxApi "opengl"** as a new line. This may take care of the crashing.

Aside, from what I have read, the GM ticket error is caused by some addons. Titan Panel seems to be one of those addons. Make sure you grab a new version of Titan Panel if that is what you use. An alternative is FuBar, found on [www.wowace.com](www.wowace.com). With some of the changes made in the last few patches of the game, addon authors have had to make changes if their addons were affected. So, it's important to update your addons, whether you do it automatically with an addon manager application or do it manually after saving bookmarks.

I really do hope this fixes the problem.

Config.wtf file - NOTE: I have included **SET gxApi "opengl"** on the 3rd last line. I also have music disabled and graphic settings are low. You may want to change the resolution on the 9th line if your monitor is not 1440x900. These settings hopefully will get the game running. I won't be around to follow up on this thread as I'll be out of town and probably without internet access. I wish you the best!

SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1440x900"
SET gxRefresh "50"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET SmallCull "0"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "50"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET expansionMovie "0"
SET realmList "us.logon.worldofwarcraft.com"
SET readTerminationWithoutNotice "-1"
SET coresDetected "2"
SET videoOptionsVersion "1"
SET lastCharacterIndex "2"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET patchlist "us.version.worldofwarcraft.com"
SET spellEffectLevel "0"
SET realmName "Moon Guard"
SET gameTip "20"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET Gamma "1.000000"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET groundEffectDist "140"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET uiScale "0.81000000238419"
SET gxWindow "1"
SET DesktopGamma "1"
SET checkAddonVersion "0"
SET scriptErrors "1"
SET mouseSpeed "1.5"
SET minimapZoom "0"
SET questFadingDisable "1"
SET showClock "0"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.40000000596046"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET weatherDensity "0"
SET rwrw "data4878"
SET horizonfarclip "400"
SET textureFilteringMode "0"
SET cameraDistanceMaxFactor "3.4"
SET profanityFilter "0"
SET guildMemberNotify "1"
SET guildRecruitmentChannel "0"
SET Sound_EnableHardware "1"
SET Sound_EnableErrorSpeech "0"
SET Sound_ZoneMusicNoDelay "1"
SET UnitNameEnemyPetName "0"
SET UnitNameEnemyCreationName "0"
SET UnitNameFriendlyPetName "0"
SET UnitNameFriendlyCreationName "0"
SET UnitNameCompanionName "0"
SET minimapInsideZoom "0"
SET Sound_NumChannels "64"
SET autoLootCorpse "1"
SET lockActionBars "1"
SET Sound_EnableSoundWhenGameIsInBG "1"
SET cameraView "0"
SET SkyCloudLOD "1"
SET accountName "ebondawn"
SET showGameTips "0"
SET autoQuestWatch "0"
SET showNewbieTips "0"
SET UberTooltips "0"
SET gxTripleBuffer "1"
SET gxMaximize "1"
SET windowResizeLock "1"
SET gxApi "opengl"
SET gxCursor "0"
SET Sound_EnableMusic "0"

---

### Post by JMuffin on 2008-08-15
It works! Don't take this the wrong way Mahinva, but I love you. I did have a config.wtf with actual content so I just added that one single line and was able to log right in. Thank you!

---

### Post by ooobuntooo on 2008-08-15
...

---

### Post by Mahinva on 2008-08-15
> **JMuffin said:**
> It works! Don't take this the wrong way Mahinva, but I love you. I did have a config.wtf with actual content so I just added that one single line and was able to log right in. Thank you!

No worries at all - I'm glad it worked! :D

Welcome back to WoW!

---

### Post by illnastyimpreza on 2009-04-22
so I just coppied and pasted that into my wtf file, and wow works PERFECT now !!! 75 FPS on ULTRA high graphics .... except I have no sound... any ideas ??

---

### Post by Zoquara on 2009-04-22
Illnasty: Turn your sounds on. He said he has music disabled.

---

### Post by illnastyimpreza on 2009-04-22
ok I got it.... don't know what I did... but my sound works now, and the game is FLYING !! thanks guys ! :)

---

### Post by 11hjpphty76lkjj on 2009-05-30
Mahinva,

You may want to edit the config output and change the line:

SET accountName "something_else"

To something else.  I'm sure you don't want everyone knowing your WoW login.. I'm pretty sure that's a security risk.

Your config works great though, thanks.

Aaron

---

