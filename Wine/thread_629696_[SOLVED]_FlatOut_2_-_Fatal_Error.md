---
title: "[SOLVED] FlatOut 2 - Fatal Error"
date: 2007-12-02
forum: Wine
---

### Post by b0rka7a on 2007-12-02
Hello ! I'm trying to play FlatOut 2 with Wine 0.9.50, but when I start flatout2.exe it opent a window which says:

Fatal Error: Failed to load binary database 'data/Database/FlatOut2.db' !

When i try start flatout2.exe from the terminal it starts, but ONLY if I'm in the FlatOut 2 folder... :confused:

From other folder:
```

boris@boris-ubuntu710:~$ wine /media/sda1/Downloads/dcpp/FlatOut\ 2/flatout2.exe 
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
(Here it says "Fatal Error: Failed to load binary database 'data/Database/FlatOut2.db' !" and I click OK)
boris@boris-ubuntu710:~$ 

```

From the game folder:
```

boris@boris-ubuntu710:/media/sda1/Downloads/dcpp/FlatOut 2$ wine flatout2.exe 
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x173f7a0,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13fa98) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13fa98) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13fa98) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13fa98) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13fa98) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13fa98) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13fa98) : stub
...... (The game starts!)

```

Can someone PLEASE tell me what's up with that ?! I don't want to go to the game directory from a terminal and start it from there to play this game! That's the only game which do that. Am I doing something wrong or just Wine is @#$% with me...
Thanks in advance!

---

### Post by cogadh on 2007-12-02
Wine is not @#$%ing with you, that's the way you are supposed to use it. Windows applications like to run in the directory where they are installed, that's not just a Wine thing, its a Windows thing. 

If you don't want to do that every time you use the game, then create a simple script that does it for you:
```
#!/bin/sh
cd ~/.wine/drive_c/Program\ Files/<game directory>/
wine <game executable>.exe
```
Name the script something like "flatout.sh", make it executable, then run it in the terminal instead of typing the long command.

---

### Post by b0rka7a on 2007-12-03
Thank you for the reply. I already created a script to run it, but I just wanted to know why :roll:

---

