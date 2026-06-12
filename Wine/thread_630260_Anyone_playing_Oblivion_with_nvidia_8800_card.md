---
title: "Anyone playing Oblivion with nvidia 8800 card?"
date: 2007-12-03
forum: Wine
---

### Post by Melhisedek on 2007-12-03
Hello folks, 
I'm keeping an eye on the 8800GT card as the 1900XT I have now really doesn't like anything *nix :(

I was just wondering how does Oblivion play using 8800 cards? Only gripe I have with it is that it only has 512 MB RAM :( And this card is supposed to last me a long time... Getting settled in and everything :) I know it will play WoW and Civ4 but Oblivion... could be tricky with mods and all. 
So anyone here has one?

---

### Post by Melhisedek on 2007-12-04
Bump... anyone using nvidia 8800 card at all? :)

---

### Post by pedro_orange on 2007-12-04
I use an nVidia 8800 GTS & from what I've seen of the new 8800 GT specs - I wish I'd waited and got one of these! Oh well! 
With a good monitor the 8800 flies. nVidia chipset is well supported & installing it with Envy is easy-peasy! 

I run WoW & Civ4 seamlessly on Wine, but I do not own Oblivion to try it out with. If you wanna post me the CD I'll give it and go & let you know, he he.

I can't check wineHQ cause I'm at work, but if I remember correctly it should run well in Wine.

---

### Post by Melhisedek on 2007-12-04
Well those are the only 3 games that I would need to run as well :) Been trying to get Civ4 to run but so far no success :( 
Wish damn 8800GT would get released here already :/

---

### Post by desertboy on 2007-12-05
I've got an 8800GTS 640meg version and Oblivion runs very good on Vista but not so good on Wine, it does run but the graphics aren't as good and performance is 1/2 of windows.

---

### Post by Melhisedek on 2007-12-05
Thanks desertboy. May I ask what resolution and settings are you using?

---

### Post by aoanla on 2007-12-05
I should note that the performance you get on 8800GTs is not related to the performance you get with the 8800GTS - they are entirely different GPU revisions, despite the misleadingly similar names.
In particular, the 8800GT *only* works with the 169.04 beta driver, at present, while the 8800GTS works with the previous stable driver (which is what gets installed by Ubuntu in Restricted Drivers). 

The stable driver,  100.14.19, is much less performant than the 169.04 beta, which is now almost comparable to the performance in Windows of the current drivers. DirectX 9 performance is still a little slow on the 8800GT, though, because the beta driver does not include the full set of OpenGL functionality (to be more precise - it can do anything you want it do to, but some of the "faster" and "advanced" ways aren't implemented yet for the 8800GT). We assume that this will come with the next stable release, which is hoped to be before the end of the year (but there's no official date, or firm rumours or anything). 
Be sure to use the latest release of Wine, by the way, as there is also a small bug in the beta driver with regards to shader language processing, which Wine 0.9.50 contains a workaround for.

I hope this helps.

---

### Post by bastiegast on 2007-12-05
> **aoanla said:**
> I should note that the performance you get on 8800GTs is not related to the performance you get with the 8800GTS - they are entirely different GPU revisions, despite the misleadingly similar names.
In particular, the 8800GT *only* works with the 169.04 beta driver, at present, while the 8800GTS works with the previous stable driver (which is what gets installed by Ubuntu in Restricted Drivers). 

The stable driver,  100.14.19, is much less performant than the 169.04 beta, which is now almost comparable to the performance in Windows of the current drivers. DirectX 9 performance is still a little slow on the 8800GT, though, because the beta driver does not include the full set of OpenGL functionality (to be more precise - it can do anything you want it do to, but some of the "faster" and "advanced" ways aren't implemented yet for the 8800GT). We assume that this will come with the next stable release, which is hoped to be before the end of the year (but there's no official date, or firm rumours or anything). 
Be sure to use the latest release of Wine, by the way, as there is also a small bug in the beta driver with regards to shader language processing, which Wine 0.9.50 contains a workaround for.

I hope this helps.

What you say about driver performance is interesting, but can you tell me from where you got that? I always thought the performance of the nvidia drivers was equal in windows and linux.

---

### Post by aoanla on 2007-12-05
This is true for 7xxx cards and below.

The 8x00 cards have had slightly worse than Windows performance since the drivers supported them, probably because they're very different from the 7xxx cards, and so need a lot of new code in the drivers. In particular, I believe that the current stable driver is slightly faster than the (very slow) driver before it, a problem which was fixed in the next beta, and is improved upon further with the current beta. I believe that performance is now back to being near identical with Windows, in most cases.

This is pretty much well known - if you look at any benchmark comparisons of GeForce 8 cards in Linux and Windows, you see this. 
In particular, have a look at the Phoronix benchmarks for the last couple of drivers: 

[http://www.phoronix.com/scan.php?page=article&item=925&num=2](http://www.phoronix.com/scan.php?page=article&item=925&num=2)
showing the massive performance improvement between the last beta and the current one,

[http://www.phoronix.com/scan.php?page=article&item=851&num=2](http://www.phoronix.com/scan.php?page=article&item=851&num=2)
showing the small improvement between the previous stable driver (100.14.11) and the current one (100.14.19)

and,
[http://www.phoronix.com/scan.php?page=article&item=781&num=3](http://www.phoronix.com/scan.php?page=article&item=781&num=3)
showing how badly 100.14.11 performed with GeForce 8 cards, versus Windows.

Overall, the performance increase in the latest beta appears to achieve parity with Windows on 8x00 cards, by those benchmarks.

As for DX9 performance on the 8800GT - have a look at some threads on the nvnews forums, where this is discussed. It looks like it's just an oversight in the beta - which is why people release betas, after all - so it'll be fixed in whatever stable release we get next, we assume.

---

### Post by Sockerdrickan on 2007-12-05
I run Prey on max settings with no lag.

---

### Post by desertboy on 2007-12-19
> **Melhisedek said:**
> Thanks desertboy. May I ask what resolution and settings are you using?

In windows I can run 1680x1050 with most setting on high with very good frame rates, in Ubuntu I think I had to set everything to medium and run at 1280x968 to get playable framerates (With occasional severe slowdown).

I've got 2gig of ram and a core duo if that helps.

I've bought it 2nd hand for my PS3  and sold my pc copy as I've ditched windows, it runs nicer on my ps3 than my 8800gts.

---

