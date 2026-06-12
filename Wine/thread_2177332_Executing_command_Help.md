---
title: "Executing command Help"
date: 2013-09-28
forum: Wine
---

### Post by JuanLuna on 2013-09-28
Hi guys its me again :) btw thanks for all the help from my first thread, this community is awesome..

Since i'm new in ubuntu (Linux OS) & I dont know what to do, I surf google for some topic/task to familiarize Linux Environment and found some Interesting.
(Topic [from wargaming official forum])

* Installing World of Tanks SEA on linux *
.
- I did manage to follow the (needed apps, patches, etc.) instruction. But when i get into  the executing command to modify the file, i did stall (No clue, No Idea & Double Faced Palm)

Can anyone elaborate this instruction into more Newbie Linux User Friendly (Font color: red-Blue-Orange) 

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[COLOR=#000000]
**Warning!!!**[/COLOR]
This method of making World of Tanks game client compatible with Linux  is totally player made and has no connection to Wargaming Company. We  just recommend this modification as a quite popular and successful  method. World of Tanks development team is not responsible for these  files and our Customer Service do not supports them.

**It’s highly recommended to check files on viruses before installation!**

This method of launching the game does not guaranty successful and  stable work of the game with some configurations of soft- and hardware.

World of Tanks Development team thanks player ***wilderwind*** for help during production of this guide.
________________________________________

**Launching World of Tanks under Linux OS: constructing wine from scratch.**

It should be mentioned that below described method is related to  so-called Debian-based distributives on GNU/Linux OS, for example,  Ubuntu — One of the easiest to understand system of this type. The main  difference from Ubuntu is the used desktop environments – KDE instead of  Gnome3 or Unity.  But there will be no change if you will follow the  instructions in Gnome, XFCE, LXDE etc. environments. Use of specific  shell is a question of taste, and comfort is question of habit

Everything described below presupposes the basic knowledge of the &#1054;S  GNU/Linux: what is login directory, what stands for data terminal (or  command string), what is sudo, root and what they can do etc. The  knowledge will help you to keep your software always up-to-dated, to  track changes flexibly, to avoid hardware and software incompatibility,  to fix occurring errors with the help of various patches application and  many more.  Besides good-compiled Wine helps to successfully run other  Windows applications or games.

**For the launching Wine is needed – a particular layer between Windows-apps and system requests of the &#1054;S GNU/Linux.**

Visit [[COLOR=#00ff00]http://www.winehq.org/[/COLOR]]("http://www.winehq.org/"),  to the right you will see Latest Release block there are two lines:  Stable and Development. First – this is a stable release of Wine, second  – the latest version available at present. Which one to chose is  completely up to you, however it is better to use Development version as  new features might be added to it, improved previous functionality and  programs might work faster.


Winetricks from Dan Kegel should be downloaded next – this is a script  or, command script, which will help to significantly simplify  installation of some Wine components and it further adjusting.

Visit [[COLOR=#00ff00]http://wiki.winehq.org/[/COLOR]]("http://wiki.winehq.org/")[COLOR=#00ff00] [/COLOR] and save the script to your parent folder according to the  instructions, save the script into the root folder. Do not forget to  assign an “executive” attribute to it, in order to do so please open the  terminal menu and execute the following command chmod +x winetricks .  After this the application can be launched as from the command string so  with the double click. The script is quite user friendly interface.
[IMG]http://worldoftanks.ru/dcont/fb/uncommon_images/linux/wine.png?MEDIA_PREFIX=/dcont/fb/[/IMG]

[IMG]http://worldoftanks.ru/dcont/fb/uncommon_images/linux/wine1.png?MEDIA_PREFIX=/dcont/fb/[/IMG]

There is a problem in Wine concerning raw input API which leads  to  impossibility of the in-game cursor usage. In order to eliminate the  problem a Wine patch by Vincas Mili&#363;nas should be installed:
[LIST]
[*][Download the patch file]("https://worldoftanks.ru/dcont/fb/uncommon_images/linux/raw3.patch")
[/LIST]
 ***In order to improve performance a bit (in-game FPS amount) another patch might be used which is located [here]("https://worldoftanks.ru/dcont/fb/uncommon_images/linux/disable-dynamic-vertex-buffers.patch").***

_______________________________________________________________________________________________________________________________________________
[LIST]
[*][COLOR=#ff0000]Put both patch files into this folder
[/COLOR]
[*][COLOR=#ff0000]Launch terminal, go to the extracted files catalog. Catalog shifting is done via the [/COLOR][COLOR=#0000ff]**cd**[/COLOR][COLOR=#ff0000] command, [/COLOR][COLOR=#0000ff]**Tab**[/COLOR][COLOR=#ff0000] button helps not write catalogs full names.
[/COLOR]
[*][COLOR=#ff0000]Apply the previously downloaded patches with the help of the patch [/COLOR][COLOR=#0000ff]**-p1 < file_name.patch. command**[/COLOR][COLOR=#ff0000]. The sequence of the patches does not matter.
[/COLOR]
[*][COLOR=#ff0000]Execute [/COLOR][COLOR=#0000ff]**./tools/make_requests**[/COLOR][COLOR=#ff0000] command (to register the changes made by the patches)
[/COLOR]
[*][COLOR=#ff0000]Optionally: execute [/COLOR][COLOR=#0000ff]**autoheader**[/COLOR][COLOR=#ff0000] and [/COLOR][COLOR=#0000ff]**autoconf**[/COLOR][COLOR=#ff0000] , however everything works without them as well.
[/COLOR]
[*][COLOR=#ff0000][/COLOR][COLOR=#ff8c00]**IMPORTANT!**[/COLOR][COLOR=#ff0000] The Wine app has a lot of dependencies. In order to tune them all automatically, please execute the sudo [/COLOR][COLOR=#0000ff]**apt-get build-dep wine**[/COLOR][COLOR=#ff0000] command and accept what will be suggested.
[/COLOR]
[*][COLOR=#ff0000]Configure Wine with a [/COLOR][COLOR=#0000ff]**sudo ./configure**[/COLOR][COLOR=#ff0000] command Additional configuration parameters might be needed if there will be some errors with the game launching.
[/COLOR]
[*][COLOR=#ff0000]You should see something  like [/COLOR][COLOR=#0000ff]"configure: Finished.  Do 'make' to compile Wine"[/COLOR][COLOR=#ff0000] when finished.
[/COLOR]
[*][COLOR=#ff0000]Start the build with the help of the [/COLOR][COLOR=#0000ff]**sudo make -j4**[/COLOR][COLOR=#ff0000] command, where [/COLOR][COLOR=#0000ff]**j4**[/COLOR][COLOR=#ff0000]  is the amount of the simultaneously run tasks. If you have multi-core  processor this parameter can b changed (increase by several digits) and  achieve a faster build process (for tests was used  Intel Core i7, OS  identifies 8 cores (4 physical + Hyper-Threading technology), it will  take a few minutes for the build with [/COLOR][COLOR=#0000ff]- **j8**[/COLOR][COLOR=#ff0000]
[/COLOR]
[*][COLOR=#ff0000]When the build is finished you will see the following message:  Wine build complete. Execute the [/COLOR][COLOR=#0000ff]**sudo make install**[/COLOR][COLOR=#ff0000] command.
[/COLOR]
[*][COLOR=#ff0000]By finishing the previous command restart the Wine app with the [/COLOR][COLOR=#0000ff]**wineboot**[/COLOR][COLOR=#ff0000] command. By doing so the program will ask you to install Wine Mono and Wine Gecko — please do it.
[/COLOR]
[*][COLOR=#ff0000]In order to launch the game, some components should be installed with the help of the Winetricks. Please execute the [/COLOR][COLOR=#0000ff]**winetricks d3dx9_36 vcrun2008 corefonts msxml3 wininet ie7**[/COLOR][COLOR=#ff0000]  command. This will help to launch not only the game but the launcher  (WOTLauncher.exe) as well for checking and installing updates
[/COLOR]
[*][COLOR=#ff0000]And finally go to the game folder, run WorldofTanks.exe and enjoy the game.[/COLOR]
[/LIST]
[COLOR=#ff0000] **Some peculiarities of the above mentioned method:**
[/COLOR]
[LIST]
[*][COLOR=#ff0000]On[/COLOR][COLOR=#ff8c00] Wine 1.5.8[/COLOR][COLOR=#ff0000] (the latest updated available at the  time of the article creation) the artillery regime works without buttons  reassigning (Shift button)
[/COLOR]
[*][COLOR=#ff0000]The game’s configuration file is  located in the [/COLOR][COLOR=#ff8c00]root folder:  .wine/drive_c/users/&#1080;&#1084;&#1103;_&#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1103;/Application  Data/Wargaming.net/WorldOfTanks/preferences.xm[/COLOR][COLOR=#ff0000]l,  the screen resolution  can be changed as from the settings of the game itself, so by adjusting  the configuration file in the Device preferences chapter. If you have  adjusted the game in the way that launching troubles appeared - just  delete this file, the game will create a new one with default settings  during the next game launch.
[/COLOR]
[*][COLOR=#ff0000]On the GNU/Linux OS the game minimized and maximized incorrectly while in the fullscreen mode.
[/COLOR]
[*][COLOR=#ff0000]Another  virtual desktop might be used ([/COLOR][COLOR=#ff8c00]not a separate X-server![/COLOR][COLOR=#ff0000]) for the sake  of convenience and launch the game in the window-mode; these steps will  help to easily switch between desktops and not close the game every  time. The multiple virtual desktop functions is available in the  majority of modern distributive kits.
[/COLOR]
[*][COLOR=#ff0000]The sound works perfectly.
[/COLOR]
[*][COLOR=#ff8c00]**ATTENTION**[/COLOR][COLOR=#ff0000]**!**  The following addition is only for the owners of the NVidia video card  (or laptop with that kind of video card) equipped with the Optimus  technology.
[/COLOR]
[*][COLOR=#ff0000]**What is this technology look like?**  There are two types of the video cards in the system: motherboard  build-in (usually Intel HD Graphics 3000 designed for battery energy  economy) and discrete (dynamically plugged in) which is designed  for  supporting “heavy’@ video applications. Despite the fact that there  are Optimus-video cards drivers for the Linux on the manufacturer’s  website, all the attempts to install them lead to the X-server crash and  general unstable behavior of the system. That is why a group of  enthusiasts started a project devoted to that problem: [/COLOR][[COLOR=#0000ff]http://bumblebee-project.org/[/COLOR]]("http://bumblebee-project.org/")[COLOR=#ff0000],  which helps to use the Optimus technology. Though its install  instruction does fit the frameworks of this guide, there exists a  special command for the World of Tanks (which is not differs much from  traditional game launching using the Wine)
[/COLOR]
[*][COLOR=#0000ff]**optirun -c proxy wine /route_to_game_folder/World_of_Tanks/WorldOfTanks.exe**
[/COLOR]
[*][COLOR=#ff0000]Simply  create a shortcut for the game launch in order not to launch the game  through terminal every time. A small clarification: optirun – is a  Bumblebee itself, -c proxy — is a ‘communication’ method of the build-in  and discrete video cards which create the highest FPS rate, i.e. as the  resource-intensive video processes are calculated by the discrete card,  whereas the build-in one is only responsible   for the display output[/COLOR]
[/LIST]
[COLOR=#ff0000] That is it. Enjoy it Linux users.[/COLOR]

[SIZE=3]Note: The above instruction / procedure / method were created by **[[COLOR=#000000]_KaZanova_[/COLOR]]("http://forum.worldoftanks.asia/index.php?/user/kazanova-112/")** (one of the Admin of Wargaming) & He/She may take the  Credit if above text is Helpfull, & I hope I'm Not invading his/her Copyright. I just post his/her Text to seek for Help & Better Understanding. And most important is - I hope you understand my grammar (kinda poor in English). [/SIZE][SIZE=3]Thank you very much.
[/SIZE][h=3][/h]

---

### Post by howefield on 2013-09-28
Thread moved to the "*Wine*" forum.

---

### Post by JuanLuna on 2013-09-28
> **howefield said:**
> Thread moved to the "*Wine*" forum.

Thank you mod howefield for sorting my thread

---

