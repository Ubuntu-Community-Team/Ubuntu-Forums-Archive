---
title: "Wine and .NET (mono)"
date: 2014-01-17
forum: Wine
---

### Post by Elastic_Potential on 2014-01-17
'evening.

I'm having trouble running a program which requires .NET framework.  I installed the .msi using Wine, and then I tried running it with mono
```
mono program.exe
```

However, this is the output.  For security reasons, I need to redact the program name, but I think any meaningful information will be here:

```

Missing method .ctor in assembly /home/aesclepius/.wine/drive_c/Program Files/MYPROGRAM/MYPROGRAM_SUBFOLDER/MYPROGRAM.exe, type System.Windows.ThemeInfoAttribute
Can't find custom attr constructor image: /home/aesclepius/.wine/drive_c/Program Files/MYPROGRAM/MYPROGRAM_SUBFOLDER/MYPROGRAM.exe mtoken: 0x0a000010

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'PresentationFramework, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies.
File name: 'PresentationFramework, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35'
[ERROR] FATAL UNHANDLED EXCEPTION: System.IO.FileNotFoundException: Could not load file or assembly 'PresentationFramework, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies.
File name: 'PresentationFramework, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35'

```

Not sure if anyone here is experienced with running .NET programs on Linux, but any help would be appreciated.

Thanks a bunch.

EDIT:  Posting the output of "mono --version"
```

aesclepius@Sera:~$ mono --version
Mono JIT compiler version 2.10.8.1 (Debian 2.10.8.1-5ubuntu1)
Copyright (C) 2002-2011 Novell, Inc, Xamarin, Inc and Contributors. www.mono-project.com
    TLS:           __thread
    SIGSEGV:       altstack
    Notifications: epoll
    Architecture:  x86
    Disabled:      none
    Misc:          softdebug 
    LLVM:          supported, not enabled.
    GC:            Included Boehm (with typed GC and Parallel Mark)

```

---

### Post by Mark Phelps on 2014-01-19
Have linked the WineHQ web page regarding  .Net -- perhaps you can find some useful info for the version you're trying to use: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586")

---

### Post by Elastic_Potential on 2014-01-19
I couldn't get this to work :\  Here's what happened when I tried installing .NET 4.0; I even tried upgrading MONO by building the recent stable version (it took like an hour), and it just gave me a similar error.

Running it in a Windows 7 virtual environment via Virtualbox works fine, however.  It's not the most recource-efficient solution, but it will do.

---

### Post by tdawgf on 2014-03-19
I can't be certain but this line has me wondering something. I think the program you are attempting to run uses WPF due to this error:

File name: 'PresentationFramework'

If that is the case, mono doesn't support WPF to the best of my knowledge. I could be wrong however.

---

