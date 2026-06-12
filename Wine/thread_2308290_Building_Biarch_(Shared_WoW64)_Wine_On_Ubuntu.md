---
title: "Building Biarch (Shared WoW64) Wine On Ubuntu"
date: 2016-01-01
forum: Wine
---

### Post by steven-misshula on 2016-01-01
Happy New Year!

So, I'm trying to install Wine on my 64 bit cpu/install (running Ubuntu 15.10)

I'm following the guide on Wine HQ found at:   [http://wiki.winehq.org/BuildingBiarchWineOnUbuntu](http://wiki.winehq.org/BuildingBiarchWineOnUbuntu)

I think I've got everything correct so far, but when I get to the part titled, 
[h=1]Build 32-bit Wine[/h](about 2/3 of the way down the page)

The first set of code:
```

mkdir $HOME/wine32-tools
cd $HOME/wine32-tools
make clean
~/wine-git/configure
make -j4
```

goes fine....

but when I get to the second set:
```

mkdir $HOME/wine32
cd $HOME/wine32
make clean
~/wine-git/configure --with-wine64=$HOME/wine64 --with-wine-tools=$HOME/wine32-tools
make -j4
```
I get the following error:
```

make: *** No rule to make target 'clean'.  Stop.
```

Any thoughts?  I'm guessing that I compiled something in a wrong directory...but just don't know where it might be....  :-(

Thanks,
Steve

---

### Post by steven-misshula on 2016-01-02
So... 

I was instructed to try and continue with out the "make clean" line....


I followed the directions and I believe that  I have things installed more or less correctly.  However, I have some  ongoing issues:

1. I don't get the wine console (where you configure wine - i.e. choose which operating system etc.
2.  My MS Office doesn't seem to be working when I try to install with  setup.exe, it cycles through and crashes.  I had a previous install  where it worked...
3.  Wine doesn't show up in my Applications list when I click the Ubuntu top left icon

My Synaptic Package Manager shows the following:

1. winehq-devel 1.9~ubuntu 15.10
2. wine-devel 1.9~ubuntu 15.10
3. wine-devel-amd64 1.9~ubuntu 15.0
4. wine-devel-i386:i386 1.9~ubuntu 15.0

any further thoughts?
Many thanks in advance
Steve

---

### Post by Bucky Ball on 2016-01-02
Why don't you install it directly from the Ubuntu repostitories? Software Centre or Synaptics> search for and install Wine ...

---

### Post by steven-misshula on 2016-01-03
Hi Bucky,

I had done that...and still wound up with problems...I had thought it was because the repository was Wine 1.6.  So, I had uninstalled ... broke a few things...rebuilt them with help of Matt Symes and then proceeded to rebuild Wine.  I thought doing it by source following directions on Wine HQ would curb the problems.

Following some more directions, I see that 

```
winecfg

```
works...no problem.

But when i try to install MS Office 2007, I get problems (application gets hung up looking for a file in MS Access- which is there in the folder).  

I posted the last 20 or so lines of terminal output on my Wine HQ thread 

([https://forum.winehq.org/viewtopic.php?f=8&t=25956](https://forum.winehq.org/viewtopic.php?f=8&t=25956)), 

but was able to attach the full file here.

[ATTACH]266522[/ATTACH]

Again, thanks for the help....much appreciated.

Steve

---

### Post by steven-misshula on 2016-01-12
Well - I had to abandon ship here as the deadline for my excel is looming.

I ran the sudo make uninstall from the directories (see post in WINEHQ:  [https://forum.winehq.org/viewtopic.php?f=8&t=25956&p=103636#p103636](https://forum.winehq.org/viewtopic.php?f=8&t=25956&p=103636#p103636))  , but I'm guessing I installed elsewhere as well?  Not sure.

In  the end, I reformatted my drive and loaded Linux Mint (a 32 bit install  on my 64 bit machine); which installed EASILY ! ! Easier than with  Ubuntu!

and Wine and subsequently MS Office seem to be working  really well...not sure what the difference is...and the final touch for  anyone who is reading:  You must override 

Riched20.dll

This  will allow your graphs in Excel to display values on the axis, data  table, graph name(s) etc.  It also allows Power Point to function.

**NOTE to DEVELOPERS**

There  are substantial numbers of "quasi-techs" like me who either run Linux  or would like to but are stymied, because they need MS Office  functionality (not our fault - it is the demand of the workplace &  Open / Libre Office does not have as robust functionality,ease of use,  nor well designed graphics). 

Development of an install script  for 64 bit machines/OS's that eliminates the terminal code or certain  steps such as setting up the container would be **extremely** helpful.

Many thanks to dimesio who helped me...and buckey

Steve

---

### Post by Bucky Ball on 2016-01-12
Any feedback for Canonical or its developers is misdirected here and if you have feedback for developers of WINE or Open/Libreoffice please contact those projects directly. 

We are all volunteers here, not Canonical developers or employees.  :)

Glad you got it working and thanks for sharing how. Please mark the thread as solved (see first link in my signature). Good luck.

---

