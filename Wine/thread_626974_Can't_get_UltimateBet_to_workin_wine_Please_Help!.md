---
title: "Can't get UltimateBet to workin wine Please Help!"
date: 2007-11-29
forum: Wine
---

### Post by BluntMAn420 on 2007-11-29
Like I said I can't get UltimateBet to work in wine I have tried this guide [http://www.compatiblepoker.com/Online+Poker-Wine.cms.htm](http://www.compatiblepoker.com/Online+Poker-Wine.cms.htm) 

but it did not work 
when I run this commando "wine /tmp/ubsetup.exe" to install  I get

home@home-desktop:~$ wine /tmp/ubsetup.exe
fixme:shell:IShellLinkA_fnGetPath (0x1611a0): WIN32_FIND_DATA is not yet filled.
fixme:shell:DllCanUnloadNow stub
fixme:shell:IShellLinkA_fnGetPath (0x1611a0): WIN32_FIND_DATA is not yet filled.
fixme:shell:DllCanUnloadNow stub
fixme:shell:IShellLinkA_fnGetPath (0x15f9b8): WIN32_FIND_DATA is not yet filled.
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub

after it is installed  i click on it and nothing runs 


anybody have any suggestion this is the only program I really want on ubuntu
thanks in advanced

---

### Post by BluntMAn420 on 2007-11-29
and when i put in "wineboot" like it says in the guide I used it said

home@home-desktop:~$ wineboot
err:wineboot:ProcessWindowsFileProtection WFP: shdocvw.dll error 0x7
err:wineboot:ProcessWindowsFileProtection WFP: urlmon.dll error 0x7
err:wineboot:ProcessWindowsFileProtection WFP: shlwapi.dll error 0x7
err:wineboot:runCmd Failed to run command L"" (18)
err:wineboot:ProcessRunKeys Error running cmd #0 (18)

---

### Post by BluntMAn420 on 2007-11-29
oo and who do I get the smiley faces off my output

---

### Post by BluntMAn420 on 2007-11-29
NeverMind I found it

home@home-desktop:~$ wine /tmp/ubsetup.exe
fixme:shell:IShellLinkA_fnGetPath (0x1611a0): WIN32_FIND_DATA is not yet filled.
fixme:shell:DllCanUnloadNow stub
fixme:shell:IShellLinkA_fnGetPath (0x1611a0): WIN32_FIND_DATA is not yet filled.
fixme:shell:DllCanUnloadNow stub
fixme:shell:IShellLinkA_fnGetPath (0x15f9b8): WIN32_FIND_DATA is not yet filled.
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub


&

home@home-desktop:~$ wineboot
err:wineboot:ProcessWindowsFileProtection WFP: shdocvw.dll error 0x7
err:wineboot:ProcessWindowsFileProtection WFP: urlmon.dll error 0x7
err:wineboot:ProcessWindowsFileProtection WFP: shlwapi.dll error 0x7
err:wineboot:runCmd Failed to run command L"" (18)
err:wineboot:ProcessRunKeys Error running cmd #0 (18)

---

### Post by cogadh on 2007-11-30
Please tell me you didn't follow those instructions to the letter. WineTools is very obsolete and it is now generally useless as a Wine assistance application. It hasn't been updated in about two years and is not even recommended by the Wine devs anymore. The how-to also recommends some very out-of-date versions of Wine (contemporaries of WineTools). By default, the version of Wine available in the 'buntu repositories is about two years newer than that, so I'm assuming that you are OK on that issue.

However, if you did you use WineTools, the first thing I would recommend is deleting your .wine directory and creating a new one the official way, by either running winecfg or wineprefixcreate. After that, the steps in that how-to are pretty much OK:
[LIST=1]
[*]Download your client installer. It doesn't need to go into the /tmp directory as per the original how-to, you can just download it to your home directory or your desktop, wherever you like.
[*]Open a terminal and change directories to wherever you decided to download the client installer and run it like this:
```
wine ultimatebetinstall.exe
```
[*]Follow the install prompts, just as you would with a normal Windows installation. You can probably just accept the defaults.
[*]Once the install is complete, you may get those same "fixme:shell:DllCanUnloadNow stub" messages. They indicate that some process of the install is hung up and the wineserver is still running. You should just be able to do a CTRL-C to break out of it and then do your wineboot. If the wineboot doesn't work (frankly I'm not even sure it is necessary), then run this:
```
wineserver -k
```
That will force the wineserver to shut down.
[/LIST]
You can try using the desktop shortcut to run the game, but that will often not work. It is usually better to run the game in the terminal like this:
```
cd ~/.wine/drive_c/Program\ Files/<gamedirectory>
wine gameexecutable.exe
```
Obviously adjust the path and executable name to match the actual game as you installed it.

EDIT - Almost forgot, when you post output from the terminal, try using the forum CODE tags. It eliminates the smiley problem without turning them off and can preserve the text layout and formatting of the original content. Plus, it's just easier to read.

---

### Post by BluntMAn420 on 2007-12-02
Cool thx for the reply cogadh very useful info :)

---

### Post by kc8hr on 2008-02-05
> **BluntMAn420 said:**
> Cool thx for the reply cogadh very useful info :)
Hey, did you ever get UltimateBet running? I tried all the suggestions, but no joy.

Thanks,
Tim

---

