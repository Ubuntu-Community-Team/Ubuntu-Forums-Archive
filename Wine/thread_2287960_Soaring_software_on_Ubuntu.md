---
title: "Soaring software on Ubuntu"
date: 2015-07-23
forum: Wine
---

### Post by john_smith32 on 2015-07-23
I'm running Ubuntu 15.04 on my laptop and would like to run [I]"Soaring Pilot's Intelligent NOTAMs Editor" (SPINE)

Has anyone out there managed to get this program running on a LINUX machine.

I contacted the author and he told me he thinks it is running on linux but I have tried with no success.

Thanks, in anticipation.
John
[/I]

---

### Post by Simon_Tomoko on 2015-07-26
Yes I downloaded it just now and got it up and running in WINE version 1.6.2 on 14.04.  I assume you did not read the author's note about the redistribution package?  At the system prompt you need to use winetricks  to install; 

winetricks vcrun2010  
wine setup.exe

I hope it works for you.

---

### Post by john_smith32 on 2015-07-29
I have looked on his website and see no reference to vcrun2010: There is reference to vcredist_x86.exe however. Would this be the same - only updated?

Thanks,
John

---

### Post by Simon_Tomoko on 2015-07-29
Yes, same thing John, "Visual C redistributable 2010" is just installed with the command line;  [COLOR=#000000]winetricks vcrun2010 

There is a legal blurb about using it (as with all software) and then it installs. Since the authors used Visual C, there are libraries it needs from the package freely distributed by MS. I think they just like reminding us where they dominate their little corner of the world.  I guess I don't understand the programmer's world to well.  I don't think I want to either.  So I take it you are a pilot?  I'm just getting into skydiving myself.[/COLOR]

---

### Post by john_smith32 on 2015-08-01
Thanks for the advice.
I did what you advised and although the SPINE logo appeared on the Launch Bar for several seconds, it disappeared and I can-not find the program anywhere...

Yes, I am a sailplane pilot.

Have fun with the skydiving.

Rgds,
John

---

