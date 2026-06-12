---
title: "Can't instal latest wine 3.0 in 17.10"
date: 2017-12-10
forum: Wine
---

### Post by sebastian1978 on 2017-12-10
Please help! 

I opened terminal (Ctrl+Alt+T) and entered commands:

 ```
sudo apt-add-repository 'https://dl.winehq.org/wine-builds/ubuntu/' 
wget https://dl.winehq.org/wine-builds/Release.key;sudo apt-key add Release.key 
sudo apt update 
sudo apt-get install wine-devel winehq-devel 
```

After this I got Wine 2.22. What is the problem?

---

### Post by Holger_Gehrke on 2017-12-11
The problem is as the anouncement of 3.0-rc1 on winehq clearly states: "The source is available now. Binary packages are in the process of being built, and will appear soon at their respective download locations.". The binaries will be done when they are done. And as this isn't even a release but a first candidate for release (that's what rc1 means), I'd leave it alone unless you don't mind some unexpected new problems.

Holger

---

### Post by fascinus on 2018-02-18
Well, what happened is that when you try to do it, it wasn&#8217;t release yet.
But the good thing here is that it was release on January 18, 2018 and you can actually download it and install it already.

you just have to download it from the official link:

[https://www.winehq.org/announce/3.0](https://www.winehq.org/announce/3.0)

if you didn&#8217;t what to loose time, this one is the page with the package:

  [https://dl.winehq.org/wine/source/3.0/wine-3.0.tar.xz](https://dl.winehq.org/wine/source/3.0/wine-3.0.tar.xz)


you just have to extract it > **tar -xvf wine-3.0.tar.xz**

and[INDENT][COLOR=#000000] [FONT=inherit]For 32 bit -- **sudo ./configure**[/FONT]
[/COLOR][/INDENT]
[INDENT][COLOR=#000000] [FONT=inherit]For 64 bit -- **sudo ./configure --enable-win64**

and to finish:

[FONT=inherit]**sudo make && sudo make install**

You should now have installed wine 3.0


**wine --version** to know if you do it right and that's it.[/FONT][/FONT][/COLOR][COLOR=blue][FONT=inherit][COLOR=blue][FONT=inherit]



[/FONT][/COLOR][/FONT][/COLOR]Or you can simply:

[FONT=inherit]  Download the key[/FONT][INDENT][B][COLOR=#000000] wget [https://dl.winehq.org/wine-builds/Release.key](https://dl.winehq.org/wine-builds/Release.key)
[/COLOR][/B][/INDENT]
[INDENT]**[COLOR=#000000] sudo apt-key add Release.key && sudo apt-add-repository 'https://dl.winehq.org/wine-builds/ubuntu/'[/COLOR]**[/INDENT]
[FONT=inherit]Update your repos[/FONT][INDENT] **[COLOR=#000000][FONT=inherit]sudo apt-get update[/FONT][/COLOR]**
[/INDENT]
[FONT=inherit]Install wine 3.0[/FONT][INDENT] **[COLOR=#000000][FONT=inherit]sudo apt-get install --install-recommends winehq-stable[/FONT][/COLOR]**
[/INDENT]
[COLOR=blue][FONT=inherit]
[/FONT][/COLOR]
[/INDENT]

---

