---
title: "WoW crashes on open"
date: 2008-03-08
forum: Wine
---

### Post by whaevr on 2008-03-08
I try and start it with 
```

wine "C:\Program Files\World of Warcraft\WoW.exe"

```
and this is what it displays in terminal
```

fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33ed78,0x00000000), stub!
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set

```
and this window pops up:
[IMG]http://i116.photobucket.com/albums/o26/photos_r_me/Screenshot-Wow.png[/IMG]


I've tried this guide here:
[http://ubuntuforums.org/showthread.php?t=579378&highlight=wow+crashes](http://ubuntuforums.org/showthread.php?t=579378&highlight=wow+crashes)

It says to edit a Config.wtf file...but you need to run WoW at least once for this file to be created...how can I create it when I can't even start it?

Anyone have any ideas...?

Edit:
So apparently I need to enable direct rendering as its currently disabled...how do I do this?

---

### Post by ssj3strife on 2008-03-08
Your error message indicates that you don't have opengl support. What graphics card do you have?

---

### Post by whaevr on 2008-03-08
I have an Nvidia Geforce 6200...

---

### Post by ssj3strife on 2008-03-08
Run the command:

glxinfo | grep direct

Do you have direct rendering enabled?

---

### Post by whaevr on 2008-03-08
Heres the output:
```

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```
So I'm guessing its not enabled...how do I enable it?

---

### Post by ssj3strife on 2008-03-10
Are you using the restricted drivers for your graphics card? If so, it should have been enabled automatically. If not, try installing them and try agian.

---

### Post by buried on 2008-03-10
Add next to "wine "C:\Program Files\World of Warcraft\WoW.exe" -opengl"

---

### Post by Toxicity999 on 2008-03-10
That won't help buried. He has no 3D support system-wide. What you need to do is skim the wiki, and the plethora of posts out there about getting 3D/Direct Rendering enabled. I think your card is supported by nvidia-glx-new (and if not then nvidia-glx) therefor you should have little issue getting 3d working on a modern Ubuntu install. Just install one of the two from the repos, and reboot.

You can then also properly use things like compiz and such as well.

---

### Post by whaevr on 2008-03-10
Well I updated my drivers with Envy, and now I have direct rendering...although now that WoW runs it doesn't have that great of a frame rate (about 10) is it possible to increase this...?

---

### Post by ssj3strife on 2008-03-12
Yes, there are a couple WoW settings and Wine registry tricks you can use to increase performance. Just google "world of warcraft ubuntu," and I'm sure you'll find plenty of good walkthroughs that will give you what you need.

---

