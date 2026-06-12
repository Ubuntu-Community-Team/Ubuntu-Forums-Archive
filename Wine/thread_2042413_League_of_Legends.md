---
title: "League of Legends"
date: 2012-08-14
forum: Wine
---

### Post by plzdontkillme11 on 2012-08-14
Hi,

I've got LoL working on Ubuntu 12.04 through Play on Linux. However, when in a game, the colors are very "dark." Since I know I did a terrible job of explaining the situation, I attached a picture. 

On another note, the FPS is low - around 15-20 - does anybody have any suggestions for this? 

My computer: Acer Aspire TimelineX; 4 GB RAM, Intel Core i3, and Intel Graphics. 

Thanks!

---

### Post by plzdontkillme11 on 2012-08-16
Bump.

---

### Post by madjr on 2012-08-16
woa am gona try it on linux now !

its the only thing making me dual boot, didnt know it worked.

how much FPS you get in windows?

anyway apart from HoN which works on linux natively, I believe dota2 will also make it soon thanks to valve/steam. And riot is planning on making a port to mac (iLOL) which I've been told should also work on linux once official (ilol is probably based on wine).

Here is are dedicated threads maybe you can find answers for this:

[http://na.leagueoflegends.com/board/showthread.php?t=2107392](http://na.leagueoflegends.com/board/showthread.php?t=2107392)
[http://na.leagueoflegends.com/board/showthread.php?t=1946188](http://na.leagueoflegends.com/board/showthread.php?t=1946188)

and maybe this:
[http://www.youtube.com/watch?v=8zAHMUwcfm8](http://www.youtube.com/watch?v=8zAHMUwcfm8)

---

### Post by plzdontkillme11 on 2012-08-16
Thanks for the reply. In windows my FPS is usually around 50. I've heard the same regarding the port to Mac, so I'm pretty excited for that, haha. The only reason I don't stay on Linux is because I am addicted to this game. 

I'll check out those links you posted soon and come back.

---

### Post by plzdontkillme11 on 2012-08-18
No luck so far. Same problems; store still doesn't work, in game graphics are still "dark," and FPS is low.

---

### Post by plzdontkillme11 on 2012-08-20
Bump.

---

### Post by plzdontkillme11 on 2012-08-22
Bump. Is my issue really that rare?

---

### Post by madjr on 2012-08-23
> **plzdontkillme11 said:**
> Bump. Is my issue really that rare?

Well the problem is that since is not native , most linux users prefer [HoN]("http://heroesofnewerth.com/") which is also free and works very good.


But I know you prefer LoL right now so, I would try some of the things here:

[http://maketecheasier.com/run-fullscreen-games-in-linux-with-dual-monitors/2010/03/01](http://maketecheasier.com/run-fullscreen-games-in-linux-with-dual-monitors/2010/03/01)

specially this part: "**windowed** mode in Wine".

running it in a smaller window might help.


Also this person seems to have partially solved a similar issue for [Diablo3]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=25953") (scroll down to "*Running on i3 graphics*").


If you're still up for it, Another thing is you can [ask how the iLOL]("http://na.leagueoflegends.com/board/forumdisplay.php?f=31") mac/linux port is going and if there's anything for you to help test and give feedback.


Anyway if things improve pls keep us updated, Thx!

---

### Post by markackerman8@gmail.com on 2012-11-25
I am having the same issue - it is way too dark to play well.

The mostly black screen was solved by running PlayOnlinux in Terminal via:  
$ force_s3tc_enable=true playonlinux

but now too dark arghhhhhhh - please Help.

Mark

p.s. windowed through PoL/wine didnt help, and I suspect it may be related to Ubuntu only using my Intel Integrated HD3000 and not my discret4 Ati/Radeon Mobiolity 6850m wich is another huge issue that if anyone can help me with I would surely appreciate it.

---

### Post by donaldhall on 2012-11-26
I see that this thread is a little old. What version of wine are you using on PoL for your LoL? If not using the newest version for LoL which I believe its 1.5.5 then try switching it to that version. May need to reinstall the LoL client and everything.  

Also what version of Ubuntu/Linux are you using? 

I got it working this week end and everything runs fine. I am using 12.10.

---

### Post by markackerman8@gmail.com on 2012-11-26
thank you very much, for a very quick response – Donald.
Play on the next advise using 1.5.3 or 1.5.5, and I used both, but still no luck.  I am using Ubuntu 12.04, 64-bit.  On an HP, Envy 17–2195ca, with the integrated HD3000 video card associated with the Intel I7 CPU, and the discrete AMD – Radeon 6850m card, which I suspect is not being used,** very sadly**.  sadly, I am writing this from Windows, as it's keeping me there, but I will try and reinstall the game within the hour - As you suggested.  Assume that that won't work.  If it does work, I will definitely amend this posting.  Thanks again, and thanks in advance for your help, 
Mark.

---

### Post by donaldhall on 2012-11-26
Are you using the Pre-defined install for PoL? Also I am having trouble with LoL and that it will only work in a emulated desktop environment. 

Please follow the guide that I found most useful for the instalation. But I am using 1.5.5

[https://www.youtube.com/watch?v=pz4eWUXsojw](https://www.youtube.com/watch?v=pz4eWUXsojw)

---

### Post by markackerman8@gmail.com on 2012-11-26
Donald,

Wow thanks for such a fast response, but sadly I used the exact YouTube installation instructions via play on Linux, with the testing enabled.  I have tried in an emulated desktop as well as full-screen, and windowed.  But with no change. while investigating this problem, I have seen suggestion to use bleeding edge Mesa, and then the next kernel, which is a little aggressive, but I will try, within the hour.  It was reminder to me, in the previous post, which referred to at Diablo fix, and I read it there again.  So maybe that might help.  As I said before, if I get the fix.  I will definitely report it.  Thanks again,
Mark.

---

### Post by bugbugbugb on 2012-12-14
This has been answered before, but this thread was one of the highest search results, so posting here should really help solve this aggravating problem for LoL on Ubuntu.

I have a similar setup to that of the OP:
Vaio VPCEH24FX
Ubuntu 12.04
Intel Core i3 with Intel HD Graphics 3000.

This worked for me to solve the dark graphics:

```

export MESA_EXTENSION_OVERRIDE="-GL_EXT_texture_sRGB_decode -GL_ARB_draw_elements_base_vertex -GL_ARB_map_buffer_range"
```Try that line in a terminal, then try running the script for LoL in that terminal. That worked for me.

Good luck!

Sources:
[askubuntu.com/questions/140161/dark-textures-on-intel-hd-3000-sandy-bridge-in-games-via-wine]("http://askubuntu.com/questions/140161/dark-textures-on-intel-hd-3000-sandy-bridge-in-games-via-wine")
[http://www.playonmac.com/en/topic-9760-Dark_display_during_game_League_of_Legends.html](http://www.playonmac.com/en/topic-9760-Dark_display_during_game_League_of_Legends.html)

---

### Post by markackerman8@gmail.com on 2013-03-29
I got it working and solved the dark issue by simply doing one thing .....

....  Installed kde-full and/or kubuntu-desktop, logged out and back into Kubuntu-Plasma-Desktop - All Issues in this thread - ALL OF THEM are fixed.  KDE versus Gnome (Unity) - WOW.

SOLVED!

---

