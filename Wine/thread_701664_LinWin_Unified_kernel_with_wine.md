---
title: "Lin/Win Unified kernel with wine"
date: 2008-02-19
forum: Wine
---

### Post by miljan on 2008-02-19
Yes it finally heappend!! :):KS:KS
so now we have  fully working (any) .exe under Linux, and they say it is done in a much better way... :) , And not by an emmulation.
There is a source code for Win/Lin Unified kernel patch that  provide full support for Windows app's under Linux.Its Wine and Reactos based and it handles
system calls directly from kernel it self, what is much better way for doing this task.

They are  guys from China called "Insigma" And you can all download a source code to try it out, maybe WineHQ should consider this in some next 
development project.
Links are:

[http://www.reactos.org/forum/viewtopic.php?p=41577](http://www.reactos.org/forum/viewtopic.php?p=41577)

[http://translate.google.com/translate?u=http%3A%2F%2Flinux.insigma.com.cn%2Fjszl.asp%3Fdocid%3D122805676&langpair=zh%7Cen&hl=en&ie=UTF-8](http://translate.google.com/translate?u=http%3A%2F%2Flinux.insigma.com.cn%2Fjszl.asp%3Fdocid%3D122805676&langpair=zh%7Cen&hl=en&ie=UTF-8)


[http://www.linuxforums.org/forum/coffee-lounge/115169-linux-unified-kernel-0-2-1-released.html](http://www.linuxforums.org/forum/coffee-lounge/115169-linux-unified-kernel-0-2-1-released.html):KS:KS:KS:KS

---

### Post by 100ubutususer on 2008-02-21
It is a good idea.





-------------------------------------------

UnifiedKernel + WINE's .dlls = UnifiedKernelOS => windows environment + linux 

Note: the UnifiedKernelOS is an operating system .  WINE is an  application. 




UnifiedKernel start from linux+wine (using ReactOS code as reference) 

---- 

"Starting point is Linux + Wine. Along with the development of, the Linux kernel becoming compatible core, the Linux + Let us said, and Wine is gradually evolving into a system call interface on Windows customization and optimization of the Wine, we tactfully called Wine '. Therefore, the entire development process is: 
(Linux + Wine) =>&#8230; =>&#8230; => (Linux + + Wine ') 
Starting point for Linux + Wine obviously can run, in the process of development every step to achieve a limited objective, the results of each step should be a run, more approximation of Windows can be released version. " 




---------------


Wine still could not solved the problem well. Out of such a concern, I suggested the idea and route of "Linux Compatible Kernel". Its objective is: extend Linux kernel and make it support both Linux's own application and device driver, and also Windows' application and device driver, becoming a "compatible kernel". To implement such a kernel, one need to add several parts on to Linux kernel: 
- A framework that matches the properties and requirements of Windows device driver, i.e. Windows device driver framework, so that multiple Windows device driver modules may be loaded into kernel, while retaining their relationship and running conditions as in Windows. 
- A set of export function defined by Windows kernel export function interface (see Windows DDK). To device driver program, these functions are like library functions provided by kernel. 
- Windows native API. Microsoft did not open their native API, but "Windows NT/2000 Native API Reference" and other materials have unveiled this secret. Implement Windows system API in Linux kernel, are like implementing another high level language in assembly. This is because, inside the kernel, usable "brick" are not macro Linux API anymore but many micro Linux kernel functions.

---

### Post by ShodanjoDM on 2008-02-21
Forgive my ignorance, but if the Windows executable works in Linux, isnt it means that it is also made easier for Linux to get infected by viruses?

---

### Post by 100ubutususer on 2008-02-21
> **ShodanjoDM said:**
> Forgive my ignorance, but if the Windows executable works in Linux, isnt it means that it is also made easier for Linux to get infected by viruses?

no viruses.

because the viruses can not run on the linux/windows unified kernel . i think.

---

### Post by Vadi on 2008-02-21
And I think that we -can-, since windows programs are getting access right inside the kernel (but I'm not an expert at all).

---

### Post by 100ubutususer on 2008-02-22
[www.insigma.com.cn](www.insigma.com.cn) , it is a chinese website. 

the lin/win unified kernel 

[http://linux.insigma.com.cn/download/software/unifiedkernel-0.2.1.tar.bz2](http://linux.insigma.com.cn/download/software/unifiedkernel-0.2.1.tar.bz2) 


it is a great  idea.


[http://www.reactos.org/forum/viewtopic.php?t=5240](http://www.reactos.org/forum/viewtopic.php?t=5240)

Below the text of automatic translation from google.com: 



"A framework, the two interfaces" 

Maode parade 


We develop Linux-compatible core objective is to enable Windows applications directly in the kernel can run on more precisely in order to the core as the core operating systems. At the same time, but also allow for the development of Windows and some of the equipment drive module can also run into the kernel. This is because for Windows device drivers are developed in terms of quantity and variety are far more than Linux on the other hand is because there are more and more applications need special equipment to drive module supporting operation, missing This device driver modules running up. Only at the same time to achieve the two goals can be said that Linux kernel compatible with the Windows kernel. So, in order to achieve these two objectives, we must make some of the Linux kernel revision and expansion of what? This paper is an analysis of this, and answer this question. 
First, the closed section of the procedure, if not call the process, nor for system calls, with the operating system is irrelevant, as long as the CPU of the machine with this procedure compile-time goal can be consistent with the CPU. This is because the PC-for example, this procedure generated by the compiler all the instructions are all x86 machine instructions, and all these directives can all normal operation of all of its instructions and subroutine calls Jump instructions are not the target this process beyond the borders. Secondly, even if the procedures need to call, as long as no direct or indirect system calls, also has nothing to do with the operating system, called the procedure because of the effect on the expansion of this procedure equivalent to the site to promote its borders. Therefore, as long as no direct or indirect system call, the application will follow the operation of the operating system irrelevant, thus can be run on any operating system. Generally, however, such a procedure is not as a separate application, the independent operation of the process, at least since the independence process has to input / output, which can not be separated from the system call. 
So how application software system calls? As we all know, this is achieved through the trap instructions, is in the x86 processor instructions int. In fact, the use of the Linux kernel, "int 0x80" Achieving system calls, and use of the Windows kernel, "int 0x2e." First of all, this makes Windows applications can run on the Linux kernel. Just think, an attempt to Windows applications through "int 0x2e" system call, and the Linux kernel that this is illegal trap instructions. So, first of all, the Linux kernel must accept the "int 0x2e" as a means of system calls. We really thank the two of the core designers, if they originally chose the 0 x80, or choose to have a 0 x2e, which we are now harder to resolve. Fortunately, this conflict is not among them. 
Since all system calls through a trap with instructions to enter kernel parameters on the need to adopt the "call" to distinguish between the specific requirements of the operation and function. So, what instructions in the system call, we must also consider the use of the total number of calls, each call, what response operation and functions, what needs some parameters, what the outcome, how to return to, what are the side effects, etc. . All of these factors together, constitute a system call interface. Of course, Windows and the Linux system call interface different. To bring Windows software to run directly on the Linux kernel, it must allow the Linux kernel also provides a Windows system call interface, it just seemed as the Wine Windows software "grafting" of the Linux system call. "Grafted", the Wine has done a very good job, but we know that effect or not ideal. 
Our system call interface for Windows, of course, say that the performance of Windows applications is the core of the outside see specific system calls call methodologies, parameters, effects, the results of the return, as well as side effects. But on the other hand, more importantly, this interface is behind things, the realization of these system calls, we have in this area but this is also the main workload. 
According to the "Undocumented Windows 2000 Secrets", a total of 248 conventional Win2k system calls (with the results of reverse engineering card). Some of these system calls is very simple, or almost directly corresponding alternative Linux system calls, and some are very complex. Obviously, we developed these systems from scratch call is not realistic (although ReactOS is doing), we should do is to make full use of the Linux kernel function in the low to achieve these Windows system calls. In a sense, Wine is outside the core Windows applications will be grafted on to the Linux system call, and we will have the compatibility of the core kernel inside Windows system calls will be grafted to the Linux kernel function on the many. Grafting is the core inside than outside the core grafting better, the kernel function on the one hand because of the "size" small core functions and system calls a bit like the relationship between language and high-level language compilation between relations. On the other hand because of the kernel space is unified, and can provide the overall vision. For example, the core process can be seen in all the process control block (PCB), and a kernel to user space, the process of separation between each other. Therefore, all require the operation of the overall vision, it should achieve in the core. 
In addition to these conventional system calls, Win2k are 639 graphical interface (GUI) system call. This is tantamount to X11 moved to the core inside. In the past WinNT 4.0, Windows, like Linux, the graphical user space services on the process to achieve graphics and window operation, and management, as of course efficiency is relatively low. WinNT 4.0 from the beginning, so graphics operation and management moved to the Windows kernel inside, a module can be installed win32k.sys. This increased the speed of graphics operations meaningful, otherwise the game software can not be so smooth operation (of course, but there has been a DirectX, and further enhance the image / graphics operation speed, it is after). Therefore, strictly speaking, the so-called Windows system call interface graphics operations also include these calls. But achieving these calls "raw materials" is no longer a function of the Linux kernel, but the correlation function of X11. Of course, things are prioritized, and there is absolutely no need in the very beginning that more than 600 calls have a pot. In fact, even the 248 call the realization of conventional systems, nor is it necessary to step in place. 

After this system call interface, customs, many system calls can be achieved, such as creating process, take time, etc. These systems, the Linux kernel inside integrity can be achieved. However, once involved input / output, device drivers involved, and there may be a problem. The problem lies not in the conventional device driver, such as the keyboard, mouse, hard disk, such as equipment used in the Linux kernel driver was alone, as long as the system call grafted on to the past. The problem is that some special equipment, in particular the new equipment. These equipment manufacturers often provide only for Windows device driver modules, namely. Sys files. If we can not turn the case. Sys modules into the Linux kernel and give them normal operation, the compatibility of Windows applications will not be complete. 
Will be. Sys modules into the Linux kernel it is not difficult, because Linux installation module with the dynamic nature of the no different. It is difficult in the Linux kernel in normal operation. To achieve this goal, the first module to load up with the relevant system call interface down (likely) interrupt response mechanism engaged with the second module is to provide a specific operating environment. In fact,. Sys module reason can be put into normal operation of the Windows kernel and it is precisely because the Windows kernel to meet these two conditions. Obviously, the existing Linux kernel does not have such a condition that it meet the dynamic installation module is a Linux operating conditions, this system call interface with the two different is the same. Therefore, this has become compatible with the development of a core component of the important, but also represents a considerable workload. 
Look at how the Windows kernel to meet these two conditions, we know what to do the. 
The first is how to make. Sys module with the relevant system calls and interrupt response engaged, and I connected. In other words, what will be. Sys module into the core of the device driver framework, including specific modules on the framework of what position, and below and adjacent to the module or how interactive components. In the Windows kernel, which is the main I / O subsystem matter, the specific mainly reflected in two aspects: one is loaded after the first module to the I / O subsystem registration, or a device driver upward Registration, which is indirectly to the I / O subsystem registration. On the other hand, when the system calls when it is through I / O subsystem into for the specific device driver layer call and return. Therefore, I / O subsystem represents a device driver framework of the main. However, the I / O subsystem is not the device driver framework, and all. Sys module with the interrupt response might be engaged. For example, a. Sys module is a part of the interrupt service routine operation, and the other may have been in part as a bh function (in Windows called DPC) operation, and also is part of the I / O subsystem drivers. The Windows. Sys modules are targeted at the Windows device driver development of the framework, since we want these. Sys modules into the Linux kernel running on the Linux kernel must be constructed from such a framework. Specifically, it is necessary to achieve the Linux kernel in Windows I / O subsystem, the Windows interrupt response / service mechanism, as well as a number of complementary ingredients. 

Windows device driver framework to address the right. Sys module load and use. If each module are closed, independent, and did not require the support of the environment, that would suffice. However, the fact is almost non-existent this closure, an independent device driver modules, the operation of almost every module needs the support of the inverted environment. For example, a device driver modules may be necessary in the operation of the distribution of the buffer zone. However, device driver module is not available and the ability, because it does not have any memory can be dynamically allocated resources. Therefore, the request had to be allocated core, which is dependent on the environment. To this end, the operating system kernel to "leads to (export)," a large number of core functions for dynamic module installed call. Set the size of this function, as well as each of the specific function to be called the conditions and parameters, role, and the return value, side effects, constitutes a specific kernel device driver support interface. Obviously, different cores have different device driver interface support, as if there are different different kernel system calls interface. Let the Windows. Sys module in the normal operation of the Linux kernel, it must be provided in the Linux kernel device driver support for Windows interface. System call interface with the different Windows device driver support interface definition is open to the public (otherwise it will be impossible for third parties to develop device driver modules), and defined in the DDK Win2k or WinXP, "Device Driver Development Kit." Win2k defined in the DDK 2000 to a support function, but is also commonly used by several hundred, or even less. Of course, Microsoft is only open this interface definition, but not its realization. 
So, how to achieve these support function? Or the old methods, turns them into, or grafting to the appropriate Linux device driver support function forward. 
It is worth mentioning that, Windows drivers for network equipment other definition of a framework, known as NDIS, and provides a specialized NDIS device driver interface support, NDIS device driver modules need only (and should only) call NDIS interface support functions. In this way, network equipment drive on their own systems, with a major in the framework of the small framework. However, regardless of the framework is still supporting NDIS interface are relatively small, only a Windows device driver framework and the client interface and expansion, and many NDIS support function in some Windows device driver is a simple function of packaging, so we will Windows NDIS device driver into the framework and interface. 

In summary, we have developed compatible with Linux kernel, is mainly in the Linux kernel to achieve this in a framework and the two interfaces: Windows device driver framework, Windows system call interface, as well as support Windows device driver interface. This is compatible with Linux kernel development of the main. Of course, there are many piecemeal, supporting the development work to be done, but relatively small compared to the workload. 
However, "a framework, the two interface" is the mainstay of development work, which is compatible with the core itself, rather than in terms of the whole operating system. Let Windows applications normal operations, the core also need some outside DLL, or dynamic link library support, as well as a number of supporting the process of support services. If only from a technical point of view, as long as it is compatible with the kernel on the line, because we are able to Windows DLL on the procedures and services from copy. But this is not only a technical problem, but a legal problem, we can not go to Microsoft's copyright infringement. Therefore, these DLL and services also need to develop procedures, Wine Fortunately, we have done a lot for this area of work, which is the need for the four DLL, the so-called "four parts" for some changes. Information Windows system calls to the detachment of the Linux system call is these four pieces: kernel32.dll, gdi32.dll, user32.dll, and ntdll.dll, but now it also true that they return to the distorted distort things back again. 
Also see, the Windows technology and applications are developing their own, these developments more DLL and services reflected in the process, such as OLE, COM / DCOM,. NET, most of these technologies and services through DLL process to achieve. Although Wine has been done many such DLL and service procedures, but that the development may never be finished, but it is Xishuichangliu affairs.

---

### Post by Vadi on 2008-02-22
No, no, no.

And no again. We do not need Windows. This will not help.

A wrongly wasted research time, imo.

---

### Post by Nash Li on 2008-02-22
oh it's good.
it gives us more choices

---

### Post by k99goran on 2008-02-22
Would the Windows application/game support be better using this kernel than it would using a regular Linux kernel with Wine running on top?

---

### Post by The Noble on 2008-02-22
Can I get a tl;dr version? I get the basic gist of the situation, but has any work been done?

---

### Post by 100ubutususer on 2008-02-22
> **The Noble said:**
> Can I get a tl;dr version? I get the basic gist of the situation, but has any work been done?


download link is 

[http://linux.insigma.com.cn/download/software/unifiedkernel-0.2.1.tar.bz2]("http://linux.insigma.com.cn/download/software/unifiedkernel-0.2.1.tar.bz2")



the windows device drivers and the applications can work in the lin/win unified kernel. 

they have implemented basic mechanism of Windows system including process/thread management, object management, virtual memory management and inter-process synchronization management etc.

Below the text of the documents of the V0.2.1:

About this list
===============
This version of Linux Unified Kernel implements some most important
mechanisms, and fixes many bugs in the last version. Now many 
general Win32 programs can run on Linux system. Here is the list
of some important applications that we have tested.

The applications on the list may not work well as on Windows system.
You can report the bugs to [email]linux@insigma.com.cn[/email].


Application name
================
Microsoft Office 2000 ( Word, Excel, PowerPoint)
Securecrt 5.0
Dream Weaver 8
WinRar
Acrobat Reader 5






To Do in Future:
================
o File System Integration.
o Bug Fix for Pthread TLS.
o Windows Application Testbed.
o The Windows Registry mechanism.
o Various system call functions on the Windows syscall interface.
o The WDM device driver framework.
o The Windows DPC mechanism.
o Exported kernel functions defined by Windows DDK.
o Others.

---

### Post by Vadi on 2008-02-22
What is the legality of this?

---

### Post by 100ubutususer on 2008-02-24
Gpl.

---

### Post by Vadi on 2008-02-24
No, I mean on the Microsoft side.

---

### Post by The Noble on 2008-02-24
I'm interested, but I don't have the tie to look into this right now. Thanks for the info.

---

### Post by miljan on 2008-02-25
Can someone compile that from source, and attach it here for me, please.
I am not so good in doing this kernell compillation process.
I want to try it on Hardy beta4 .
Thank you all for clearing out some things about this topic, to me!
:) 
I feel, you are all wery friendly , in contrast to a Serbian Ubuntu forum, where they have Locked up my topic, and emmidiately  start an argue and
neglect my effort.
  Thank you all again!

---

### Post by super carrot on 2009-05-27
> **Vadi said:**
> No, no, no.

And no again. We do not need Windows. This will not help.

A wrongly wasted research time, imo.

Its an absolutely brilliant idea. And its not Windows, it Linux, its just that Linux will now support the Win32 API

---

### Post by super carrot on 2009-05-27
> **ShodanjoDM said:**
> Forgive my ignorance, but if the Windows executable works in Linux, isnt it means that it is also made easier for Linux to get infected by viruses?

Certainly does mean that Linux can be suseptable to Windows viruses. However, they still need to be run and so on. When the Linux desktop gets mainstream success it will get viruses written for it anyway. Our only truly innate security was the user level thing, and user education so that all users are forced normally or just used to using their computer without admin rights. What we don't have is computers being infected just by being connected to the Internet.(XP ahem)This will not affect that. So no problem as long as you don't download and install random things from the Internet, which is not good, what ever operating system you have.

---

### Post by albinootje on 2009-05-27
> **super carrot said:**
> Its an absolutely brilliant idea. And its not Windows, it Linux, its just that Linux will now support the Win32 API

I read about LUK in another thread, and I'd like to try it. 
But.. are there any up-to-date mirrors ? Downloads have a maximum of 2 Kb/s it looks like, and are md5sums available ?

[http://en.wikipedia.org/wiki/Linux_Unified_Kernel](http://en.wikipedia.org/wiki/Linux_Unified_Kernel)

---

### Post by asdfoo on 2009-05-27
so it works less well than Wine and requires more privileges to run?  I think I'll stick to Wine.

---

### Post by albinootje on 2009-05-27
> **asdfoo said:**
> so it works less well than Wine and requires more privileges to run?  I think I'll stick to Wine.

I just tested it (The mirror in poland was fast, and had a pretty recent version). The pre-compiled kernel was lacking a few modules, so I didn't have internet connection, and ufw wouldn't load, but.. it works as promised, although Kingsoft Office also failed to run properly with this setup, and made my machine freeze completely.

---

### Post by NightMKoder on 2009-05-27
Apparently linux isn't the next windows, but the next OS/2. Great.

There is an inherent insecurity in letting windows apps into the kernel. And FYI - wine's graphics implementation is almost perfect. The problem is that the linux graphics stack...well isn't too good. But that's being working on right now. 

The only possible good thing I see from this is allowing windows drivers to work on linux. My only concern is - it seems that if, say, a windows video card driver works on this kernel, it may not necessarily be seen as a driver by linux userspace. But that may be wrong.

Perhaps the only useful thing this may give us is Gameguard games working ;)

---

### Post by ov3rcl0ck on 2009-06-10
> **ShodanjoDM said:**
> Forgive my ignorance, but if the Windows executable works in Linux, isnt it means that it is also made easier for Linux to get infected by viruses?

I think you make a pretty valid argument. It will cause security issues under Linux by opening it to the threats of windows. But thats a risk you'll have to be willing to take. Probably the best thing to do is to only use the kernel when you need to run windows applications, and make a new linux account with very restricted access to the other portions of your hard drive to prevent any damage to your linux system, so when you want to run windows applications just select the kernel from GRUB(or anyother kernel) and login.

---

