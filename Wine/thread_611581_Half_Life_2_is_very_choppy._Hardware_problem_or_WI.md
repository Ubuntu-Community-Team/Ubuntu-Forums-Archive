---
title: "Half Life 2 is very choppy. Hardware problem or WINE?"
date: 2007-11-13
forum: Wine
---

### Post by Opeth on 2007-11-13
Whenever I try to run WINE, it pushes all of my resources up to nearly 100% usage. It skips frames and it's barely playable. It's very choppy and very laggy. Could this be due to my outdated hardware, or is this just how it is with WINE? Note that CS:S works fine, lag here and there, but definitely playable, along with regular CS. I'm thinking that it is possibly my video card, and I could upgrade, but i wouldn't want to upgrade and still have the same problem. 

Ubuntu 7.04 Feisty
Nvidia Geforce 6200LE (128MB RAM)
GA-M61P-S3
AMD Athlon 64 X2 4000+ 2.1GHz Brisbane
1GB DDR2 667 RAM


Furthermore, if I do need to upgrade, what would I need to play games like Half Life 2, Unreal Tournament, etc in max without any lag? 7600GT? 7900GS? 

Thanks!

---

### Post by Mblackwell on 2007-11-13
It's probably not your computer.

Are you disabling compiz/switching to metacity before you play?

Also there's some console commands I believe that should improve performance, like -heapsize 512000 would tell the game to use half of your ram.

You can also try using DX8.1 shaders instead of DX9.

Also, what are your game settings?

---

### Post by Opeth on 2007-11-13
> **Mblackwell said:**
> It's probably not your computer.

Are you disabling compiz/switching to metacity before you play?

Also there's some console commands I believe that should improve performance, like -heapsize 512000 would tell the game to use half of your ram.

You can also try using DX8.1 shaders instead of DX9.

Also, what are your game settings?

I disable compiz by disabling desktop effects, correct? Because I don't have Beryl or Compiz installed, nor do I ever use the wobbly windows.

I'll look for those commands. 

I found the DX command option thing. Let me try it out. The settings are default.

---

### Post by Mblackwell on 2007-11-13
Yes but I don't know what the defaults come up as for your system. For instance it could have a really really high resolution setting, etc.

And yes, desktop effects is compiz.

---

### Post by Opeth on 2007-11-13
Yes, thank you very much! You probably just saved me 100 dollars and a few headaches. It works wonderfully now. 

One thing though, when I use the terminal and have to navigate to the Steam directory, it goes like this...

cd ~/.wine/Program Files/Steam

It stops at Program because there is a space between Program and Files, so I have to rename it and delete the space every time I want to do something. What is the character so that I can do what I need to do without having to backspace the space everytime?

---

### Post by aoanla on 2007-11-13
> **Opeth said:**
> Yes, thank you very much! You probably just saved me 100 dollars and a few headaches. It works wonderfully now. 

One thing though, when I use the terminal and have to navigate to the Steam directory, it goes like this...

cd ~/.wine/Program Files/Steam

It stops at Program because there is a space between Program and Files, so I have to rename it and delete the space every time I want to do something. What is the character so that I can do what I need to do without having to backspace the space everytime?

You can "escape" special characters like spaces by prepending them with a \.
So

cd ~/.wine/Program\ Files/Steam 

will be parsed as you want it to be.

---

### Post by KillerJoe on 2007-11-13
Well, with your graphics card be sure to turn off all sorts of antialiasing and anisotropic filtering. Play max at 1024x768 and also disable HDR and color correction.

If that doesn't help put your settings to medium and reflections to 'world only' and you can even try playing at 800x600.

If nothing help add -dxlevel 81 or -dxlevel 80 to your start parameters.

**EDIT:**

The heapsize command should be:

```
-heapsize 524288
``` for 1 GB of system memory!!

---

### Post by wsonar on 2007-12-19
I'm tring halflife 1 older system I tried in blackbox to have the best performance all startin videos work good but when choose start game it leaves me at the loading screen and I can here the gameplay in the back ground and even here my guy react to the controller is the command to allocate ram a wine optinon? I do have alot older system AMD 800mgh 1 gig ram but a nvidia 256

---

### Post by stuart.crouch on 2007-12-19
Hi

The heapsize command is a halflilfe/valve software specific thing, as is the dxlevel command.  

To fix the black screen thing - have you installed the drivers for your graphics card and is it even capable of 3d
Try -sw (run in software mode was available for hl1 if I recall correctly). if you see graphics then it means your graphics card hasn't been configured correctly.  

If you have set up your card, it means its not powerful enough for 3d acceleration.

:KS

As an aside - here is a bunch of fullstops.
..............................................................................
Please feel free to scatter them through any posts you make.  I can provide more full stops and commas if you find that you run out.

:KS

---

### Post by wsonar on 2007-12-20
Well COmpiz and AWN work decent in gnome, I played open arena and it seems to play fine,  but I think I need to ubgrade my box I think it got hot a few times and I got a few swelled caps. it's time for somethin new just tring to get by till then....

Thanks for the quick responce.

---

### Post by wsonar on 2007-12-20
I do have the nvidia geforce fx5200 256 the card shouldn't have a problem with the game

---

### Post by wsonar on 2007-12-20
Well just wanted to say got it working perfect now I just had to change the video mode to 600x480 the recomended  openGL I have to use some patience to switch it from window mode to full screen but when the game starts everthing looks perfect and runs smooth. I decided to run it under enlightenment

---

### Post by Gepetto on 2007-12-28
I'm having trouble with my HL2 being really slow as well. When I played in Windows Vista, I had no problem sustaining 80+ FPS on with medium graphics settings at 1440x900, but in Ubuntu, I can't even hold 30fps on the menu screen - And that's while running in DX8.1 mode! When I go to DX9, it's near 20 fps. 

My specs are:
Dell Inspiron E1705 with Intel T7400
2 Gigs ram
Nvidia Go7900Gs Overclocked at 450x550
I have the latest 100.14.19 drivers 
Running Wine 0.9.51

Compiz is disabled, running metacity instead, and still no improvement. This is starting to get very, very frustrating...Any help would be appreciated

---

