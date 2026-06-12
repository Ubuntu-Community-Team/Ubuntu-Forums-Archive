---
title: "Can't run Uplay in wine, but in Lutris all ok. Please help!"
date: 2018-01-23
forum: Wine
---

### Post by sebastian1978 on 2018-01-23
Firstly I installed Uplay in Lutris. It works ok. Here is script from [https://lutris.net/games/uplay/](https://lutris.net/games/uplay/)
```
exe: drive_c/Program Files (x86)/Ubisoft/Ubisoft Game Launcher/Uplay.exe
files:
- uplay: https://ubistatic3-a.akamaihd.net/orbit/launcher_installer/UplayInstaller.exe
game:
  arch: win64
  prefix: $GAMEDIR
installer:
- task:
    arch: win64
    name: create_prefix
    prefix: $GAMEDIR
- task:
    app: corefonts
    name: winetricks
    prefix: $GAMEDIR
- task:
    executable: uplay
    name: wineexec
    prefix: $GAMEDIR
wine:
  version: staging-2.21-x86_64
```

I have Wine 2.21 staging. Also I installed in prefix corefonts and [https://ubistatic3-a.akamaihd.net/orbit/launcher_installer/UplayInstaller.exe](https://ubistatic3-a.akamaihd.net/orbit/launcher_installer/UplayInstaller.exe)
All from script but Uplay get error "Uplay has detected unrecoverable error...". Please help! I have no ideas:confused:

---

