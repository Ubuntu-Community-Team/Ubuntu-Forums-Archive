---
title: "ati 3d drivers"
date: 2008-06-01
forum: x86 64-bit Users
---

### Post by bregale on 2008-06-01
hi i have hardy installed and works ok , i have installed the ati drivers and catalyst control but can only get my graphice to run in 2d are there any drivers else where or is there none available yet ?
    any help will be welcome 
         thanks

---

### Post by stephenb on 2008-06-01
Do you mean getting desktop effects to work, etc? The only way I could get fglrx working properly for my ATI was to follow the latter part of these instructions, where you create your own deb files:[INDENT][http://wiki.cchtml.com/index.php/Ubu...allation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")
[/INDENT]The regular Ubuntu xorg repositories for fglrx just gave me Mesa OpenGL whereas with the above instructions I get ATI OpenGL. However, I was also getting a black screen problem when logging in, which I think I found a fix for. 

Anyway, good luck.

---

### Post by bpl07 on 2008-06-01
> **stephenb said:**
> However, I was also getting a black screen problem when logging in, which I think I found a fix for.

What's the fix?  I think I have the same issue you mention.

---

### Post by stephenb on 2008-06-01
The following would appear to stop the hanging black screen issue for me. I haven't done multiple reboots to thoroughly test it, though.[INDENT] sudo gedit /usr/share/xserver-xgl/Xgl-session
[/INDENT]In that file, go down the end to where is says this:[INDENT]     xauth add $XGL_DISPLAY . $(xauth nextract - $DISPLAY | cut -d ' ' -f 9)

    verbose "Starting Xgl with options: " $XGL_ACCEL_OPTS $XGL_OPTS "\n"
    $XGL_WRAPPER $XGL_DISPLAY $XGL_ACCEL_OPTS $XGL_OPTS &
[/INDENT]After that just add another line with this:[INDENT]sleep 5
[/INDENT]Then save and reboot to test. This is an old fix to an old problem it would seem. I found another way of doing it somewhere that involved a more extensive code change, but this simple step above seemed to solve it for me. 

I can dig up the other method if need be, however, I think they both basically do the same thing in delaying xserver.

---

### Post by Kilz on 2008-06-01
Why not use aiglx since you are using the ati drivers?

Add this to the xorg.conf

```
Section "ServerFlags"
	Option	    "AIGLX" "on"
EndSection
```

Then 

```
Section "Extensions"
	Option	    "Composite" "enable"
EndSection
```

To turn on effects.

---

### Post by kingtaurus on 2008-06-02
If you use the AIGLX option does this override the need to have a file called disable in .config/xserver-xgl/ ?

---

### Post by Kilz on 2008-06-02
> **kingtaurus said:**
> If you use the AIGLX option does this override the need to have a file called disable in .config/xserver-xgl/ ?

Im not sure, but I dont have that file. AIGLX should replace xgl.

---

### Post by kingtaurus on 2008-06-02
> **Kilz said:**
> Im not sure, but I dont have that file. AIGLX should replace xgl.

Hmmm ... sounds like a quick
```

ps auxw | grep Xgl

```
will solve :)

---

### Post by stephenb on 2008-06-02
> **Kilz said:**
> Why not use aiglx since you are using the ati drivers?


I had problems with my ATI card and AIGLX a long time ago and I was advised to turn it off. I did that and just left it. 

However, your query prompted me to give it another try with the new drivers and see what happens. I changed xorg.conf and uninstalled xserver-xgl. 

After rebooting everything looked great. But I discovered a bad flickering problem when running Stellarium and video playback (Miro). Hardy also seemed to take longer to boot up, just before the login screen.

I'm not sure how to fix the flickering or even if it can be fixed. I've noticed in my searches that many people have experienced the same problem in the past but couldn't solve it. So I turned off AIGLX again and reinstalled xserver.

---

### Post by RAOF on 2008-06-03
> **stephenb said:**
> ...
I'm not sure how to fix the flickering or even if it can be fixed. I've noticed in my searches that many people have experienced the same problem in the past but couldn't solve it. So I turned off AIGLX again and reinstalled xserver.

This makes me sad!  I was looking forward to drivers being non-crap enough for me to ignore the xserver-xgl package :cry:.

---

### Post by Kilz on 2008-06-03
> **stephenb said:**
> I had problems with my ATI card and AIGLX a long time ago and I was advised to turn it off. I did that and just left it. 

However, your query prompted me to give it another try with the new drivers and see what happens. I changed xorg.conf and uninstalled xserver-xgl. 

After rebooting everything looked great. But I discovered a bad flickering problem when running Stellarium and video playback (Miro). Hardy also seemed to take longer to boot up, just before the login screen.

I'm not sure how to fix the flickering or even if it can be fixed. I've noticed in my searches that many people have experienced the same problem in the past but couldn't solve it. So I turned off AIGLX again and reinstalled xserver.

There has been a flickering problem using xvideo or xv video output with the ati drivers since 7.11. Use x11 video output.

But you have a lot of issues with your Hardy that you upgraded from previous versions. You should do a clean install and see if you experience the same problems.

---

### Post by stephenb on 2008-06-03
> **RAOF said:**
> This makes me sad!
I'm sorry, I didn't intend to reduce anyone to tears.  ;-) 

> **Kilz said:**
> There has been a flickering problem using xvideo or xv video output with the ati drivers since 7.11. Use x11 video output.

I'll give it a try.

> **Kilz said:**
>  But you have a lot of issues with your Hardy that you upgraded from previous versions. You should do a clean install and see if you experience the same problems.

Yes, indeed. I think I'll be doing that in the near future.

---

### Post by radamo on 2008-06-03
> **Kilz said:**
> There has been a flickering problem using xvideo or xv video output with the ati drivers since 7.11. Use x11 video output.

But you have a lot of issues with your Hardy that you upgraded from previous versions. You should do a clean install and see if you experience the same problems.

Is it possible to set Google Earth to use x11 video?  The flickering in GE is unbearable with Compiz enabled.
Thanks,
RA

---

### Post by Kilz on 2008-06-03
> **radamo said:**
> Is it possible to set Google Earth to use x11 video?  The flickering in GE is unbearable with Compiz enabled.
Thanks,
RA

The reason google earth is flickering is desktop effects. Turn them off when using it.

In a terminal before using
```

metacity --replace
```

After its closed to enable effects

```
compiz --replace
```

---

### Post by radamo on 2008-06-03
> **Kilz said:**
> The reason google earth is flickering is desktop effects. Turn them off when using it.


Yes, I realize that is why it was flickering... I get flickering in all OpenGl apps, like glxgears when the desktop effects are enabled.  

So other than disabling desktop effects there is no way to address this?

Thanks for the suggestion.  That will be helpful.

RA

---

### Post by Melcar on 2008-06-03
Just turn it off.  There is no way around it.  Not yet at least.

---

### Post by radamo on 2008-06-03
> **Melcar said:**
> Just turn it off.  There is no way around it.  Not yet at least.

okay, nuff said. 
Thanks,
RA

---

### Post by mac143_01 on 2008-06-04
I think Ubuntu works fine with Nvidia video cards

---

### Post by Kilz on 2008-06-04
> **mac143_01 said:**
> I think Ubuntu works fine with Nvidia video cards

Ubuntu works just fine with ATI cards.

---

### Post by ASULutzy on 2008-06-04
Just to make sure everyone knows, you can get full screen apps to stop flickering by going to the general options in compiz config and toggling unredirect full screen windows, I was unaware of this for some time so figured I'd share it

---

### Post by radamo on 2008-06-04
> **ASULutzy said:**
> Just to make sure everyone knows, you can get full screen apps to stop flickering by going to the general options in compiz config and toggling unredirect full screen windows, I was unaware of this for some time so figured I'd share it

Have you tried this with GoogleEarth? Interesting... I will try it tonight if I have a chance.
RA

---

### Post by bregale on 2008-06-04
thanks for all the ideas it seems i have fixed it now i installed the ati drivers from from ati web site [i know they are unsupported] i remvoved the catalyst pro and reinstalled the full compiz manager, i now have the 3d desktop , but dont know how to make the cube smaller , 
   never mind we can keep going 
    thanks again for the help

---

