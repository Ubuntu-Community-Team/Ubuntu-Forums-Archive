---
title: "Directx For Wine?"
date: 2008-05-11
forum: Wine
---

### Post by reyhan on 2008-05-11
Hello do i Need DirectX for my Game
under wine?

---

### Post by schtufbox on 2008-05-11
Generally, no. Though some games do require that sonme of the directx dll's are present.  One instance is Tabula Rasa, but it will install those DLL's when you install it.
It really varies from game to game.

---

### Post by gnivler on 2008-05-11
Wine includes support for alot of directx out of the box, up to 9.0c.  Not everything is implemented yet, which is where using 'native' (microsoft) dlls comes in, as a workaround.  If something needs a native library it means the wine library has bugs or is missing something and reporting these can help improve the software.  The idea being that you shouldn't need to use native dlls, in a perfect world.

You basically will never want to install directx in wine, it will just cause you trouble.

---

