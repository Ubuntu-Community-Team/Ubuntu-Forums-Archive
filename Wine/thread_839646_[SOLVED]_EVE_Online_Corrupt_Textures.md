---
title: "[SOLVED] EVE Online Corrupt Textures"
date: 2008-06-24
forum: Wine
---

### Post by napalm brain on 2008-06-24
Hello everyone.

I recently just installed EVE Online. Everything has run smoothly and I can play the game without any *real* problems.

When I was creating my character, I first noticed a graphical corruption in the portrait. (See the attachment)

I enter the game and everything is fine. The textures are fine, including my portrait. I continue to play and then, while undocking, the ship gets the same corruption and I notice the station I am leaving has the same corruption. The corruption is on planets, space itself, other ships, and just about every other texture in the game. 

The textures are never like that to start off. It usually occurs while playing the game. I mean, the issue doesn't prevent me from playing but it isn't very aesthetically pleasing. 

Anyone have any suggestions with what to do?

[I am using the Linux client.]

---

### Post by Vadi on 2008-06-24
Yes - install wine, and install the windows .exe in wine.

I had the same issue. Wine solved that and it gives even better graphics than their cedega thing (props to CCP for doing it and supporting Linux however).

---

### Post by napalm brain on 2008-06-24
Well, see, I did that too. Everything looked great until I get to the license agreement and I can't scroll down because there's no text, which obviously prevents me from proceeding any further. Do you know of a possible fix for this?

---

### Post by Vadi on 2008-06-25
Yes, you need to download and install this: [http://mesh.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/arial32.exe)

---

### Post by napalm brain on 2008-06-25
Nothing at all. Thanks though. There doesn't appear to be anything in the wine font directory either. Maybe I did something wrong..

Any other suggestions?

---

### Post by Epsilon on 2008-06-26
Just use wine and the windows client, it's much better. After having installed the windows client,you need to start regedit just type regedit from console or alt-f2 regedit.
Then create a new key  HKEY_CURRENT_USER/Software/wine/Direct3D
under this new key create a string called "OffscreenRenderingMode
" with the value "fbo" now exit regedit start eve again, making sure shadows and hdr is turned off then it should render just as on Windows, except for the F11 maps which still aren't working.

---

### Post by napalm brain on 2008-06-26
Thank you, Epsilon! That actually solved part of the problem. The part of the login screen where the graphics are is now showing up. The text is still not there though. For some reason, the arial32.exe does nothing. It says it has installed but I can't find exactly where. There's nothing in the /windows/fonts folder. I've still yet to figure out why nothing has happened.

Vadi, do you happen to know why it isn't installing? Or anyone else for that matter?

---

### Post by Vadi on 2008-06-26
I had these fonts in "/home/vadi/.wine/drive_c/windows/fonts", try extracting the archive in there and see if it helps

---

### Post by napalm brain on 2008-06-26
Vadi, thank you! 

This has solved everything. I can now run it in Wine without any immediate problems! I will get back to you all if there are any other issues. Thank you once again Vadi and Epsilon! Your help has been tremendous.

---

### Post by Vadi on 2008-06-26
You're welcome

---

### Post by Progenitor101 on 2008-07-11
Hey Napalm, I'm playing Eve-online as well, moved windows to linux... which client are you playing with? Classic or the premium graphics one? Seems a bit dodgy for me at the moment.

---

### Post by napalm brain on 2008-07-11
I ended up using Windows client on WINE instead of the Linux client because the graphics were corrupt on it. Everything runs extremely well on WINE and I haven't had any real problems (aside from the missing text which was solved). What client are you using then?

---

### Post by Progenitor101 on 2008-07-11
I used the linux .deb installation which installs Cedega (runs as classic)..after tampering with different settings it was eventually playable with graphics although I could not run 2 clients (1 on a different desktop).
I'm downloading the windows client as you did to see if it's better.

---

### Post by Vadi on 2008-07-11
Yeah, it'll do better. Install wine (from add/remove) and use that to launch the client.

Props to CCP for making a deal to make the client easily available on Linux, but unfortunately they chose the wrong company to support it.

---

### Post by Progenitor101 on 2008-07-11
Thanks so much guys! Even says I can use premium graphics. Although if I'm running 2 clients I switch to classic graphics as my video card isn't a high end one but great to use premium when in single play action! Look out Eve...yarrrr!

---

### Post by napalm brain on 2008-07-12
Glad to help out a little. Have fun. :)

---

### Post by Progenitor101 on 2008-07-13
Well, it doesn't like running premium graphics after all....but still runs classic graphics better than cedega although still a bit clunky....sorta staggers a bit (for the lack of a better word) when more is happening on the screen. Turning off a lot of effects does help.
Will run 2 clients more successfully but again, with lots of effects turned off. I'm not a linux techno savvy person but don't want to go back to windows...
Keen to hear of others experiences!

---

### Post by t.rei on 2008-07-16
You might want to set wine to "vista" as OS.  Maybe that makes the premium run?

---

