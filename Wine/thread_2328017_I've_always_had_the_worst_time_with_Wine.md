---
title: "I've always had the worst time with Wine"
date: 2016-06-16
forum: Wine
---

### Post by cblnchat on 2016-06-16
Hey there,

So I've always had a terrible, terrible time with Wine. I think it's one of the reasons I stopped using Ubuntu a few years ago. I just couldn't get it to work.

But it seems like its come quite a ways in the last few years so I just want to ask a few questions. 

My main one is: What is the easiest way to get the Windows version of Steam and those Windows games to work?

I found [this]("http://stardewvalleywiki.com/Linux") page for Stardew Valley where it seems like the easiest way is Play On Linux, but will this install of Steam in Wine also work for other games? 
Btw I do realize each game needs to be supported in Wine to work at all. 

Also on [this]("https://appdb.winehq.org/objectManager.php?sClass=version&iId=32314") page for World of Warcraft it says the Wine version is 1.9.9, will it work as well on versions other than that one? Also how do I get 1.9.9? When I installed Wine it came with version 1.6.2.

These are all probably very basic questions everyone will hate me for asking, but Wine is my new ndiswrapper problem and it's very frustrating.

---

### Post by TheFu on 2016-06-16
If you primarily want to run Windows games, then you should boot Windows.  For the casual gamer, WINE provides an subset of the Windows API in a translation layer. It is not a full implementation, so when there are bugs in 
a) WINE
b) Windows
c) Linux
the programs being run may not perform as expected. For example, WINE tends to work best with a 32-bit API layer, not 64-bit. That means 32-bit compatibility libraries are needed for 64-bit Linux installations.  This can cause other issues on a system, though it shouldn´t.

I´ve never used Play On Linux, so cannot answer that aspect.
I´ve only used WINE to make Quicken work about 80%.  As more and more parts that I needed to work failed, it was just easier to move Quicken into a VM that was already using Windows here.

What is the easiest way to run Windows games?  Run Windows.

How to install WINE v1.9.9?   Use the source, Luke.  Or use a PPA (preferred): [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)
Installing anything with source code breaks the fantastic package management that most Linux distros provide. You are accepting full responsibility to patch those programs and libraries manually forever.

---

### Post by cblnchat on 2016-06-16
Okay I didn't know that 32-bit libraries were needed for the best work, I'll make sure to look into that.

And my current goal is to run Ubuntu exclusively. I've been going into Windows when I want to do something that is easier in Windows. But I don't like rebooting and going into Windows when I need to. I'd rather have everything in one OS, and I really like Linux.

I also feel a bit dumb, I think I came across that PPA info but I don't think I read it fully.

Thank you for the info

---

### Post by TheFu on 2016-06-16
Virtual machine?  I haven´t dual-booted in years, but I don´t game very much.

---

### Post by Mark Phelps on 2016-06-17
> **cblnchat said:**
>  ... And my current goal is to run Ubuntu exclusively. I've been going into Windows when I want to do something that is easier in Windows. But I don't like rebooting and going into Windows when I need to. I'd rather have everything in one OS, and I really like Linux.

I understand and appreciate your goal -- but you need to understand two things: (1) that goal conflicts with running Windows games, (2) at some point you are going to have to make a choice between these two contradictory goals.

Why?

Because the long-term experience of using Wine for Windows gets worse, not better.  This is because the Windows app and game developers are using more and more Windows-only stuff that does not work in Wine.

Consider that at one time, BOTH MS Office and Internet Explorer (the two most commonly used apps in Windows) worked great in Wine.  But that was in 2007 -- 9 years ago!  Current MS Office versions include 2016 and Office 365, neither of which works at all in Wine.  Current MS Browsers include IE v11 and Edge, neither of which works at all in Wine.

Sure, Steam has made a difference in Gaming, but eventually, current Windows games will not run in Linux -- period.

---

### Post by cblnchat on 2016-06-17
> **Mark Phelps said:**
> I understand and appreciate your goal -- but you need to understand two things: (1) that goal conflicts with running Windows games, (2) at some point you are going to have to make a choice between these two contradictory goals.

Why?

Because the long-term experience of using Wine for Windows gets worse, not better.  This is because the Windows app and game developers are using more and more Windows-only stuff that does not work in Wine.

Consider that at one time, BOTH MS Office and Internet Explorer (the two most commonly used apps in Windows) worked great in Wine.  But that was in 2007 -- 9 years ago!  Current MS Office versions include 2016 and Office 365, neither of which works at all in Wine.  Current MS Browsers include IE v11 and Edge, neither of which works at all in Wine.

Sure, Steam has made a difference in Gaming, but eventually, current Windows games will not run in Linux -- period.


You're completely right. I've been thinking kind of along those lines. 
I'm glad I didn't completely get rid of my Windows install. 

I actually remember running MS Office back then when I needed it in Wine (because I was young and didn't think I would ever need Windows...boy was I wrong)

I guess I'll HAVE to keep jumping back to Windows when I want to play a game that isn't supported on Linux.

One day I'll probably go 100% Linux again. But for now I just like to game too much.

---

