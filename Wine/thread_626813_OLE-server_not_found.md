---
title: "OLE-server not found"
date: 2007-11-29
forum: Wine
---

### Post by hca on 2007-11-29
I get this error message when I try to install/run a free Windows program under wine for drawing airfoil sections for model airplanes. 

Where do I find such a server? My knowledge of Windows is very restricted, but i have the understanding that OLE stands for object linkage and embedding. 

Any helpful advice is highly appreciated!
/Hans Christian Andersen, Holte, Denmark.

---

### Post by cogadh on 2007-11-29
It would help to know a little more information, such as the name of the program, plus what version of Wine are you using and what error messages are output to the terminal when you run it (if any).

BTW - Is your name really [Hans Christian Andersen](http://en.wikipedia.org/wiki/Hans_Christian_Andersen)?

---

### Post by hca on 2007-11-29
The name and version of the program is Winfoil 3.2, and I tried to run it under wine-0.9.46. under Ubuntu 7.10. It used to work flawlessly under Ubuntu 6.06.
But after the re-enstall it demants the OLE-server which wine appears to be unable to find.
And yes, my name really is Hans Christian Andersen. I was christened just before WW2 and on the time a name repeating earlier Danish kings was very appropriate. There is NO family relations to a famous writer of the same name - alas!

/Hans Christian

---

### Post by cogadh on 2007-11-29
I'm shocked it worked at all. I've spent the last hour trying to get it to run on my system and after copying numerous DLL files and trying several different Wine configs, the app locks up at the registration prompt. I actually got into the application once, but when I tried to open files or do anything, it complained about one more missing DLL file. Adding it seems to have caused the lock up issue I'm having. Interestingly, I never got the same OLE error that you got. I am using Wine 0.9.49 currently, so that might be what you need to get around the OLE error, but if my experience is any indication, you might not like the results.

---

### Post by hca on 2007-11-29
To cogadh!
Your link to your "stuff you have learned about wine" turned out to be helpful. I ran wqinecfg and changed windows version to Win-98. Now the program can export data without missing the OLE-driver.
/Hans Christian

---

### Post by hca on 2007-11-29
> **cogadh said:**
> I'm shocked it worked at all. I've spent the last hour trying to get it to run on my system and after copying numerous DLL files and trying several different Wine configs, the app locks up at the registration prompt. I actually got into the application once, but when I tried to open files or do anything, it complained about one more missing DLL file. Adding it seems to have caused the lock up issue I'm having. Interestingly, I never got the same OLE error that you got. I am using Wine 0.9.49 currently, so that might be what you need to get around the OLE error, but if my experience is any indication, you might not like the results.

Sorry for your inconvenience. and sorry for my being enough precise in the first hand. The verbatim error message had the word excell in front of it. The Winfoil application was said to work in different versions of Windows. I went to a different pc an installed an XP home edition and ran the program there. On that machine I got the same error message. So it most likely is a program error in the application. 

But it is true that it now works in my Ubuntu/wine setup. I got  the message when I tried to import or export data. I found a way for finding a solution at last!

Thank you for your efforts!!
/Hans Christian

---

