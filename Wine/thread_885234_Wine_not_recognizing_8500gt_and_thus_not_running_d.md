---
title: "Wine not recognizing 8500gt and thus not running directx"
date: 2008-08-09
forum: Wine
---

### Post by devosion on 2008-08-09
This is what I assume is happening because I have done a couple of tests to verify my suspicions. Apparently my 8500gt is not being recognized and directx is not operating. After attempting to install and run a variety of directx applications (Guild Wars, World of Warcraft, Starcraft, and Diablo II) I have routinely received d3d: errors, or something similar. Bash ends with close to a thousand lines of these errors just upon startup of a program, but incidentally some of these programs run on a limited basis. Guild Wars will get to the title screen, but won't proceed past loading an area. Diablo II just refuses to run as well as Starcraft. World of Warcraft arrived at the title screen and got no further. What sealed the deal was when I installed Photoshop CS2 and have routinely received hardware errors shortly after it loads. After which Photoshop will promptly close. I have attempted various OS settings, and ensured the graphic keys are set up as mentioned on the Wine AppDB but none of this helps. Im somewhat at a loss so im open to suggestions. It's also noteworthy that I can run glx apps just fine in ubuntu. EVE online works perfectly. Any assistance will be appreciated.

---

### Post by astroboy78 on 2008-08-09
Here's my humble guess...

The 8500GT is a DirectX 10 card. It could be incompatible with some DX9 calls, which MS Windows "translate" to the new API (Wine doesn't, it's based on DX9).

Do you have the latest nVidia drivers installed (not the one from Ubuntu restricted drivers, but from an installer application like ENVY)? Try to update your graphic driver and see if the games you try to play works better...

The Envy installer url: [URL="http://albertomilone.com/nvidia_scripts1.html"]http://albertomilone.com/nvidia_scripts1.html
[/URL]

---

### Post by devosion on 2008-08-09
The 8500gt is actually a DX9 card with some DX10 enhancements so im pretty sure thats not it. Im beginning to think using Envy instead of the proprietary drivers may help, but I hadnt checked recently to see if there was a version of Envy that worked in Hardy. Now that I know i'll give it go and see if it helps. Thanks!

---

### Post by hikaricore on 2008-08-10
First why aren't you running these games in opengl mode? They support it.

Second have you checked that you installed the drivers properly?

```
glxinfo | grep rendering
```

Please let us know your installation method and what version of the NVIDIA driver you are using.
Example I'm using:  *NVIDIA 173.14.12*

Third, I hope to god you didn't try to install directx under WINE, as this doesn't do a damn thing in most cases except cause more problems.
DirectX is not supported by Linux or WINE, your card has perfectly good OpenGL capabilities.
DX calls in wine are converted to OpenGL using more cpu/gpu resources.
Running games that support it in OpenGL mode will work greatly in your benefit.

---

### Post by devosion on 2008-08-10
> direct rendering: Yes


Too be quite honest im not quite sure how to do that. If you are speaking about enabling the registry key DirectDrawRenderer=opengl, then it has already been taken care of along with a number of other recommended keys from wine's app database Guild Wars entry.

Incidentally I was able to play my games just fine using the 8500gt and envy drivers in Gutsy. It wasn't until I upgraded to Hardy that things went awry and I went back to using the proprietary drivers. And with that im also unsure what version of proprietary drivers im currently using, but im going to give Envy a shot to see if it will rectify this problem because everything else I have tried hasnt worked, including trying to get Guild Wars to run in Windows 98. If I continue to experience problems after installing the Envy drivers i'll update my post.

-

So after installing Envy I am able to run Starcraft, without sound, and probably Diablo II but I can seem to locate my disc. Photoshop continues to close with an error regarding hardware, and doesnt even allow me the chance to try to open a file. Guild Wars though continues to give me the same over a thousand lines of fixme messages, and then closing, usually on a segementation fault after the title screen and as it is about to open an area. I've included the trailing end of these messages in the hopes that somebody can help me out. WINEDEBUG=-all doesnt assist with this either, and the other flags such as -dx8, -noshaders, and -dsound do nothing as well, nor changing to different versions of Windows.

Hopefully with a little more work I can get Guild Wars and Photoshop up and running. I'd have given some info on World of Warcraft but I uninstalled it. When I have time i'll give it a shot, but im sure i'll end up with a stack of fixme's similar to those that Guild Wars kicks out.

---

### Post by Ferrat on 2008-08-11
Have you tried reinstalling WINE and getting latest graphic drivers? 

saw a similar problem here 

[http://ubuntuforums.org/showthread.php?t=635044](http://ubuntuforums.org/showthread.php?t=635044)

and since he got it working by switching to OpenGL my guess it that the extension in WINE is just broken, remove the .wine lib in your /home/$yourusername/ folder and remove WINE completely, install latest drivers for your card (173.14.12) and then reinstall WINE.

run winecfg, then just with out touching anything try and run Diablo again and see if you get the same result.

---

