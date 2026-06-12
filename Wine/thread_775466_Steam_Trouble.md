---
title: "Steam Trouble"
date: 2008-04-30
forum: Wine
---

### Post by jjstein on 2008-04-30
I recently installed Steam with wine. Everything seemed to work fine, but all the games were running incredibly slow due to the fact that I had not yet set up my graphics drivers. I set them up but now every time I attempt to open a game, steam just closes. Any insight on this problem would be much appreciated. 

thanks

---

### Post by aoanla on 2008-04-30
Hi. It's quite hard to help people when they don't actually give any details.

Can you tell us what version of Ubuntu you're using, the version of Wine, the graphics card (and the version of its drivers) and the output on the terminal when the game closes.

Also, tell us if things work better if you launch games with the "-dxlevel 81" option set in their Launch Options in Steam.

---

### Post by jjstein on 2008-04-30
Alright I will try to provide details to the best of my ability.  I am using gutsy, Wine is version 0.9.59, the graphics card is an ati radeon express 200m.  I'm not too sure how to check the driver version.  Also, how do you set it to the "dxlevel 81"?

Oh and any attempts to open steam with terminal is failing which means I am undoubtedly doing something incredibly wrong.  how do i do that?

---

### Post by aoanla on 2008-04-30
The fact that you don't know your driver version implies that it is the stock one that comes with Gutsy. Did you enable it by turning on Restricted Drivers or something?

I strongly suggest you upgrade your graphics card driver to a newer version - the ATI drivers may be bad, but the older ones are considerably worse.
Have a look at using Envy to do this, since it'll be easier for you.

Run Steam in a terminal by using:

cd ~/.wine/drive_c/Program\ Files/Steam
wine steam.exe

You set Launch Options in Steam by selecting your game, then clicking on Properties (in the bottom right corner of the Steam window), and setting the Launch Options accordingly.

---

### Post by jjstein on 2008-05-01
I used envy to install drivers. Also, I will try this

---

### Post by jjstein on 2008-05-01
Exactly what do i type for launch options?


Oh, and when I launch a game i get this:


X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  1938972
  Current serial number in output stream:  1938973

---

### Post by aoanla on 2008-05-01
I told you what to type for your Launch Options in my first reply!

Add "-dxlevel 81", without the quotes.


That error looks like your 3d graphics acceleration isn't working properly.

Can you tell me the output of typing

fglrxinfo

and

glxinfo | grep render

in a terminal, please?

---

### Post by jjstein on 2008-05-01
ah I'm sorry I didn't realize you had said that.

I typed : 
fglrxinfo

and got:
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)

and I typed: glxinfo | grep render
and I got:

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

---

### Post by aoanla on 2008-05-01
Right. 
Those results indicate that the drivers you installed are not working. This is why Steam games aren't working for you, either.

I suggest that you get some help with your graphics drivers (or search the forum for such help - lots of people have issues with ATI graphics drivers, in particular, and your particular issue has probably already been had by someone else), and then Steam games will almost certainly start working.

---

### Post by jjstein on 2008-05-01
Well thats just terriffic.  Thanks for the help and Ill look into it.

---

