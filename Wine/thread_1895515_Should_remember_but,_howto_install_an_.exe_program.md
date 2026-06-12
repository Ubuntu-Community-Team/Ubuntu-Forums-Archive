---
title: "Should remember but, howto install an .exe program?"
date: 2011-12-14
forum: Wine
---

### Post by Bobrm2 on 2011-12-14
I got a new TOMTOM XXL 550 and the installing requires me to convert(?) a .exe to run the install. The problem is so simple that I can't locate a howto so I can proceed. Can someone point me in the right direction.:confused:

I haven't call TOMTOM's help yet, thinking that it's a windose world program.

Running Ubuntu 11.10 with a Gnome desktop.

Thanks

Bob

---

### Post by claracc on 2011-12-15
You have to install an .exe program in wine, so first of all, you have to install wine: sudo apt-get install wine (in a xterm), and then install the .exe program with wine.

---

### Post by llamabr on 2011-12-15
wine is very rarely the correct solution to your problem.  Instead, there is probably a native application that will do what you want.

What does your exe do, or what do you need a program to do?  Probably, we can suggest one that will actually work.

---

### Post by johnisaac17 on 2011-12-15
So Wine is what we should use to install exe programs like in windows?
I use wine but sometimes have trouble opening them. Or they don't work correctly.

---

### Post by claracc on 2011-12-15
> So Wine is what we should use to install exe programs like in windows?

Yes, when you want to run an .exe (windows program) in ubuntu yo have to install it with wine and run it into wine. If you are lucky, the program will run, but no all .exe software is capable of running inside wine, you can look for your .exe app in wine database: [http://appdb.winehq.org/](http://appdb.winehq.org/) and obtain some useful tips.

Other you can try is palyonlinux but I think is fundamentally dedicated to .exe videogames?

---

### Post by Elfy on 2011-12-15
Thread moved to Wine.

---

### Post by Mark Phelps on 2011-12-15
If you're trying to install SW to use the GPS, or even worse, trying to install drivers to use it -- the first is most likely NOT to work, the second definitely will NOT work.  You can't use Wine to install Windows drivers.

---

### Post by Bobrm2 on 2011-12-15
Spoke with TOMTOM rep., TOMTOM is not compatible with Linux, i.e. can't down load maps updates. Does anyone know of a workaround?
Bob

---

