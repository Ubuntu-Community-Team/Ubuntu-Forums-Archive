---
title: "Microsoft Office 2007 in Ubuntu?"
date: 2008-06-21
forum: Wine
---

### Post by Sebazzz on 2008-06-21
Anybody know how to install Microsoft Office 2007 using Wine? (Step-by-step tutorial) I'm using Ubuntu 8.04 LTS and my Microsoft Office 2007 version is Enterprise version. Thanks!!!
Note: Do not suggest using Crossover Office because it's Comercial!

Open-Source Rules!!!:evil::evil::evil:

---

### Post by hikaricore on 2008-06-22
I don't see your problem with Crossover, they are in direct relations with the WINE project and donate patches/money to the community.

Anyway... moving on.

From the looks of it: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

Microsoft Office 2007 is sketchy at best under WINE.
Probably better off using OpenOffice or running MS Office on a virtual machine.

Best of luck.

--Aaron

p.s. I'd also like to point out the irony of trying to run a Microsoft product and stating "Open-Source Rules!!!" at the end of your post.

---

### Post by upchucky on 2008-06-22
The entire office suite for ms office is about $500.00, assuming u have legit copy, Openoffice does everything ms office does, openoffice is free.

there are those that use enhanced ms office embedding that only works in ms office, however when they use such embedding they are assuming that the entire world uses it too, not so!  if someone does lets say a Resume', with special embedding, and a potential employer cant open it properly cause he does not use ms office. the resume is useless as it will only open as a garbled mess.

there are file converters that try to compensate for the world domination bloat-ware effect of ms software, but they do not always produce the intended results.

With the cost of ms, and the problems using it, all i can say is, why?

---

### Post by Kinst on 2008-06-22
Sure it's easy.


1. You need a native copy of rpcrt4.dll. This is the most important step. Only some of them will work. I think the vista one works. Put it in /home/you/.wine/drive_c/windows/system32.

2. ```
wget www.kegel.com/wine/winetricks
```

3. ```
sh winetricks msxml3 dotnet20 gdiplus riched20 riched30 vcrun2005sp1
```

4. Run setup.exe.

5. Tell me if you're confused.

---

### Post by Druke on 2008-06-24
this works with onenote, and everything else?

---

### Post by Jordysportracing on 2008-06-25
> **Kinst said:**
> Sure it's easy.


1. You need a native copy of rpcrt4.dll. This is the most important step. Only some of them will work. I think the vista one works. Put it in /home/you/.wine/drive_c/windows/system32.

2. ```
wget www.kegel.com/wine/winetricks
```

3. ```
sh winetricks msxml3 dotnet20 gdiplus riched20 riched30 vcrun2005sp1
```

4. Run setup.exe.

5. Tell me if you're confused.



I am very confused cos i am an almost novice at ubuntu and i don't understand step 1 lol thanx

---

### Post by Kinst on 2008-06-26
Okay...In your home folder you need to enable hidden files. Then look for the .wine folder. Put [this file]("http://www.dll-files.com/dllindex/dll-files.shtml?rpcrt4")(i hope) in .wine/drive_c/windows/system32

Copy+paste this into the terminal
```
wget www.kegel.com/wine/winetricks
```
```
sh winetricks msxml3 dotnet20 gdiplus riched20 riched30 vcrun2005sp1
```

```
winecfg
```
Then using winecfg, open the override tab and make sure rpcrt4, msxml3, riched20 and riched32 are set to native. Hope that makes sense.

---

### Post by Jordysportracing on 2008-06-30
> **Kinst said:**
> Okay...In your home folder you need to enable hidden files. Then look for the .wine folder. Put [this file]("http://www.dll-files.com/dllindex/dll-files.shtml?rpcrt4")(i hope) in .wine/drive_c/windows/system32

Copy+paste this into the terminal
```
wget www.kegel.com/wine/winetricks
```
```
sh winetricks msxml3 dotnet20 gdiplus riched20 riched30 vcrun2005sp1
```

```
winecfg
```
Then using winecfg, open the override tab and make sure rpcrt4, msxml3, riched20 and riched32 are set to native. Hope that makes sense.

Done everything there and it won't start installing ie i get to the install bar screen but it doesn't move from there. is it the type of 2007 i am using?

---

### Post by Kinst on 2008-06-30
Yeah...um...I *think* that's because of the rpcrt4 file I gave you. I can promise it will work for wine 0.9.58, but for the latest wine there's another tweak I'm missing or something.

If you want, compile [wine 0.9.58 from source]("http://sourceforge.net/project/downloading.php?group_id=6241&use_mirror=internap&filename=wine-0.9.58.tar.bz2&19937605") by following the readme. It'll take about half an hour to compile.

When you're done installing you can upgrade back to wine 1.1. 

I don't know how much that helps. :(

---

