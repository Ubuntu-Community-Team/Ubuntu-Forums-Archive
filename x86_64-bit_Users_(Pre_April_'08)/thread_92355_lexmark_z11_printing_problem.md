---
title: "lexmark z11 printing problem"
date: 2005-11-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by burnhamd on 2005-11-19
I like everything about Ubuntu except I cant get my printer to work. (The only reason I dont remove Windows).
I downloaded the lz11 driver from sourceforge and put the ppd in usr/share/cups/model/  I tried setting it up using the graphical utility in system-admin but it doesnt print a test page.  Then I read that I had to run the install script but the thing doesnt compile 
  The errors are:
```
------------------------------------------------------------------
ERROR while compiling the program!
The program could not be compiled.
the log file reads:


gcc -c -Wall cZ11-V2.c -O3 -DDEBUG=
cZ11-V2.c:75:19: error: stdio.h: No such file or directory
cZ11-V2.c:76:20: error: stdlib.h: No such file or directory
cZ11-V2.c:77:20: error: string.h: No such file or directory
In file included from /usr/lib/gcc/x86_64-linux-gnu/4.0.2/include/syslimits.h:7,                 from /usr/lib/gcc/x86_64-linux-gnu/4.0.2/include/limits.h:11,
                 from cZ11-V2.c:78:
/usr/lib/gcc/x86_64-linux-gnu/4.0.2/include/limits.h:122:61: error: limits.h: No such file or directory
cZ11-V2.c:79:20: error: malloc.h: No such file or directory
cZ11-V2.c: In function ‘WidthCMYKtoBIT’:
cZ11-V2.c:531: warning: implicit declaration of function ‘rand’
cZ11-V2.c:531: error: ‘RAND_MAX’ undeclared (first use in this function)
cZ11-V2.c:531: error: (Each undeclared identifier is reported only once
cZ11-V2.c:531: error: for each function it appears in.)
cZ11-V2.c: In function ‘WidthRGBtoBIT’:
cZ11-V2.c:584: error: ‘RAND_MAX’ undeclared (first use in this function)
cZ11-V2.c: In function ‘InitDataPipe’:
cZ11-V2.c:620: warning: implicit declaration of function ‘memset’
cZ11-V2.c:620: warning: incompatible implicit declaration of built-in function ‘memset’
cZ11-V2.c:706: warning: implicit declaration of function ‘malloc’
cZ11-V2.c:706: warning: incompatible implicit declaration of built-in function ‘malloc’
cZ11-V2.c: At top level:
cZ11-V2.c:724: error: syntax error before ‘FILE’
cZ11-V2.c: In function ‘ReadDataPipe’:
cZ11-V2.c:727: error: ‘p’ undeclared (first use in this function)
cZ11-V2.c:738: warning: implicit declaration of function ‘fread’
cZ11-V2.c:738: error: ‘in’ undeclared (first use in this function)
cZ11-V2.c:739: warning: implicit declaration of function ‘getc’
cZ11-V2.c:739: error: ‘EOF’ undeclared (first use in this function)
cZ11-V2.c:755: error: ‘fDiscardContents’ undeclared (first use in this function)cZ11-V2.c:764: error: ‘fUnget’ undeclared (first use in this function)
cZ11-V2.c: At top level:
cZ11-V2.c:793: error: syntax error before ‘FILE’
cZ11-V2.c: In function ‘EndPage’:
cZ11-V2.c:795: error: ‘p’ undeclared (first use in this function)
cZ11-V2.c:795: error: ‘in’ undeclared (first use in this function)
cZ11-V2.c: At top level:
cZ11-V2.c:809: error: syntax error before ‘FILE’
cZ11-V2.c: In function ‘IsDataPipeEmpty’:
cZ11-V2.c:811: error: ‘p’ undeclared (first use in this function)
cZ11-V2.c:811: error: ‘in’ undeclared (first use in this function)
cZ11-V2.c: At top level:
cZ11-V2.c:820: error: syntax error before ‘FILE’
cZ11-V2.c: In function ‘GetNextLine’:
cZ11-V2.c:822: error: ‘p’ undeclared (first use in this function)
cZ11-V2.c:830: error: ‘in’ undeclared (first use in this function)
cZ11-V2.c: In function ‘StartRndLine’:
cZ11-V2.c:878: error: ‘RAND_MAX’ undeclared (first use in this function)
cZ11-V2.c: In function ‘FinishDataPipe’:
cZ11-V2.c:981: warning: implicit declaration of function ‘free’
cZ11-V2.c:982: warning: incompatible implicit declaration of built-in function ‘memset’
cZ11-V2.c: In function ‘ClearBuffer’:
cZ11-V2.c:996: warning: incompatible implicit declaration of built-in function ‘memset’
cZ11-V2.c: In function ‘SweepBufferInit’:
cZ11-V2.c:1012: warning: incompatible implicit declaration of built-in function ‘malloc’
cZ11-V2.c: At top level:
cZ11-V2.c:1034: error: syntax error before ‘*’ token
cZ11-V2.c: In function ‘fPutLString’:
cZ11-V2.c:1036: warning: implicit declaration of function ‘fwrite’
cZ11-V2.c:1036: warning: incompatible implicit declaration of built-in function ‘fwrite’
cZ11-V2.c:1036: error: ‘data’ undeclared (first use in this function)
cZ11-V2.c:1036: error: ‘out’ undeclared (first use in this function)
cZ11-V2.c: At top level:
cZ11-V2.c:1043: error: syntax error before ‘*’ token
cZ11-V2.c: In function ‘LexMove’:
cZ11-V2.c:1049: error: ‘pixel’ undeclared (first use in this function)
cZ11-V2.c:1052: error: ‘out’ undeclared (first use in this function)
cZ11-V2.c: At top level:
cZ11-V2.c:1059: error: syntax error before ‘*’ token
cZ11-V2.c: In function ‘LexInit’:
cZ11-V2.c:1061: warning: incompatible implicit declaration of built-in function ‘fwrite’
cZ11-V2.c:1061: error: ‘out’ undeclared (first use in this function)
cZ11-V2.c: At top level:
cZ11-V2.c:1068: error: syntax error before ‘*’ token
cZ11-V2.c: In function ‘LexEOP’:
cZ11-V2.c:1075: error: ‘out’ undeclared (first use in this function)
cZ11-V2.c: At top level:
cZ11-V2.c:1165: error: syntax error before ‘FILE’
cZ11-V2.c: In function ‘PrintSweep’:
cZ11-V2.c:1176: error: ‘sweep’ undeclared (first use in this function)
cZ11-V2.c:1191: warning: incompatible implicit declaration of built-in function ‘malloc’
cZ11-V2.c:1192: warning: incompatible implicit declaration of built-in function ‘memset’
cZ11-V2.c:1212: error: ‘lineDrive’ undeclared (first use in this function)
cZ11-V2.c:1220: error: ‘emptyLines’ undeclared (first use in this function)
cZ11-V2.c:1221: error: ‘out’ undeclared (first use in this function)
cZ11-V2.c:1225: warning: incompatible implicit declaration of built-in function ‘fwrite’
cZ11-V2.c: At top level:
cZ11-V2.c:1240: error: syntax error before ‘FILE’
cZ11-V2.c: In function ‘PrintBWSweep’:
cZ11-V2.c:1246: error: ‘emptyLines’ undeclared (first use in this function)
cZ11-V2.c:1247: error: ‘sweep’ undeclared (first use in this function)
cZ11-V2.c:1247: error: ‘out’ undeclared (first use in this function)
cZ11-V2.c:1247: error: ‘lineDrive’ undeclared (first use in this function)
cZ11-V2.c: At top level:
cZ11-V2.c:1342: error: syntax error before ‘*’ token
cZ11-V2.c: In function ‘LexPrintCMYK’:
cZ11-V2.c:1362: error: ‘pParam’ undeclared (first use in this function)
cZ11-V2.c:1382: error: ‘in’ undeclared (first use in this function)
cZ11-V2.c:1392: error: ‘out’ undeclared (first use in this function)
cZ11-V2.c:1561: warning: implicit declaration of function ‘fprintf’
cZ11-V2.c:1561: warning: incompatible implicit declaration of built-in function ‘fprintf’
cZ11-V2.c:1561: error: ‘stderr’ undeclared (first use in this function)
cZ11-V2.c: At top level:
cZ11-V2.c:1598: error: syntax error before ‘*’ token
cZ11-V2.c: In function ‘LexPrintK’:
cZ11-V2.c:1610: error: ‘pParam’ undeclared (first use in this function)
cZ11-V2.c:1616: error: ‘in’ undeclared (first use in this function)
cZ11-V2.c:1626: error: ‘out’ undeclared (first use in this function)
cZ11-V2.c:1735: warning: incompatible implicit declaration of built-in function ‘fprintf’
cZ11-V2.c:1735: error: ‘stderr’ undeclared (first use in this function)
cZ11-V2.c: At top level:
cZ11-V2.c:1756: error: syntax error before ‘*’ token
cZ11-V2.c: In function ‘LexPrintKAdjust’:
cZ11-V2.c:1774: error: ‘out’ undeclared (first use in this function)
cZ11-V2.c:1857: warning: implicit declaration of function ‘sprintf’
cZ11-V2.c:1857: warning: incompatible implicit declaration of built-in function ‘sprintf’
cZ11-V2.c:1858: warning: implicit declaration of function ‘strlen’
cZ11-V2.c:1858: warning: incompatible implicit declaration of built-in function ‘strlen’
cZ11-V2.c:1899: error: ‘in’ undeclared (first use in this function)
cZ11-V2.c:1899: error: ‘EOF’ undeclared (first use in this function)
cZ11-V2.c: In function ‘DecodeOption’:
cZ11-V2.c:1940: warning: incompatible implicit declaration of built-in function ‘strlen’
cZ11-V2.c:1941: warning: implicit declaration of function ‘strncmp’
cZ11-V2.c: In function ‘DecodeColorDithering’:
cZ11-V2.c:2045: warning: implicit declaration of function ‘strcmp’
cZ11-V2.c: In function ‘PrintHelp’:
cZ11-V2.c:2173: warning: incompatible implicit declaration of built-in function ‘fprintf’
cZ11-V2.c:2173: error: ‘stderr’ undeclared (first use in this function)
cZ11-V2.c:2178: warning: implicit declaration of function ‘exit’
cZ11-V2.c:2178: warning: incompatible implicit declaration of built-in function ‘exit’
cZ11-V2.c: In function ‘PrintVersion’:
cZ11-V2.c:2187: warning: incompatible implicit declaration of built-in function ‘fprintf’
cZ11-V2.c:2187: error: ‘stderr’ undeclared (first use in this function)
cZ11-V2.c:2188: warning: incompatible implicit declaration of built-in function ‘exit’
cZ11-V2.c: In function ‘InvalidInvokation’:
cZ11-V2.c:2198: warning: incompatible implicit declaration of built-in function ‘fprintf’
cZ11-V2.c:2198: error: ‘stderr’ undeclared (first use in this function)
cZ11-V2.c: In function ‘ConflictingInvokation’:
cZ11-V2.c:2209: warning: incompatible implicit declaration of built-in function ‘fprintf’
cZ11-V2.c:2209: error: ‘stderr’ undeclared (first use in this function)
cZ11-V2.c: In function ‘DuplicateInvokation’:
cZ11-V2.c:2221: warning: incompatible implicit declaration of built-in function ‘fprintf’
cZ11-V2.c:2221: error: ‘stderr’ undeclared (first use in this function)
cZ11-V2.c: In function ‘IncompleteInvokation’:
cZ11-V2.c:2233: warning: incompatible implicit declaration of built-in function ‘fprintf’
cZ11-V2.c:2233: error: ‘stderr’ undeclared (first use in this function)
cZ11-V2.c: In function ‘IgnoringParameter’:
cZ11-V2.c:2244: warning: incompatible implicit declaration of built-in function ‘fprintf’
cZ11-V2.c:2244: error: ‘stderr’ undeclared (first use in this function)
cZ11-V2.c: In function ‘main’:
cZ11-V2.c:2471: error: ‘FILE’ undeclared (first use in this function)
cZ11-V2.c:2471: error: ‘InputFile’ undeclared (first use in this function)
cZ11-V2.c:2472: error: ‘OutPutFile’ undeclared (first use in this function)
cZ11-V2.c:2488: error: ‘stdin’ undeclared (first use in this function)
cZ11-V2.c:2489: error: ‘stdout’ undeclared (first use in this function)
cZ11-V2.c:2508: warning: implicit declaration of function ‘fclose’
make: *** [cZ11-V2.o] Error 1
-----------------------------------------------------------------
```
can anyone help

---

### Post by bonzodog on 2005-11-19
lexmark printers...
It looks like you don't have the development environment installed. 
do a sudo apt-get install build-essential
then try it again.

---

