---
title: "Armageddon Empires and Wine issue, first mouse then the world"
date: 2008-04-14
forum: Wine
---

### Post by lastredoubt on 2008-04-14
Hello potential helpers, I've been trying to get Armageddon Empires to work under wine -- should have been an easy feat, since it has a solid platinum rating on the appDB -- but I have encountered several critical problems.

First, while using wine 0.9.49 the game worked beautifully, sound, speed, graphics, whatever -- except for one essential element, the game is gold.  That element, of course, is the mouse. Now, I had a cursor, and I had left-click action working fine...but the error occurred whenever I would try to right-click.  Right-clicking just did nothing -- no response, nada, zilch.  And if you've ever played Armageddon Empires (if you haven't you should check it out -- perhaps the best TBS game of recent memory) you know that the right-click is essential to progression in the game.

So, after not understanding that one for awhile, I decided to upgrade to the latest wine, 0.9.59 and tried it again.  Now this time, instead of increased performance, what I had on my hands, dear readers, was bogus lack of working.  The game took forever to load up and then once it had consumed my screen, it remained black instead of taking me to the main menu.  After clicking frantically about the screen for awhile the menu popped up, though it would soon freeze if I attempted to choose one of the tempting options, such as "New Game" or "Quit"...

So, I did a complete removal of wine via synaptic, as well as removing my /.wine folder from the terminal, and then reinstalled.  Same problem. 

I don't think it matters, but here is my terminal output from running the game:
> 
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:win:SetLayeredWindowAttributes (0x1002a,0x00000000,255,2): stub!
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\temp\\tmp6F380.FOT",L"C:\\windows\\temp\\AAX83e0.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\temp\\tmpF0480.FOT",L"C:\\windows\\temp\\AAX8406.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\temp\\tmp53480.FOT",L"C:\\windows\\temp\\AAX8423.tmp",(null)): stub
X connection to :0.0 broken (explicit kill or server shutdown).
 

That last bit was me killing the pesky program...
Any advice, aids, suggestions?

---

