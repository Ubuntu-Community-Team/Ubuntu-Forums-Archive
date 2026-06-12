---
title: "xAcetoneISO2"
date: 2007-07-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by jusmurph on 2007-07-20
So i found how to get Acetone working in Gnome (xAcetoneISO2) but it refers to a 32bit deb for fuseiso. 

Has anyone got this working on 64?

---

### Post by bulletxt on 2007-07-30
xAcetoneISO2:


where did you get the deb of it? it is till in beta 1 stage and it is released only as an installer.

what problems are you having? if you are on a 64 bit read the manual on official website

---

### Post by bulletxt on 2007-09-02
64-bit users

Install a package then:
-install libqt4-dev
-download AcetoneISO2-generic-src.tar.gz (Source download), uncompress,
enter src dir and compile:
qmake-qt4
make
Then replace /usr/bin/acetoneiso2 with the new acetoneiso2 file in src directory.

NOTE: if you get an error when doing qmake-qt4, simply type qmake.


[http://www.acetoneteam.org/faq.html](http://www.acetoneteam.org/faq.html)

---

### Post by jusmurph on 2007-09-02
> **bulletxt said:**
> 64-bit users

Install a package then:
-install libqt4-dev
-download AcetoneISO2-generic-src.tar.gz (Source download), uncompress,
enter src dir and compile:
qmake-qt4
make
Then replace /usr/bin/acetoneiso2 with the new acetoneiso2 file in src directory.

NOTE: if you get an error when doing qmake-qt4, simply type qmake.


[http://www.acetoneteam.org/faq.html](http://www.acetoneteam.org/faq.html)

Cheers!

---

### Post by wikiguy on 2007-10-08
thanks a lot bullet that how to works perfectly:guitar:

---

### Post by supersonicdarky on 2007-10-20
am I missing something here, or am I supposed to type something after **qmake-qt4**? All I get is

```
kernel@laptop:~/Desktop/acetoneiso2$ qmake-qt4
Usage: qmake-qt4 [mode] [options] [files]

QMake has two modes, one mode for generating project files based on
some heuristics, and the other for generating makefiles. Normally you
shouldn't need to specify a mode, as makefile generation is the default
mode for qmake, but you may use this to test qmake on an existing project

Mode:
  -project       Put qmake into project file generation mode
                 In this mode qmake interprets files as files to
                 be built,
                 defaults to *.c; *.ui; *.y; *.l; *.ts; *.qrc; *.h; *.hpp; *.hh; *.hxx; *.H; *.cpp; *.cc; *.cxx; *.C
  -makefile      Put qmake into makefile generation mode (default)
                 In this mode qmake interprets files as project files to
                 be processed, if skipped qmake will try to find a project
                 file in your current working directory

Warnings Options:
  -Wnone         Turn off all warnings
  -Wall          Turn on all warnings
  -Wparser       Turn on parser warnings
  -Wlogic        Turn on logic warnings

Options:
   * You can place any variable assignment in options and it will be     *
   * processed as if it was in [files]. These assignments will be parsed *
   * before [files].                                                     *
  -o file        Write output to file
  -unix          Run in unix mode
  -win32         Run in win32 mode
  -macx          Run in Mac OS X mode
  -d             Increase debug level
  -t templ       Overrides TEMPLATE as templ
  -tp prefix     Overrides TEMPLATE so that prefix is prefixed into the value
  -help          This help
  -v             Version information
  -after         All variable assignments after this will be
                 parsed after [files]
  -norecursive   Don't do a recursive search
  -recursive     Do a recursive search
  -cache file    Use file as cache           [makefile mode only]
  -spec spec     Use spec as QMAKESPEC       [makefile mode only]
  -nocache       Don't use a cache file      [makefile mode only]
  -nodepend      Don't generate dependencies [makefile mode only]
  -nomoc         Don't generate moc targets  [makefile mode only]
  -nopwd         Don't look for files in pwd [project mode only]

```

same for **qmake**

---

### Post by bulletxt on 2007-10-20
you are in acetoneiso2 folder. wrong!

as clearly stated above you must enter src directory!

cd src !

---

### Post by supersonicdarky on 2007-10-20
haven't used ubuntu in a month, and i forgot such a simple thing.  thnx :)

---

