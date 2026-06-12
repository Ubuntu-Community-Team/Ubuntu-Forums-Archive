---
title: "[SOLVED] Blender 3D"
date: 2006-07-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by radopenev on 2006-07-02
I've installed all the 'latest' updates, and upgraded from Ubuntu 5.10 to Dapper.
 In Ubuntu 5.10 Blender 2.37a worked OK,but after  upgraded  to  Blender 2.41:-s 
RMB make nothing,I can't select objects ,can't use all manipulators.
What might be the problem??:confused:

p.s.: sorry for my english

---

### Post by thingy on 2006-07-02
1. Can you start blender and then shut it down and then attach the ~/.xsession-errors file here.

2. Does your right mouse button work at all? I.e. in other applications, does pressing it do something?

3. Can you rule out your user configuration files...you can do this by creating a new temporary user, and the log in as that user and launch blender. Does blender still display the same behaviour?

4. I checked launchpad and there are no bugs about this behaviour.

5. Can you look at these two threads and tell me if they apply to you:

Alt + Right Mouse Button in Blender -
[http://ubuntuforums.org/showthread.php?t=25493&highlight=blender+mouse](http://ubuntuforums.org/showthread.php?t=25493&highlight=blender+mouse)

Driver problem with Blender and right mouse button -
[http://ubuntuforums.org/showthread.php?t=72720&highlight=blender+mouse](http://ubuntuforums.org/showthread.php?t=72720&highlight=blender+mouse)

6. Can you let us know what graphics card you have and confirm to us that youve set up the 3d working properly in xorg or not

7. If it is indeed the case that the ALT+RMB is whats not working for you then, you can look at this thread:

[http://ubuntuforums.org/showthread.php?t=47680&highlight=blender+mouse](http://ubuntuforums.org/showthread.php?t=47680&highlight=blender+mouse)


Basically, we need more info. about the problem...im not running 64bit ubuntu at the moment and so I wont be able to replicate your issue, but maybe someone else can.

regards

jin

---

### Post by radopenev on 2006-07-03
Thanks for the help,thingy!I carefuly follow your advices,but I'm beginner!So,thanks for your patience.RMB worked OK in other applications!In addition to,in the Edit Mode
(Blender)can select (RMB ok).But,how I have been told you,can't use ALL manipulators 
by mouse.The behaviour is like Gkey and move(for all).So, I avoid this problem:
Gkey after that X or Y or Z,the same for rotation(Rkey after that X or Y or Z keys) and scale(Skey after that X or Y or Z keys),but that is too...
When I press RMB at different pleaces on the object ,situation is not a same(I attach
 some png,I simulate what happen ,becouse when move mouse,or press some key ,everything is go ok) 
I start Blender and then shut it down,but can't find ~/.xsession-errors .I think that it is in  /etc/gdm/  but take a look .
I create a new temporary user,but the behaviour is the same.

I look at these two threads ,comment the line    Load "dri" (# Load "dri") from
xorg.conf,the Blenders behaviour is the same.
I've got AMD 64 2600+, ATI Radeon 9600
I change "mouse_button_modifier" under /apps/metacity/general ,the behaviour is the same.
So,thanks for your patience.:oops: 

regards
p.s.:I saw that 1st RMBclick=nothing,2nd RMBclick is collapse !!!
p.p.s.: sorry for my english.:oops:

---

### Post by thingy on 2006-07-03
Hi

I'm at a loss to understand the problem...I've searched google and even asked about any right mouse button issues with blender on the #blender channel on chat.us.freenode.net. No luck!

Can you tell me the output of the following command: (type it into a terminal window)

fglrxinfo 


Can you also attach the following files to this thread:

/var/log/Xorg.0.log
/etc/X11/xorg.conf

jin

---

### Post by radopenev on 2006-07-04
Hi,
Thanks,thanks,thanks, for the help,thingy!I

---

### Post by thingy on 2006-07-04
Aah ok this makes sense now...

From looking at your xorg config and the log file, it seems you are using the standard xorg ATI driver. This is why Blender 3d is not acting properly.

I don't have an ATI card but I always understood that the standard xorg ATI driver only accelerated in hardware bits of opengl and not all of it.

If you install the official ATI driver, you will get full 3d acceleration and hopefully this problem with blender will go away.

Ok to give you the choice on how to install the official driver, here are two ways:

(1) Use the EasyUbuntu script

Website - [http://easyubuntu.freecontrib.org/index.html](http://easyubuntu.freecontrib.org/index.html)

Overview of what this script does - [http://easyubuntu.freecontrib.org/overview.html](http://easyubuntu.freecontrib.org/overview.html)

Download and running script instructions - [http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)


(2) Use the instructions from the official Ubuntu docs 

[https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html)

After you have installed the ATI driver, shutdown and restart your system. Then in the Terminal window, again type in: "fglrxinfo" and if you get some information displayed, go ahead and try running blender.

good luck

jin


Note: I don't know whether easyubuntu will modify the xorg.conf file. So if you use easyubuntu script to download and install the ati drivers and there is no effect, then it means you need to modify the xorg.conf file. I'll provide the instructions for that if needed.

---

### Post by radopenev on 2006-07-04
God bless you,thingy!!Thanks for all!
I follow way(2) ...and OK.
Thanks for your patience,explanations...:p 
sorry for my english.\\:D/ :oops: 

regards

---

### Post by Pettman on 2006-08-15
I've got the same problem as radopenev but I cannot use the fglrx driver without causing the system to freeze (mouse still moves but that's it). Also when I started blender after having removed the fglrx drivers (since they made the system freeze) and switched to the ati driver but not yet rebooted blender worked just fine (or it was a bitt laggy but you could live with that). The ati (not ATi's fglrx) drivers provides some acceleration but seemingly not enough.
```
pettman2@CPPKalinka:~$ glxinfo | grep render
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
direct rendering: Yes
OpenGL renderer string: Mesa DRI R300 20040924 AGP 1x TCL
pettman2@CPPKalinka:~$ glxgears -printfps
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
*********************************WARN_ONCE*********************************
File r300_render.c function r300_get_num_verts line 188
user error: Need more than 2 vertices to draw primitive QS !
***************************************************************************
6686 frames in 5.0 seconds = 1337.126 FPS
6732 frames in 5.0 seconds = 1346.291 FPS
6708 frames in 5.0 seconds = 1341.592 FPS

```

Edit: I've got a 32-bit processor

---

