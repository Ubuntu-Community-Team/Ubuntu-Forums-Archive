---
title: "Hammer"
date: 2008-02-12
forum: Wine
---

### Post by blackdragon1157 on 2008-02-12
I've installed steam, played CSS, and now would like to get to the final thing I did on windows- map with Hammer.

I installed the SDK, configured it with -engine ep1.   Hammer starts up fine, but when I try to create a new map, I get a flashy black screen.  AppDB says that running hammer.exe directly with -opengl works, but I've had no luck doing this (and the AppDB entry seems vague at best).  Anyone have any ideas?

I'm running wine 9.54 and the terminal output if I run steam and then Hammer consists of several lines of 
err:d3d:IWineD3DSwapChainImpl_Present Cannot change the destination window of the owner of the primary context
fixme:d3d:IWineD3DSwapChainImpl_Present Unhandled present options 0x34fbb0/0x34fbc0

---

### Post by blackdragon1157 on 2008-02-14
Nobody? :(

---

### Post by hansarinomeister on 2008-02-22
i have a problem very close to yours

i too did the -engine EP1 thing which got it running, only like you it was flickering and mostly black and unusable.
then i tried running hammer with:
"wine hammer.exe -- -opengl"
first it gave me an error saying it couldn't find steam.dll, so i symlinked it into the dir that hammer.exe was in, now it gives me this:
$ wine hammer.exe -- -opengl
AppFramework : Unable to create system VEngineCvar003!

note: the working dir was:
/home/horratio/.cedega/Half-Life 2 (DVD)/c_drive/Program Files/Valve/Steam/SteamApps/ihatesteam617/sourcesdk/bin
but im running it with wine because cedega stopped working. it doesn't seem to have any negative effects, css works great(aside from the rather annoying registry in use thing, but i'm not fussed about that atm). i tried moving the valve directory tree too the wine cdrive but it doesn't work and i have to move it back to the cedega dir to make it work.

i'm running wine 9.55 and ubuntu 7.06 feisty

i feel that if i could get past that strange error i would be set, but i just don't know what it means, and neither does google :(


please help us knowledgeable guru's

thanks in advance

---

### Post by blackdragon1157 on 2008-02-22
Wine 9.56 release notes say:
Proper handling of OpenGL/Direct3D windows with menu bars.

Hope, perhaps?

---

