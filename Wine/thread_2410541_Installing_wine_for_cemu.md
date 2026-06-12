---
title: "Installing wine for cemu"
date: 2019-01-16
forum: Wine
---

### Post by simoncks1994 on 2019-01-16
Hi everyone,

I am trying to install wine for cemu for Breath of the Wild. I tried to install cemu.exe with wine but it crashed immediately. I have the whole installation log here.

```
# Refer to https://www.reddit.com/r/cemu/comments/6o0obp/complete_guide_to_cemu_on_linux/

# Wine setup
rm -rf ~/.wine
sudo apt install wine
sudo apt install wine-staging
export WINEARCH=win64
export WINEPREFIX="/home/simon/.wine"
winecfg         # set Windows version to Windows 10
                ## no Windows 10! select Windows 8


# Winetricks setup
cd ~/Softs
wget -r -c -N https://raw.githubusercontent.com/Winetricks/winetricks/master/src/winetricks
mv raw.githubusercontent.com/Winetricks .
rm raw.githubusercontent.com
cd Winetricks/winetricks/master/src
chmod +x winetricks
bash winetricks         # default wineprefix; Installation of Windows DLL or components; vcrun2017
                        ## Prompt error: Working around wine bug 37781
                        ## This may fail in non-XP mode, see https://bugs.winehq.org/show_bug.cgi?id=37781
                        ## Running /usr/bin/wineserver -w. This will hang until all wine processes in prefix=/home/simon/.wine terminate (wait for 15 mins)
                        ## Note: command wine vc_redist.x86.exe returned status 180. Aborting.

```

When I install cemu_1.15.1, I encounter the following error:[INDENT]Program Error Details
(Loading detailed information, please wait...) (after 15 minuets of wait)
[/INDENT]

I am not sure how to proceed. But please feel free to ask for more info. Any suggestion is appreciated.

---

