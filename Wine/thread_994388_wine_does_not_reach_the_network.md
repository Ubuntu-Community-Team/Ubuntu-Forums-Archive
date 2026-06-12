---
title: "wine does not reach the network"
date: 2008-11-26
forum: Wine
---

### Post by izar on 2008-11-26
my problem is that wine does not reach the network 

the history of the problem: 
[INDENT]{ 
i have recently installed a clean coppy of ubuntu 8.10 64bit. 
i installed through wine a program that has netHASP protection (meaning that it needs to call the network server in order to work) (the program is called responsa)
the installation went without problems 
at first i couldn't run the program because and i found out it was missing sum DLLs. 
i copied those from the installed folder on my windows partition. 
then i tried running the program again and i got an error from the HASP 
[my friend ran this program successfully on ubuntu 8.10 32bit, and he didn't find any reason that it shouldn't work on my pc]
}[/INDENT]
i tried a few more things which led me to the thought that my wine can't reach the network.
[I can reach the network perfectly through samba]
>>> I must state that I have also installed IE4linux and it doesn't have any problems connecting to the Internet <<<

to test if this analysis is correct I tried using the commands 'ping' 'telnet' and 'ipconfig' through wine.
(we had to copy the .exe files from windows and also some DLL files)

this is the output from the terminal:
```
avi@avi-laptop:~$ wine cmd 
Warning: could not find DOS drive for current working directory '/home/avi', starting in the Windows directory. 
CMD Version 1.0.1 

C:\windows>cd.. 
C:\>ipconfig 
fixme:advapi:RegisterTraceGuidsW 0x7081f765 0x7082f140 0x70801458 1 0x33fd30 (null) (null) 0x7082f148 
fixme:advapi:RegisterTraceGuidsW 0x6d4e8600 0x6d4fb0a0 0x6d4e13c8 1 0x33fd30 (null) (null) 0x6d4fb0a8 
fixme:heap:HeapSetInformation (nil) 1 (nil) 0 
wine: Call from 0x1001d8a to unimplemented function IPHLPAPI.DLL.GetAdaptersAddresses, aborting 
wine: Call from 0x1004ccc to unimplemented function msvcrt.dll._except_handler4_common, aborting 
wine: Call from 0x1004ccc to unimplemented function msvcrt.dll._except_handler4_common, aborting 
wine: Call from 0x1004ccc to unimplemented function msvcrt.dll._except_handler4_common, aborting 
wine: Call from 0x1004ccc to unimplemented function msvcrt.dll._except_handler4_common, aborting 
wine: Call from 0x1004ccc to unimplemented function msvcrt.dll._except_handler4_common, aborting 
```

this line repeats hundreds of times then i get:
```
err:seh:setup_exception_record stack overflow 1984 bytes in thread 0019 eip f7c7cc83 esp 00240b70 stack 0x240000-0x241000-0x340000
```

(the same exact output is given when I type:
 avi@avi-laptop:~$ wine C:\\ipconfig.exe )

a similar error is given when running the command “telnet”
ping gives me:
```

avi@avi-laptop:~$ wine C:\\ping 
Warning: could not find DOS drive for current working directory '/home/avi', starting in the Windows directory. 
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
``` 

I tried reinstalling wine, didn't help.

what is your solution?

Thanx for your help
(if I cant get this program running I'll need to return back to the old dumb windows.)

****************
Ubuntu 8.10 amd64 
dual boot with winVista 
amd athlon x2 processor 
1Gb RAM 
wine vr. 1.0.1

---

### Post by hikaricore on 2008-11-26
If Internet Explorer is working it is doing so under WINE so your issue is not what you think.
I can almost certainly tell you that neither ipconfig nor telnet will run under WINE in "cmd" mode.
This is by all means not a stupid idea of how to test, but in reality it's not any good.

I have to say I suspect what ever software you are trying to use is the issue.
Try a few other programs under WINE such as utorrent, the windows version of putty, or an online game and let me know what happens.

Another idea would be to boot up a 32bit Ubuntu livecd, install WINE in the live environment and test your program there, you may find that the issue is with your 64bit OS.
Is there a certain reason that you need to be running a 64bit kernel?
IMHO unless you have over 4Gb of ram, do realtime video or sound editing, or have a specialized field that requires it... you're better off with 32bit.

---

### Post by izar on 2008-11-29
thanks for the quick answer.
Your assessment seems logical
i thought about trying a live cd but the installation requires nearly 500 Mb and i have only 1Gb RAM. is there a way i can use area on the hard disk when im working with a live cd?
about the 64-32 bit question: i don't have any special reason to use 64bit beside the fact that my processor is designed that way.
Ill try utorrent as you suggest and i'll let you know the results

---

### Post by izar on 2008-11-30
utorrent works!
do you have an answer to my othet questions or do i need to look it up by my own?

---

### Post by izar on 2008-11-30
sorry posted this by mistake, cant delete

---

### Post by hikaricore on 2008-11-30
I think the live CD can use a swap partition, but afaik there's no way for it to use your whole drive for such a purpose.

---

### Post by izar on 2008-12-01
i tried a kubuntu 8.10 i386 live cd.
the results were the same as before:
insalled wine
installed responsa (i mounted a folder from my ubuntu partition as "e:" in wine and installed there)
tried running responsa. it started and before the GUI was up it aborted
i ran it through terminal. said some dll's are missing. 
i copied theme from windows partiton and ran the program again
this time i got the messege: "no answer from netHASP license manager"
i rechecked (out of wine) that the hasp port is available
ran through terminal. output:
```
avi@avi-laptop:~$ env WINEPREFIX="/home/avi/.wine" wine "C:\PROG~FBU\RESP~MT1\RESPONSA.EXE" &
[1] 6861
avi@avi-laptop:~$ Warning: could not find DOS drive for current working directory '/home/avi', starting in the Windows directory.
fixme:wtsapi:WTSQuerySessionInformationA Stub (nil) 0xffffffff 4 0x32fbd8 0x32fbcc

```
(i copied this from my installed ubuntu which i am using right now, but it showed the same thing on the live cd)

any other suggestions?

---

