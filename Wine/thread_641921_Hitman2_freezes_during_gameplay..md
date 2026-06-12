---
title: "Hitman2 freezes during gameplay."
date: 2007-12-16
forum: Wine
---

### Post by ajopaul on 2007-12-16
I installed Hitman2 using wine. was able to launch the game. But when i started my first mission the game freezes especially when i open fire :confused: this happens everytime i close and restart the game. 

when i launched it from console i get the following error message
```
fixme:d3d:tex_bumpenvlscale WINED3DTSS_BUMPENVLSCALE not supported yet
err:seh:setup_exception stack overflow 352 bytes in thread 000e eip 7bf59fcf esp 00240ea0 stack 0x241000-0x350000
```

My Specs,
Wine: 0.9.51 with Win Xp config on Gutsy
3D card, nVidia 8400 GS

---

### Post by hikaricore on 2007-12-16
Have you read through the setup tips here?
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1848](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1848)

---

### Post by ajopaul on 2007-12-16
> **hikaricore said:**
> Have you read through the setup tips here?
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1848](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1848)
yes I did, but I wasnot able to use OpenGL rendering instead of D3D, when used with OpenGL get the following error message ```
OpenGL: SelectPixelFormat failed. Hardware acceleration not supported. Try changing color depth. 
```

---

### Post by hikaricore on 2007-12-16
Hmm... I'm wondering if you're using the proper video drivers for the 8xxx series of Nvidia cards.

I can't remember if the version included in the repos supports them properly.  Perhaps you should test drive the beta drive: [http://www.nvidia.com/object/linux_display_ia32_169.04.html](http://www.nvidia.com/object/linux_display_ia32_169.04.html)

I'm not going to say for sure that this will solve your problem, but it may be worth a shot.

If you're not familiar with installing drivers from binary packages I suggest searching the forums for a walkthrough.  ^_^

---

### Post by ajopaul on 2007-12-16
oops! removed the restricted driver and installed the binary driver! now my X is having only 800x600 res :) glxinfo throws this message ```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat

```

hv try to figure this before reverting back to restricted drivers. any ideas?

---

### Post by omega_user on 2007-12-16
how did u get the game installed? Did u use a CD or did you use an ISO?  If an ISO, how'd you mount it?

I was hoping I could get my hitman working, but the fact that it's not a legitimate copy might mess things up. Any help would be appreciated

---

### Post by ajopaul on 2007-12-17
> **omega_user said:**
> how did u get the game installed? Did u use a CD or did you use an ISO?  If an ISO, how'd you mount it?

I was hoping I could get my hitman working, but the fact that it's not a legitimate copy might mess things up. Any help would be appreciated
I mounted the ISO this way ```
sudo mount -o loop /home/ajopaul/games/hitman2.iso /media/iso/

``` went to /media/iso and ran ```
wine autorun.exe
```. Initial gameplay is smooth and perfectly fine in both fullscreen and windowed mode.

---

