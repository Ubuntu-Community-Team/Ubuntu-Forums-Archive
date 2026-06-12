---
title: "World of Warcraft wont Install!"
date: 2008-04-24
forum: Wine
---

### Post by iheartubuntu on 2008-04-24
I have installed WoW on two other ubuntu linux computers without a problem. They work great. No problems. 

I have followed the 'WoW on Ubuntu' guidelines here, and the normal procedure is to install Wine, then copy the files from the WoW discs to a folder on the Ubuntu desktop, then run the install file in the folder and the game will install. Not on this new computer. While installing, I get an error message saying it is either a media problem or a drive problem (error code 38 ).

I have also installed the DLL files listed in the troubleshooting guide here, but that didnt help any.

As one of the last resorts, I downloaded the 3GB game from the internet (via the WoW Ubuntu forum link above) and the computer froze at about 2/3s of the way through. Any opportunity to restart the download crashes the whole computer.

This computer is a new laptop 4GB of mem and 512mb nVidia video card. Any help would be appreciated to get WoW working on this system.

Thanks for any help!

---

### Post by jbysmith on 2008-04-24
You say you have WoW installed on another machine?  Save yourself a lot of headache and trouble; just copy the entire WoW directory over the network.  (It'll save you patching time later too)  If you don't have access to those other installs, you can do the same thing via a virtual machine too.  Not a fix, but it's a viable workaround.  I had a similar problem on one machine myself back when I used to play WoW and never did figure out why it wouldn't install properly.

There's no special registry entries for WoW; when I used to play WoW I've copied it around a lot with zero issues.  The only registry entry I made by hand was for "GL_ARB_vertex_buffer_object" to boost OpenGL performance on a new Wine install.  Other than that, just need to make yourself a menu entry for the program and off you go.  I also set WoW to run in a "full screen window".  Runs just as fast, and didn't play havoc with Wine when you switched desktops and the like.  (Used to have the WoW window 'get lost' when I switched to another desktop, running in a full screen window got around that)

---

