---
title: "[SOLVED] Such a newb it hurts."
date: 2007-11-27
forum: Wine
---

### Post by hvac3901 on 2007-11-27
Nice to meet you all, after many years of debating it with myself, I made the switch to linux, i especially like what I found in Ubuntu. it was a 3 day learning curve just to settled in behind the monitor again. not as abd as i thought it would be.

So of all the stuff I found, and liked, I am having some trouble with WINE. I THINK :) 

I tried to follow the dirrections available everywhere so here you go...before i rant.

VISIO was installed under applications-other and when I try to load it up, it results in a error. I was expecting it to be somewhere in programs under the wine directory. Is that my problem, why did my install go haywire? any help is greatly appreciated.

or if its simply a matter of moving some files in terminal any insight would be helpful

---

### Post by hikaricore on 2007-11-27
What's the error when you try running it from a terminal session?

---

### Post by hvac3901 on 2007-11-27
here is where the newb in me is gonna kick in. gimme a few minutes to try that. 

and i havn't even started to get use to the directory structure so i don't know where to find the "applications" folder.

---

### Post by hvac3901 on 2007-11-27
OK i am not having any luck finding the right syntax to perform that task. I know this belongs somewhere else, maybe. but how is that done? Sorry to have to ask

---

### Post by hvac3901 on 2007-11-27
still working on finding that error number.

I have noticed in wine, that the files were installed just like my original WindowsOS did, except the executable. that is missing somewhere outside of WINE.

---

### Post by hvac3901 on 2007-11-27
well i told the terminal to bash the file once i found it and moved it somewhere i could read the properties ... i hope this is what you wanted. here goes

ron@desktop:~/Desktop$ bash Microsoft%20Office%20Visio%202003.desktop
Microsoft%20Office%20Visio%202003.desktop: line 1: [Desktop: command not found
Microsoft%20Office%20Visio%202003.desktop: line 4: Office: command not found
err:ole:CoGetClassObject class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} not registered
err:ole:CoGetClassObject no class object {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} could be created for context 0x1
fixme:imm:ImmReleaseContext (0x10028, 0x121c08): stub
Warning: unknown mime-type for "and" -- using "application/*"
Warning: unknown mime-type for "share" -- using "application/*"
Warning: unknown mime-type for "diagrams" -- using "application/*"
Warning: unknown mime-type for "by" -- using "application/*"
Warning: unknown mime-type for "using" -- using "application/*"
Warning: unknown mime-type for "Microsoft" -- using "application/*"
Warning: unknown mime-type for "Office" -- using "application/*"
Warning: unknown mime-type for "Visio." -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"
Error: no "edit" mailcap rules found for type "application/*"
Error: no "edit" mailcap rules found for type "application/*"
Error: no "edit" mailcap rules found for type "application/*"
Error: no "edit" mailcap rules found for type "application/*"
Error: no "edit" mailcap rules found for type "application/*"
Error: no "edit" mailcap rules found for type "application/*"
Error: no "edit" mailcap rules found for type "application/*"
ron@desktop:~/Desktop$

---

### Post by bonzodog on 2007-11-28
Normally, to run a program in wine, you first cd into the directory where the program is installed, make sure you know the actual name of the executable, then you run the executable with 'wine' before it.

I don't know the name off hand of the MS Visio executable, but I would assume that it should go something like this (the directories might not be entirely right):
```

ron@desktop:~/Desktop$ cd ~
ron@desktop:~$ cd .wine/C_Drive/Program\ Files/MSVisio/
ron@desktop:~/.wine/C_Drive/Program\ Files/MSVisio$ wine msvisio.exe

```

---

### Post by hvac3901 on 2007-11-28
:oops: now why does that make perfect sense, thanks bonzodog.

I will once again try to attain the error message. in a few hours

---

### Post by cogadh on 2007-11-28
What version of Visio are you using? According to Wine's AppDB, most of them don't work very well or at all in Wine:
[http://appdb.winehq.org/appview.php?appId=119](http://appdb.winehq.org/appview.php?appId=119)

You might want to consider using a Linux native alternative to Visio, like [Dia](http://www.gnome.org/projects/dia/). I haven't used it myself, but it appears to be very similar to Visio, though maybe not as robust in its functionality.

---

### Post by hvac3901 on 2007-11-28
I have reviewed all the alternatives i could find, I just don't see as you say the robustness of VISIO in any of them. thanks for the suggestion though.

I finally did something that worked. i copied all the program files to the C;/ folder in wine, ran an install, and when i try to open the EXE file i get this error IOPL not enabled

Oh sorry Visio 2003

---

### Post by cogadh on 2007-11-28
That's a known bug with Visio 2003 in Wine versions higher than 0.9.36:
[http://bugs.winehq.org/show_bug.cgi?id=9422](http://bugs.winehq.org/show_bug.cgi?id=9422)

It has something to do with Wine's implementation of gdiplus.dll. However, replacing Wine's gdiplus.dll with a Windows native one will get you past the IOPL error only to run into a different one that cause the app to crash completely.

---

### Post by hvac3901 on 2007-11-28
I ran into some info on that somewhere else however that gent sais he rolled back to 0.9.37 and got it  work.

Can i run an earlier version of WINE in ubuntu 7.10? I am hopeing to go completely linux with my laptop as well since IBM has great support (so it seems on the surface for thinkpads) but without visio i will feel not so productive. I use it repaetedly for nearly every document i produce.

---

### Post by hvac3901 on 2007-11-28
So until someone much much smarter than me comes along anf finds a way to run office in WINe without hangups from .dll stuff I am screwed? for the most part?

---

### Post by hvac3901 on 2007-11-28
ok after some searching, and the help of you guys, I went into synaptic package manager, and removed wine, then i went to sourceforge.net and got an earlier wine 0.9.3 for my machine and installed that, I got visio open and running now, thanks for all your help

---

### Post by hvac3901 on 2007-11-28
but the function is not there, the search goes on.

I keep getting serious errors and the program dumps me out.

---

### Post by hvac3901 on 2007-11-28
Well its no longer a WINE issue, it appears that now that it opens and partially functions, it is attempting to communicate with MS via my internet connection and report how i am using the software. along with the normal tidbits, licence hardware etc.

I will post my request for information elsewhere once again gents Thank you very much for your information.

---

### Post by Vadi on 2007-11-29
Visio's search function is iffy at best. We were using it for one project because the guy was all hip about his new Vista - while Visio did offer a large database of pre-made items, it was a pain to work with. In the end, yeah, we just got Dia.

---

### Post by hvac3901 on 2007-11-29
> **cogadh said:**
> That's a known bug with Visio 2003 in Wine versions higher than 0.9.36:
[http://bugs.winehq.org/show_bug.cgi?id=9422](http://bugs.winehq.org/show_bug.cgi?id=9422)

It has something to do with Wine's implementation of gdiplus.dll. However, replacing Wine's gdiplus.dll with a Windows native one will get you past the IOPL error only to run into a different one that cause the app to crash completely.

I have found exactly what you were talking about (i think). my gut feeling having run this program in windows XP, with an antikeylogger actively monitoring (which blocked and reported a low system level key logging in use by windows rendering the same kind of crash) at apparently the very same instance of the "different error" that crashes the system while running it in wine.

Can this be removed from the MS office programs at the program level, or does my new opensource enlightenment have me asking too much from a MS program?

---

### Post by cogadh on 2007-11-29
You're asking too much. That's why OSS rules over closed source.

---

### Post by hvac3901 on 2007-11-29
Thanks again to all of you.

---

