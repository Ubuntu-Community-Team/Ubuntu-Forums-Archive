---
title: "Perfect World International Descent Working"
date: 2012-03-19
forum: Wine
---

### Post by vanquishedangel on 2012-03-19
I have 2 computers that use this game and the install was very different on both, what worked on one didn't work on the other. **The way i did computer 2 is prolly the best**. Please post helpful replies only, your method or helpful additions, please no complaining.

Computer one= amd64 dual core 2.5GHZ, 8gigs ram, sapphire ATI 6450 pci card. Lubuntu 64bit newest version 11.10(worked for me but I wasn't able to repeat it try computer 2 way first)

Computer 2= intel ht 3.8 ghz 64bit, 4 gigs ram, ATI 2400xt pci card. Lubuntu 64bit newest version 11.10


Ok here is what i have done on **computer one**:

1. Add wine ppa [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

2. Run "sudo apt-get build-dep wine wine1.3" and hit enter and put in your password

3. Get and install playonlinux (4.0.15 for me)from their site [http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html) and let playonlinux grab wine from the repositories.

4. After the dependancies and playonlinux is installed open it and let it refresh and install microsoft fonts. It should be under games.

5. I clicked install, and in the left pane I clicked testing and then found perfect world and double clicked it. this will install wine 1.2.2 and vcrun6

6. I had an old PWI installer that i torrented and it is version 515 but I read some where that the torrented version off the site doesn't have pmb.exe wich has given me and others many problems but I cannot verify this. choose your installer when asked.

7. I had to change a cfg file to tell playonlinux to use 32bit, in the file /home/"USER NAME HERE"/.PlayOnLinux/wineprefix/PerfectWorld edit playonlinux.cfg and add the line "ARCH=x86" if you are using a 64bit system.

8. I then installed d3dx9, fake ie6, wmp codecs, vcrun 2005, vcrun 2008, d3dx10 and directx9 in that order by clicking configure button, install packages tab, and choosing them from playonlinux.

then the game worked, I downloaded and used patches to update the game and if you use them, they need to be marked executable. and you should be able to auto update to.

**Computer two**: (revised 3-31-2012)


1. Purge all wine and playonlinux versions, delete the .wine and .playonlinux files in your home folder.

2. Run sudo apt-get build-dep wine1.2

3.Install wine1.2 from synaptic

$. Install playonlinux from synaptic or the downloaded versin from the pol website(pol glitched when I installed it first, and if it does glitch reinstall wine 1.2, wine gecko, and winetricks)

5. Download ie_zht.exe and ie_zhc.exe (do a google search)

6. download the perfect world descent installer ([http://pwi.perfectworld.com/download](http://pwi.perfectworld.com/download))

7, Run the perfect world script from playonlinux (menu-games-playonlinux, let it update, install-testing-perfect world international)

8. run the perfect world descent installer and it will download 5 gigs of stuff(may crash mine did) then when prompted and wine open a folder choose install.exe, if a wine folder doesn't open then open pol, click install-install a .pol package or an unsupported application-manual-forwardedit an exsisting application-perfectworld open a file manager and go to /home/USERNAME/desktop/Pwi_Descent_Installer and choose the install.exe

9. when install is done open pol click install-other-playonlinux functions-forward just choose one, and install vcrun2005, vcrun2008, and directx9 (not d3dx9 or the full set up) and then it worked

10. install language packs you downloaded and when asked to make a short cut in pol click yes on both and on one choose elementclient.exe and on the other choose patcher.exe. the short cuts made from pol didnt work so you may delete those.

11. Now the game needs to be set up so when running the update for it click graphics when it is finished updating, and choose windowed mode 800x600 and select your other settings, then confirm. when the game starts you can expand the window by clicking the box and it will work, i have never gotten this game to run outside of windowed mode.

---

### Post by vanquishedangel on 2012-03-27
Configure wine through playonlinux right click game in pol and choose configure wine and go to audio tab when prompted click apply then got to libraries and change msvcrt to builtin native.

also go through play on linux again and right click and choose registry editor then go to HKEY_CURRENT_USER\Software\Wine\Direct3D

and enter these keys

&#8220;DirectDrawRenderer&#8221;=&#8221;opengl&#8221;
&#8220;Nonpower2Mode&#8221;=&#8221;repack&#8221;
&#8220;OffscreenRenderingMode&#8221;=&#8221;fbo&#8221;
&#8220;RenderTargetLockMode&#8221;=&#8221;auto&#8221;
&#8220;UseGLSL&#8221;=&#8221;disabled&#8221;
&#8220;VertexShaderMode&#8221;=&#8221;hardware&#8221;
&#8220;VideoDescription&#8221;=&#8221;ATI Radeon HD 6450&#8221; (Change this to your current Graphics card)
&#8220;VideoDriver&#8221;=&#8221;nv4_disp.dll&#8221; for NVIDIA or  "ati2dvag.dll" for ati
&#8220;VideoMemorySize&#8221;=&#8221;500&#8243; (Use your current video memory size)

if you are able also enter these (you can google to get your info or figure out how)

"VideoPciVendorID"="0x1002" for ati cards

"VideoPciDeviceID"="0x6779" for ati Radeon HD 6450

---

### Post by vanquishedangel on 2012-04-01
There is yet more, If you are using ubuntu and the like, after computer 2 way of installing, Download playonlinux from their site and install it (if there are issues just reinstall wine1.2, wine geko, and winetricks) you can then open synaptic and install the meta-package of wine (or sudo apt-get install wine) but if you do, **do not install anything or make any changes to the perfect world prefix after doing this**, the prefix will update and break if you do.

The reason for doing this is to update or upgrade ubuntu. with the wine meta package, wine will be included in the upgrade process and will be able to update. I will test this on the next release of ubuntu but the update from wine1.2-wine1.3 using the "wine" package went ok

---

