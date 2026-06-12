---
title: "Adobe Digital Editions &quot;already running&quot; when try to open with Wine"
date: 2020-05-05
forum: Wine
---

### Post by sgroffman on 2020-05-05
Hello,

I just downloaded Wine so I can read an ebook which requires Adobe Digitial Editions. But when I try to install Adobe Digital Editions from the .exe file with Wine, (right clicked and selected wine64 from the browse menu) it tells me it's "already running" and that I must close program and try again. I tried moving the .exe to trash, deleting, restarting computer and downloading again, but no luck. I tried the wine64 file as well as the wineconsole file, with the same result. Any tips?

---

### Post by CelticWarrior on 2020-05-05
The support for Adobe Digital Editions under WINE is far from perfect but not bad at all considering the huge constrains: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=33276](https://appdb.winehq.org/objectManager.php?sClass=version&iId=33276)
The above is for the latest version tested.

---

### Post by wildmanne39 on 2020-05-05
*Thread moved to **Wine for a more appropriate fit**.*

---

### Post by sgroffman on 2020-05-05
Hmm that didn't have much... When I try through the terminal to run 

wine PROGRAM [ADE_4.5_Installer.exe] 

It tells me:

wine: cannot find L"C:\\windows\\system32\\PROGRAM.exe"

Is there something I can change in the configurations to make it find it?

---

### Post by HC48 on 2020-05-10
Good morning. I have the same problem as sgroffman and have tried the latest version of ADE and several earlier ones that I managed to find online. I have Ubuntu 18.4 and lost ADE when I upgraded. It worked in Ubuntu 14.
I have installed the stable version of wine for Ubuntu 18.4 as advised, wine tricks and play on wine, to no avail. Is this a problem with Ubuntu 18.4 as it is 64 bit and wine warns that some programs work best with 32 bit? I have seen the notes about different wine prefixes but started to get a bit lost. In any case I have tried both to the best of my ability. Thanks for any help. :)

---

### Post by HC48 on 2020-05-13
I just found a post in which someone got Adobe Digital Editions to work using virtualbox on the  linuxmint forums but doesn't say how he did it. I don't know any thing about virtualbox and have started looking for information. Can anyone give me a step by step method (for dummies) as to how I could do this? I was wondering if I added my old Ubuntu 14.4  in virtualbox I could get ADE back as it was working on that system. Am I on the right track? Would this upset my present 18.4 system. I am using an old PC.

---

### Post by CelticWarrior on 2020-05-13
Virtualbox is virtualization software, it can be used to create and manage virtual machines. A virtual machine is a guest OS running "inside" the host OS. 

So, yes, the software would be running natively in a Windows VM as mentioned in forum you've been reading. That said, please note that not all computers support virtualization or may not not have enough resources and for a Windows VM you also need a Windows license for a supported Windows version.

---

### Post by HC48 on 2020-05-14
Thank you for the reply Celtic Warrior. Yes, I realised it would be a problem to get a Windows VM as I only use Ubuntu OS so I was thinking of getting an older version of Ubuntu VM in which ADE actually worked. I wish someone would simply deal with the problem in a more simple way. Indeed I'm worried about using virtualbox on my old computer and I was hoping someone would get ADE to work again in Wine. I will wait and see I think. I researched the  Calibre plug-in for my reader but it's a Pocket Book Touch and there is no configuration for it.

---

### Post by CelticWarrior on 2020-05-14
I'm not sure you understand what a virtual machine is.

---

### Post by HC48 on 2020-05-14
Thank you Celtic Warrior. Ok, I will try to understand better if I decide it's worth the trouble, so never mind, and thanks again. Meanwhile if anyone can get ADE working in Wine with Ubuntu 18.04 i will be on the lookout! :)

---

### Post by HC48 on 2020-05-15
I have just found the latest wine version 5.0 and have managed to install it and an old version of ADE (1.7). ADE 4.5 wouldn't install. When I tried to use playonlinux I got a message to say I needed a newer version. I tried winetricks but I got the hang up message  'until all Wine processes in prefix .wine terminate', which wouldn't close, but it went away when I got rid of winetricks and restarted my PC., after which I managed to install ADE 1.7 with a right click on the .exe file and 'install with wine'. Anyway, so now I just have to get an .acsm file to see if it works. :p
This works, I was able to read my new book!

---

### Post by DuckHook on 2020-05-15
Perhaps I'm not catching on to something otherwise obvious, but why is ADE needed? Can Calibre do the job?

The problem with WINE is that continuing reliance on it will lead to an unending cycle of Windows app breakage. Every new app release risks breakage. Every new WINE release, likewise.

Such a state of affairs does not strike me as either productive or conducive to serenity in the long term.

I understand that some Linux apps cannot fully substitute for their Windows equivalents, but it may be worthwhile to try them out. I've often been surprised at how usable Linux apps are. There's always a learning curve, but it's usually a worthwhile investment.

---

### Post by HC48 on 2020-05-16
I understand your point of view DuckHook, and I agree, but the reality of the situation is that some of us like to read epub books and Calibre doesn't do the job with the .acsm files. There is a plug in for the usual readers but I happen to have a reader which is not in the plug in. I have to manage with ADE. The reason why I buy epub is that it suits my reader and I like to be able to read every kind of book, not just the free ones. The latest book of a well-known author for example will be protected. I have found online book stores with very decent prices for epub books and they always need ADE unfortunately to be readable. I have tried many alternatives and wish that Calibre could replace ADE completely, but it doesn't. Maybe someone will come up with something as I have come across many people with the same problem in Ubuntu 18.

---

