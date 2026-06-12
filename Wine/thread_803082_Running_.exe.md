---
title: "Running .exe"
date: 2008-05-22
forum: Wine
---

### Post by Paris Heng on 2008-05-22
Dear,

How to run the .exe in Ubuntu? I know that using Wine. But so far I never sucess, keeps giving error, please give some link that really successful in running the Wine.

---

### Post by yaknowwat on 2008-05-22
You shouldn't depend on Wine for running .exe.  I would have to suggest either finding an alternative to the application otherwise, virtual machine or dual boot for the application.


The reason linux cannot run .exe's (windows binaries)  because linux is not windows just like windows cannot run linux binaries because windows is not linux.

---

### Post by SunnyRabbiera on 2008-05-22
It depends on the application, wine is not perfect.
If there is a software you want try to find a linux alternative.

---

### Post by vibinlakshman on 2008-05-22
Wine is beta version dont try it..

---

### Post by EXCiD3 on 2008-05-22
Wine will be version 1.0 on friday! :D

To run an application with wine do this in terminal:
```
wine <path to .exe>
```

As mentioned before, Wine will not work with a LOT of applications and may take special configuration. You can see if the app you are trying to run is compatible at the Wine Database: [http://appdb.winehq.org/](http://appdb.winehq.org/)

Your best bet would be to install windows in a virtual machine that way you are guaranteed compatibility.

---

### Post by p_quarles on 2008-05-22
Moved to the Wine section.

---

### Post by SunnyRabbiera on 2008-05-22
> **vibinlakshman said:**
> Wine is beta version dont try it..

actually by all accounts wine will always be a beta, its taken it a long time to get this far.

---

### Post by EXCiD3 on 2008-05-22
> **vibinlakshman said:**
> Wine is beta version dont try it..

and look at the version numbers of most of your linux apps...alot of them havent passed version 1.0 yet. We wouldnt be using linux if we were afraid of using software in beta. Fortunately for us beta software in linux is stable for the most part and isnt anywhere near as buggy as windows beta software. ;)

---

### Post by Sleaka J on 2008-05-22
I was under the impression that Wine 1.0 Release Candidate 2 (RC2) was being released on Friday, not Wine 1.0, and that Wine 1.0 would be released another 2 weeks after that.

Still waiting for better DirectX 9 support though  as I'm stuck running Team Fortress 2 in Windows for now as I like my DirectX 9 look (The DX8 look pales in comparison and I like my eye candy).

---

### Post by srawat on 2008-05-22
[FONT="Verdana"]hi
I have just installed ubuntu 8.04 and I am using linux for the first time. 
I am having problems in accessing .exe files. From other threads I came to know that I need to install wine for this. But all the links I got were for installing it directly on ubuntu via internet. My problem is, that my net requires a setup file to run and only then I can access net through that installed file by logging in there. And I can't run .exe files on ubuntu. How can i install wine without net?
please help [/FONT]

---

### Post by Paris Heng on 2008-05-22
Any alternative to Wine? 

If using virtual machine and put the Ubuntu under Windows, the graphic or the display of the Ubuntu is not nice, the margin of interface run away (you need to scroll for this case), the text is too small, can't even see it. So i not prefer Virtual machine.

---

### Post by Paris Heng on 2008-05-22
> **srawat said:**
> [FONT="Verdana"]hi
I have just installed ubuntu 8.04 and I am using linux for the first time. 
I am having problems in accessing .exe files. From other threads I came to know that I need to install wine for this. But all the links I got were for installing it directly on ubuntu via internet. My problem is, that my net requires a setup file to run and only then I can access net through that installed file by logging in there. And I can't run .exe files on ubuntu. How can i install wine without net?
please help [/FONT]

Download the binary from below link and compile it.
[URL="http://www.winehq.org/site/download"]
http://www.winehq.org/site/download[/URL]

---

### Post by ajackson on 2008-05-22
> **Paris Heng said:**
> Dear,

How to run the .exe in Ubuntu? I know that using Wine. But so far I never sucess, keeps giving error, please give some link that really successful in running the Wine.
It might help if you told us what you are trying to run, what version of wine you are using and what errors you are getting. Just saying I'm having trouble running .exe isn't all that helpful or informative.

---

### Post by cogadh on 2008-05-22
> **Sleaka J said:**
> I was under the impression that Wine 1.0 Release Candidate 2 (RC2) was being released on Friday, not Wine 1.0, and that Wine 1.0 would be released another 2 weeks after that.

Still waiting for better DirectX 9 support though  as I'm stuck running Team Fortress 2 in Windows for now as I like my DirectX 9 look (The DX8 look pales in comparison and I like my eye candy).
That is the impression I have as well, we would be getting release candidates until June, then a real 1.0 release. After that, releases will be split into a stable version and an unstable version (possibly).

DirectX 9 support is about 95% complete already, I don't think there is really much left to improve.


> **Paris Heng said:**
> Dear,

How to run the .exe in Ubuntu? I know that using Wine. But so far I never sucess, keeps giving error, please give some link that really successful in running the Wine.
As ajackson said, you need to give us more information before we can really help. However, in the meantime, you might want to check out a few of the sticky threads at the top of this forum for some pointers on things you can try.

---

### Post by aoanla on 2008-05-22
> **cogadh said:**
> 

DirectX 9 support is about 95% complete already, I don't think there is really much left to improve.

Which does confuse me - using DirectX 9 rendering paths seems to be much less efficient in the current Wine implementation than DirectX 8, especially (as previously noted) in Source-engine games. Indeed, TF2 and Portal are almost unplayable with DirectX 9 turned on...

I just hope the mysterious "missing 5%" improves matters ;)

---

### Post by cogadh on 2008-05-22
It really doesn't seem to make sense, but if you think about it, there could be many explanations for the issue: 
- Its entirely possible that the coding is (nearly) complete, but still needs to be optimized some. 
- The translation from DX9 to OpenGL might not be as "clean" as it is with DX8. 
- It could have something to do with the capabilities of the video drivers in Linux being somewhat lacking in comparison to the Windows drivers. 
- It also seems to me that the problem only really occurs with Source-based games (at least for me), so it might have nothing to do with Wine's DX9 support at all, but rather Source itself.

Then again, maybe that "mysterious missing 5%" is the whole key to the performance issue. I guess we'll just have to wait and see.:)

---

### Post by Sleaka J on 2008-05-23
> **cogadh said:**
> 
- It could have something to do with the capabilities of the video drivers in Linux being somewhat lacking in comparison to the Windows drivers. 


I seriously don't think that's the case for the drivers.

I get exactly the same performance in the Linux client of Quake Wars as I do in Windows Quake Wars, so that rules out an underperforming video driver. I'm quite sure that someone would have figured out if the drivers were lacking by now (considering a good number of Linux users are quite capable of finding out such a thing).

The others reasons are quite likely though. I haven't tried out anything but Team Fortress 2 and Half-Life 2: Deathmatch using Wine. Performance in both suck using DirectX 9 (In fact, HL2:DM crashes a lot for me using any DX path).

Here's hoping that extra 5% makes the game playable using DX9.

---

### Post by cogadh on 2008-05-23
The performance of a single game is not a true comaprison test of the drivers. All you have confirmed is that Quake Wars makes use of the same OpenGL functionality on both systems and that functionality alone is used with equal performance on both systems. Wine translating Direct3D calls to nearly equivalent OpenGL calls is a completely different animal. For all we know, whatever calls the Source engine makes are being translated into OpenGL functions that are poorly implemented in the Linux OpenGL drivers, when compared to the original Direct3D function in Windows. Its all just speculation, but you can't really rule out anything at this point.

---

