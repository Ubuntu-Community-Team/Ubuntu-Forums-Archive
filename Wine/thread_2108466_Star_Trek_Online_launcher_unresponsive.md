---
title: "Star Trek Online launcher unresponsive"
date: 2013-01-24
forum: Wine
---

### Post by linuxman72 on 2013-01-24
I have been trying to get STO to run under wine. I installed wine 1.5.22, and then typed winetricks ie8. I got an error saying that it was not compatable with my 64-bit system, but it seemed to install correctly. I then typed winetricks ie7, as some forums said having 7 helped. same error, seemed to work as before. I ran ie and it worked, so that seemed good. I then used winetricks to install directx9 and a few other things forums suggested. All seemed good. downloaded installer. wouldn't run. ran installer with
```
GC_DONT_GC=1 wine ST.25.20121026a.8_EN.exe
```and it ran fine, but got "too many file open" errors twice and had to restart, fortunately the download continued where it left off each time. It then installed error free. now the problem. I ran the game. the launcher appeared. It looked perfect. I typed in my user/password. I clicked login. nothing happened. in fact, nothing is clickable on the whole launcher except the text fields! The enter key fails as well. Wireshark reports no net activity sent to/from launcher when I click login. launching with terminal allows me to see "fixme " printouts(many) whenever my mouse moves on or off an element, and the ad glows when moused over, so the mouse is detected, but clicking isn't. clicking anything clickable other than the login button or text fields prints this to the terminal:
```
err:ole:create_server class {0002df01-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {0002df01-0000-0000-c000-000000000046} could be created for context 0x4
```is there any way to fix this? I have found fixes for many other issues with wine/STO, but it seems no one else has had this issue yet. even a way to manually patch the game so I could run the now missing client would be appreciated.

System: Ubuntu 12.10 64-bit, wine 1.5.22, Hardware: more than sufficient

---

### Post by aarons6 on 2013-02-19
i play sto everyday on wine.. 

the only thing i have installed in my STO wine prefix is IE8

the rest is built in wine.. no directx no dotnet, nothing.. just ie8

you have to use winetricks to specify video memory.. in my case its 1024 or the game will crash with d3d out of memory error.. even tho you have plenty.

youre biggest problem is 64bit linux.. 
wine hates 64bit linux.. to get it to work you have to compile it with 32bit libraries and use the 32bit switch.. its kinda a pita.. 

with pae linux doesnt need 64bits to run with more then 4gb ram and you will have more success with games..

also make sure your game is installed in an EXT partition and not a FUSE one..

---

### Post by r00st3r3 on 2013-02-19
If the above does not work I use Crossover from Codeweavers. They have a 15 day trial. STO works great with it and they have automated scripts to install other games automagically.

Hope this helps.:D

---

### Post by aarons6 on 2013-02-20
sto launcher wont work without ie8 and ie8 wont work on 64bit system

this is all

---

