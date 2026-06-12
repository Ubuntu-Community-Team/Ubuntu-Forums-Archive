---
title: "tips for getting XGL installed."
date: 2006-06-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by codemills on 2006-06-12
I am surfing on ubuntuforum's wiki's and all guides. there is NO new FRESH thread with guide for installing XGL on 6.06 drapper final ( TLS ) fresh install.

So far,   i have managed to install ati drivers smoothly.

```
anshu@amd64:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600SE Generic
OpenGL version string: 2.0.5814 (8.25.18)

```


and wanted to proceed with XGL install, one guide failed me, so i removed xgl-server compiz and wanting to get this installed again.

[http://www.ubuntuforums.org/showthread.php?t=127090](http://www.ubuntuforums.org/showthread.php?t=127090)

This thread looks good cause it has somewhat complete list of needed things to get XGL running. (other guides depend of apt-get to sort out dependency and dont mention)

I got stuck with installing all files.

```
anshu@amd64:~$  sudo apt-get install libx11-6 libx11-dev libxau-dev libxau6 libxcomposite-dev libxcomposite1 libxcursor-dev libxcursor1 libxdamage-dev libxdamage1 libxdmcp-dev libxdmcp6 libxext-dev libxext6 libxfixes-dev libxfixes3 libxfont-dev libxfont1 libxft-dev libxft2 libxi-dev libxi6 libxinerama-dev libxinerama1 libxkbfile-dev libxkbfile1 libxklavier10 libxmu-dev libxmu-headers libxmu6 libxmuu-dev libxmuu1 libxp6 libxpm-dev libxpm4 libxrandr-dev libxrandr2 libxrender-dev libxrender1 libxres1 libxss1 libxt-dev libxt6 libxtrap-dev libxtrap6 libxtst-dev libxtst6 libxv-dev libxv1 libxvmc1 libxxf86dga1 libxxf86misc1 libxxf86vm1 x11proto-bigreqs-dev x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-fonts-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-record-dev x11proto-render-dev x11proto-resource-dev x11proto-scrnsaver-dev x11proto-randr-dev x11proto-record-dev x11proto-render-dev x11proto-resource-dev x11proto-scrnsaver-dev x11proto-trap-dev x11proto-video-dev x11proto-xcmisc-dev x11proto-xext-dev x11proto-xinerama-dev libpng12-dev build-essential gcc gcc-3.4 libncurses5 libncurses5-dev libqt3-mt-dev m4 autoconf automake1.7 autotools-dev libtool libxfont-dev xtrans-dev libfreetype6-dev zlib1g-dev libgl1-mesa-dev gconf libgconf-dev gconf-editor cvs libgconf2-dev libwnck-dev
Password:
Reading package lists... Done
Building dependency tree... Done
libx11-6 is already the newest version.
libx11-dev is already the newest version.
libxau-dev is already the newest version.
libxau6 is already the newest version.
libxcomposite1 is already the newest version.
libxcursor1 is already the newest version.
libxdamage1 is already the newest version.
libxdmcp-dev is already the newest version.
libxdmcp6 is already the newest version.
libxext-dev is already the newest version.
libxext6 is already the newest version.
libxfixes3 is already the newest version.
libxfont1 is already the newest version.
libxft2 is already the newest version.
libxi-dev is already the newest version.
libxi6 is already the newest version.
libxinerama1 is already the newest version.
libxkbfile1 is already the newest version.
libxklavier10 is already the newest version.
libxmu6 is already the newest version.
libxmuu1 is already the newest version.
libxp6 is already the newest version.
libxpm4 is already the newest version.
libxrandr2 is already the newest version.
libxrender1 is already the newest version.
libxres1 is already the newest version.
libxss1 is already the newest version.
libxt-dev is already the newest version.
libxt6 is already the newest version.
libxtrap6 is already the newest version.
libxtst6 is already the newest version.
libxv1 is already the newest version.
libxxf86dga1 is already the newest version.
libxxf86misc1 is already the newest version.
libxxf86vm1 is already the newest version.
x11proto-core-dev is already the newest version.
x11proto-input-dev is already the newest version.
x11proto-kb-dev is already the newest version.
x11proto-xext-dev is already the newest version.
libpng12-dev is already the newest version.
build-essential is already the newest version.
gcc is already the newest version.
libncurses5 is already the newest version.
libncurses5-dev is already the newest version.
m4 is already the newest version.
zlib1g-dev is already the newest version.
gconf-editor is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: mesa-common-dev (= 6.4.1-0ubuntu8) but 6.5.1-0ubuntu14 is to be installed
E: Broken packages

```

Kindly guide me. is there any fresh new howto somewhere?

I am going to go with this nvidia guide [http://www.compiz.net/viewtopic.php?id=652&p=1](http://www.compiz.net/viewtopic.php?id=652&p=1) and pick up ati steps from elsewhere 

Thanks.

---

### Post by Bokonon on 2006-06-12
I am an nVidia user, but I think the guides are pretty good.  Check the stickied one from the "General" forums.  Something like "One thread to rule them all".  From there you can find a link that will work.

Good luck.  Getting things to work on ATI is not an easy task.  I liked the performance when ATI had the inside info on DX9 and nVidia didn't, but nVidia has caught up/passed them now and has always had better linux support.

Edit: You might have to poke around a bit more for AMD64 support.  AMD+ATI is probably the least supported config for Xgl/Compiz.  This [thread]("http://ubuntuforums.org/showthread.php?t=133427") worked for me on my AMD64, but the packages are outdated.  My latest install uses AMD64 packages from the compiz.net site that you liked to and I have it working in dual session mode--including water.

---

### Post by JoWilly on 2006-06-12
All the latest and always updated xgl/compiz/glitz/mesa 64bit packages are in the raof repo : [http://raof.dyndns.org/falcon/]("http://raof.dyndns.org/falcon/")

Once you have 3D running (tested), you only need to edit gdm.conf-custom as per the howtos and add "gnome-window-decorator" and "compiz --replace gconf" to your gnome startup session.

Nothing else to do, its very easy.

---

### Post by codemills on 2006-06-14
[QUOTE=JoWilly]All the latest and always updated xgl/compiz/glitz/mesa 64bit packages are in the raof repo : [http://raof.dyndns.org/falcon/]("http://raof.dyndns.org/falcon/")

Once you have 3D running (tested), you only need to edit gdm.conf-custom as per the howtos and add "gnome-window-decorator" and "compiz --replace gconf" to your gnome startup session.

Nothing else to do, its very easy.[/QUOTE]

This link worked, installed all, but the window (gnome-terminal) border use to disappearwhen starting xgl/compiz . everything else ran super smooth.

just want to tell you, XGL / Compiz run smoothly on this configuration (AMD 64 / Ati Radeon 9600 Nforce 3 mobo etc) in fedora 5, 


Now the last and hardest way to test this is source compile which i never thought i would have to choose on ubuntu reading all over net how it has super community support etc. anyway.

Will tell you guys later about this, I am doing all this when i hav no time actually between work and rest_of_life.

---

### Post by JoWilly on 2006-06-14
[quote=codemills]This link worked, installed all, but the window (gnome-terminal) border use to disappearwhen starting xgl/compiz . everything else ran super smooth.

just want to tell you, XGL / Compiz run smoothly on this configuration (AMD 64 / Ati Radeon 9600 Nforce 3 mobo etc) in fedora 5, 


Now the last and hardest way to test this is source compile which i never thought i would have to choose on ubuntu reading all over net how it has super community support etc. anyway.

Will tell you guys later about this, I am doing all this when i hav no time actually between work and rest_of_life.[/quote] 
Why do you want to compile from source ? There's actually no need for that...

Regardign the window borders disappearing : the problem is "gnome-window-decorator". Make sure it is in your gnome startup sessions as well as "compiz --replace gconf" (menu/system/preferences/session/startup) ; in earlier version gnome-window-decorator needed to be liste before compiz for is to work properly, you could check this too.

---

### Post by codemills on 2006-06-14
[QUOTE=JoWilly]Why do you want to compile from source ? There's actually no need for that...

Regardign the window borders disappearing : the problem is "gnome-window-decorator". Make sure it is in your gnome startup sessions as well as "compiz --replace gconf" (menu/system/preferences/session/startup) ; in earlier version gnome-window-decorator needed to be liste before compiz for is to work properly, you could ckeck this too.[/QUOTE]

i admit , i rather quickly gave up on using repo's and quickly deciding to resolve by going source compile.

now after having second third look on this, i do think its matter of gnome-window-decorator.

at my system here in ubuntu , i only have one binary for it, i.e /usr/bin/gnome-window/decorator . isnt there a XGL binary of it? i think there is ,

plus, i have the below mentioned setup regarding sessions.
```

---------------------------------------------------------------
anshu@amd64:~$ cat /usr/bin/startcompiz
killall gnome-window-decorator
wait
gnome-window-decorator &
compiz --replace gconf miniwin decoration wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water &
----------------------------------------------------------------
```

Now i have added /usr/bin/startcompiz at my session in gnome. and that doesnt work , the borders of any window are gone and weird behaviour when doing stuff. only wobbly menu effect for tool-tip and menu action is good. and can rotate the cube easily.


BTW at gdm.conf-custom , below is the setting.
```

[servers]
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX).
#1=Xgl

#[server-Xgl]
#name=Xgl server
#command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
#flexible=true
anshu@amd64:~$


```

additionally, if i do startcompiz in terminal, the below errors start spitting all over in terminal non-stop with workspace switch getting disabled due to this. i just haveto restart X for this.


```

iz.real: No GLXFBConfig for depth 32
compiz.real: Couldn't bind redirected window 0xa00002 to texture
compiz.real: No GLXFBConfig for depth 32
compiz.real: Couldn't bind redirected window 0xa00002 to texture
compiz.real: No GLXFBConfig for depth 32
compiz.real: Couldn't bind redirected window 0xa00002 to texture
compiz.real: No GLXFBConfig for depth 32
compiz.real: Couldn't bind redirected window 0xa00002 to texture
compiz.real: No GLXFBConfig for depth 32
compiz.real: Couldn't bind redirected window 0xa00002 to texture
compiz.real: No GLXFBConfig for depth 32
compiz.real: Couldn't bind redirected window 0xa00002 to texture
compiz.real: No GLXFBConfig for depth 32
compiz.real: Couldn't bind redirected window 0xa00002 to texture
compiz.real: No GLXFBConfig for depth 32

```

:confused:

---

### Post by warp99 on 2006-06-14
[QUOTE=codemills]

```

iz.real: No GLXFBConfig for depth 32
compiz.real: Couldn't bind redirected window 0xa00002 to texture
compiz.real: No GLXFBConfig for depth 32
compiz.real: Couldn't bind redirected window 0xa00002 to texture
compiz.real: No GLXFBConfig for depth 32
compiz.real: Couldn't bind redirected window 0xa00002 to texture
compiz.real: No GLXFBConfig for depth 32
compiz.real: Couldn't bind redirected window 0xa00002 to texture
compiz.real: No GLXFBConfig for depth 32
compiz.real: Couldn't bind redirected window 0xa00002 to texture
compiz.real: No GLXFBConfig for depth 32
compiz.real: Couldn't bind redirected window 0xa00002 to texture
compiz.real: No GLXFBConfig for depth 32
compiz.real: Couldn't bind redirected window 0xa00002 to texture
compiz.real: No GLXFBConfig for depth 32

```

:confused:[/QUOTE]

Are you getting this error in /var/log/Xorg.**.log:

No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 24

If this is you a bug report was issued:

[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/37980]("https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/37980")

The problems you are having with compiz and the missing windows decorations is the EXACT same problem I'm having. I updated using the RAOF packages, but to be fair before the RAOF packages nothing in the repos worked. No compiz, no Xgl, nothing. :-(

---

### Post by JoWilly on 2006-06-14
[quote=codemills]i admit , i rather quickly gave up on using repo's and quickly deciding to resolve by going source compile.

now after having second third look on this, i do think its matter of gnome-window-decorator.

at my system here in ubuntu , i only have one binary for it, i.e /usr/bin/gnome-window/decorator . isnt there a XGL binary of it? i think there is ,

plus, i have the below mentioned setup regarding sessions.
```

---------------------------------------------------------------
anshu@amd64:~$ cat /usr/bin/startcompiz
killall gnome-window-decorator
wait
gnome-window-decorator &
compiz --replace gconf miniwin decoration wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water &
----------------------------------------------------------------
``` 
Now i have added /usr/bin/startcompiz at my session in gnome. and that doesnt work , the borders of any window are gone and weird behaviour when doing stuff. only wobbly menu effect for tool-tip and menu action is good. and can rotate the cube easily.


[/quote] 
Why do you use this startcompiz script ?

I have only added "gnome-window-decorator" and "compiz --replace gconf" to the gnome session startup (as above) and it has always worked perfectly since the first days of xgl/compiz on ubuntu.

Furthermore, there is no need to list all the plugins in the compiz line, these settings will be ignored anyway by gconf.

I understand you are having this trouble with the packages you have built from source. Have you tried the binary packages ? Do you get the same errors with them ?

---

### Post by joshrobinson on 2006-06-14
i have the same glxfbconfig problem, i posted a thread on here with the title name as the error, and no good help was recieved.. i posted one on the compiz.net forums, and also recieved no help, i even pm'd the guy who builds the source code and maintains one of the repo's and all he did was get angry at me and told me to post a thread about it.. which i had already done, and was 5 days old with no helpfull replies..

i think we are screwed on this problem

there is a patch for it.. but i couldnt get it to apply to the source code.. so xgl is out for me on my laptop, due to bad support on the compiz packages, and Quinnstorm himself

edit: here is the thread i made on compiz.net.. maybe if some more people reply with the problem they will actually help out the people who use their code/packages

[http://www.compiz.net/viewtopic.php?pid=8934#p8934](http://www.compiz.net/viewtopic.php?pid=8934#p8934)

---

### Post by fadeh on 2006-06-16
Look at this:

[http://www.compiz.net/viewtopic.php?id=1304](http://www.compiz.net/viewtopic.php?id=1304)


Hope it helps,

fadeh

---

