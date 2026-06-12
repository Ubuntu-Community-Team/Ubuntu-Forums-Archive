---
title: "Terrible World of Warcraft 4.2.0 Glitches on Ubuntu 11.10"
date: 2011-11-21
forum: Wine
---

### Post by Desiderantes on 2011-11-21
I get those graphical glitches when running WoW 4.2.0 with wine (Ubuntu 11.10 AMD64), in  a Dell XPS 15(L501X), even with ironhide.

Anyone can help me?

EDIT: 
-CPU: Intel Core i5-460M
-4gb RAM
-because it's a Dell XPS 15(Optimus Technology), i have 2 graphic cards:
 An Intel HD 460M integrated graphics card, which driver is i915
 A nVidia GeForce GT 420M, Due to Ironhide/Bumblebee, i have to use noveau drivers for this, even if ironhide asked for propietary drivers.
-Running Ubuntu 11.10 AMD64 with custom XFCE Desktop
-Wine 1.2.1(Emulating win2000)
-corefonts and vc2005 installed on Wine

[http://i.imgur.com/FDU6x.jpg](http://i.imgur.com/FDU6x.jpg)

---

### Post by cwwilson721 on 2011-11-21
[SIZE="4"]***_DIRECTLY FROM THE STICKY:_***[/SIZE]
> Things you should try before asking for help:
[COLOR="Red"]Use the proprietary drivers for your video card - many graphics issues in Wine are due to missing features in the free drivers for various video cards. Try enabling the proprietary drivers for your video card, if available, using System->Administration->Additional Drivers.[/COLOR]
Check AppDB - Wine's Application Database is one of the best sources for help with running apps in Wine. First and foremost, it will tell you when an application is not worth trying at all. Secondly, but almost as important, an application's AppDB entry may include how-to information on a working way to install and run your application.
Never run Wine with sudo - Do not run Wine as root or by using sudo. Doing so doesn't help anything and will break your fake Windows installation entirely.
Do not try and install DirectX - Wine already has its own implementation of DirectX, and attempting to install the Windows version might break some things. Cancel or skip the install if an application prompts you.
Reinstalling Wine won't help - Reinstalling the same Wine package in Synaptic or Software Center won't do anything - your virtual Windows drive and applications will be just the same unless you manually remove them. What you probably wanted to do is erase your fake Windows install entirely; to do this, you must remove (or rename) the hidden .wine folder in your home directory (view->show hidden files). This will erase all Windows applications you've installed with Wine and let you start fresh. Note that you'll still have (nonworking) start menu entries for the removed apps in Applications->Wine unless you first removed them with Wine's uninstaller.
Update Wine - Unless you have specific information that the latest version of Wine won't work, you should try updating to the most current version of Wine. Each update includes many bugfixes that can correct your issue. However, it is important to note that an update could include new bugs or regressions that will cause problems with some applications. If you are manually selecting versions, please note that they are two digit numbers: Wine 1.1.10 is newer than 1.1.9.
Search the forums - There are many, many posts on running specific applications in Wine already. Chances are really good that someone has already asked the same question you have.
Try different Windows versions - Much like Windows itself, Wine supports different "compatibility modes" for different versions of Windows.
Check the terminal output - Perhaps I should say "Use the terminal" first. When run from the terminal, Wine outputs any error messages to the terminal window, which may tell you exactly what is wrong. This is especially useful for identifying when a DLL is missing and using winetricks may be needed. Check the output for details like that and anything else that may identify where your error is occurring.

Things to include when asking for help:
Wine and Ubuntu version - Wine betas are updated roughly every two weeks. Each update includes numerous changes and fixes. Knowing which version you are using can often lead to very specific fixes for whatever problem you may be having.
Terminal output - Run your application from the terminal and include the output in your post (make sure you use the forum CODE tags). The informational and error messages provided in the terminal can be very helpful in pinpointing where the problem is occurring.
Wine configuration - How you have Wine configured changes how Wine behaves greatly and may be the cause of whatever issue you may be having. Configuration changes you should mention are anything you've modified in winecfg or the registry, any winetricks steps you've done, and any other special software you've installed (eg, .NET framework).
[COLOR="red"]Hardware specs/drivers - Name your video card and say whether you're using the proprietary or stock drivers. lspci on a terminal can help identify the chipset if needed (it'll show up as VGA compatible controller, display adapter, or something similar).[/COLOR]
Other Wine applications - Include any other apps you may have installed in your Wine directory. Be sure to mention if you've used third party tools like winetricks or PlayOnLinux.
Providing this info will greatly increase the chances that someone on these forums will be able to help solve your problem.


Search will reveal, info will get an answer

---

### Post by Desiderantes on 2011-11-21
Added more info. Hope it helps.

---

### Post by ubupirate on 2011-11-21
You should probably update Wine to either latest stable or latest development. 1.2.1 is quite old, and there have been major changes since that time especially in the Wine development version.

Also try considering emulating Windows XP instead of Windows 2000, XP mode seems to work the best all around.

Also, are you using the Intel integrated or the nVidia card to play? Intel has rather weak OpenGL support, and most people using Intel cards to play usually end up with such graphical glitches.

---

### Post by Desiderantes on 2011-11-21
I've upgraded to Wine 1.3.32 from the Wine ppa, still tha same issue. I get that behaviour with both intel and nvidia cards. Also, i've tried switching to winxp emulation, but, still the same issue. Other games seems to work.

---

### Post by cwwilson721 on 2011-11-22
ok. Hate to say this AGAIN

[LIST]
[*]Intel: Forget about it. Search this forum for a 'resolution'. It works for some, and doesn't for others.
[*]Nvidia: Whether you want to or not YOU HAVE TO INSTALL PROPRIETARY DRIVERS if you want to play WoW
[/LIST]

Or, you're on your own.

There are TONS of threads on this VERY subject all over this forum.

So, install the proprietary drivers for Nvidia. Or don't play on Linux.

It's not Ubuntu that is the issue. It's your kernel drivers. Would happen for all versions/distros of Linux using wine/WoW.

The open source drivers, while doing a GREAT job, cannot handle '3D' graphics like the proprietary drivers do.

---

### Post by Desiderantes on 2011-11-22
Now i tried with the propietary driver, and still the same issue. However, for some reason, audio got a better quality :l

---

### Post by cwwilson721 on 2011-11-22
Basic list to get WoW to work:
[LIST]
[*]Install latest wine (Look at the stickies in this forum to get the PPA)
[*]Install proprietary driver
[*]Run WoW in XP mode (winecfg. While there, disable sound for now. if the option is even available. Get video working first)
[*]Edit launcher command to launch WoW in OpenGL (Add '-opengl' at end. This will also add the appropriate line in config.wtf). Don't even bother with D3D for now. Get it working first.
[*]Make sure that Compiz is OFF (Do a Google search of 'Ubuntu Compiz Disable' if you don't know how). Compiz and other Desktop Effects can really mess with wine/WoW
[/LIST]

Try those ALL. Don't assume you have already done so.

---

### Post by ubupirate on 2011-11-22
> **cwwilson721 said:**
> Edit launcher command to launch WoW in OpenGL (Add '-opengl' at end. This will also add the appropriate line in config.wtf). Don't even bother with D3D for now. Get it working first.

You can also optionally add this line to your Config.wtf file instead of using the -opengl option:

```
SET gxApi "OpenGL"
```

---

