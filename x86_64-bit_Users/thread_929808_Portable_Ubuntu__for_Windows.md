---
title: "Portable Ubuntu  for Windows"
date: 2008-09-25
forum: x86 64-bit Users
---

### Post by demonccc on 2008-09-25
Hello Ubunteros!

I'm developing an Ubuntu system that can be executed such as Windows native application. This is useful where you can't install Ubuntu (Job, school, partner house, or whatever...). You can put the system into to your pendrive and carry it wherever. The system use the X server for windows called Xming to intgrate the linux applications in the Windows desktop and Pulseaudio server for Windows to reproduce the sound in your portable Ubuntu. [This]("http://portableubuntu.sourceforge.net/") is the homepage of the project. Enjoy it! Regards.

---

### Post by JOKe on 2009-03-30
The portable ubuntu cannot boot under Vista 64 bit Ultimate with up2date updates.

---

### Post by Der_Ventilator on 2009-03-30
Same here. Vista x64

Microsoft Windows [Version 6.0.6001]
 Directory of E:\Portable Programme\Portable Ubuntu

15.09.2008  20:49    <DIR>          .
15.09.2008  20:49    <DIR>          ..
25.05.2008  00:36            90.624 colinux-console-nt.exe
25.05.2008  00:36            80.896 colinux-daemon.exe
18.08.2008  02:59            80.384 colinux-slirp-net-daemon.exe
11.09.2008  23:03    <DIR>          config
14.09.2008  01:31             4.286 folder_ubuntu.ico
14.09.2008  01:38    <DIR>          images
31.08.2006  23:46           415.873 initrd.gz
25.05.2008  00:36            68.096 linux.sys
09.09.2008  22:10               497 portable_ubuntu.bat
09.09.2008  21:56    <DIR>          pulseaudio-0.9.6
11.09.2008  21:54                50 run_portable_ubuntu.bat
04.08.2006  14:08            57.344 TrayRun.exe
25.05.2008  00:27         3.144.276 vmlinux
25.05.2008  00:31         2.457.300 vmlinux-modules.tar.gz
12.09.2008  00:23    <DIR>          Xming
              11 File(s)      6.399.626 bytes
               6 Dir(s)     867.373.056 bytes free

E:\Portable Programme\Portable Ubuntu>portable_ubuntu.bat
Cooperative Linux Daemon, 0.7.3
Daemon compiled on Sat May 24 22:36:07 2008

driver not installed
Cooperative Linux Daemon, 0.7.3
Daemon compiled on Sat May 24 22:36:07 2008

loading E:\Portable Programme\Portable Ubuntu\linux.sys
failure: StartService (0x4fb)
cannot install (rc 80a3d80c)
File C:\Users\DER_VE~1\AppData\Local\Temp\swap.img is created
File C:\Users\DER_VE~1\AppData\Local\Temp\temp.img is created
Cooperative Linux Daemon, 0.7.3
Daemon compiled on Sat May 24 22:36:07 2008

colinux: manager open: The system cannot find the file specified.
daemon: exit code 82c7540e
daemon: can't access CoLinuxDriver, please check status driver!
Cooperative Linux Daemon, 0.7.3
Daemon compiled on Sat May 24 22:36:07 2008

driver not installed

---

### Post by JoelMay on 2009-04-03
Same here also.  Windows 7 x64.


> **Der_Ventilator said:**
> Same here. Vista x64

Microsoft Windows [Version 6.0.6001]
 Directory of E:\Portable Programme\Portable Ubuntu

15.09.2008  20:49    <DIR>          .
15.09.2008  20:49    <DIR>          ..
25.05.2008  00:36            90.624 colinux-console-nt.exe
25.05.2008  00:36            80.896 colinux-daemon.exe
18.08.2008  02:59            80.384 colinux-slirp-net-daemon.exe
11.09.2008  23:03    <DIR>          config
14.09.2008  01:31             4.286 folder_ubuntu.ico
14.09.2008  01:38    <DIR>          images
31.08.2006  23:46           415.873 initrd.gz
25.05.2008  00:36            68.096 linux.sys
09.09.2008  22:10               497 portable_ubuntu.bat
09.09.2008  21:56    <DIR>          pulseaudio-0.9.6
11.09.2008  21:54                50 run_portable_ubuntu.bat
04.08.2006  14:08            57.344 TrayRun.exe
25.05.2008  00:27         3.144.276 vmlinux
25.05.2008  00:31         2.457.300 vmlinux-modules.tar.gz
12.09.2008  00:23    <DIR>          Xming
              11 File(s)      6.399.626 bytes
               6 Dir(s)     867.373.056 bytes free

E:\Portable Programme\Portable Ubuntu>portable_ubuntu.bat
Cooperative Linux Daemon, 0.7.3
Daemon compiled on Sat May 24 22:36:07 2008

driver not installed
Cooperative Linux Daemon, 0.7.3
Daemon compiled on Sat May 24 22:36:07 2008

loading E:\Portable Programme\Portable Ubuntu\linux.sys
failure: StartService (0x4fb)
cannot install (rc 80a3d80c)
File C:\Users\DER_VE~1\AppData\Local\Temp\swap.img is created
File C:\Users\DER_VE~1\AppData\Local\Temp\temp.img is created
Cooperative Linux Daemon, 0.7.3
Daemon compiled on Sat May 24 22:36:07 2008

colinux: manager open: The system cannot find the file specified.
daemon: exit code 82c7540e
daemon: can't access CoLinuxDriver, please check status driver!
Cooperative Linux Daemon, 0.7.3
Daemon compiled on Sat May 24 22:36:07 2008

driver not installed

> **JOKe said:**
> The portable ubuntu cannot boot under Vista 64 bit Ultimate with up2date updates.

---

### Post by descott on 2009-04-03
I've got the same issue. Vista64

Looks to be a colinux service issue?

```
G:\Portable_Ubuntu>colinux-daemon --install-driver
Cooperative Linux Daemon, 0.7.3
Daemon compiled on Sat May 24 22:36:07 2008

loading G:\Portable_Ubuntu\linux.sys
failure: StartService (0x4fb)
cannot install (rc 80a3d80c)
```

---

### Post by ian_x64 on 2009-04-04
The colinux kernel won't run on 64bit Windows.

See [this ]("http://colinux.wikia.com/wiki/Dashboard_for_developing_a_64_bit_coLinux") for more information on how to get it to work. Just started looking myself, but I might spend some time on this.

---

### Post by milio1401 on 2009-04-06
it happened to me too,i tried to run it under vista ultimate 64 ,and it didn't work,i'll be waiting  to see if someone  posts  a reply on how to make it  work  ):P

---

### Post by Nuno Bettencourt on 2009-04-27
Hi, the same happens in Windows XP Pro x64.

Here's the error I got:

Cooperative Linux Daemon, 0.7.3
Daemon compiled on Sat May 24 22:36:07 2008

driver not installed
Cooperative Linux Daemon, 0.7.3
Daemon compiled on Sat May 24 22:36:07 2008

loading D:\install\linux\PortableUbuntu\Portable_Ubuntu\linux.sys
failure: StartService (0x4fb)
cannot install (rc 80a3d80c)
File C:\DOCUME~1\nuno\LOCALS~1\Temp\swap.img is created
File C:\DOCUME~1\nuno\LOCALS~1\Temp\temp.img is created
Cooperative Linux Daemon, 0.7.3
Daemon compiled on Sat May 24 22:36:07 2008

colinux: manager open: The system cannot find the file specified.
daemon: exit code 82c7540e
daemon: can't access CoLinuxDriver, please check status driver!
Cooperative Linux Daemon, 0.7.3
Daemon compiled on Sat May 24 22:36:07 2008

driver not installed

---

### Post by jrynik on 2009-05-22
Hello,
 
I installed portable ubuntu to my Windows XP (win 32). However, when I double clicked on file run_portable_ubuntu.bat, the green arrow appeared in the system (launch) tray only for an instant and then it disappeared.
 
No logo as described in the tutorial appeared and no Portable Ubuntu panel (taskbar) appeared at the top of my desktop. 
 
I turned my antivirus and firewall resident protection off before the installation. 
 
Do you happen to know what could get wrong? If you need more info, feel free to ask.
 
Thank you very much for your help.

---

### Post by RonCam on 2009-05-24
> **jrynik said:**
> ... when I double clicked on file run_portable_ubuntu.bat, the green arrow appeared in the system (launch) tray only for an instant and then it disappeared.I ran the batch file from the MS Windows' CMD-line prompt, not from the GUI.  And, best to do it as Administrator, should that not be automatic in your OS.  

Technically, you're right, reading from the forum's official installation documentation, but this is what I recall doing (got the idea from directions I saw on *YouTube*) and it installed just fine.

Once the holiday weekend (in Argentina, also) is over, version TWO (or likely, DOS, not to be confused with the 'other DOS' #-o) is expected to replace UNO, so you may want to wait a day or two, as it has been promised for a week by now.

---

### Post by RonCam on 2009-05-24
x

---

### Post by PGHammer on 2009-05-25
> **JOKe said:**
> The portable ubuntu cannot boot under Vista 64 bit Ultimate with up2date updates.

That is the biggest quibble with Linux run that way (as opposed to a Wubi-style *buntu install, which differs from a native install only by it being nested; it can be updated, or even upgraded, like any other *buntu).  Otherwise, I would simply suggest VirtualBox (or even Virtual PC, now that it's free) if you can't use Wubi (which works just fine with 64-bit flavors of Windows/*buntu; I have Ubuntu Jaunty 64-bit installed within 7 RC 64-bit, and I'm having no issues).

---

