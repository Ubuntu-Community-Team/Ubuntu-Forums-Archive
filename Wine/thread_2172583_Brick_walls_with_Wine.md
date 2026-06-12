---
title: "Brick walls with Wine"
date: 2013-09-05
forum: Wine
---

### Post by dyers2 on 2013-09-05
I've been using Ubuntu Studio 13.04 for less than 3 weeks. A fair amount  of that time was spent trying to grow accustomed to GIMP. I'm past  disliking GIMP; now, I don't have neither desire nor motivation to learn  it.  To increase my chances of getting Photoshop CS3 to run in Wine, I  am attempting to upgrade Wine from 1.4.1 to 1.7.1 by following[ these directions]("http://www.noobslab.com/2013/08/wine-17-available-for-ubuntulinux.html"):

> Install Winehq 1.7.1 from source in Ubuntu 13.04 Raring/13.10/Linux Mint 15 open Terminal (Press *Ctrl+Alt+T*) and copy the following commands in the Terminal:

> > Terminal Commands:
sudo apt-get install flex bison qt4-qmake
wget [http://prdownloads.sourceforge.net/wine/wine-1.7.1.tar.bz2](http://prdownloads.sourceforge.net/wine/wine-1.7.1.tar.bz2)
tar -xjvf wine-1.7.*
cd wine-1.7.*

> > For 32bit: Terminal Commands:
./configure
cd tools; ./wineinstall

> > For 64 bit: Terminal Commands:
./configure --enable-win64
cd tools; ./wineinstall

When I ran tar -xjvf wine-1.7.*, this was the output:
> $ tar -xjvf wine-1.7.*
tar (child): wine-1.7.1: Cannot read: Is a directory
tar (child): At beginning of tape, quitting now
tar (child): Error is not recoverable: exiting now

bzip2: Compressed file ends unexpectedly;
    perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: Error is not recoverable: exiting now
$

I kind of don't know how to move forward, so if you can make a friendly suggestion or two, I'll be much obliged. Thanks for having taken the time to read.

[SIZE=4][SIZE=2]Dave[/SIZE] &#9774; [/SIZE]

---

### Post by ian-weisser on 2013-09-05
> **dyers2 said:**
> When I ran tar -xjvf wine-1.7.*, this was the output:
```
$ tar -xjvf wine-1.7.*
tar (child): wine-1.7.1: Cannot read: Is a directory
tar (child): At beginning of tape, quitting now
tar (child): Error is not recoverable: exiting now
```
 

Perhaps you have more than one file or directory that matches the wildcard (*). Try the following command and post the entire output here:
```
ls -l | grep wine
```

---

### Post by dyers2 on 2013-09-05
Thanks for your response, Ian. The output: 
> $ ls -l | grep wine
drwxrwxr-x 12 dave dave     4096 Sep  5 15:03 wine-1.7.1
-rw-rw-r--  1 dave dave 21266203 Aug 30 13:55 wine-1.7.1.tar.bz2
-rw-rw-r--  1 dave dave 21266203 Aug 30 13:55 wine-1.7.1.tar.bz2.1
-rw-rw-r--  1 dave dave 21266203 Aug 30 13:55 wine-1.7.1.tar.bz2.2
-rw-rw-r--  1 dave dave   620625 Jul  7 19:10 winetricks
$
You were right about the multiple incidents. What would you suggest I do?

[SIZE=4]&#9774;[/SIZE]  Dave

---

### Post by coldraven on 2013-09-06
Personally I never use the tar command, I just double click the file in Nautilus and the Archive Manager pops up. Then just select "Extract".

---

### Post by dyers2 on 2013-09-06
Interesting. When I found the 3 incidents of wine-1.7.1.tar.bz2, I used  Catfish to search for '1.7.1'. Among the results of that search, there  was a directory that I decided to open after I finished the last post I  wrote to this topic, and didn't think about it again. After reading your  post, coldraven, I opened my file browser to look for them again. In  the process, I found that directory again, and opened it. While I'm not  very familiar with Linux file system structure yet, the sub directories,  and files inside the directory looked like an application. So, I  checked the version of wine that's installed; it's 1.71.

[SIZE=4]&#9774;[/SIZE] Dave

---

### Post by dyers2 on 2013-09-07
Not making much speed here, and it seems I'm stuck again/still. I have 2 registered copies of Photoshop; 7, and CS3. Earlier today, I found a download on the Adobe site for a [free copy of CS2]("https://www.adobe.com/cfusion/entitlement/index.cfm?loc=en&e=cs2_downloads"). The keys are just beside the downloads. I never used CS2, but I think I remember that their primordial 3D studio was released with CS3 Extended.

So, once I realized that I was successful in installing Wine 1.7.1, I tried installing PS.  
> $ wine /media/dave/Photoshop\ CS3/Adobe\ CS3/Setup.exe
fixme:service:scmdatabase_autostart_services Auto-start service L"SixBitAgent" failed to start: 2
fixme:console:AttachConsole stub ffffffff
Begin Adobe Setup
UI mode: Full GUI
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:msxml:domdoc_setProperty Unknown property L"async"
fixme:browseui:ProgressDialog_SetAnimation (0x1f0658, 0x400000, 1000) - stub
fixme:browseui:ProgressDialog_StartProgressDialog Flags PROGDLG_NOTIME not supported
fixme:storage:create_storagefile Storage share mode not implemented.
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:msi:ITERATE_Actions Execution halted, action L"ProcessPropertyFile.E35C3ECB_5FDA_49E1_AB1F_D472B7CB9017" returned 1603
^Cfixme:console:CONSOLE_DefaultHandler Terminating process 8 on event 0
$
The SixBit Agent is associated with another app I'd like to install in Ubuntu. It's an app we use in our business. I'm dual booting this machine, but I'd really love to reclaim the space that XP occupies. I tried to install SixBit several days ago, but the installation aborted part way into it. There wasn't any way to uninstall it of which I was aware, so I searched with catfish, and deleted those files and folders. Now, I'm wondering if that was such a good idea as it appears something was left behind somewhere, and it's messin' with functionality.

I covet your ideas, and suggestions.

[SIZE=4]&#9774;[/SIZE] Dave

---

### Post by coldraven on 2013-09-07
If your PC has plenty of memory (mine has 4GB) and it supports virtualisation then consider running XP in VirtualBox.
Download the latest version from [https://www.virtualbox.org/](https://www.virtualbox.org/)
If you do not have an XP disc with a serial number  but only an OEM restore disc then read this:
[http://ubuntuforums.org/showthread.php?t=2070347&p=12293480#post12293480](http://ubuntuforums.org/showthread.php?t=2070347&p=12293480#post12293480)

You will be able to run Photoshop fullscreen and also your business app.
I don't have Photoshop but it runs Sketchup nicely.
The advantage is that once installed you can either create "snapshots" or "Export VM" or just copy the VM so that when XP breaks you can restore to mint condition it in minutes.
The "Export VM" option always states that it will take two hours but actually takes about ten minutes

---

### Post by dyers2 on 2013-09-07
Thanks! Those are good reasons to go with a VM. I did briefly look into VirtualBox, and it does seem like it might be the best solution in many ways. A couple of circumstances make it complicated in my situation. I am running an older machine (Toshiba Satellite A105) that looks like this:

* Processor: Intel(R) Celeron(R) M processor 1.70GHz, x86 Family 6 Model 13 Stepping 8
* RAM: 894 Mb
* Graphics Card: ATI RADEON XPRESS 200M Series, 128 Mb
* Hard Drives: C: Total - 57231 MB, Free - 25130 MB; (The following 3 drives are partitions of the same physical drive) E: Total - 28003  MB,  Free - 9505 MB; G: Total - 29996 MB, Free - 10867 MB; H: Total -  180464  MB, Free - 12570 MB;
* Motherboard: ATI, SB450

This machine supports 2 x 1GB modules RAM. Crutial doesn't carry anything anymore that's compatible with this machine. A number of eBay sellers say they do, so I purchased some from one with great feedback. It wasn't recognized in my machine. I wrote, he had something else that was also supposed to, and gave me a RMA#. When the second sticks arrived, same deal; they weren't recognized, and had to be returned, too. I really don't have a good idea where to find those modules.  Having the extra memory would make a lot of things easier. This is my "spare"; I lost the MB of my primary machine, and I haven't been able to buy the parts to rebuild it. Anyway, for now, this is the hardware I have to work with.

[SIZE=4]&#9774;[/SIZE]  Dave

---

### Post by ian-weisser on 2013-09-07
> **dyers2 said:**
> Not making much speed here, and it seems I'm stuck again/still. I have 2 registered copies of Photoshop; 7, and CS3. Earlier today, I found a download on the Adobe site for a [free copy of CS2]("https://www.adobe.com/cfusion/entitlement/index.cfm?loc=en&e=cs2_downloads"). The keys are just beside the downloads. I never used CS2, but I think I remember that their primordial 3D studio was released with CS3 Extended.

So, once I realized that I was successful in installing Wine 1.7.1, I tried installing PS.  

Did you check the wine website for CS-specific guidance? Quite a bit there....
[http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)

---

### Post by dyers2 on 2013-09-07
> **ian-weisser said:**
> Did you check the wine website for CS-specific guidance?

Yes, I have...quite a bit over several days, and have taken a good bit of direction from there, as well as from other sources. Much of the information available is for Wine v.1.1 & v.1.2; very little is available for > v.1.4. Like most developers, Wine's suggest using the most recent version. That's v.1.71, and I am using it. I do multiple web searches for error messages, and spend hours pouring through files on my HD in search of those error orrigins.  Because there is almost nothing yet about any CS with the most recent versions of Wine, I came here for wisdom, and experience. By the way; which version of CS, and which version of Wine are you using?

[SIZE=4]&#9774;[/SIZE] Dave

---

### Post by coldraven on 2013-09-08
> * Processor: Intel(R) Celeron(R) M processor 1.70GHz, x86 Family 6 Model 13 Stepping 8
* RAM: 894 Mb
* Graphics Card: ATI RADEON XPRESS 200M Series, 128 Mb
* Hard Drives: C: Total - 57231 MB, Free - 25130 MB; (The following 3  drives are partitions of the same physical drive) E: Total - 28003  MB,   Free - 9505 MB; G: Total - 29996 MB, Free - 10867 MB; H: Total -   180464  MB, Free - 12570 MB;
* Motherboard: ATI, SB450

With those specs I think a VM is out of the question.

FYI my laptop is a HP Compaq 6715b, you could get one on ebay for about £100.
It has an AMD dual core 2GHz processor. (2 x Turion)
I put an extra 2GB memory in it for around £30. (max 4GB) and a 250GB hard drive for £35
It's weakness is the ATI X1250 video card, it is no use for gaming in Linux.
It's now five or six years old and is a reliable, well built machine.

Hopefully you will get Wine to work with Photoshop.

---

### Post by dyers2 on 2013-09-08
Thank you, I'd like to run a reasonably up-to-date computer again. I spend an inordinate amount of time trying - successfuly for the large part - to coax a little something more from this one until I can rebuild my primary PC. 

As to current reality, I'm not finding a way to solve [this]("http://ubuntuforums.org/showthread.php?t=2172583&p=12781149#post12781149"). 

[SIZE=4]&#9774;[/SIZE]  Dave

---

