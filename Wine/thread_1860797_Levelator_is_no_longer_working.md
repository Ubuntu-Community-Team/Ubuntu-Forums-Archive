---
title: "Levelator is no longer working"
date: 2011-10-15
forum: Wine
---

### Post by wil on 2011-10-15
In 10.04 it work fine now I get the following error:


```
wil@mypc:~/.wine/drive_c/Program Files/Levelator$ wine levelator.exe wine: Unhandled page fault on read access to 0x00000400 at address 0x6876b466 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000400 in 32-bit code (0x6876b466).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:6876b466 ESP:0033f2f8 EBP:0033f528 EFLAGS:00210216(  R- --  I   -A-P- )
 EAX:001279a0 EBX:68792ff4 ECX:68779fcf EDX:00000000
 ESI:00000000 EDI:00000400
Stack dump:
0x0033f2f8:  0013a810 0015cf80 1466b66a 00000000
0x0033f308:  00000000 0015cf80 1e00d046 0015cf80
0x0033f318:  0015cf80 1e0163c8 0015cf80 0014ddf0
0x0033f328:  1e1cdfac 1e026c7e 0013a810 0033f4bb
0x0033f338:  00000000 1e1cdfac 0033f4bb 68767b50
0x0033f348:  00000000 0033f480 00000000 00000001
Backtrace:
=>0 0x6876b466 pf_printf_w+0x96() in msvcrt (0x0033f528)
  1 0x6876f3ba MSVCRT_vsnwprintf+0x79() in msvcrt (0x0033f528)
  2 0x6876fab3 MSVCRT_vswprintf+0x32() in msvcrt (0x0033f528)
  3 0x00f276a1 in wxbase28uh_vc (+0x576a0) (0x0033f528)
  4 0x0033fe90 (0x00cb0814)
0x6876b466 pf_printf_w+0x96 in msvcrt: movzwl	0x0(%edi),%eax
Modules:

```

[COLOR="black"][SIZE="2"]and with MS common controls 5.80[/SIZE][/COLOR]

```
wil@mypc:~/.wine/drive_c/Program Files/Levelator$ wine levelator.exe 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
wine: Unhandled page fault on read access to 0x00000400 at address 0x6f9c4466 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000400 in 32-bit code (0x6f9c4466).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:6f9c4466 ESP:0033d724 EBP:0033d958 EFLAGS:00210202(  R- --  I   - - - )
 EAX:001279a0 EBX:6f9ebff4 ECX:6f9d2fcf EDX:00000000
 ESI:00000000 EDI:00000400
Stack dump:
0x0033d724:  00107e04 6802a000 681919a2 6834abae
0x0033d734:  6839aff4 000036b1 68420000 0033d840
0x0033d744:  6834b317 68420000 00000001 00000002
0x0033d754:  0033d814 6831b9bd 006b65b8 00000000
0x0033d764:  0033fe90 6836fea0 00000004 6f9c0b50
0x0033d774:  00000000 0033d8ac 6827e00f 6f9ebff4
Backtrace:
=>0 0x6f9c4466 pf_printf_w+0x96() in msvcrt (0x0033d958)
  1 0x6f9c83ba MSVCRT_vsnwprintf+0x79() in msvcrt (0x0033d958)
  2 0x6f9c8ab3 MSVCRT_vswprintf+0x32() in msvcrt (0x0033d958)
  3 0x00f276a1 in wxbase28uh_vc (+0x576a0) (0x0033d958)
  4 0x0033fe90 (0x006b5ad4)
  5 0x006d0061 (0x00720067)
0x6f9c4466 pf_printf_w+0x96 in msvcrt: movzwl	0x0(%edi),%eax
Modules:

```

**To work around this bug: install vcrun2008 using Winetricks**

---

### Post by christopher.wortman on 2011-10-15
here is a solid question...

Why aren't you just using the Linux version of Levelator?

---

### Post by wil on 2011-10-16
Well Levelator for Linux requires python 2.5 which is no longer in the package repositories. Python 2.5 has not been supported since Ubuntu 10.04. Since then I was forced to use Wine and now I will have to dual boot until a solution to the problem is found.

Thanks for the reply.

---

### Post by wil on 2011-10-22
I submitted the following bug on wine.

[http://bugs.winehq.org/show_bug.cgi?id=28855](http://bugs.winehq.org/show_bug.cgi?id=28855)

---

