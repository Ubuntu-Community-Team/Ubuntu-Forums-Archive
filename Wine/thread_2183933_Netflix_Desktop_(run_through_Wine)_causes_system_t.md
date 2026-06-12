---
title: "Netflix Desktop (run through Wine) causes system to overheat"
date: 2013-10-27
forum: Wine
---

### Post by b|ackhole on 2013-10-27
I figured a grumpy red face was probably how my computer feels when I run Netflix Desktop through wine.

Hey, I've come back to Linux after 3 years and it's been a great experience coming back until I realized that Netflix (a new addition to my entertainment life) did not support being viewed on Linux systems! How silly, I pay for it monthly.  Anyway, I have installed it onto my computer through Wine as the majority of ubuntu-related-install-suggestions have offered for me to do.  

So let me put up the pros:
[LIST]
[*]Audio is works great,
[*]Video quality isn't actually that bad, unlike much of the reviews I had read,
[*]Other than it freezing in full screen at one point it's easy to control the window.
[/LIST]

[COLOR=#ff8c00]**Okay and here is the problem!:**[/COLOR]
[LIST]
[*]When I run Netflix Desktop with Wine (how other way is there to run it?), my system heat goes from around [COLOR=#008000]**45[COLOR=#333333][FONT=Open Sans]&#8451;[/FONT][/COLOR] **[/COLOR]to **[COLOR=#008000]60[COLOR=#333333][FONT=Open Sans]&#8451;[/FONT][/COLOR] [/COLOR]**to a rather radiating **[COLOR=#ff0000]80[COLOR=#333333][FONT=Open Sans]&#8451;[/FONT][/COLOR] [/COLOR]**and sometimes up into the [COLOR=#ff0000]**100**[/COLOR]**[COLOR=#333333][FONT=Open Sans]&#8451;[/FONT][/COLOR]**s! (Which means at some points my computer has the potential to boil water, what is remarkable is that it doesn't shut down out of fear of melting itself, so I have to do it manually.)
[/LIST]

So far my computer has not had a heat issue running HD video in integrated video players or online streaming sources, it seems to be isolated to just running Netflix Desktop. I, from my memory, did not have a heat issue playing Netflix from Windows 7.

I cleaned my fan anyway to make sure that wasn't part of the problem, and some other suggestions put me through a list of things to do to make sure I didn't have any unessisary drivers running, and I didn't seem to be, but if someone thinks I should walk through those checks again or try new checks I'm up to suggestions.  

I'm running on ASUS U33JC (Bamboo):[INDENT]Memory: 5.6 GiB
Processor: Intel® Core™ i5 CPU M 480 @ 2.67GHz × 4 
Graphics: Intel® Ironlake Mobile  
64-Bit
[B]
Ubuntu 12.04 LTS[/B]

[/INDENT]

I'm always worried about posting things like this in case this has been reported already but in my searches I couldn't find this issue yet. If it's reported already, please let me know and I'll go there!

Thanks for the support!

---

### Post by b|ackhole on 2013-10-28
I reinstalled Ubuntu 12.04, reinstalled Netflix-Desktop a few times and now it seems that my heat issue has vanished! So, solved ... with a question mark as to what was causing the over heating.


EDIT: Okay I actually found the culprit! It seems that running the Hola Unblocker through Firefox in Wine was what was causing some of the heat issues. Not as bad as it was before but it did jump system heat up by 20 C after installing it.

---

