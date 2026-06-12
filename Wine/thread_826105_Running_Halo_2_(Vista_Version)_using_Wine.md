---
title: "Running Halo 2 (Vista Version) using Wine ?"
date: 2008-06-11
forum: Wine
---

### Post by Wild Wolverine on 2008-06-11
Hello,
      New to the forum here.
    
 This question has been asked already here:
[http://ubuntuforums.org/archive/index.php/t-430713.html](http://ubuntuforums.org/archive/index.php/t-430713.html)

      But I am asking it again to see if anybody on this forum has been able to get it to work.
          
      I have been able to get the full version of "Halo Combat Evolved" to run perfectly at full frame rate with no problems, using Wine.
      
      I have checked out the forums on winehq.org and it appears( Halo 2 Vista Version) is still a work in progress, to get it to run using Wine.
      
      So has anybody here been able to get it to work ?

                                 Wild Wolverine

---

### Post by timinator94 on 2009-11-16
apparently not.....:biggrin:
Seriously I would like to now if anybody has done it...

---

### Post by timinator94 on 2010-05-13
Hey dunno if your still intrested but i found [http://thepiratebay.org/torrent/3720411/HALO_2_XP_Patch____](http://thepiratebay.org/torrent/3720411/HALO_2_XP_Patch____)  i dont own Halo 2 so would anybody be willing to try it out? If i know for a fact that it would work then i would totally buy it:guitar:

---

### Post by Howy on 2011-08-28
I've got something for the interested. (But I hope I'm not breaking rules by reviving this thread?)
The error about the installer seems to appear with parsing Xml.
This is the output:
```
err:winediag:wined3d_dll_init The GLSL shader backend has been disabled. You get to keep all the pieces if it breaks.
fixme:ole:CoInitializeSecurity ((nil),0,(nil),(nil),1,3,(nil),0,(nil)) - stub!
fixme:msxml:domdoc_get_parseError (0x13fbec)->(0x33a550): creating a dummy parseError
fixme:msxml:parseError_get_line (0x13fc98)->(0x33a56c)
fixme:msxml:parseError_get_linepos (0x13fc98)->(0x33a570)
fixme:msxml:domdoc_get_parseError (0x13fbec)->(0x33a550): creating a dummy parseError
fixme:msxml:parseError_get_line (0x13fc98)->(0x33a56c)
fixme:msxml:parseError_get_linepos (0x13fc98)->(0x33a570)
fixme:commctrl:TaskDialogIndirect 0x339cf0, 0x339ce4, (nil), (nil)
fixme:commctrl:TaskDialogIndirect dwCommonButtons=20 uType=0 ret=1

```
From this, I can see that it's all because of the Xml parser being incompatible. And what do we do about that?
[s]Fix it. I'll try and replace it with official libraries and see how it goes.[/s]
It seems to be a problem with OLE... [s]It says it's a stub. Does anyone know the system functionality of it?[/s] (It's obviously an equivalent to DBus.)
I found that the Xml-errors are caused by the XP loader, so they can be striked out if you run it correctly.
Now, I get to the point where it disappears with only the OLE-error.
It could have something to do with the installer trying to elevate security to avoid being hijacked or eavesdropped?

---

### Post by Dlambert on 2011-08-29
> **timinator94 said:**
> Hey dunno if your still intrested but i found [http://thepiratebay.org/torrent/3720411/HALO_2_XP_Patch____](http://thepiratebay.org/torrent/3720411/HALO_2_XP_Patch____)  i dont own Halo 2 so would anybody be willing to try it out? If i know for a fact that it would work then i would totally buy it:guitar:

I know this is old, but you may not want to link to TPB. This forum doesn't support piracy.

---

