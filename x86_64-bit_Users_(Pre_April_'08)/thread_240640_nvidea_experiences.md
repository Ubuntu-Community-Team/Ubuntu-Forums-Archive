---
title: "nvidea experiences?"
date: 2006-08-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by cocteau on 2006-08-21
Hi

I'm considering replacing my ATI 9600 graphics with a nvidea one. To be able to aford one I'm aiming at around the FX5900, or a model from around that series.

Can anyone tell me what their experience has been with those cards?

---

### Post by Haegin on 2006-08-21
Great cards, especially under linux as the driver support is great. Don't expect to play all the latest games with that card as it is quite old but I had a Geforce FX 5950 Ultra that worked a dream. 

The only issue I did have with it was that some of the FX range (inc mine) didn't shut down properly so wouldnt power off after halting but that was easily solved by altering /boot/grub/menu.lst to remove the word "splash" from line #defoptions=quiet splash.

Hope this helps

---

### Post by AlanV on 2006-08-21
Just finished playing Quake 4 on Dapper x64 using a Nvidia 6600GT. Ran just as good as if in XP.

---

### Post by juicemansam on 2006-08-21
When I upgraded my system (mobo/cpu/ram/video) I couldn't use my ATI9250 anymore, luckily I obtained two Geforce 6600LE's. And with my motherboard (ECS C19-A SLI) I'm able to play my ol' UT2004 better than I ever could. In fact, with just one of the cards I was able to get a really nice and comfortable performance for most of everything I do with my PC; the other's just icing on the cake.

The Nvidia drivers were many times easier to work with. Their own scripts handled my configuration without problems, unlike ATI's drivers. I pretty much knew how to deal with ATI's drivers manually, and patch it by hand, but with every new release it just became unbearable.

So Nvidia gets my vote, even if it's a proprietary driver.

---

### Post by Hg80 on 2006-08-21
i own a 5200 and a 7800GT and they both work great,
I also owned a radeon 9800pro for a year and it was nothing to call home about

---

### Post by Ribs on 2006-08-21
MY XFX GeForce FX 5950 Ultra works just great.

The only issue is that you should remove 'splash' from your kernel lines and from the default options section of your /boot/grub/menu.lst file. Otherwise you'll find you won't be able to switch terminal, log out, or shut down (your computer will simply freeze with all sorts of junk on the screen). It's a known problem, but it's in the hands of NVidia.

Beyond that, no issues at all. The card works fine in 64-bit once you get the drivers installed. It's just as easy to get working as in 32-bit.

---

### Post by jamesford on 2006-08-21
much better than my old ati driver-wise, in fact its working just perfectly

---

### Post by cocteau on 2006-08-22
Thanks for the feedback. I'll order one soon. And the reason for choosing an older model is that old usually translates to affordable :P

---

### Post by Lord Illidan on 2006-08-22
NVIDIA all the way. Until ATI make their drivers better, and I see less people complaining about them, I am boycotting them, and telling my friends to do so.

---

### Post by cell-gfx on 2006-08-25
Running a GeForce 6600 GT on AMD64 on 64-bit. I've had a VMWare Server VM running Windows Vista Ultimate B2 in a wobbly window being dragged across the desktop cube in realtime with little slowdown. NVIDIA rocks!

---

