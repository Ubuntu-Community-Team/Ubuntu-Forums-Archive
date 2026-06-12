---
title: "DirectX 9.0c on Linux with Wine"
date: 2007-11-27
forum: Wine
---

### Post by BuffaloX on 2007-11-27
Saw this howto article about installing DX9 on Linux with wine.
!!!! Beware you should not attempt this, unless you can fix it again if it breaks.

[http://wine-review.blogspot.com/2007/11/directx-90c-on-linux-with-wine.html]("http://wine-review.blogspot.com/2007/11/directx-90c-on-linux-with-wine.html")

Seems extremely cool.
Anyone try it, please state your experiences. :popcorn:

---

### Post by hikaricore on 2007-11-27
I can't really imagine where this would serve a purpose...

I personally do NOT advise doing it unless you have a specific need to do so.

---

### Post by BuffaloX on 2007-11-27
Maybe I was a bit unclear.
I didn't mean anyone should try it, but if they do.
It would be cool to hear about it.

---

### Post by hikaricore on 2007-11-27
Aye, I just worry about average users attempting this thinking it will make everything work.

The WINE devs have already implemented DX functionality, this should only be used in specific cases or on test machines.
There's a good chance it can/could make your current perfectly functioning WINE a mess.

---

### Post by BuffaloX on 2007-11-27
Sure I see what you mean, I edited original post to include a warning.

---

### Post by cogadh on 2007-11-27
I hate to say it, but he basically did the same thing you could do if you just copied some of the DX DLLs over from a Windows machine and applied overrides for them, which many of us already do. He ended up leaving all the core DX components that already come with Wine intact (d3d8, d3d9, dsound, etc.) and adding overrides for the rest of the DLLs installed by the DX redistributable. The only thing gained by installing the actual DirectX was the DXDiag application, which is a decent acomplishment, but serves no real purpose in Wine.

---

