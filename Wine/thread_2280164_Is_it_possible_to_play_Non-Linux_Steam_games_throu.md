---
title: "Is it possible to play Non-Linux Steam games through Wine?"
date: 2015-05-28
forum: Wine
---

### Post by cwblanch on 2015-05-28
Hey,

So I'm wondering if its possible to install Wine and then install a game in the Linux Steam client and change the path or do something to make that particular game run through Wine?

It seems like it would be possible...or at least not impossible, I'm just not sure how it would happen. I haven't used Wine in years.

Also while I'm in the Gaming forum I want to ask. On Windows Minecraft runs decently, but so far with my tests on Ubuntu it runs much better, but a simple game like Game Dev Tycoon runs really slowly and laggy. I'm curious as to why that is.
Game Dev Tycoon even has a Linux specific install so it's not running through Wine or anything.
[This]("http://www.greenheartgames.com/app/game-dev-tycoon/") is Game Dev Tycoon for those who don't know. It's pretty entertaining.

I edited the title to try to make it clearer. I'm trying to install non-Linux games in Ubuntu through Wine.

Thanks!

---

### Post by ajgreeny on 2015-05-28
I think you are getting the wrong idea of what wine is and what it does.

Wine allows you to run some Windows executables and applications (read games here) by replacing the whole windows operation system with an "emulated API", so I can not see how or why it would be possible, or even helpful, to try to run a Linux executable (your Linux steam game) through wine.

Perhaps I just don't know enough about steam and how it works, but I thought it was totally different from wine, and that the games it plays are not the windows versions but native Linux games; have I got that wrong?

PS:  I'm not a gamer on either platform, so I may be miss-informed.

---

### Post by cwblanch on 2015-05-28
> **ajgreeny said:**
> I think you are getting the wrong idea of what wine is and what it does.

Wine allows you to run some Windows executables and applications (read games here) by replacing the whole windows operation system with an "emulated API", so I can not see how or why it would be possible, or even helpful, to try to run a Linux executable (your Linux steam game) through wine.

Perhaps I just don't know enough about steam and how it works, but I thought it was totally different from wine, and that the games it plays are not the windows versions but native Linux games; have I got that wrong?

PS:  I'm not a gamer on either platform, so I may be miss-informed.

Sorry, I don't think I asked the question correctly.

I'm asking if its possible to run a game that you wouldn't normally be able to run in Linux, because it's not supported, through Wine.

You're right about Steam though, it does install and play the Linux version in a Linux platform.

But for example a game like Risk of Rain can run natively in Linux, but something like Bioshock can't because its not supported in Linux, only Windows. 
I'm pretty sure you can download the files for the games that aren't supported in Linux. I haven't actually tried yet.

Would it be possible to install these games in Wine through the Linux Steam Client?
So run them from Steam, but have Wine take over after you've clicked play?

---

### Post by ajgreeny on 2015-05-28
OK, I did not follow your meaning at first, but unfortunately, even though I now do understand, I don't know the answer to your specific query.

---

### Post by mastablasta on 2015-05-29
it is possible but you might need to install steam in wine to do it.

---

### Post by Bucky Ball on 2015-05-29
*Thread moved to **Wine**.*

Wine is for running Windows programs in Ubuntu. Your success will vary. Best to look up your app/game [here]("https://appdb.winehq.org/"). 

Some apps will work great, others fair, others not at all. There is also PlayonLinux. I know nothing about it and little more about Wine. Be aware that if you install Wine, aren't happy, and decided to uninstall, it is virtually impossible to eradicate it all. Bits of Wine remain, unlike regular Ubuntu apps which you can remove leaving no trace.

---

### Post by oldrocker99 on 2015-05-29
If you use PlayOnLinux, [https://www.playonlinux.com/en/](https://www.playonlinux.com/en/), you can install Steam for Windows, along with its several dependencies, from which you **may** be able to install the game(s) you want.

It is a bit of a crapshoot; may Windows games run very well on wine (I installed Skyrim using PlayOnLinux, and installed Oblivion in the same Steam bottle, and both run very well. X-COM didn't.

---

