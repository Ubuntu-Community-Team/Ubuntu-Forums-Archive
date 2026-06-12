---
title: "DXError.log"
date: 2011-11-01
forum: Wine
---

### Post by KaenDris on 2011-11-01
Before going on, I am a new Ubuntu user, and I switched from a Mac OSX, and i'm not too computer savvy.

I am trying to run "Rift" but as I finish with patching, it tells me: "Your Directx9 install needs to be updated." with the "DirectX out of date!" above. so I go through, and follow the steps to "update" it. I'm not sure EXACTLY what DirectX is exactly, but as i'm through with the 'download' it gives me an "Internal System Error Occured" message, telling me to refer to my DXError.log in my Windows folder. I don't have a Windows folder, to my knowledge. So, what i'd like to know is how do I make it so this doesn't keep occurring? Can I even run RIFT on this computer?:confused:

---

### Post by Suroh66 on 2011-11-01
Sounds like you may just need to throw in some missing Dll's and maybe a few other things if you haven't already open up your terminal and type winetricks ( or sh winetricks) For some reason they changed the script around so once you're in go to  "Select the default wineprefix" go to the first option then grab d3dx9_43, vcrun2005 and dotnet ( I use rift as well as wow and lotro and a few random others this is all I've really ever had to bother to get to make them work other then little workarounds) so once you have installed those try it again if it wors awesome :P If not open up your terminal and type "lspci" and post the info here Or just launch the game through the terminal and post the out put here it seems like a lot but it goes quick :D the last two steps I only sugest if the game doesn't work as some one may be able to give a more specific anser as to why

---

