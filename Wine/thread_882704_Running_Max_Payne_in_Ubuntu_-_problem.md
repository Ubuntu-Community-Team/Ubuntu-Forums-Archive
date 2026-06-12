---
title: "Running Max Payne in Ubuntu - problem"
date: 2008-08-07
forum: Wine
---

### Post by Choccster on 2008-08-07
I'm trying to run the game Max Payne in Ubuntu 8.0.4 and the screen keeps flickering, which is quite annoying. I've installed the latest patch of the game (1.05) and I've tried changing various settings. Some changes made it flicker more, others had no impact.
I'm running it through the latest (stable) version of Wine. Does anyone know what I can do to get rid of said flickering?
Cheers!

---

### Post by aoanla on 2008-08-07
> **Choccster said:**
> I'm trying to run the game Max Payne in Ubuntu 8.0.4 and the screen keeps flickering, which is quite annoying. I've installed the latest patch of the game (1.05) and I've tried changing various settings. Some changes made it flicker more, others had no impact.
I'm running it through the latest (stable) version of Wine. Does anyone know what I can do to get rid of said flickering?
Cheers!

By "latest stable version of Wine", you mean 1.0.0 or 1.1.2, right?

The appdb entries suggest that Max Payne should be near perfect in any relatively recent version of Wine.

What graphics drivers and graphics card are you using? "Flickering" suggests an issue with the frame-rate, which might be related to your graphics settings.

Also, have you tried turning Compiz off? (Set your desktop effects to "None")

---

### Post by Syndacate on 2008-08-07
Max Payne was the only game I was able to run with 100% functionality (exactly like windows).

SC was decent, but both SC (starcraft: broodwars) and D2 LOD (Diablo II Lord of Destruction) have mouse issues + b.net issues :(.

This is a recommendation, and I know this isn't what you're looking for.  If you want to game and game properly, stick with Windows.  WINE is an awesome program with awesome designers behind it, but it simply doesn't have the stability that one of those games would have on Windows.

Dual boot ftw :-\.

****, I had the flickering too.  I forgot what I did to get rid of it.
Try running, when you run the game:

Well try running this first:
```
wineprefixcreate
```

Then when you go to run the game go:
```
WINEDEBUG=-all wine MaxPayne.exe
```

It may not seem it, but printing things in terminal is actually a pretty extensive process.  I've tested this in Java with some pi calculation programs, judging by rough estimated times on how long it was taking to acquire numbers, it took roughly 4x as long to get to the same # while printing out each number than it did if it didn't print out anything.

Printing in terminal takes up a lot, believe it or not.
"WINEDEBUG=-all" quiets the terminal, so it doesn't print every action, mouse click, memeory use, and key-stroke - I'm not sure if that was what I did (I had to make a few changes to play Max Payne perfectly), but I noticed a difference afterwards.  Though after I beat Max Payne, I also have Max Payne 2, and that doesn't have a good rating from the Wine Ap DB if I recall correctly, so I didn't bother with that.

Try that, see what happens, post back, I'll dig through my old posts and see what I can find - I'm like 99% sure I had that problem at one point.

EDIT:  PS:  With the debug off, all games run smoother too due to less CPU useage, though I can't recall if that's what fixed the flickering problem or not.  Try it and see...

(Dual boot ftw, as VM's can't do good vid card emulation)

---

### Post by Choccster on 2008-08-07
Thanks to you both. The only reason I installed Ubuntu was because my laptop's internal HD crashed. I have two external HDs and decided to install Ubuntu on one of them so that I had something to do whilst waiting for money to magically appear in my bank account, so that I could buy a new internal HD. It's on its way now so I think I'm just going to wait and do most of my gaming in Windows! I'll still keep Ubuntu, though because it's very swish and impressive. I thought I'd play some Max Payne so that I had something to do in the evenings after work, and I only picked it because it's one of the few games I could find the disc for.
Thanks again for your words of wisdom :)

---

### Post by CookieNinja on 2010-01-22
Strangely, I've managed to cure my flickering screen problems by turning ON desktop effects. They were off when the screen was flickering for me.

My laptop is a HP NX6325 if anyone wants to know the spec of my machine.

---

