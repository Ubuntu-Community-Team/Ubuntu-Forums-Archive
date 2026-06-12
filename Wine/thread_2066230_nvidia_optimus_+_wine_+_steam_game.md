---
title: "nvidia optimus + wine + steam game"
date: 2012-10-04
forum: Wine
---

### Post by morswin on 2012-10-04
Hi all,

I had some troubles with installing Black Mesa with wine.  Here what i've done to make game run properly. All I'll write you can  find in web, but not in the one place. So firstly I'd like to thank all  good people sharing their knowledge publicly.   I'm sorry if all of  those is easy, and I'm only retarded in here. 

Environment: Linux + Wine + Double graphics card (intel + nvidia) + Steam + Black Mesa.

  I think it's gone work for Half Life, CS and every steam game, not just BM. 

The procedure:

1) Follow instruction from [http://linuxgamecast.com/2012/09/l-g-c-how-to-install-black-mesa-on-linux-with-winetricks/](http://linuxgamecast.com/2012/09/l-g-c-how-to-install-black-mesa-on-linux-with-winetricks/). 

Now  if run the game you will see some black-pink textures, silly eyes,  white line across the screen and you will have low fps rate. All that  because you are using weak intel card. So:
  
2) Install Bumblebee:

```
  sudo apt-add-repository ppa:bumblebee/stable 
sudo apt-get update
sudo apt-get install bumblebee

```and restart PC.

In order to run bumblebee with BM you need to do following (there are also more complicated alternatives):  

3)  Make script linking you with steam (link to steam you can find clicking  'properties' in 'Steam' icon from desktop ). I'll use vi and call my  script "steam":

```

vi steam

```now 'a' to insert mode and write:
[PHP]
#!/bin/bash

WINEDEBUG=-all wine .local/share/wineprefixes/steam/drive_c/Program\ Files\ \(x86\)/Steam/Steam.exe -no-dwrite
[/PHP]'ESC'  + ':wq'. If you installed steam using winetricks,  have 64bit linux and  put file in your home directory, you should have identical 'steam' like  me (as far as i know). 

4)  Thats all. You can delete 'Steam' icon from desktop - it will be useless. Now everytime you wanna play BM: 
 a) open terminal;
 b) ```
optirun bash
``` c) ```
sh steam
``` d) run your game from steam.
 e) when you close steam put 'exit' in terminal in order to stop optirun.

Sorry for my poor English. 
Best regards,
morswin

---

