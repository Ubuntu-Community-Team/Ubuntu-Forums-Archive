---
title: "PunkBuster for WINE Petition"
date: 2008-09-14
forum: Wine
---

### Post by Devine on 2008-09-14
Greetings!

I have made a petition to provide evidence of community support for a punkbuster client for WINE.

[http://www.petitionspot.com/petitions/PunkBusterforWINE](http://www.petitionspot.com/petitions/PunkBusterforWINE)

[i]
As legitimate owner of a game, regardless of platform (providing that it will actually run) - one should be entitled to the online experience attached to the game.
Sadly, for many Windows(tm) games under WINE this cannot be done because of the PunkBuster Anti-Cheat protection which does not allow those using a WINE based API to access a PunkBuster protected server.

There is PunkBuster support for Linux game servers, so there is already in-house knowledge of Linux at Even Balance. CodeWeavers and Transgaming are distributors of commercial branches of WINE who would work with Even Balance to support their largest demographic. (the gamers!)

Anything that is which allows WINE users to access PunkBuster protected servers will be appreciated. (full implementation or not!)

This petition is to show community and market support to the parties who will be involved in providing PunkBuster support for community and commercial WINE based products.[/i]

BTW, for those who are about to post "Your issue isn't with X it is with Y" - I don't care, somebody has to budge to resolve this issue.

Just sign.
Please tell your friends!

[CLICK HERE TO SIGN!]("http://www.petitionspot.com/petitions/PunkBusterforWINE")

---

### Post by asdfoo on 2008-09-18
> **Devine said:**
> Greetings!

I have made a petition to provide evidence of community support for a punkbuster client for WINE.

[http://www.petitionspot.com/petitions/PunkBusterforWINE](http://www.petitionspot.com/petitions/PunkBusterforWINE)

[i]
As legitimate owner of a game, regardless of platform (providing that it will actually run) - one should be entitled to the online experience attached to the game.
Sadly, for many Windows(tm) games under WINE this cannot be done because of the PunkBuster Anti-Cheat protection which does not allow those using a WINE based API to access a PunkBuster protected server.

There is PunkBuster support for Linux game servers, so there is already in-house knowledge of Linux at Even Balance. CodeWeavers and Transgaming are distributors of commercial branches of WINE who would work with Even Balance to support their largest demographic. (the gamers!)

Anything that is which allows WINE users to access PunkBuster protected servers will be appreciated. (full implementation or not!)

This petition is to show community and market support to the parties who will be involved in providing PunkBuster support for community and commercial WINE based products.[/i]

BTW, for those who are about to post "Your issue isn't with X it is with Y" - I don't care, somebody has to budge to resolve this issue.

Just sign.
Please tell your friends!

[CLICK HERE TO SIGN!]("http://www.petitionspot.com/petitions/PunkBusterforWINE")

I'm not sure that your approach is right, I think you should have put some more thought into this and maybe gathered some more information about the situation, PunkBuster works for some games, I play on PB enabled servers with Battlefield 1942.

Maybe it would be a better idea come up with an letter to EvenBalance stating the short comings of their software and give them something more like a solution rather than a problem.  That way everyone interested can say something constructive by using it as a template for voicing their concerns to EvenBalance rather than just give their details to a petition on some website.

EvenBalance can do a native linux client of PunkBuster that ships with the windows version of games that can be loaded if the software knows its running under Wine.  Considering they've already done a native client for Americas Army, it might not even be that hard.

---

### Post by Devine on 2008-09-20
That is a pretty good idea - perhaps I will combine the two.

However, I feel that one of the problems is that they cannot see the greater scheme of things and only see "a few users here and there".

Gathering the community together will help make a **solid impact**.

We need to be recognized as a large community of their customers who require a service... Not just a few people not using Windows. (yes it should be simple) 

I think the best way (I'm not a software engineer though) for Even Balance to provide a version of PB for Wine users would be to make the version for Wine - not for Linux. Trying to make a version for Linux which also enables WINE users is the long way around and possibly pretty difficult to develop. 
Note: Yes, having Linux developers already in Even Balance should help a lot.

The shipping of the version of the client would to be through online download, because trying to get the support of the game company to include the Wine client on their disc is well... futile.

---

### Post by asdfoo on 2008-09-20
> **Devine said:**
> That is a pretty good idea - perhaps I will combine the two.

However, I feel that one of the problems is that they cannot see the greater scheme of things and only see "a few users here and there".

Gathering the community together will help make a **solid impact**.

We need to be recognized as a large community of their customers who require a service... Not just a few people not using Windows. (yes it should be simple) 

I think the best way (I'm not a software engineer though) for Even Balance to provide a version of PB for Wine users would be to make the version for Wine - not for Linux. Trying to make a version for Linux which also enables WINE users is the long way around and possibly pretty difficult to develop. 
Note: Yes, having Linux developers already in Even Balance should help a lot.

The shipping of the version of the client would to be through online download, because trying to get the support of the game company to include the Wine client on their disc is well... futile.

If you are not a software engineer, I'm not sure how you can judge how difficult my suggestion is.  There is nothing difficult about it and it has been done before to interface with other things.  It's easy to forward functions from a Wine dll to a Linux library.

It is also possible to call other programs and Linux library functions from a Windows program running under Wine, which can be detected by checking for the wine version function in ntdll.

Doing this, they would be reusing their existing Linux codebase.

PunkBuster already does online delivery for all PB enabled games, all clients check for updates against EvenBalance's servers periodically.

This method is the only one they'd likely pursue because PB in its current form uses techniques (finger printing) that are only likely to work on Windows which is the premise of the technology. Modifying PB to check for genuine Wine as I think you are suggesting doesn't make sense, since anyone is free to modify Wine as they see fit, as well as factors such as varying compiler optimizations, changes in compiler versions would see code layout, size and variations which cannot be relied upon to be constant.

*Edit*

In retrospect, the reasons above might add further weight to why they wouldn't want to support Wine and that it might be a pointless endeavour to try, since everyone has the freedom to modify how things will work as provided by the LGPL.  They can only rely on security by obscurity, as provided by Microsoft, hence only support Windows platforms.

---

### Post by Devine on 2008-09-20
Your explanation about why a native Linux version is better makes sense now. I agree with you - but I was thinking that they could simply mod a Windows version to check some Wine specific calls to validate if it is Wine or not.

Yes, I have also thought about the GPL/Open Source factor... I will think about it a bit more before I comment on that.

---

### Post by Shining Arcanine on 2010-06-26
All they need to do is remove the code that does kicks when "UNKNOWN WINDOWS API FUNCTION [131124]" is detected and WINE would run perfectly:

[http://bugs.winehq.org/show_bug.cgi?id=9685](http://bugs.winehq.org/show_bug.cgi?id=9685)

---

### Post by cogadh on 2010-06-26
Nice resurrection of a very old thread.

The "removal" of that code is not the problem, the way PunkBuster works is the problem. Like most anti-cheat software made for Windows, it relies on a kernel-mode driver to accomplish its task and since Windows drivers do not and never will work in Wine, PunkBuster won't work. Until there is a fundamental re-working of PunkBuster itself (unlikely to happen), it will never fully work in Wine.

---

### Post by hadi2 on 2010-09-07
Bill wont allow evenbalance to do this LOL
The real problem is Bill

---

### Post by Insomn1a on 2010-09-20
There use to be a CVAR in many games that punkbuster was a part of that would allow punkbuster to ignore all API calls, this would also stop the Windows Api Error [131133] from occuring. I've submitted a trouble ticket regarding that specific CVAR to punkbuster and I'll update this thread whenever the reply comes.


Yes i know, very old thread, would rather keep it in one thread though.:KS

---

### Post by VH-BIL on 2010-09-22
I signed the petition...
Looking forward to updates!

---

