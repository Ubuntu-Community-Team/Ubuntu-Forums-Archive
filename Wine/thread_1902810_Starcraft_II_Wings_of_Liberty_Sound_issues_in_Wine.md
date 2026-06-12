---
title: "Starcraft II Wings of Liberty Sound issues in Wine - OpenAL"
date: 2011-12-31
forum: Wine
---

### Post by BryceHarding on 2011-12-31
I have recently got Starcraft II Wings of Liberty and have this issue where the sound cuts off after 1-2 minutes. I had this issue previously on an earlier Ubuntu install with the Starcraft II Starter edition and the solution at the time that resolved it was to recompile wine from the source to enable openAL support. This worked but i have no idea how i mannaged to do it. I had originaly used info from several different tutorials to achieve this and after about a week of ferocious googling i still cant figure out how i did it.

I am running Ubuntu 11.10 for 64bit and have installed the default wine from the Software Center on a inspiron 1720 core 2 duo laptop. 

The Wine AppDB entry for Starcraft II Retail ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882")) says the following about audio issues.

> To get sound, start winecfg, go to DLL overrides, add "mmdevapi" and set it to "disabled".

If you compile Wine with OpenAL, you do not need this override. Some packages (like the ones shipped in Debian, for example) may not compile OpenAL, so you may need to download the Wine source code and the OpenAL development package to get OpenAL compiled. Once Wine is compiled with OpenAL support, you do not need to override mmdevapi.

 

Since 1.3.18 there are some sound issues. The bug report recommends compiling the svn version from alsa-plugins:


cd ~ 
git clone git.alsa-project.org/alsa-plugins.git alsa-plugins 
cd alsa-plugins 
./gitcompile 
sudo make install 
sudo /sbin/alsa force-reload

IMPORTANT

Since wine 1.3.25svn you need to remove the mmdevapi exception to get sound working 

all of the recommendations for these issues are prior to patch 1.3.25 and I haven't fount much further help.

Like i said before I am confident that the recommendation that wine should be recompiled with openAL support is the solution I'm just hoping somone who knows how to do this can tell me what i need to do or else point me to a howto that works after patch 1.3.25.

---

### Post by BryceHarding on 2012-01-21
I have resolved the sound issues by installing OpenAL-soft [from here]("https://launchpad.net/ubuntu/+source/openal-soft") and downloading the Wine source [from here]("http://sourceforge.net/projects/wine/files%2FSource/"). There are many hardware and distro specific reasons that people may want to compile their own wine rather than installing from the repositories and there are a million different game specific tweaks & bug fixes that can improve your wine experience when you compile it yourself. In my case my laptop is using pulse audio which requires OpenAL support to be compiled into wine which is not done with the wine installed from the repos. I figgured this out from trial and error but if anyone else needs to get this working or resolve a simmilar problem here's how I did it.

First install the most recent OpenAL from the source by extracting it to a directory. Once this is done open a terminal and navigate to the build directory inside the source folder. To build the OpenAl-Soft source code you will need to install cmake just type sudo apt-get cmake and enter your root password when prompted. once cmake is installed use it to build OpenAL-Soft by typing cmake .. from within the build direcorty in terminal. Once this is done it can be installed by typing sudo make install and if prompted entering your root password. 

Once OpenAl-Soft has installed successfully just chose your preferred version of Wine from the sourceforge (link is above) and once you have extracted the source to a folder you need to uninstall any previously installed version of Wine from your package mannager or Ubuntu software center. The README in the source folder has instructions on how to do this from the terminal if you have previously compiled your own wine. If you have never uninstalled wine before you will NOT loose any programms installed in Wine by removing it, you just won't be able to run them again untill you reinstall.

**Pro Tip#1:*** When I tried building Wine it kept failing saying I hadn't installed one of the build dependencies. after installing the missing package and trying again... tada it tells you it's missing another package. To resolve this open a terminal and type the following: sudo apt-get build-dep wine1.3 all of the required dependencies downloaded & installed. [See Here]("http://wiki.winehq.org/Recommended_Packages#head-4b5211d3fa4652eb9cfa2c8ebd369073a62cba57")* 

Just navigate to the source folder in a terminal and you can run the install command ./tools/wineinstall when it askes you if you want to continue type yes  & then go watch a movie or something cause it's gonna take a while. When it's done compiling you will be prompted to enter your root password before the installation which is relatively quick.

After installation of Wine from the source Icons for Wine will not be added to your program launcher but any previously created shortcuts for windows programms will continue to work. Also you will still be able to launch windows executables by left clicking and choosing run with wine and ofcourse wine programs will also be launchable in terminal. Just open Starcraft II as normal and in the menu options go to sound and choose the appropriate audio device and save the changes. Now the game works but i notice some performance issues but this is most likely due to system reqirements however the game seems to crash whenever i try to exit the game normallly but overall all it works.

**Pro Tip #2:***Do not delete the source folder after you are finished building. afer playing for a while i ran into a mission where the screen was compleetly black and i couldn't resolve it and it turned out it was due to a [bug (SEE HERE)]("http://bugs.winehq.org/show_bug.cgi?id=23906#c23") on the bug report Erich Hoover on post #23 posts some modified code for one of the .dll libraries and after adding 1 line of code and replacing 2 others it works like it's supposed to after i uninstalled/recompiled. by not deleting your files when  your done you can shave about 45 min of the compile time as only the modified files are recompiled.*

---

