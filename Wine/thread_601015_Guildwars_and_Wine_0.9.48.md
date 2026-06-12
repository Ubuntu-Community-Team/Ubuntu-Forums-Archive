---
title: "Guildwars and Wine 0.9.48"
date: 2007-11-02
forum: Wine
---

### Post by thaekor on 2007-11-02
I am running Wine 0.9.48 and Ubuntu 7.10 Gutsy. When I click on my icon for Guildwars, the connection screen pulls up and tries to connect to Arena Net, but the game screen it self does not pull up. 

I have tried both the -windowed command, and the -dsound commands to see if that is the issue, but neither of them work. 

If it isn't obvious I am new to Ubuntu and Linux in general. I consider myself pretty computer savy, but if you could  be as detailed as possible I would greatly appreciate it.

Once again thanks in advance.

---

### Post by donkyhotay on 2007-12-21
Try running guildwars in the CLI (command line interface) and post the output when it crashes. Hopefully that will tell us what the problem is.

---

### Post by thaekor on 2007-12-28
not sure how to run a wine program on the command line. Sorry, I am very new to Linux.

---

### Post by kfcSmitty on 2007-12-28
I'm having the same issue. Well, not exactly.

I can load the main screen fine and I even once managed to get to the character selection screen using the ATI Proprietary Linux Drivers, but when I had those running Compiz-Fusion and AWN would not work for me, so I switched back to whatever the heck I am using now.

I've tried running from the CLI using:

env WINEPREFIX="/home/smitty/.wine" wine "C:\Program Files\GUILD WARS\Gw.exe" -dsound -dx8 -noshaders -windowed

as well as

env WINEPREFIX="/home/smitty/.wine" wine "C:\Program Files\GUILD WARS\Gw.exe" -dsound -windowed

and a few other variations. They all end up with the same result. A login screen that will not load.

Here is the error I believe is the culprit, but the game is still technically running when I receive these:

[quote=Errors]
fixme:d3d_shader:IWineD3DPixelShaderImpl_GenerateShader HW PixelShader Error at position 634: "1017: 'fogcoord': invalid fragment property"
fixme:d3d_shader:IWineD3DPixelShaderImpl_GenerateShader HW PixelShader Error at position 687: "1017: 'fogcoord': invalid fragment property"
fixme:d3d_shader:IWineD3DPixelShaderImpl_GenerateShader HW PixelShader Error at position 663: "1017: 'fogcoord': invalid fragment property"
fixme:d3d_shader:IWineD3DPixelShaderImpl_GenerateShader HW PixelShader Error at position 352: "1017: 'fogcoord': invalid fragment property"
[/quote]

Now, when I use the ATI drivers (which run much smoother, and I think some minor tweaks could have gotten the game running) I get an incompatible video card error. I continue on and it works much better than it is now. However, when I run this current setup, I get no error and the login screen shows only specific layers it seems. Sometimes a tree, sometimes the login box, sometimes the sky, etc.

If someone could either suggest a better driver to use or help me get this running on my current drivers, it would save me days more of playing around with this.


*edit* Figured I would post my lspci | grep VGA as well:

[quote=VGA]
02:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]
[/quote]

*edit2*

Hardware info

[quote=Hardware]
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
direct rendering: Yes
[/quote]

Thanks,

Smitty

---

### Post by kfcSmitty on 2007-12-30
on 3rd page and it's been 2 days..soooo...bump.

---

### Post by Catalyst2Death on 2008-01-05
I'm also trying to run guild wars, but I am having no luck.  I can't get anything that supposedly works in wine working... Guild wars crashes with the unrecoverable graphics driver error and then forces me to quit.  I've tried different settings, but nothing works...

---

### Post by kendase3 on 2008-01-31
A lot of it has to do with your graphics card.  While it runs perfectly fine (though at a lower framerate) on my nvidia card, my ati card machine just won't run the game properly.  It could be there are flags and such you can use to make it playable, but from my experience playing the game with ati cards is a no-go.

---

### Post by Toffeeapple on 2008-01-31
I know this dosent help... 

but!

I to have found that ATI is hopeless for most things in the world of Linux.. I've got myself an Nvidia card and now everything works fine..

---

