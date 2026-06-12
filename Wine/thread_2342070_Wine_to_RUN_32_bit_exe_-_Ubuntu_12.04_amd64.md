---
title: "Wine to RUN 32 bit exe - Ubuntu 12.04 amd64"
date: 2016-11-03
forum: Wine
---

### Post by tousios on 2016-11-03
I have been trying to install mt4 unsuccessfully. Although I have created the necessary 32 bit prefix directory which can be seen under > "home/username/Home/wine32Bit when I use the command ```
wine notepad.exe
```  I get the following error:

> wine: WINEARCH set to win32 but 'home/username/ .wine' is a 64-bit installation.


In an attempt to run an mt4 32 bit executable file by typing the following command 

```
WINEPREFIX=~/ .wine32Bit wine 'home/username/Downloads/mt4setup.exe'
```


I also received this error:

> .wine32Bit: command not found


Having unistalled and re-installed wine and winetricks multiple times but I have a feeling that I am missing some important files as when I run the ```
~/ .wine32
``` command I get the following:

[FONT=arial]> 
bash: /home/username/: Is a directory[/FONT]> 
[FONT=arial]username@Name:~$ WINEPREFIX="$HOME/prefix32" WINEARCH=win32 wine wineboot[/FONT]
[FONT=arial]wine: created the configuration directory '/home/username/prefix32'[/FONT]
[FONT=arial]p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory[/FONT]
[FONT=arial]p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory[/FONT]
[FONT=arial]fixme:storage:create_storagefile Storage share mode not implemented.[/FONT]
[FONT=arial]err:mscoree:LoadLibraryShim error reading registry key for installroot[/FONT]
[FONT=arial]err:mscoree:LoadLibraryShim error reading registry key for installroot[/FONT]
[FONT=arial]err:mscoree:LoadLibraryShim error reading registry key for installroot[/FONT]
[FONT=arial]err:mscoree:LoadLibraryShim error reading registry key for installroot[/FONT]
[FONT=arial]err:mscoree:LoadLibraryShim error reading registry key for installroot[/FONT]
[FONT=arial]err:mscoree:LoadLibraryShim error reading registry key for installroot[/FONT]
[FONT=arial]fixme:iphlpapi:NotifyAddrChange (Handle 0xebe8cc, overlapped 0xebe8b0): stub
[/FONT][FONT=arial]

Any help for a newbie would be very much appreciated - thanks
S[/FONT]

---

### Post by TheFu on 2016-11-04
Don't know about WINE, but it appears you've placed spaces incorrectly.  It matters.

WINEPREFIX=~/.wine32Bit wine 'home/username/Downloads/mt4setup.exe'

No space between the ~/.wine32Bit ... that is VERY important.  ~/ means $HOME, so ~/.win32Bit means the directory $HOME/.win3Bit/ ... which is probably what you want.  Can't help with the 32-bit vs 64-bit aspects of WINE.

---

### Post by tousios on 2016-11-05
TheFu, thank you for spotting that out.

I have managed to sort everything out, it's been a time consuming process but I have installed the executable files needed in wine.

Now, I get stopped with a different issue and I hope that you, or someone, will be able to help!

The program I installed requires a bit of space (essentially I would copy and paste them from my windows version) however wine dosdevices' c: e: and h: are only 3GB. Any ideas how I can make c: take up all allocated space available in the system?

I run the command ```
/home/intagir/.wine/drive_c/home/intagir->/home/intagir
``` to allocate home's space to drive c: and I got the following error:

> bash: /home/intagir: Permission denied

My System Monitor directory shows /dev/sda5 and has 914GB available out of 1TB. Ideally I'd like /dev/sda5 to become c:

Thank you again for reading and for the support

S

---

