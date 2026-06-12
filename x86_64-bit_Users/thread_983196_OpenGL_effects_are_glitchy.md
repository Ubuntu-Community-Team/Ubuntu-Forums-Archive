---
title: "OpenGL effects are glitchy"
date: 2008-11-15
forum: x86 64-bit Users
---

### Post by Coder543 on 2008-11-15
Greetings, I have been using Ubuntu 8.04 for some time with no problems in OpenGL. As soon as 8.10 came out, I upgraded. Currently, I am at a loss for reasoning on my issue. I have a MacBook (3,1) with an intel GMA X3100 graphics card. This did not appear to be an issue on 8.04, however it seems that 8.10 can't handle it. This has one of three possible causes: 8.10 is just down right stupid for losing compatibility with a graphics card, the new X.Org, or 64-bit OpenGL is having problems. Some examples of this glitchy-ness is as follows: Playing OpenArena, after awhile suddenly the colors go darker, and the menus are without text. Playing Supertux one time graphics updates did not occur correctly so there was a stuttered effect; it looked weird and was unplayable, so I had to restart supertux. On glTron I've experienced the text becoming unreadable and distorted. What is happening??? Please help me. I think it is that there is something wrong with the 64-bit opengl, but how can I fix this?

---

### Post by Coder543 on 2008-11-19
Is there no one who can help? (*bump*)

---

### Post by dpena on 2008-12-20
I have an Acer 5735z with an Intel X4500M graphics card, using Ubuntu-amd64 8.10, and I can not use any 3D game (Alien Arena, Armagetron Advanced, Extreme Tux Racer, OpenArena, Tremulous, Warsow, ..).

The screen gets corrupted in a few seconds or some minutes depending on the game, and sometimes I had to hard reset the laptop.

Even Kubrick, a game based on Rubik's Cube using OpenGL 3-D, when I move the window, it leaves images on the background outside the window.

Yesterday I tried the i386 version, obtaining the same results.

I thought that the graphic card could be broken, but today I tried a 3D game using M$ Vista and works fine.

I have read some weeks ago that there is something wrong with the Intel driver and opengl, and it is possible that we have to wait to the next ubuntu version to get solved this problems (newer versions of: kernel + xorg + mesa) :( 

Can someone leave any information/link about this?

---

### Post by collinp on 2008-12-20
It may have something to do with the latest xorg not liking Intel cards, or your card might be blacklisted for the exact reason that you described. I do not know if it is either of these two, just giving possibilities.

---

