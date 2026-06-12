---
title: "Wine Not running anything error"
date: 2013-08-05
forum: Wine
---

### Post by rob8 on 2013-08-05
I installed Wine using ap get on Ubuntu 12.04  No matter what program i install for it to run when i run it i get the flowing error. 

wine cant find L"C:\\windows\\system32\\??.exe

?? = what ever the name of the program i am trying to run.

I have tried double clicking on the icon for the program to run and nothing happens no errors nothing. if i go to the terminal and type wine ??.exe it give me the error above.

Any ideas?

---

### Post by GwL3eNC on 2013-08-05
Hi rob8,

i'm wondering after 12 hours no one replyed to your thread. I have never had this error. We can try to find out the problem.
You said you used sudo apt-get install wine. Have you added the wine ppa or have you used the integrated thing? Also i would
like to know how you installed a application to wine and which application for example you installed. Please post the result of

 sudo dpkg -l | grep wine

which shows what wine packages you have installed.

And

ls -la | grep wine 

from your home directory ,to see if there is a hidden .wine folder

---

### Post by rob8 on 2013-08-06
> **GwL3eNC said:**
> Hi rob8,

i'm wondering after 12 hours no one replyed to your thread. I have never had this error. We can try to find out the problem.
You said you used sudo apt-get install wine. Have you added the wine ppa or have you used the integrated thing? Also i would
like to know how you installed a application to wine and which application for example you installed. Please post the result of

 sudo dpkg -l | grep wine

which shows what wine packages you have installed.

[COLOR=#006400]Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
robkiller@robkiller-server:/home$ sudo dpkg -l | grep wine
ii  wine-gecko1.4                          1.4.0-0ubuntu2                          Microsoft Windows compatibility layer (embedded web browser)
ii  wine-gecko1.4:i386                     1.4.0-0ubuntu2                          Microsoft Windows compatibility layer (embedded web browser)
ii  wine1.4                                1.4-0ubuntu4.1                          Microsoft Windows Compatibility Layer (Binary Emulator and Library)
ii  wine1.4-amd64                          1.4-0ubuntu4.1                          Microsoft Windows Compatibility Layer (64-bit support)
ii  wine1.4-common                         1.4-0ubuntu4.1                          Microsoft Windows Compatibility Layer (transitional package)
ii  wine1.4-i386:i386                      1.4-0ubuntu4.1                          Microsoft Windows Compatibility Layer (32-bit support)
ii  winetricks                             0.0+20120308                            Microsoft Windows Compatibility Layer (winetricks)
robkiller@robkiller-server:/home$ [/COLOR]


And

ls -la | grep wine 

[COLOR=#006400]nothing showed up in my home directory when i typed this in.
[/COLOR]
from your home directory ,to see if there is a hidden .wine folder

[COLOR=#006400]Thanks for helping me. I am new to ubuntu. I dont know what wine ppa is so i may not have added that. Do i need it? The programs for windows i have installed are CMS for ip cameras and Ispy for cameras. I installed them by opening the .exe file and asked wine to install them.[/COLOR]

---

### Post by GwL3eNC on 2013-08-06
Hi rob8,

you'r welcome! Nice to see you on a linux system. Shure, first steps are sometimes difficult but you can do it!

First about the meaning of ppa. Ubuntu has many programs in it that you can, what you have already found, simply
install using

sudo apt-get install applicationname.

The Versions of the shipped apps are often older ones. If you want  a newer version you
have to add a package repositorie. As you can see in your first green text, you installed wine1.4. The
newest version is wine1.6. Without a

sudo apt-add-repository ppa:ubuntu-wine/ppa

ubuntu dont knows about wine1.6. The term ppa:ubuntu-wine/ppa i found by googleing about wine ppa. 
Every program has a ppa, i believe.

That there is no hidden .wine folder in your home is odd. There is something wrong.

I think we should first try the installation of the newest version. 

1. sudo apt-add-repository ppa:ubuntu-wine/ppa
2. sudo apt-get update
3. sudo apt-get install wine1.6

After that try installation the windows application and starting it like you did before. Hope it takes you further.
And, you can get help about every command if you type it's appname --help or man appname. In example

apt-add-repository --help
man apt-add-repository

Ps: To see if your windows apps are supported by wine you should ever first visit [http://www.winehq.org/](http://www.winehq.org/)
and read the information about your app.

---

### Post by CatKiller on 2013-08-06
> **rob8 said:**
> 
wine cant find L"C:\\windows\\system32\\??.exe

?? = what ever the name of the program i am trying to run.

You need to be in the same place as the file you're trying to run (using cd path/to/file before running it) or direct Wine to the appropriate place (with wine /path/to/file/program.exe). It's not a mind reader.

Also, most things don't work in Wine. Check Wine HQ's AppDB for the programs you're interested in.

---

### Post by GwL3eNC on 2013-08-06
Hi CatKiller,

thanks. i will try to improve.

---

### Post by rob8 on 2013-08-06
Ok i updated Wine. I reinstalled CMS which is on the list of working apps on the WINE database. I am not sure what files i am looking for to know what directory i need to be in to run CMS. I tried to use the cd path/to/CSM.exe before running it and wine /path/to/file/CSM.exe with no results.

I get the same error

wine cant find L"C:\\windows\\system32\\??.exe

?? = what ever the name of the program i am trying to run.

---

### Post by GwL3eNC on 2013-08-06
hi rob8,

you can try a filesearch with dolphin to find the path of csm.exe (Edit->Search). Go to this location using
cd command and try again wine csm.exe. Or possibly right click the exe in dolphin and select open with wine.

I dont know how to tell you about the path thing.  

find /home/YOURUSERNAME -name csm.exe

you can try. You have to replace YOURUSERNANE with the name you use on the computer. Dont copy the
command simply.

Please try to read [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
Only the chapter about file and directory commands.

---

### Post by CatKiller on 2013-08-06
> **rob8 said:**
> Ok i updated Wine. I reinstalled CMS which is on the list of working apps on the WINE database. I am not sure what files i am looking for to know what directory i need to be in to run CMS. I tried to use the cd path/to/CSM.exe before running it and wine /path/to/file/CSM.exe with no results.

The only program I found called CMS was rated as Garbage.

The path will be something like ~/.wine/drive_c/Program\ Files/... something something. Wherever you told it to install, basically. Also, you've called the program CMS but then referred to the executable as CSM.exe. You'll need to know which one it's supposed to be, and also whether it's supposed to have capital letters. You can use Tab-completion to help guard against those kinds of typos.

---

### Post by rob8 on 2013-08-07
ok so i was able to get CMS to start i had to install a dll files using winetricks. It worked and i got to the login screen and was able to login. I however received an error after that that said the program was going to have to shut down. I attached the log file to see if anyone has any clue as to what is wrong. 

Also i am using CMS because i have no other program to run on Ubuntu[ATTACH]245147[/ATTACH] to record multiple cameras. I tried zoneminder but i cant get it to work with my cameras. So i am left with this one unless someone knows of a better program for unbutu that i can run ip cameras on and record?
[ATTACH]245147[/ATTACH]

---

### Post by rob8 on 2013-08-07
This is the log from the terminal if this helps any

[email]robkiller@robkiller-server:~/.wine[/email]/drive_c/CMS$ wine CMS.exe
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000001 not handled
fixme:win:EnumDisplayDevicesW ((null),0,0x32f3b8,0x00000000), stub!
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
err:winsock:interface_bind Failed to bind to interface, receiving broadcast packets will not work on socket 0524.
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (_WSAIOW(IOC_WS2, 9))
err:winsock:interface_bind Failed to bind to interface, receiving broadcast packets will not work on socket 0528.
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (_WSAIOW(IOC_WS2, 9))
fixme:winsock:WSAJoinLeaf stub.
fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit [http://ubuntuforums.org/showthread.php?t=1960599](http://ubuntuforums.org/showthread.php?t=1960599)
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000005 not handled
fixme:win:EnumDisplayDevicesW ((null),0,0x2cf488,0x00000000), stub!
err:listview:LISTVIEW_WindowProc unknown msg 1044 wp=00000000 lp=002cf958
wine: Unhandled page fault on read access to 0x00000004 at address 0x5f4159c7 (thread 0009), starting debugger...

---

### Post by GwL3eNC on 2013-08-07
Hi rob8,

i'm sorry that i couldn't help you getting your app work. I dont know such programs you looking for.
For this question you should make a new thread.

The file gnome-keyring-pkcs11.so is in a package called

[TABLE]
[TR]
[TD="class: file"][/TD]
[TD]                   [libp11-kit-gnome-keyring]("http://packages.ubuntu.com/raring/libp11-kit-gnome-keyring")[/TD]
[/TR]
[/TABLE]
  
But i'm not shure understandig that message. Is that package installed?

Good luck!

---

### Post by chhailu on 2013-08-09
i install photoshop cs 2 on ubuntu 12.04 by wine but when i start photoshop then comes message 'unable to continue because of a hardware or system error but this error is unrecoverable'
plz tell me solution

---

