---
title: "Compile source code to install older wine version?"
date: 2011-08-20
forum: Wine
---

### Post by emcphers on 2011-08-20
So apparently the newer versions of wine have trouble running Office 2007. I have an Office 2007 .exe (rather than a CD because I'm on a netbook) and can only get to the very beginning of the install process. It says it can't proceed because I'm not connected to the internet, which is crazy.

I found the wineHQ .deb packages archive, but I'm having a hard time compiling the source code for version 1.1.14 (Or maybe a should be using the binary package?)

I'm hoping someone could explain to me how to do the install once I've downloaded the .deb package (a tar.gz file). E.g., what to do with the extracted files. (Compile using the terminal?)

Thanks in advance for your help!
Emily

---

### Post by emcphers on 2011-08-20
I can get to step 4 on [these directions]("https://help.ubuntu.com/community/CompilingEasyHowTo"), but it doesn't explain how to use the "make" command (and I haven't been able to find info on that by searching around).

---

### Post by disabledaccount on 2011-08-20
The instructions on Ubuntu page are "general" way of compiling from source. In case of wine it's a bit different:
1. Get the wine source in desired version:
[http://sourceforge.net/projects/wine/files/Source/](http://sourceforge.net/projects/wine/files/Source/)
2. Install dependancies:
sudo apt-get install build-essential (optionally also checkinstall)
sudo apt-get build-dep wine
3. Look here for the how to compile it:
[http://www.winehq.org/docs/wineusr-guide/installing-wine-source](http://www.winehq.org/docs/wineusr-guide/installing-wine-source)

After ./configure check error messages before compilation - otherwise You can land with no sound support or other strange effects.
Additionaly ./configure --help will show many interesting options, like setting prefix for installation - thanks to that You can have two (or more) versions of wine in the system.

---

### Post by emcphers on 2011-08-21
Thanks so much for your response!

Can I ask a couple more questions? Here goes:

Should I remove my current version of wine before installing an older one? I thought that was the thing to do, but if you say that you can have multiple versions on your system then maybe not.

How do I navigate to the wine source tree? Is it "cd Downloads" (if that's where I put the tar folder).

Thanks again,
Emily

---

### Post by emcphers on 2011-08-21
Nevermind. I got it.

Awesome.

---

### Post by emcphers on 2011-08-21
Oh wait. 

```
emo@emo-1215T:~$ wine office.exe
wine: could not load L"C:\\windows\\system32\\office.exe": Module not found
emo@emo-1215T:~$ err:menubuilder:WinMain unknown option -a
err:menubuilder:WinMain unknown option -r
```

There must be a problem with my wine installation, right?

It would be great if anybody could let me know how I might diagnose this.

Thanks!
Emily

---

### Post by disabledaccount on 2011-08-21
I would say that file path is incorrect - it should be something like "c:\\Program Files\\Microsoft Office\\office.exe", unless You've changed default installer settings
Additionally it's sometimes necessary to cd (change working directory) to where the file is placed before running the program.

---

