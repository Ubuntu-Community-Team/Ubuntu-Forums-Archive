---
title: "WARNING: 64-Bit Blender in Feisty"
date: 2007-04-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by zsouthboy on 2007-04-19
I bring this up, because that's what Ubuntu installed when I went to add/remove programs, and selected Blender.

Ton has repeatedly said (and its even in the source) Blender is NOT 64-bits safe yet. It's on the agenda for 2.44 or possibly 2.5

Run Blender in a terminal - it'll give you some console output to this effect:

```

The following warning messages come from the Blender coders. The Debian 
maintainers would like to point to the following file for rationales: 
  /usr/share/doc/blender/NEWS.Debian.gz

64 bits compiles will give incorrectly saved .blend files. Do not use it.

*** If you continue to run this executable, you really are quite stupid ***

```

The NEWS.Debian says:
```

blender (2.42a-6) unstable; urgency=high

  * As of 2.43, one needs to use a ``YESIAMSTUPID'' macro in
    source/creator/creator.c to be able to compile Blender on a 64-bit system.
    This matter has not been advertised, but it mainly resides in the fact
    that Blender is not 64-bit safe, in particular with respect to saved and
    loaded files, especially when that happens between 32-bit and 64-bit
    systems. Attention was paid to 64-bit systems, efforts were made, but not
    enough to get a releasable version on those systems.

  * So, be aware that there might be issues with files manipulated on 64-bit
    systems, although everything could be or look fine. The file format might
    also change in further releases to make it 64-bit safe, which might lead
    to incompatibilities with the files saved with the current 64-bit builds.

  * After the 2.43 release, the lead developer also promised (on Freenode, on
    the #blendercoders chan):
      ``We won't do another release without 64 bits blender!''
    This problem is a priority, and it will be addressed in CVS as soon as
    possible, possibly for 2.44.

  * Interested readers might want to refer to the following thread on
    upstream's bf-committers list:
      http://projects.blender.org/pipermail/bf-committers/2007-January/017258.html

 -- Cyril Brulebois <cyril.brulebois@enst-bretagne.fr>  Mon, 14 Mar 2007 11:46:00 +0100

```

We don't need people losing their work, unknowingly, because of this.
There is only a problem in this case because nowhere is the user made aware of this possible caveat; and why wouldn't it just work?


How should this be handled?

---

### Post by zsouthboy on 2007-04-19
Here is how to fix this problem:
Do not install Blender from Add/Remove Applications. If you have already installed it, uninstall it using the same.

Then download the .tar.gz from the main blender site.

Extract to a directory of your choice.

Install 32-bit sdl lib:
sudo aptitude install ia32-libs-sdl

then it should run.

Still, something should be done about it being in the main place newbies go to install stuff in Ubuntu. Who do I contact to get this resolved?

---

### Post by zsouthboy on 2007-04-19
Ah crap.

So yeah, it installs in this way. However, I think it doesn't like the python install.

Doing anything, with any script (for example import, or export) fails, and prints 

```

Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.4/apport_python_hook.py", line 30, in apport_excepthook
    import apport.report, apport.fileutils
  File "/var/lib/python-support/python2.4/apport/__init__.py", line 1, in ?
    from apport.report import Report
  File "/var/lib/python-support/python2.4/apport/report.py", line 14, in ?
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
  File "/usr/lib/python2.4/subprocess.py", line 376, in ?
    import select
ImportError: /usr/lib/python2.4/lib-dynload/select.so: wrong ELF class: ELFCLASS64

Original exception was:
Traceback (most recent call last):
  File "<string>", line 86, in ?
ImportError: /usr/lib/python2.4/lib-dynload/math.so: wrong ELF class: ELFCLASS64



```

I don't know how to fix this one. Help?

---

### Post by stmiller on 2007-04-20
Yeah there was a big thing on the blender list earlier. Basically 64bit support is not solid, and not working correctly. 64bit blender is not recommended and not supported by the blender folks. They need help getting a 64bit version coded, if anyone can help.

---

### Post by diesel1 on 2007-05-27
Hi all, 

Check out blender.org for 2.44 64bit!

Seems to run ok.

Diesel1.

---

### Post by Kilz on 2007-05-27
> **diesel1 said:**
> Hi all, 

Check out blender.org for 2.44 64bit!

Seems to run ok.

Diesel1.

As long as you were not going to transfer files to a 32bit machine the other one was ok also.

---

### Post by benlooi on 2007-10-18
I'm having difficulties in even getting Blender 2.45 x64 to run properly. Whenever I do a render, my whole system HANGS. Black screen of death. Can't even see any error msgs. How do you install a 32bit blender on a 64bit machine?

---

### Post by Paul820 on 2007-10-18
I'm using blender 2.45 in gutsy, i have been doing for about 3 weeks now. I got the package from blender.org The only warning i got from the terminal were that it needed python 2.4.4
I'm using 64bit gutsy aswell. What's going on? If it is broken why are they allowing us to download it? Although i have not expreienced anything wrong with it.

---

### Post by henrichg on 2007-11-21
[blender.org - 64 bits support]("http://www.blender.org/development/release-logs/blender-244/64-bits-support/")
:guitar:

---

### Post by John.Michael.Kane on 2007-11-21
> **henrichg said:**
> [blender.org - 64 bits support]("http://www.blender.org/development/release-logs/blender-244/64-bits-support/")
:guitar:

That should put some blender users mind at ease.

---

### Post by OpenFish on 2007-11-21
I've bin running 2.45 for ages (its running now) and is completely fine it seems to be much more reliable than 2.44 but double b select isn't very good when running with beryl! it works fine with old .blend's off the internet too though i haven't tryed it the other way -- by the way i'm running 64 bit etch on a amd 6000 if u use lots of vertexes u may wish to get a proper graphics card as moving them can get quite a strain on a cheep card blender also has to be the easiest app to install

---

