---
title: "OpenGL apps not working"
date: 2006-06-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by sanketmedhi on 2006-06-11
Hello,

I am facing some problems with OpenGL support with my Nvidia card. I have installed nvidia-glx, nvidia-kernel-common and kernel-restricted modules. My xorg.conf also contains "nvidia" in the Driver section. I see the logo when gdm starts. But I am not getting Opengl support in any applications like Neverball, Quake4, America's Army, and other games. However XGL seems to work perfectly. Glxheads, glxgears and glxinfo show me output properly. This is the error I get when I run quake4 from the terminal.

[http://paste.ubuntu.org.cn/425](http://paste.ubuntu.org.cn/425)

What could be going wrong?

---

### Post by Patsoe on 2006-06-11
I think you hit the wrong subforum :) this is for 64-bit Procs, there's another subforum for Video.

Also, I don't see any OpenGL errors in your file?

---

### Post by kombipom on 2006-06-11
You can't run OpenGL apps in XGL.  XGL grabs the OpenGL rendering (or something like that).  There are workarounds so that you can run them outside XGL.  Search for "nonXgl" in the forum and you should find a how-to.

---

### Post by sanketmedhi on 2006-06-11
I am not running Open GL apps in XGL. I use XGL occasionally. And I forgot to mention, I am on AMD64. So I guess I am in the right section. 

Well, I cannot show any other code because all other applications work but without OpenGL support. For example, in Neverball, I dont get the effects I should be getting. I am sure this is an OpenGL problem but I am confused as I get the logo at startup and also XGL works fine when I choose the Compix section.

---

### Post by kombipom on 2006-06-11
Perhaps posting your xorg.conf file might give someone a better idea.  Did you make mods to it to get XGL working?

---

### Post by sanketmedhi on 2006-06-11
Here is my xorg.conf

[http://paste.ubuntu.org.cn/429](http://paste.ubuntu.org.cn/429)

And here are the outputs of a few programs:

1) nvidia-settings

sanket@ubuntu:~$ nvidia-settings

ERROR: NV-CONTROL extension not found on this Display.
ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.
ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.

2) glxinfo

[http://paste.ubuntu.org.cn/430](http://paste.ubuntu.org.cn/430)


3) glewinfo

[http://paste.ubuntu.org.cn/431](http://paste.ubuntu.org.cn/431)

---

### Post by RAOF on 2006-06-11
Your glxinfo above was run from in XGL, yes?  nvidia-settings also?  They both seem fine, if they were.

Your Quake 4 log doesn't show GL errors - it finds a bunch of OpenGL extensions, then crashes - that doesn't seem to be the behaviour of a program which has a GL problem.

How do you switch between your XGL and Xorg X servers?  That may be a problem for the other programs?

---

### Post by sanketmedhi on 2006-06-11
[QUOTE=RAOF]Your glxinfo above was run from in XGL, yes?  nvidia-settings also?  They both seem fine, if they were.[/QUOTE]

No I havent run any of these commands from within XGL.

[QUOTE=RAOF]
Your Quake 4 log doesn't show GL errors - it finds a bunch of OpenGL extensions, then crashes - that doesn't seem to be the behaviour of a program which has a GL problem.
[/QUOTE]

All games were working perfectly before I installed XGL. I tried uninstalling XGL and then trying these commands, but got the same result.

[QUOTE=RAOF]
How do you switch between your XGL and Xorg X servers?  That may be a problem for the other programs?[/QUOTE]

I switch from the GDM menu selecting the Session option.

---

### Post by RAOF on 2006-06-12
[QUOTE=sanketmedhi]No I havent run any of these commands from within XGL.[/QUOTE]
Really?  You've clearly got the nvidia driver loaded, and it's registering itself with mesa, but your X server isn't supporting the nvidia-settings extension, or Direct Rendering.  I've not seen this happen without running an XGL server.  But there's always something new to see ;)

Just for the record, we're talking about the same thing?  The xserver-xgl package, and it's contents?  **Not** compiz, the fancy wobbling windows, rotating cube etc?

Maybe a solution would be to uninstall XGL then reinstall all the GL libraries.  Like this:
```
sudo aptitude remove xserver-xgl
sudo aptitude reinstall ~nmesa
sudo aptitude reinstall nvidia-glx

```

---

### Post by sanketmedhi on 2006-06-12
Hey, thanks a lot! It worked. All OpenGL apps working fine now. I think it had something to do with the mesa libs or with the xorg.conf-custom that I made for Xgl to work.

But a new thing came up. Running gdmsetup gives a seg fault! Any clues?

---

