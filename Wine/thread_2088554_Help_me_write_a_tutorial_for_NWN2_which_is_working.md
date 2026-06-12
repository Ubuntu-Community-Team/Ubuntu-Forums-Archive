---
title: "Help me write a tutorial for NWN2 which is working."
date: 2012-11-26
forum: Wine
---

### Post by em3raldxiii on 2012-11-26
Alrighty, I'll try to make this brief.  I have successfully gotten [COLOR="Green"]NeverWinter Nights 2[/COLOR] to work in Ubuntu 12.10 using WINE and it plays quite well.  I would love to write up a how-to, but I have a classic problem:  I have been running Ubuntu on this machine for a very long time, having tweaked a variety of things to make them work perfectly over the various versions, and I am not precisely sure which "fixes" were involved in making the game work, and which "fixes" are superfluous.  [COLOR="DarkRed"]_So I need help from the community to figure out precisely what information is important_[/COLOR], and which CLI commands I can run to get a report of the important configuration settings, etc.  Things like drivers, WINE settings, and so forth.

Example:  I have installed a huge number of Windows DLLs using WineTricks and I don't know which ones are responsible for making this bad boy run.

Now, for anyone else who wants to get NWN2 to work, here's a brief outline of some of the things I did.

1.  I own NWN2, but I downloaded the UN-Patched version (1.0) with a NOCD crack which I then mounted to install the game.  I felt a tiny bit dirty doing it this way, but it is what it is.

2.  I am using wine-1.4.1

3.  I had to install the *actual* DirectX9 package using WineTricks (and probably some others, but just so you know, d3dx9_xx.dll did not do the trick on it's own, I got 3 successive errors regarding my video card until I installed directx9 using WineTricks).

4.  I am running the Open Source driver for my Radeon6550 videocard.

5.  Other things that are pertinent probably apply, but I don't know what sorts of things should be noted in my tutorial.

Finally, I don't know (and am having a hard time finding out) just what steps are "morally ethical" and which steps should include a disclaimer.  I realize that one or more of the steps I took probably include steps that go against various End User licenses and so forth.  Guidance here would be appreciated.

So any help with this tutorial would be great.  Once I have all my ducks in a row, I will add an entry to the AppDB on WineHQ.

Thanks!

---

