---
title: "Is there an &quot;idiot's guide&quot; to wine (emphasis on idiot)?"
date: 2008-11-16
forum: Wine
---

### Post by fox.esq on 2008-11-16
I've been using Ubuntu now for about 9 months, mostly for web surfing and word processing; been figuring things out bit by bit, although the terminal stuff is way over my head (I can do things with it if detailed, specific instructions are included).  However, wine completely befuddles me to this day.  I have been unable to figure out how to load anything on it, such as PC games - which is what I primarily want to do with it - I've tried to configure it according to some instructions, but most skip over details or use idioms that don't clearly state what I'm supposed to do.  I've tried installing a number of different games, but none will initialize installation or setup (I've clicked an .exe file and selected 'open with wine', no dice).

My main objective right now is to load the game 'Spore'.  I have checked the wineHQ database and found it is supported and am also aware the game has some kind of piracy protection that needs to be overridden, but I have no idea how to do that (again, because the instructions lack specific details and are written for users that can run wine in their sleep).

Can someone write up something that gives detailed, specific yet not too complicated instructions on how to install a game off a DVD-ROM into wine; not Spore, per se, but any game. ("stuff I've learned about wine" is nice, but it skips around too much and is not clear in details or specific enough).

I'm currently using Wine 1.1.8 (yes, I did manage to figure out how to update the damn thing) on Ubuntu 8.04.

Thanks in advance!

---

### Post by rehaby on 2008-11-17
ive seen one or two guides on ubuntu forms webs site. Cant remeber the link or what there called thought.To over ride the piracy protection you will have to download a cd crack and replace the exe file that you use to run the game with the cracked one. Hope that helps.

---

### Post by lakersforce on 2008-11-17
You could start out with:

```
man intro
```

---

### Post by Jacob Collstrup on 2008-11-17
I installed a game called AssaultTech 1: BattleTech (A Battletech community project) on my ubuntu system. What I did was to open the installer through wine and then let it install through that. But I don't really know if you already tried that. Thats what I've done with all my windows programs (two). Ran the installer through wine.

I'm thinking that maybe its the copyright protection thats hitting you. Have you tried installing other programs through wine that are not copyright protected?

Jacob

---

### Post by fox.esq on 2008-11-17
> **Jacob Collstrup said:**
> I installed a game called AssaultTech 1: BattleTech (A Battletech community project) on my ubuntu system. What I did was to open the installer through wine and then let it install through that. But I don't really know if you already tried that. Thats what I've done with all my windows programs (two). Ran the installer through wine.

I'm thinking that maybe its the copyright protection thats hitting you. Have you tried installing other programs through wine that are not copyright protected?

Jacob

You mean by opening an .exe, such as a 'setup.exe" with wine (i.e. right clicking the file then selecting 'open with wine')?... Yeah I've done that with a number of programs, hasn't worked once.

---

### Post by fox.esq on 2008-11-17
> **lakersforce said:**
> You could start out with:

```
man intro
```

How do I go about doing that?... using terminal I'm guessing, right?  What are the exact lines I need to type in terminal to get that to apply to wine?

---

### Post by fox.esq on 2008-11-17
> **rehaby said:**
> ive seen one or two guides on ubuntu forms webs site. Cant remeber the link or what there called thought.To over ride the piracy protection you will have to download a cd crack and replace the exe file that you use to run the game with the cracked one. Hope that helps.

Yeah, I understand what I have to do, I just don't understand how to do it.  I can do what you're describing in Windows, but I'm still figuring out how to download stuff in Linux and getting it to run/install; also, the .exe file is located on the DVD-ROM and I don't know how to transfer it over to the hard drive in Linux.

---

### Post by cogadh on 2008-11-17
Click on the "Stuff I've learned aboout Wine" link in my sig. Some of the info is out of date (i'll get around to updating it eventually), but most of it will still help you get started.

---

### Post by Dizzle7677 on 2008-11-17
> **fox.esq said:**
> Yeah, I understand what I have to do, I just don't understand how to do it.  I can do what you're describing in Windows, but I'm still figuring out how to download stuff in Linux and getting it to run/install; also, the .exe file is located on the DVD-ROM and I don't know how to transfer it over to the hard drive in Linux.

Yoo don't need to transfer anything over. I usually just right click the setup.exe [or whatever the install file is] and select - Open with 'Wine Windows Program Loader' or look in Open with other application and 'Wine Windows Program Loader' might be in there. From the terminal change to the cdrom drive and try 'wine ./setup.exe' or 'wine setup.exe'. 
If you don't get a install dialog or any output , then something else may be funky.

---

### Post by lakersforce on 2008-11-18
> **fox.esq said:**
> How do I go about doing that?... using terminal I'm guessing, right?  What are the exact lines I need to type in terminal to get that to apply to wine?

I'm an idiot...didn't see the "wine" word in there :(

---

### Post by YokoZar on 2008-11-18
> **fox.esq said:**
> I've tried installing a number of different games, but none will initialize installation or setup (I've clicked an .exe file and selected 'open with wine', no dice).
If programs aren't launching *at all* that could be a different problem.  Can you run winecfg (Applications->Wine->Configure Wine) or the built in notepad (Applications->Wine->Programs->Notepad)?

If not, please indulge me for a moment, open a terminal window, type "wine notepad" and then tell me what it says.  Thanks

---

### Post by fox.esq on 2008-11-25
> **YokoZar said:**
> If programs aren't launching *at all* that could be a different problem.  Can you run winecfg (Applications->Wine->Configure Wine) or the built in notepad (Applications->Wine->Programs->Notepad)?

If not, please indulge me for a moment, open a terminal window, type "wine notepad" and then tell me what it says.  Thanks

Sorry it's taken me a while to get to this.  Yeah, I can get notepad to run. I can't get anything else to though... not a single .exe file I've tried to open with wine has been successful.

---

### Post by fox.esq on 2008-11-25
> **cogadh said:**
> Click on the "Stuff I've learned aboout Wine" link in my sig. Some of the info is out of date (i'll get around to updating it eventually), but most of it will still help you get started.

Sorry it's taken me awhile to get back to this.  Yeah, I read through your guide... it was somewhat helpful but I got lost a lot.  No offense, but it jumped in some places and you used terms that a newbie like me wouldn't be familiar with - hence the request for an idiot's guide :) .

---

### Post by fox.esq on 2008-11-25
> **Dizzle7677 said:**
> Yoo don't need to transfer anything over. I usually just right click the setup.exe [or whatever the install file is] and select - Open with 'Wine Windows Program Loader' or look in Open with other application and 'Wine Windows Program Loader' might be in there. From the terminal change to the cdrom drive and try 'wine ./setup.exe' or 'wine setup.exe'. 
If you don't get a install dialog or any output , then something else may be funky.

Sorry I've taken awhile to get back to you.  I've tried to do what you're describing, i.e. right-clicking a .exe file and selecting 'open with Wine Windows Program Loader' but when I do that, nothing happens :( .

How exactly do I change to the cdrom in terminal and try what you're suggesting... such as specific steps on what to type, etc.?

---

### Post by fox.esq on 2008-11-25
> **lakersforce said:**
> I'm an idiot...didn't see the "wine" word in there :(

I did not mean to offend you... I was just wanting specific instructions on how to go about doing what you suggested... please keep in mind, I need lots of detail, that's all I was asking for.

---

### Post by cogadh on 2008-11-25
Based on your responses here, I would suggest you spend some time learning how to actually use Linux before you try getting into Wine. Most of the issues you seem to be having are not actually problems with Wine, but problems using Linux, like understanding how to use the terminal. There is plenty of good beginner information at [http://www.justlinux.com/](http://www.justlinux.com/), I recommend starting with the [Basic Command Reference](http://www.justlinux.com/nhf/Command_Reference).

---

### Post by tylerisfat on 2009-02-04
> **YokoZar said:**
> If programs aren't launching *at all* that could be a different problem.  Can you run winecfg (Applications->Wine->Configure Wine) or the built in notepad (Applications->Wine->Programs->Notepad)?

If not, please indulge me for a moment, open a terminal window, type "wine notepad" and then tell me what it says.  Thanks

Same problem for me. Notepad doesn't open, this is what i get.

```
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\services.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\services.exe" failed, status c0000135
err:wineboot:start_services_process Unexpected termination of services.exe - exit code -1073741515
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\ole32.dll") not found
err:module:DelayLoadFailureHook failed to delay load ole32.dll.CoTaskMemAlloc
wine: Call from 0x7b8458a0 to unimplemented function ole32.dll.CoTaskMemAlloc, aborting
err:module:attach_process_dlls "shell32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\notepad.exe" failed, status 80000100
```

Tha

---

### Post by Ferrat on 2009-02-04
How did you install wine in the first place? :)

---

### Post by oedipuss on 2009-02-05
> **tylerisfat said:**
> Same problem for me. Notepad doesn't open, this is what i get.

```
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\services.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\services.exe" failed, status c0000135
err:wineboot:start_services_process Unexpected termination of services.exe - exit code -1073741515
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\ole32.dll") not found
err:module:DelayLoadFailureHook failed to delay load ole32.dll.CoTaskMemAlloc
wine: Call from 0x7b8458a0 to unimplemented function ole32.dll.CoTaskMemAlloc, aborting
err:module:attach_process_dlls "shell32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\notepad.exe" failed, status 80000100
```

Tha

The first message seems to indicate that you're missing a dll file. Specifically 'rpcrt4.dll' .. I don't know why this would happen with a builtin application like wine notepad, but you could try reinstalling wine, or searching for that file. Downloading a native windows dll and using it is also an option, and if this was about any other application it would be my first guess, but since it's notepad, I wouldn't recommend it. It's supposed to run as-is, without any windows dlls.



@fox.esq 

It's been suggested already, but you should really familiarize yourself with the terminal before using wine. Nothing fancy, no need to be intimidated by it, just basic folder navigation ('cd' and 'ls -l' pretty much covers it). Wine is much easier to use from a terminal (for me at least), since you can kill misbehaving apps easily, and generally diagnose what's going on. Most messages will be incomprehensible for non-developers, but there's the occasional missing dll message that's very helpful, and you can actually tell if the application has crashed and exited or takes a long time trying to run.

cd folder : go to that folder
ls : simple list of files
ls -l  : comprehensive list of files
ls -a  : show hidden files too 

ls --help : for all the options

CONTROL+C while something is running : terminate it
TAB : autocomplete a command or path ( cd /ho[TAB] -> cd /home/ ) or display paths or commands that match what you've typed, if there's more than one match ( cd Ab[TAB] will show whatever starts with 'Ab' on the current folder)
  

The cds and dvds are mounted in the /media folder, usually as /media/cdrom or as /media/LABEL (the label of the cd/dvd) . Try navigating there with nautilus to see what each folder contains. 

Alternatively, you could try [_Crossover Games or Crossover Office_]("http://www.codeweavers.com"), which is basically wine + a neat GUI for installing and running apps. Much easier than wine, no terminal needed at all, but it's not free, and it uses a slightly older but more stable version of wine.

---

