---
title: "Pacific Poker and WINE"
date: 2006-08-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Yuric on 2006-08-10
I'm new to linux and can't quite figure out how to fix this myself. i'm getting the error message 

yuric@Y-Top:~$ wine pacificpoker.exe
err:module:import_dll Library Shared_.dll (which is needed by L"C:\\windows\\system32\\pacificpoker.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\pacificpoker.exe" failed, status c0000135

and was wondering if anyone knew how to fix it. Thanks.

---

### Post by Kilz on 2006-08-10
> **Yuric said:**
> I'm new to linux and can't quite figure out how to fix this myself. i'm getting the error message 

yuric@Y-Top:~$ wine pacificpoker.exe
err:module:import_dll Library Shared_.dll (which is needed by L"C:\\windows\\system32\\pacificpoker.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\pacificpoker.exe" failed, status c0000135

and was wondering if anyone knew how to fix it. Thanks.

Ok it looks like you have wine installed. If not click on the wine howto link in my signature. Make sure to install the sidenet setup script in the howto.
Next Install the Windows version of Firefox. [You can download it with thsi link.]("http://www.mozilla.com/products/download.html?product=firefox-1.5.0.6&os=win&lang=en-US") Then reinstall the pacificpoker.exe

---

### Post by Yuric on 2006-08-11
I did what you recomended. Mozilla Installed just fine but now i get

yuric@Y-Top:~$ wine pacificpoker.exe
wine: could not load L"c:\\windows\\system32\\pacificpoker.exe": Module not found

I also tried installing World of Warcraft and get the same problem.

yuric@Y-Top:~$ wine WoW.exe
wine: could not load L"c:\\windows\\system32\\WoW.exe": Module not found


I'm sorry to ask for more help but I searched the WoW installer guides and the net and still could not figure out what to do.

---

### Post by Kilz on 2006-08-11
> **Yuric said:**
> I did what you recomended. Mozilla Installed just fine but now i get

yuric@Y-Top:~$ wine pacificpoker.exe
wine: could not load L"c:\\windows\\system32\\pacificpoker.exe": Module not found

I also tried installing World of Warcraft and get the same problem.

yuric@Y-Top:~$ wine WoW.exe
wine: could not load L"c:\\windows\\system32\\WoW.exe": Module not found


I'm sorry to ask for more help but I searched the WoW installer guides and the net and still could not figure out what to do.

I think the problem is that you are not typing the paths into the terminal, wine has no idea where the .exe files are. The paths need to be enterd in a specific way. But to make sure everything works try this.
Did you install wine with my howto? If you did and you installed the sidenet script there should be a c folder in your home folder. Open it, then program files, then pacific poker, right click on the pacific poker.exe and chose open with other application. The application list will open, click "use custom command" at the bottom, a space to type will open, type in wine then click open. This will assoicate wine with exe files and start pacific poker.
Once thats done clicking on exe files will start them with wine. You can try this with wow. But running WoW with wine isnt the easiest thing to do, a specific wine version with patches in it needs to be used. Did you install the wine version on my howto or did you get it from the Wow setup page in the wiki?

---

### Post by Yuric on 2006-08-11
> **Kilz said:**
> I think the problem is that you are not typing the paths into the terminal, wine has no idea where the .exe files are. The paths need to be enterd in a specific way. But to make sure everything works try this.
Did you install wine with my howto? If you did and you installed the sidenet script there should be a c folder in your home folder. Open it, then program files, then pacific poker, right click on the pacific poker.exe and chose open with other application. The application list will open, click "use custom command" at the bottom, a space to type will open, type in wine then click open. This will assoicate wine with exe files and start pacific poker.
Once thats done clicking on exe files will start them with wine. You can try this with wow. But running WoW with wine isnt the easiest thing to do, a specific wine version with patches in it needs to be used. Did you install the wine version on my howto or did you get it from the Wow setup page in the wiki?

I did install by using your HOWTO with sidenet. I have already tried the "use custom command" option for trying it to start with WINE. It now automatically tries to open it up with WINE but when i double click, nothing occurs. Any other suggestions?

---

### Post by Kilz on 2006-08-11
> **Yuric said:**
> I did install by using your HOWTO with sidenet. I have already tried the "use custom command" option for trying it to start with WINE. It now automatically tries to open it up with WINE but when i double click, nothing occurs. Any other suggestions?

Ok well at least I now know the paths to use. try this command in the terminal.changing UserName for your username

```
wine "/home/UserName/c/windows/notepad.exe"
```

Does Notepad start? If so try this in the terminal changing UserName again to your username

```
wine "/home/UserName/c/Program Files/PacificPoker/pacificpoker.exe"
```

---

### Post by Yuric on 2006-08-11
Notepad didn't work.

---

### Post by Kilz on 2006-08-11
Did you recieve an error? Try ```
winecfg
``` and copy/paste any errors you get please.

---

### Post by Yuric on 2006-08-12
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
err:module:load_builtin_dll failed to load .so lib for builtin L"winealsa.drv": libasound.so.2: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winearts.drv": libartsc.so.0: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: cannot open shared object file: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack


is the only error i get by running winecfg

---

### Post by Kilz on 2006-08-12
> **Yuric said:**
> fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
err:module:load_builtin_dll failed to load .so lib for builtin L"winealsa.drv": libasound.so.2: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winearts.drv": libartsc.so.0: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: cannot open shared object file: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack


is the only error i get by running winecfg

Please install this package to get rid of some of those errors.
```
sudo apt-get install lib32asound2
```

Im not sure if these others would help, but they cant hurt if you want to make sure they are installed.
ia32-libs lib32ncurses5 ia32-libs-sdl ia32-libs-gtk

---

