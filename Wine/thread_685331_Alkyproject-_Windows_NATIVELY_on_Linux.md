---
title: "Alkyproject- Windows NATIVELY on Linux"
date: 2008-02-02
forum: Wine
---

### Post by booljayj on 2008-02-02
The Alky Project died not too long ago, and that is a darn shame. The Alky Project was an ambitious attempt to modify windows software to make it run natively- meaning with no problems whatsoever, as if it were made to run- on Linux. This was achieved using a 'scouting' program that would scan software and convert Win32 API calls to native Linux library calls. This is major, because it means fast, accurate windows software support on Linux.

When the project died, they released all of their source code. This is an urging to the masses: spread the word. This project is too good to just die away. This project could supersede Wine, and that's saying something.

---

### Post by loell on 2008-02-02
it died and could not be resurrected because the task is overwhelmingly difficult, remember wine started a decade ago, so imagine  how long it will take  to develop an aplication that could somehow run windows app natively on a non windows platform.

---

### Post by bastiegast on 2008-02-02
From Wine Weekly News issue 339:

> Alky

The Alky Project has recently closed shop. One key thing about their closing though is their decision about what to do with already written code:

However, every ending tends to open another door for opportunity and though we are saddened to announce our departure, we are almost as excited to announce the immediate availability of ALL source code for the Alky Project!

This of course ignited some discussion on wine-devel. Stefan Dösinger explains that unfortunately most of the code will not be of use to wine.

Looking at their D3D10 implementation, it is comparable to Andras' soc code, with the difference that Alky has a few lines to create a gl context and send off vertices, but Andras has written a D3D10.idl header. Adding the functionality of Alky to Andras' code is a matter of hours, if we do it the hacky way. So all in all I think that the not yet integrated d3d10 that Wine has is more advanced.

As far as other libraries go, there isn't much to see either [...]

While the code may not be of any use for us(or anyone else, since Wine exists), Cody seems to have written a lot of code. It might not be comparable to Wine, which has enjoyed the work of almost thousand developers and is almost 15 years old, it seems to be quite some accomplishment for a project which has been developed by apparently one(two?) persons. (I have no comparison how Wine started though. I only had a Gameboy back then :-) ) 

---

### Post by OHJOY90 on 2008-02-02
Swings and roundabouts, when a door  is closed a window is opened, I suppose. Now that more than two developers can get their hands on the project's code eventually there may be a new version of it made by someone else, maybe even used in Wine seeing as they said that they wouldn't use most of the code, implying that they may use some of it.

---

