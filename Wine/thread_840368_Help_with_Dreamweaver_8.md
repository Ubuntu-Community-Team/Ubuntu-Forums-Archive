---
title: "Help with Dreamweaver 8"
date: 2008-06-25
forum: Wine
---

### Post by mbarvian on 2008-06-25
Hi all,

I am having a problem getting Dreamweaver 8 to install in Ubuntu Hardy 8.04.  I installed and configured Wine properly.  I've also tried two methods of installing Dreamweaver: installing it in Windows XP and copying the files over, and inserting the CD and installing that way.  However, both of these end up in the same result: I have all the files and registry necessary, but when I go to /home/maxwell/.wine/drive_c/Program Files/Macromedia/Dreamweaver 8 and click on Dreamweaver.exe, it does not open.  No errors or anything, it just won't open.

Does anyone have any ideas?  I have tried many other alternatives, but they are not nearly as good imho.

---

### Post by llama320 on 2008-06-25
I have a fantastic site to help you with this (just installed DW8 a couple weeks ago)

[http://luiscosio.com/how-to-dreamweaver-running-on-ubuntu-in-10-easy-steps](http://luiscosio.com/how-to-dreamweaver-running-on-ubuntu-in-10-easy-steps)

concerning the registry, you need to install recode and then export registry stuff in XP to ubuntu and then do
```
recode ucs-2..ascii macromedia.reg
```

..it's all in there

enjoy

---

### Post by mbarvian on 2008-06-25
Will this work with Ubuntu 8.04?  Because the tutorial says Dapper Drake, which is older.

---

### Post by llama320 on 2008-06-25
Yeah I should have mentioned that

I installed it on hardy and it worked flawlessly, so no worries there

EDIT: also, for reference, I'm using wine v0.9.59 (from the repositories), so while they released v1.0 recently, I can't speak to that version

---

### Post by mbarvian on 2008-06-25
Unfortunately, I tried this and I got errors when trying to do:

wine regedit dreamweaver.reg

here's the errors:

preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

---

### Post by llama320 on 2008-06-25
i found this site online, maybe it'll help, it seems directed at precisely your problem

[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

### Post by mbarvian on 2008-06-26
OK, well, I was able to correct the errors, thank you for that link, but, same as before:  after I copy all the folders and registry over and follow the tutorial, I go into home/maxwell/.wine/Program Files/Macromedia/Dreamweaver 8 and click Dreamweaver.exe and nothing happens.  Any suggestions?

---

### Post by llama320 on 2008-06-26
go into home/maxwell/.wine/Program Files/Macromedia/Dreamweaver 8

then paste the output from this command in terminal
```
wine dreamweaver.exe
```

maybe that will give us some debug clues

---

### Post by mbarvian on 2008-06-26
Here you go:

```
maxwell@maxwell-laptop:~$ cd /home/maxwell/.wine/drive_c/Program\ Files/Macromedia/Dreamweaver\ 8
maxwell@maxwell-laptop:~/.wine/drive_c/Program Files/Macromedia/Dreamweaver 8$ wine dreamweaver.exe
err:module:attach_process_dlls "odbc32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Macromedia\\Dreamweaver 8\\dreamweaver.exe" failed, status c0000005
maxwell@maxwell-laptop:~/.wine/drive_c/Program Files/Macromedia/Dreamweaver 8$ wine Dreamweaver.exe

```

BTW, thanks for your help, it is greatly appreciated :)

---

### Post by llama320 on 2008-06-26
no problem, i'm happy to help
this is a bit of a shot in the dark, but try this

```
mv ~/.wine ~/.wine-bak
wineprefixcreate
```

The idea's coming from this bug report
[http://bugs.winehq.org/show_bug.cgi?id=12809](http://bugs.winehq.org/show_bug.cgi?id=12809)
^^it's composed in large part of broken english, but still readable

***
if that doesn't work, i have another idea, coming from this thread
[http://ubuntuforums.org/showthread.php?t=753649&page=2](http://ubuntuforums.org/showthread.php?t=753649&page=2)

specifically 
> **gilda said:**
> I managed to get past this on my box by going into the wine config and overriding the odbc32 dll and then dropping the odbcint.dll in my wine system32 folder - the versions did not match but i was able to proceed and get dreamweaver to launch and work at that point

so you can try that too, just grab the file from your windows box and add it to the library in wine config

---

### Post by mbarvian on 2008-06-26
I see where you were going with the first one, but it just deleted all the Macromedia stuff, so I undid it

I did what was instructed in the second one, and now I am getting these errors while doing wine Dreamweaver.exe:

```
fixme:advapi:RegisterEventSourceW ((null),L"ODBC"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000000,0x32d7b0,(nil)): stub
err:eventlog:ReportEventW L"Failed to load resource DLL odbcint.dll"
err:module:attach_process_dlls "ODBC32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Macromedia\\Dreamweaver 8\\Dreamweaver.exe" failed, status c0000142

```

EDIT: I grabbed the odbcint.dll from Windows and put it in, and now I am able to load Dreamweaver!!! I haven't run into any problems yet, but please stay tuned, as I've heard of it closing prematurely

---

### Post by llama320 on 2008-06-26
awesome! hope it keeps working :)

---

### Post by mbarvian on 2008-06-26
me too!:)

---

