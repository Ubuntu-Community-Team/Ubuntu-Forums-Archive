---
title: "How to Compile qjoypad on Jaunty x86_64"
date: 2009-05-03
forum: x86 64-bit Users
---

### Post by Siggma on 2009-05-03
Hopefully this works for you as well as it does for me. First install the basics for compiling and the libs necessary for the qjoypad package.

```
sudo apt-get install build-essential qt3-dev-tools libxtst-dev joystick jscalibrator
```

Plug in your gadget and run jscalibrate to be sure it's working.

That should be enough to compile qjoypad and test your device. If not, install any missing build-dep (build-dependencies) packages. There's no source in the repo so you can't use apt-get build-dep. I had a compile environment in place when I did this so all I needed were the two dependencies "qt3-dev-tools libxtst-dev" to finish the compile.

Download the source first. This direct link may or may not work. It took forever for me so I gave up and searched sourceforge for the project.
[http://sourceforge.net/project/downloading.php?group_id=98952&filename=qjoypad-3.4.1.tgz&a=81996283](http://sourceforge.net/project/downloading.php?group_id=98952&filename=qjoypad-3.4.1.tgz&a=81996283)

If the link above does not work, get the latest source (qjoypad-3.4.1.tgz) from here: [http://sourceforge.net/projects/qjoypad/](http://sourceforge.net/projects/qjoypad/)

[COLOR="DarkRed"]NOTE added July 15th 2009: Makefile (for gcc 4.3) and loop.cpp patches are available at [http://aur.archlinux.org/packages.php?ID=5573](http://aur.archlinux.org/packages.php?ID=5573)
To patch, navigate to the src/ directory. Download the two patch files and apply them. 
"patch Makefile makefile.patch" and "patch loop.cpp qjoypad.patch"
[/COLOR]
Compile it:

```
tar xzf qjoypad-3.4.1.tgz
cd qjoypad-3.4.1/src
./config
make
sudo make install
```

Now run it for testing. 

```
qjoypad&
```

You should see an icon in the taskbar. If not unplug and plugin your gadget again and run jscalibrate.
You can add it to "System->Preferences->Startup Applications" so it will start for you when you log in. Create a new item named "QjoyPad" and add this for the command:

```
sh -c "sleep 30; exec /usr/local/bin/qjoypad&"
```

Or

You can run it in a terminal while you use it
```
/usr/local/bin/qjoypad&

```

Note, it loads OK at startup but does not display right away. I haven't fiddled with it enough to figure out why.

Thanks to reading the mandriva source package dependency list (there is an 86_64 binary package for mandriva) I discovered the ubu equivalent for older qt3 development packages. Plus Archlinux has a usable source package patch in their AUR repository.

-Tom

---

### Post by Jaredu on 2009-05-28
This works Great.

Please do add this to the Ubuntu Sixaxis section... I'm attempting to play via USB but the only thing I could find there was for bluetooth! 

Awesome job man, I appreciate it.

On my install though, I did have to do sudo apt-get -f install, that may be just me, but it worked after :)

---

### Post by Siggma on 2009-05-31
I don't know what Sixaxis is, but you are welcome to add a link there.

You may notice it chews up more than it's share of CPU time. You can edit the source file named "loop.cpp". It's in ..qjoypad-3.4.1/src
```
gedit loop.cpp
```

Search for "sleep" and experiment with different values. 800 works well for my Dual Core 2GHz. If I set it any lower it fails to work correctly. Change the value in red from 100 for a 1GHZ processor to as high as 2000 for a 3+GHZ processor. Number of cores has nothing to do with this value. It's based on cpu clocks per second and thus cpu speed.

```
	//sleep for a moment. This is just to keep us from throwing all the
	//available processer power into madly checking for new events.
	usleep([COLOR="Red"]800[/COLOR]);
```

Note, if it won't compile again use:
```
make clean && make && sudo make install
```
Also, I think 30 seconds is a bit long for the startup sleep time. Below is directly from my startup applications.
```
sh -c "sleep 10; /usr/local/bin/qjoypad"
```
-Tom

---

### Post by BryanFRitt on 2009-08-02
> The default USB data rate is **125Hz**(but some overclock to 1000Hz), (1_s/**125**)/((10^-6)_s)=***8000***, so maybe the ideal setting (for USB joysticks) would be ***8000-X***, where ***X*** is the maximum time in microseconds it takes for this program to do its thing. Anybody know how to find ***X***?

from this post:
[http://ubuntuforums.org/showpost.php?p=5355005&postcount=34](http://ubuntuforums.org/showpost.php?p=5355005&postcount=34)
in this tread:
[http://ubuntuforums.org/showthread.php?t=147918](http://ubuntuforums.org/showthread.php?t=147918)

***8000*** worked good enough for me on a 2.2GHz Dual Core 2, but I'm not being finicky.

If you really don't want to miss a stroke (**1000Hz** polling USB) you can try
(1_s/**1000**)/((10^-6)_s)=***1000***
or ***1000-x***
or if you really don't want it to consume to much cpu, you could try as much as (majority of LCD monitors are **60Hz**)
(1_s/**60**)/((10^-6)_s)=***(50000/3)***, or ***approx*** ***16666.666666666...***
and so on ... (movies 24, 199.88/5, PAL 25, 50, NTSC 30, 60, 120, 119.88/4, 119.88, 599.4, 600, USB 125, 250, 500, 1000, monitor 60, 72, 75, 85, etc... )

(It's possible I misunderstand how sleep works within qjoypad, but the math is correct)

---

### Post by Constantino on 2009-10-13
guys, excuse me
i have this issue:

<command-line>: warning: missing terminating " character
<command-line>: warning: missing terminating " character
<command-line>: warning: missing terminating " character
In file included from axis.cpp:1:
axis.h:7:18: error: QTimer: Arquivo ou diretório inexistente
axis.h:8:23: error: QTextStream: Arquivo ou diretório inexistente
axis.h:9:19: error: QRegExp: Arquivo ou diretório inexistente
axis.h:10:23: error: QStringList: Arquivo ou diretório inexistente
In file included from axis.cpp:1:
axis.h:21: error: expected class-name before ‘{’ token
axis.h:22: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
axis.h:24: error: expected ‘;’ before ‘friend’
axis.h:29: error: ‘QTextStream’ has not been declared
axis.h:31: error: ‘QTextStream’ has not been declared
axis.h:40: error: ‘QString’ does not name a type
axis.h:44: error: ‘QString’ does not name a type
axis.h:89: error: ISO C++ forbids declaration of ‘QTimer’ with no type
axis.h:89: error: expected ‘;’ before ‘*’ token
axis.h:90: error: expected ‘:’ before ‘slots’
axis.h:91: error: expected primary-expression before ‘void’
axis.h:91: error: ISO C++ forbids declaration of ‘slots’ with no type
axis.h:91: error: expected ‘;’ before ‘void’
axis.cpp: In constructor ‘Axis::Axis(int)’:
axis.cpp:15: error: ‘timer’ was not declared in this scope
axis.cpp:15: error: expected type-specifier before ‘QTimer’
axis.cpp:15: error: expected ‘;’ before ‘QTimer’
axis.cpp: In destructor ‘Axis::~Axis()’:
axis.cpp:24: error: ‘timer’ was not declared in this scope
axis.cpp: At global scope:
axis.cpp:27: error: ‘bool Axis::read’ is not a static member of ‘class Axis’
axis.cpp:27: error: ‘QTextStream’ was not declared in this scope
axis.cpp:27: error: ‘stream’ was not declared in this scope
axis.cpp:27: error: expected ‘,’ or ‘;’ before ‘{’ token
make: ** [axis.o] Erro 1

---

### Post by Constantino on 2009-10-14
by the way, i compiled version 3.4.1 now and working ok =]

---

