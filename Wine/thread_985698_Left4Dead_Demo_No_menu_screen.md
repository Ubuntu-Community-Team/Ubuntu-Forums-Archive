---
title: "Left4Dead Demo No menu screen"
date: 2008-11-17
forum: Wine
---

### Post by Questioneer on 2008-11-17
Hello-
I'm trying out the Left4Dead demo through Steam.

I successfully get past the intro video, and I reached a video loop of some zombies at twilight.
It appears as if this video loop is supposed to be behind the menu, but I cannot see the menu. However, scrolling the mouse around gives a familiar 'clicking' sound, as if I'm scrolling over a menu...

Can anyone help figure out what is wrong?

Thanks.

---

### Post by Questioneer on 2008-11-17
Here is the command I am launching the game with:
```
env WINEDEBUG="fixme-all" WINEPREFIX="/home/alex/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 530 -dxlevel 80 -width 1280 -height 1024
```

---

### Post by dfreer on 2008-11-17
That's the main menu alright, that's about all I can help you with. Maybe try changing your resolution?

---

### Post by Dizzle7677 on 2008-11-17
Enable GLSL?

---

### Post by Questioneer on 2008-11-18
I think GLSL might be the problem.... I cannot find it in the Wine Registry! There is no folder: HKEY_CURRENT_USER/Software/Wine/Direct3D!
GLSL does not appear to even be there... what could be wrong?

---

### Post by Dizzle7677 on 2008-11-18
> **Questioneer said:**
> I think GLSL might be the problem.... I cannot find it in the Wine Registry! There is no folder: HKEY_CURRENT_USER/Software/Wine/Direct3D!
GLSL does not appear to even be there... what could be wrong?

Just create a string under D3D and name it 'UseGLSL' ... enabled. The winewiki has all the reg keys. By default it's set to on even if it's not in the registry so it may not be the solution. Are Vertex & Pixel shader hardware set to on in the WineConfig?

---

### Post by Questioneer on 2008-11-18
Hi-
Sorry, I don't even have a D3D folder, or any DirectX related folder under HKEY_CURRENT_USER/Software/Wine...

I'll check on the rest once I get back home, however.

Thanks.

---

### Post by Questioneer on 2008-11-18
OK, PixelShader is set to "Allow", and Vertext shader is set to "hardware"

---

### Post by Dizzle7677 on 2008-11-18
> **Questioneer said:**
> env WINEDEBUG="fixme-all" WINEPREFIX="/home/alex/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 530 -dxlevel 80 -width 1280 -height 1024

  Starting back at the top....Try Dxlevel 90 & 95. Don't set the starting resolution on startup. Get rid of the WINEDEBUG so you can see all the errors and fixmes. Beyond that I'm out of ideas. :)

---

### Post by Scottles on 2008-11-29
Questioneer, what graphics card do you have? Is it an ATI card using the proprietary drivers? I have the same issue, and have noticed that on all forums where people say the game runs fine they appear to be people with nvidia cards. I am wondering if its an ATI driver issue...

I have the full game, so can still play it despite the demo having been withdrawn...

---

