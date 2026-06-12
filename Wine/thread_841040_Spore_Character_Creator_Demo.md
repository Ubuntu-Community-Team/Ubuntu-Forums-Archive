---
title: "Spore Character Creator Demo"
date: 2008-06-26
forum: Wine
---

### Post by siegeszug on 2008-06-26
Hi, I'm an Ubuntu newbie that tries to get random games to work in Wine.  Today's challenge has been getting the Spore Character Creator Demo to work under Wine, but I can't even get the game to come up.  When I run it from terminal, it stalls.  When I run it from the icon it makes on the desktop, the screen goes all black, the mouse cursor pops up, and then it crashes and goes back to desktop.  Here's the Exception Report it poops out when I run it:

[Build info]



[System info]

Computer name: [CENSORED]
User name: [CENSORED]
EA_PLATFORM: Windows on X86

OS name: Windows XP

OS version number: 5.1.2600

OS service pack: Service Pack 2

Debugger present: no

CPU count: 2

Processor type: x86

Processor level: 15

Processor revision: 17155

Memory load: 16%

Total physical memory: 2027 Mb

Available physical memory: 1699 Mb

Total page file memory: 4984 Mb

Available page file memory: 4656 Mb

Total virtual memory: 2047 Mb

Free virtual memory: 2047 Mb



[Application info]

Language: C++

Compiler: Microsoft Visual C++ compiler, version 1310

App path: C:\Program Files\Electronic Arts\SPORE\Sporebin\SporeCreatureCreator.exe

App version: 0.0.0.1112



[Exception info]

date: 06-25-08

time: 18.17.25

type: ACCESS_VIOLATION reading address 0x00000000

address: 0x7dc70350 <unknown module>



[Call stack]

Callstack not available



[Stack data]

7f619dd0 | 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 | ................ |

7f619de0 | 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 | ................ |

7f619df0 | 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 | ................ |

7f619e00 | 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 | ................ |

7f619e10 | 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 | ................ |

7f619e20 | 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 | ................ |

7f619e30 | 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 | ................ |

7f619e40 | 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 | ................ |

7f619e50 | 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 | ................ |

7f619e60 | 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 | ................ |

7f619e70 | 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 | ................ |

7f619e80 | 05 00 00 c0 00 00 00 00 00 00 00 00 50 03 c7 7d | ............P..} |

7f619e90 | 02 00 00 00 00 00 00 00 00 00 00 00 08 5f ea 11 | ............._.. |

7f619ea0 | a0 04 14 7c 05 00 00 00 05 00 00 00 40 9f 61 7f | ...|........@.a. |

7f619eb0 | e1 80 00 00 e4 02 61 7d 80 b2 4b 7c cc 9e 61 7f | ......a}..K|..a. |

7f619ec0 | 01 00 00 00 00 00 00 00 40 60 4b 7c 01 00 00 00 | ........@`K|.... |

7f619ed0 | 40 60 4b 7c 63 61 b0 7d<00>cd 1e 7d 00 00 00 00 | @`K|ca.}...}.... |

7f619ee0 | 08 68 4b 7c 10 9f 61 7f 00 00 00 00 00 00 00 00 | .hK|..a......... |

7f619ef0 | 00 00 00 00 00 00 00 00 48 a0 61 7f 00 00 00 00 | ........H.a..... |

7f619f00 | 00 00 00 00 73 fe 94 7d 00 cd 1e 7d 00 00 00 00 | ....s..}...}.... |

7f619f10 | 00 02 00 00 00 00 00 00 00 1f 5e 00 80 4f c5 7d | ..........^..O.} |

7f619f20 | 00 04 40 00 78 05 b1 7d 00 10 4a 7c 08 20 32 00 | ..@.x..}..J|. 2. |

7f619f30 | fc 01 00 00 00 02 00 00 fc 01 00 00 00 02 00 00 | ................ |

7f619f40 | 00 00 00 00 00 00 00 00 80 00 00 00 80 00 00 00 | ................ |

7f619f50 | 80 0c 00 00 00 cd 1e 7d 00 00 00 00 00 02 00 00 | .......}........ |

7f619f60 | 00 10 4a 7c 8b dc b0 7d 00 10 4a 7c 48 a0 61 7f | ..J|...}..J|H.a. |

7f619f70 | 01 00 00 00 00 dc 5d 7d 00 cd 1e 7d 00 02 00 00 | ......]}...}.... |

7f619f80 | 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 | ................ |

7f619f90 | bf a3 61 7f 09 00 00 00 40 00 00 00 00 00 00 00 | ..a.....@....... |

7f619fa0 | 02 00 00 00 00 00 00 00 20 03 00 00 58 02 00 00 | ........ ...X... |

7f619fb0 | 80 00 00 00 38 73 1d 7c 90 c1 dc 00 01 00 00 00 | ....8s.|........ |

7f619fc0 | 00 00 00 00 01 14 00 00 88 24 71 2a 04 00 00 00 | .........$q*.... |

7f619fd0 | 00 dc 5d 7d 08 20 32 7d 00 00 00 00 00 00 00 00 | ..]}. 2}........ |



[Instruction data]

7dc702d0 => DasmX86Dll.dll not found. 



[Registers]

eip: 7dc70350

eax: 00000008

ebx: 00000200

ecx: 00000000

edx: 7d1ecd00

esi: 00000000

edi: 7d1ecd00

ebp: 00000200

efl: 00010246

esp: 7f619ed8



[Modules]

base 0x00400000 size 0x016ae000 entry 0x00000000 "SporeCreatureCreator.exe"                       "C:\Program Files\Electronic Arts\SPORE\Sporebin\SporeCreatureCreator.exe

base 0x7bc10000 size 0x00095000 entry 0x7bc77320 "ntdll.dll"                                      "c:\windows\system32\ntdll.dll

base 0x7b820000 size 0x0010c000 entry 0x7b8a1db0 "KERNEL32.dll"                                   "c:\windows\system32\KERNEL32.dll

base 0x7ed60000 size 0x00129000 entry 0x7ee13660 "user32.dll"                                     "c:\windows\system32\user32.dll

base 0x7ecc0000 size 0x00083000 entry 0x7ed1c3f0 "gdi32.dll"                                      "c:\windows\system32\gdi32.dll

base 0x7ec60000 size 0x00048000 entry 0x7ec99ca0 "advapi32.dll"                                   "c:\windows\system32\advapi32.dll

base 0x7c340000 size 0x00056000 entry 0x7c34229f "MSVCR71.dll"                                    "C:\Program Files\Electronic Arts\SPORE\Sporebin\MSVCR71.dll

base 0x7ec40000 size 0x00017000 entry 0x7ec51890 "dinput8.dll"                                    "c:\windows\system32\dinput8.dll

base 0x7ec10000 size 0x0002f000 entry 0x7ec32700 "dinput.dll"                                     "c:\windows\system32\dinput.dll

base 0x7eb70000 size 0x00098000 entry 0x7ebe88e0 "ole32.dll"                                      "c:\windows\system32\ole32.dll

base 0x7eb10000 size 0x00054000 entry 0x7eb50d20 "rpcrt4.dll"                                     "c:\windows\system32\rpcrt4.dll

base 0x7eaf0000 size 0x00014000 entry 0x7eb002a0 "iphlpapi.dll"                                   "c:\windows\system32\iphlpapi.dll

base 0x7eab0000 size 0x00014000 entry 0x7eabf260 "imm32.dll"                                      "c:\windows\system32\imm32.dll

base 0x7ea90000 size 0x00015000 entry 0x7eaa32d0 "version.dll"                                    "c:\windows\system32\version.dll

base 0x7ea80000 size 0x0000c000 entry 0x7ea89e60 "lz32.dll"                                       "c:\windows\system32\lz32.dll

base 0x7ea60000 size 0x00018000 entry 0x7ea70ff0 "d3dx9_27.dll"                                   "c:\windows\system32\d3dx9_27.dll

base 0x7ea50000 size 0x0000f000 entry 0x7ea57890 "d3dx9_36.dll"                                   "c:\windows\system32\d3dx9_36.dll

base 0x7ea30000 size 0x00012000 entry 0x7ea3ba50 "d3dx8.dll"                                      "c:\windows\system32\d3dx8.dll

base 0x7ea00000 size 0x00023000 entry 0x7ea1c6b0 "ws2_32.dll"                                     "c:\windows\system32\ws2_32.dll

base 0x7e9e0000 size 0x00017000 entry 0x7e9f4200 "usp10.dll"                                      "c:\windows\system32\usp10.dll

base 0x7e9a0000 size 0x0003f000 entry 0x7e9d00b0 "dbghelp.dll"                                    "c:\windows\system32\dbghelp.dll

base 0x7e990000 size 0x00005000 entry 0x7e9930a0 "psapi.dll"                                      "c:\windows\system32\psapi.dll

base 0x7e940000 size 0x00040000 entry 0x7e970de0 "dsound.dll"                                     "c:\windows\system32\dsound.dll

base 0x7e8b0000 size 0x00086000 entry 0x7e8e5e60 "winmm.dll"                                      "c:\windows\system32\winmm.dll

base 0x7e7b0000 size 0x000f8000 entry 0x7e817260 "shell32.dll"                                    "c:\windows\system32\shell32.dll

base 0x7e750000 size 0x0004e000 entry 0x7e78b2f0 "shlwapi.dll"                                    "c:\windows\system32\shlwapi.dll

base 0x7e690000 size 0x000b5000 entry 0x7e722e10 "comctl32.dll"                                   "c:\windows\system32\comctl32.dll

base 0x7e660000 size 0x00026000 entry 0x7e67cf90 "d3d9.dll"                                       "c:\windows\system32\d3d9.dll

base 0x7e570000 size 0x000e6000 entry 0x7e626ed0 "wined3d.dll"                                    "c:\windows\system32\wined3d.dll

base 0x7e540000 size 0x00015000 entry 0x7e54e750 "wsock32.dll"                                    "c:\windows\system32\wsock32.dll

base 0x7e3a0000 size 0x00081000 entry 0x7e404e50 "winex11.drv"                                    "c:\windows\system32\winex11.drv

base 0x7e200000 size 0x00023000 entry 0x7e2196c0 "winealsa.drv"                                   "c:\windows\system32\winealsa.drv

base 0x7e110000 size 0x0000b000 entry 0x7e1194c0 "msacm32.drv"                                    "c:\windows\system32\msacm32.drv

base 0x7e0e0000 size 0x00024000 entry 0x7e0fdd80 "msacm32.dll"                                    "c:\windows\system32\msacm32.dll

base 0x7e0d0000 size 0x0000e000 entry 0x7e0dc800 "midimap.dll"                                    "c:\windows\system32\midimap.dll

base 0x7e0a0000 size 0x0002a000 entry 0x7e0b9280 "uxtheme.dll"                                    "c:\windows\system32\uxtheme.dll

base 0x7c510000 size 0x0000e000 entry 0x7c51a2a0 "rasapi32.dll"                                   "c:\windows\system32\rasapi32.dll



[Register memory]

ebx 00000200 |<??>?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? | ???????????????? |

    00000210 | ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? | ???????????????? |

edx 7d1ecd00 |<??>?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? | ???????????????? |

    7d1ecd10 | ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? | ???????????????? |

edi 7d1ecd00 |<??>?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? | ???????????????? |

    7d1ecd10 | ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? | ???????????????? |

ebp 00000200 |<??>?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? | ???????????????? |

    00000210 | ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? ?? | ???????????????? |



[Extra]

<none>



Thanks!

---

### Post by cogadh on 2008-06-26
The Creature Creator does not work in Wine (yet) due to the copy protection on it:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12614](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12614)

The demo version only partially works:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12558](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12558)

---

### Post by ghoti2007 on 2008-06-27
I've been working on these trying to get them both to work (both the retail and the demo) but have gotten as far as you in almost all cases.

I submitted both bugs with wine (copy protection AND the UI drawing problem) but it seems there just isn't much interest in getting these two to work.

If anyone here has any ideas, I'm open to em.  Even the demo working would be an improvement over what I have now.

---

