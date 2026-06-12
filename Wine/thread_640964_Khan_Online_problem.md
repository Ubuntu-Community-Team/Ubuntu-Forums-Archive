---
title: "Khan Online problem"
date: 2007-12-14
forum: Wine
---

### Post by ares623 on 2007-12-14
I installed [Khan Online](http://khan.levelupgames.ph/index.html) today and it installed fine. But when I try to run it, I get an error:
------------------------------
|Process Khan_exe   |
|Version : ver11        |
|DNS : USER_SERVER |
|          OK                |
------------------------------
need help..

---

### Post by cogadh on 2007-12-14
Please see this post for the kind of info we need from you for you to help us help you:
[http://ubuntuforums.org/showthread.php?t=624424](http://ubuntuforums.org/showthread.php?t=624424)

---

### Post by ares623 on 2007-12-15
thanks. 
   1. Wine version - 0.9.50
   2. Terminal output - how do i run an app from the terminal? 
   3. Wine configuration - Defualt configuration afaik. Didn't change anything. 
   4. Hardware specs/drivers - nvidia drivers installed fine afaik.. 
   5. Other Wine applications - I installed Portal, worked fine.

---

### Post by cogadh on 2007-12-15
Open a new terminal, you can find in the Applications > Accesories menu. In the terminal, change directories to where the game is installed:
```
cd .wine/drive_c/Program\ Files/<game directory>/
```
Then run the game with Wine:
```
wine <game executable>.exe
```

---

### Post by ares623 on 2007-12-16
thanks, but i'm still getting the same error. Looks like this game isn't supported by wine after all.. too bad.

---

### Post by cogadh on 2007-12-16
I assume that was a game error, the errors in the terminal from Wine may tell us why the game produced that error and point us in the right direction of a fix (hence why we ask for the terminal output).

---

### Post by ares623 on 2007-12-17
oh sorry. there are two .exe files, one named Khan.exe and the other named KhanClient.exe
running KhanClient.exe doesn't output anything in the terminal.. only the dialog box which looks like the one in the original post.

running Khan.exe outputs this:
```

administrator@Linux-Home-Desktop:~/.wine/drive_c/Program Files/Khan Online$ wine Khan.exe
administrator@Linux-Home-Desktop:~/.wine/drive_c/Program Files/Khan Online$ err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\Khan Online\\UpGrade.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Khan Online\\UpGrade.exe" failed, status c0000135

```

---

### Post by cogadh on 2007-12-18
Here's an important error message:
```

 err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\Khan Online\\UpGrade.exe") not found

```
Basically, that means you need to copy MFC42.DLL from a Windows machine and place it in .wine/drive_c/windows/system32. If you don't have a Windows machine to copy from, just Google it, you can download it from any number of places.

After you copy the DLL, try running the game again. The above error will definitely go away, but other errors may crop up (it happens). Post back with any other errors you get and we'll work from there.

---

### Post by ares623 on 2007-12-19
yeah another error just popped up..
```

administrator@Linux-Home-Desktop:~/.wine/drive_c/Program Files/Khan Online$ wine Khan.exe
administrator@Linux-Home-Desktop:~/.wine/drive_c/Program Files/Khan Online$ fixme:shdocvw:PersistMemory_Load (0x14d4b8)->(0x419224 9c)


```
but this time i don't get the prompt after running that.. i have to press ctrl+c to get the prompt again.

---

