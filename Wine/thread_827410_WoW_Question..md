---
title: "WoW Question."
date: 2008-06-12
forum: Wine
---

### Post by Pido on 2008-06-12
Hello all, I recently installed Hardy Heron and managed to install and configure WINE. 

The problem is I am getting is when I run WoW.exe my screen looks like this

[IMG]http://iroxu.com/uploads/pido/Screenshot.png[/IMG]
If you can't tell the there are 3 grey boxes in that picture, 1 for the cursor and 2 for the Login/Password fields.

I have an ATI Radeon x1300 graphics card. And the visual effects in Ubuntu are enabled and at max setting.

Can any share some insight on what may be the problem?

---

### Post by jjmurph on 2008-06-12
Are you running WoW in opengl mode?  By default it uses directx which doesn't work very well with wine.

```
wine WoW.exe -opengl
```You can also use glxinfo to check the status of your video card driver.  Here's a sample output:

~$ glxinfo
name of display: :0.0
display: :0  screen: 0
**direct rendering: Yes**
server glx vendor string: **NVIDIA Corporation**
server glx version string: 1.4

It should say direct rendering: Yes and the vendor string should be ATI in your case.  If the vendor string says Mesa then it's using the software renderer and there's a problem with your driver.

You might also want to try disabling the desktop effects and see if that makes a difference.

Hope that helps

---

### Post by Faud on 2008-06-12
There is one line that you need to add to your config.wtf file in WoW and it will work fine. Its all over this forums and is specific for ATI cards.
I'll see if I can find it but I know that its all over these forums and its in the main wow help thread.

---

### Post by johnl on 2008-06-12
I believe the line is

```

SET M2UseShaders "0"

```


Also, I agree with the poster above -- if you have desktop effects turned on, turn them off before playing!  It will make a huge difference, especially if your graphics card does not have a lot of video memory.

---

### Post by Pido on 2008-06-12
> **johnl said:**
> I believe the line is

```

SET M2UseShaders "0"

```


Also, I agree with the poster above -- if you have desktop effects turned on, turn them off before playing!  It will make a huge difference, especially if your graphics card does not have a lot of video memory.


Thank you very much, that worked perfect!

---

