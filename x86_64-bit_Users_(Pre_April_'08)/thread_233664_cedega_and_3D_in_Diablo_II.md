---
title: "cedega and 3D in Diablo II"
date: 2006-08-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by cocteau on 2006-08-10
Hi

I'm having a problem getting past the videotest in Diablo II when I running it in Cedega. The videotest completes when I had Diablo II installed under wine but not in Cedega (note that wine is not installed at present). The problem is that when it is testing direct 3D it crashes, and this is it what it says in the debug file:

15:17:10.728  Direct3DDetect...

15:17:12.732  GlideDetect...

15:17:13.740  Detecting boards which support Glide...

15:17:13.741  Missing glide3x.dll.  Assuming no 3dfx boards present!

15:17:16.752  Done with Detection phase...

In Cedega's video test both graphics test succeed.

---

### Post by Kilz on 2006-08-10
> **cocteau said:**
> Hi

I'm having a problem getting past the videotest in Diablo II when I running it in Cedega. The videotest completes when I had Diablo II installed under wine but not in Cedega (note that wine is not installed at present). The problem is that when it is testing direct 3D it crashes, and this is it what it says in the debug file:

15:17:10.728  Direct3DDetect...

15:17:12.732  GlideDetect...

15:17:13.740  Detecting boards which support Glide...

15:17:13.741  Missing glide3x.dll.  Assuming no 3dfx boards present!

15:17:16.752  Done with Detection phase...

In Cedega's video test both graphics test succeed.

That may be one little problem I overlook. Are you using ATI graphics by any chance? Because I have 2 keys and cedega and diablo installed on another computer, but its a pentium 3 with intell graphics. The video test works, but the graphics are real slow with missing tiles on the direct3d. So I dont use it.
The direct 3d with open gl may not work or work real bad from what [I have read because]("http://appdb.winehq.org/appview.php?iVersionId=49") 

"Running and Playing Diablo 2
Do not use the '-opengl' switch to run the game. Blizzard never completed OpenGL support so they removed it, but left the switch in. All you see when you run it is a badly initialized DDraw mode."

So if you do get the test to run, it isnt going to work in the game anyway. I just run it in 2d mode.

---

### Post by cocteau on 2006-08-13
Thanks for the answer.

Yes I am using an ATI card, a 9600 Mobile to make matters worse. The weird thing is that if I install D2 under wine the test runs and 3d works, as long as the screen isn't too cluttered.

I was worried that it was a problem with the 64bit ATI driver. With that installed cedega fails the 3d accelleration test, but with the fireGL they are both good.

Anyway. Diablo in 2d mode is far better than booting into windows for quick game.

---

