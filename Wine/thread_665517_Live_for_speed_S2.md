---
title: "Live for speed S2"
date: 2008-01-12
forum: Wine
---

### Post by LoneWolfUK on 2008-01-12
I can't seem to get the game Live for Speed working properly. Well, it does kind of work, but it has no sound and terrible fps.

Does anyone know why this could be?

I also keep getting this in terminal when running it;

[IMG]http://img186.imageshack.us/img186/6970/16280027db5.jpg[/IMG]

---

### Post by LoneWolfUK on 2008-01-12
Just a quick update.

I found out that I was using an older version of Wine, so I upgraded to v0.9.52.

I went into Wine configuration and when I clicked on Audio it said something about a driver not being selected or installed... I clicked apply and now I have sound in LFS.
It seems to run slightly better and the error message I was getting before has gone, however the FPS is still just 20... (was 120+ in Windows XP). I realise that there will be a slight drop in FPS in Ubuntu, but surely not 100fps?

I am now getting these messages in terminal;

```
fixme:win:EnumDisplayDevicesW ((null),0,0x34f884,0x00000000), stub!
fixme:d3d8:ValidateVertexShader (0x678b9a8 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0x501eaf0 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0xd3413e8 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0xb381c10 (nil) (nil) 0 (nil)): stub
fixme:d3d:state_zfunc D3DCMP_NOTEQUAL and D3DCMP_EQUAL do not work correctly yet
fixme:d3d8:ValidateVertexShader (0xb11d3f0 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0xc081650 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0xddcfc80 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0xd0030e0 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0xc7ae730 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0xcbe9258 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0xb240ef8 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0xa155100 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0xc7ae730 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0xc7ae730 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0x452e968 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0xcbe9258 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0xc477d00 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0xc7ae730 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0xe8937c0 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0xcf7ad30 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0xc7dea10 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0x4538250 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0xe884380 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0xce4ebf0 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0xcfd4838 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0xc97d270 (nil) (nil) 0 (nil)): stub

```

---

### Post by hikaricore on 2008-01-12
None of those output messages really indicate any errors, fix me messages are default debug output and can be largely ignored.

However you never mentioned what video hardware you have or how you installed the drivers for said hardware.

You may also wanna check the AppDB page for any info others might have posted: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3755](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3755)

---

### Post by LoneWolfUK on 2008-01-13
> **hikaricore said:**
> None of those output messages really indicate any errors, fix me messages are default debug output and can be largely ignored.

However you never mentioned what video hardware you have or how you installed the drivers for said hardware.

You may also wanna check the AppDB page for any info others might have posted: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3755](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3755)

Thanks. I have an nvidia 7900GS card and I got my graphics drivers through the restricted drivers thingy when I first installed Ubuntu about 10 days ago.

---

