---
title: "Can't install wine staging using winehq install instructions."
date: 2018-12-12
forum: Wine
---

### Post by Ziad_Arafat on 2018-12-12
I'm trying to install wine staging from winehq using the Ubuntu instructions on the site. When I run the command to install it after adding the repo I get this. 

```
[FONT=monospace][COLOR=#000000]sudo apt-get install --install-recommends winehq-staging [/COLOR]
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Some packages could not be installed. This may mean that you have 
requested an impossible situation or if you are using the unstable 
distribution that some required packages have not yet been created 
or been moved out of Incoming. 
The following information may help to resolve the situation: 

The following packages have unmet dependencies: 
winehq-staging : Depends: wine-staging (= 4.0~rc1~bionic) 
E: Unable to correct problems, you have held broken packages.
[/FONT]
```

I am using Kubuntu 18.04 LTS 64 bit 

What I've tried:
1. apt update and apt dist-upgrade
2. [COLOR=#000000]dpkg --add-architecture i386 && apt update[/COLOR]

---

### Post by epineda on 2018-12-12
run:

dpkg --add-architecture i386 && apt update

and try again...

---

### Post by Ziad_Arafat on 2018-12-16
I tried that. Same issue.

---

### Post by ununtrium on 2018-12-18
This problem is less of a WINE issue but more of a distro-specific dependencies issue.
Therefore, I'm pretty sure you are using the wrong repo for your distro version.
These are the correct install commands for your version of Ubuntu:
You can remove current wine:
```
sudo apt purge wine
```and enter:
and to install:
```

sudo dpkg --add-architecture i386 
wget -nc https://dl.winehq.org/wine-builds/Release.key
sudo apt-key add Release.key
sudo apt-add-repository https://dl.winehq.org/wine-builds/ubuntu/
sudo apt-get update
sudo apt-get install --install-recommends winehq-staging

```
You can check if all went kosher with
```
 wine --version
```
which shows the highest version of WINE installed
Hope this helps.

---

### Post by arcman7 on 2018-12-20
I'm having the same problem as well. Ran the code posted above and got this message at the end.




Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
winehq-staging : Depends: wine-staging (= 4.0~rc2~cosmic)
E: Unable to correct problems, you have held broken packages.


*I'm using Ubuntu 18.04.1 bionic beaver.

---

### Post by henriqueferrolho on 2018-12-22
I am having the same issue...

```

[B]$ sudo apt-get install --install-recommends winehq-staging
[/B]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 winehq-staging : Depends: wine-staging (= 4.0~rc2~bionic)
E: Unable to correct problems, you have held broken packages.

```

I thought that *aptitude* would help me as it has helped before, but the solutions it is proposing are ridiculous:

```
**$ sudo aptitude -f install winehq-staging**
```

```

The following NEW packages will be installed:
  glib-networking:i386{a} gstreamer1.0-plugins-base:i386{a} i965-va-driver:i386{a} libasn1-8-heimdal:i386{a} libasound2:i386{a} libasound2-plugins:i386{a} 
  libasyncns0:i386{a} libatk-bridge2.0-0:i386{a} libatk1.0-0:i386{a} libatspi2.0-0:i386{a} libavahi-client3:i386{a} libavahi-common-data:i386{a} 
  libavahi-common3:i386{a} libavcodec57:i386{a} libavutil55:i386{a} libcairo-gobject2:i386{a} libcairo2:i386{a} libcap2:i386{a} libcapi20-3{a} libcapi20-3:i386{a} 
  libcdparanoia0:i386{a} libcolord2:i386{a} libcroco3:i386{a} libcrystalhd3:i386{a} libcups2:i386{a} libdatrie1:i386{a} libdbus-1-3:i386{a} libegl-mesa0:i386{a} 
  libegl1:i386{a} libepoxy0:i386{a} libexif12:i386{a} libflac8:i386{a} libfontconfig1:i386{a} libfreetype6:i386{a} libgbm1:i386{a} libgd3:i386{a} 
  libgdk-pixbuf2.0-0:i386{a} libglib2.0-0:i386{a} libglu1-mesa:i386{a} libgmp10:i386{a} libgnutls30:i386{a} libgomp1:i386{a} libgphoto2-6:i386{a} 
  libgphoto2-port12:i386{a} libgraphite2-3:i386{a} libgsm1:i386{a} libgssapi-krb5-2:i386{a} libgssapi3-heimdal:i386{a} libgstreamer-plugins-base1.0-0:i386{a} 
  libgstreamer1.0-0:i386{a} libgtk-3-0:i386{a} libharfbuzz0b:i386{a} libhcrypto4-heimdal:i386{a} libheimbase1-heimdal:i386{a} libheimntlm0-heimdal:i386{a} 
  libhogweed4:i386{a} libhx509-5-heimdal:i386{a} libicu60:i386{a} libidn2-0:i386{a} libieee1284-3:i386{a} libjack-jackd2-0:i386{a} libjbig0:i386{a} 
  libjpeg-turbo8:i386{a} libjpeg8:i386{a} libjson-glib-1.0-0:i386{a} libk5crypto3:i386{a} libkeyutils1:i386{a} libkrb5-26-heimdal:i386{a} libkrb5-3:i386{a} 
  libkrb5support0:i386{a} liblcms2-2:i386{a} libldap-2.4-2:i386{a} libltdl7:i386{a} libmp3lame0:i386{a} libmpg123-0:i386{a} libnettle6:i386{a} libnuma1:i386{a} 
  libodbc1{a} libodbc1:i386{a} libogg0:i386{a} libopenal1:i386{a} libopenjp2-7:i386{a} libopus0:i386{a} liborc-0.4-0:i386{a} libosmesa6:i386{a} libp11-kit0:i386{a} 
  libpango-1.0-0:i386{a} libpangocairo-1.0-0:i386{a} libpangoft2-1.0-0:i386{a} libpcap0.8:i386{a} libpixman-1-0:i386{a} libpng16-16:i386{a} libproxy1v5:i386{a} 
  libpulse0:i386{ab} librest-0.7-0:i386{a} libroken18-heimdal:i386{a} librsvg2-2:i386{a} librsvg2-common:i386{a} libsamplerate0:i386{a} libsane1:i386{a} 
  libsasl2-2:i386{a} libsasl2-modules:i386{a} libsasl2-modules-db:i386{a} libsdl2-2.0-0:i386{a} libshine3:i386{a} libsnappy1v5:i386{a} libsndfile1:i386{a} 
  libsndio6.1:i386{a} libsoup-gnome2.4-1:i386{a} libsoup2.4-1:i386{a} libsoxr0:i386{a} libspeex1:i386{a} libspeexdsp1:i386{a} libsqlite3-0:i386{a} 
  libssl1.1:i386{a} libswresample2:i386{a} libtasn1-6:i386{a} libthai0:i386{a} libtheora0:i386{a} libtiff5:i386{a} libtwolame0:i386{a} libunistring2:i386{a} 
  libusb-1.0-0:i386{a} libv4l-0:i386{a} libv4lconvert0:i386{a} libva-drm2:i386{a} libva-x11-2:i386{a} libva2:i386{a} libvdpau1:i386{a} libvisual-0.4-0:i386{a} 
  libvorbis0a:i386{a} libvorbisenc2:i386{a} libvpx5:i386{a} libwavpack1:i386{a} libwayland-client0:i386{a} libwayland-cursor0:i386{a} libwayland-egl1-mesa:i386{a} 
  libwayland-server0:i386{a} libwebp6:i386{a} libwebpmux3:i386{a} libwind0-heimdal:i386{a} libwrap0:i386{a} libx264-152:i386{a} libx265-146:i386{a} 
  libxcb-render0:i386{a} libxcb-shm0:i386{a} libxcb-xfixes0:i386{a} libxcomposite1:i386{a} libxcursor1:i386{a} libxi6:i386{a} libxinerama1:i386{a} 
  libxkbcommon0:i386{a} libxml2:i386{a} libxpm4:i386{a} libxrandr2:i386{a} libxrender1:i386{a} libxslt1.1:i386{a} libxss1:i386{a} libxvidcore4:i386{a} 
  libzvbi0:i386{a} mesa-va-drivers:i386{a} mesa-vdpau-drivers:i386{a} ocl-icd-libopencl1:i386{a} va-driver-all:i386{a} vdpau-driver-all:i386{a} wine-staging{a} 
  wine-staging-amd64{a} wine-staging-i386:i386{a} winehq-staging 
0 packages upgraded, 169 newly installed, 0 to remove and 1 not upgraded.
Need to get 99.7 MB of archives. After unpacking 666 MB will be used.
The following packages have unmet dependencies:
 libpulse0 : Breaks: libpulse0:i386 (!= 1:12.2-5~bionic1) but 1:11.1-1ubuntu7.1 is to be installed
 libpulse0:i386 : Breaks: libpulse0 (!= 1:11.1-1ubuntu7.1) but 1:12.2-5~bionic1 is installed
The following actions will resolve these dependencies:


     Keep the following packages at their current version:  
1)     libasound2-plugins:i386 [Not Installed]              
2)     libpulse0:i386 [Not Installed]                       
3)     libsdl2-2.0-0:i386 [Not Installed]                   
4)     wine-staging [Not Installed]                         
5)     wine-staging-i386:i386 [Not Installed]               
6)     winehq-staging [Not Installed]                       


     Leave the following dependencies unresolved:           
7)     libopenal1:i386 recommends libpulse0:i386 (>= 0.99.1)
8)     wine-staging-i386:i386 recommends libsdl2-2.0-0:i386 

```

```
Accept this solution? [Y/n/q/?] n
```

```

The following actions will resolve these dependencies:


      Remove the following packages:                                                                              
1)      ffmpeg [7:3.4.4-0ubuntu0.18.04.1 (bionic-security, bionic-updates, now)]                                  
2)      gdm3 [3.28.3-0ubuntu18.04.3 (bionic-updates, now)]                                                        
3)      gnome-control-center [1:3.28.2-0ubuntu0.18.04.2 (bionic-updates, now)]                                    
4)      gnome-initial-setup [3.28.0-2ubuntu6.16.04.4 (bionic-updates, now)]                                       
5)      gnome-settings-daemon [3.28.1-0ubuntu1.1 (bionic-updates, now)]                                           
6)      gnome-shell [3.28.3-0ubuntu0.18.04.3 (bionic-updates, now)]                                               
7)      gnome-tweak-tool [3.28.1-1 (bionic, now)]                                                                 
8)      gnome-tweaks [3.28.1-1 (bionic, now)]                                                                     
9)      gstreamer1.0-plugins-bad [1.14.1-1ubuntu1~ubuntu18.04.1 (bionic-updates, now)]                            
10)     gstreamer1.0-pulseaudio [1.14.1-1ubuntu1~ubuntu18.04.1 (bionic-updates, now)]                             
11)     indicator-bluetooth [0.0.6+17.10.20170605-0ubuntu3 (bionic, now)]                                         
12)     indicator-sound [12.10.2+18.04.20180420.3-0ubuntu1 (bionic, now)]                                         
13)     indicator-sound-gtk2 [12.10.0.1-0ubuntu6 (bionic, now)]                                                   
14)     libasound2-plugins [1.1.1-1ubuntu1 (bionic, now)]                                                         
15)     libavdevice57 [7:3.4.4-0ubuntu0.18.04.1 (bionic-security, bionic-updates, now)]                           
16)     libcanberra-pulse [0.30-5ubuntu1 (bionic, now)]                                                           
17)     libespeak-ng1 [1.49.2+dfsg-1 (bionic, now)]                                                               
18)     libfluidsynth1 [1.1.9-1 (bionic, now)]                                                                    
19)     libfreerdp-client2-2 [2.0.0~git20170725.1.1648deb+dfsg1-7ubuntu0.1 (bionic-security, bionic-updates, now)]
20)     libpcaudio0 [1.0-1 (bionic, now)]                                                                         
21)     libpulse-mainloop-glib0 [1:12.2-5~bionic1 (now)]                                                          
22)     libpulse0 [1:12.2-5~bionic1 (now)]                                                                        
23)     libpulsedsp [1:12.2-5~bionic1 (now)]                                                                      
24)     libsdl-image1.2 [1.2.12-8 (bionic, now)]                                                                  
25)     libsdl1.2debian [1.2.15+dfsg2-0.1 (bionic, now)]                                                          
26)     libsdl2-2.0-0 [2.0.8+dfsg1-1ubuntu1.18.04.1 (bionic-updates, now)]                                        
27)     mpg123 [1.25.10-1 (bionic, now)]                                                                          
28)     mutter [3.28.3-2~ubuntu18.04.2 (bionic-updates, now)]                                                     
29)     orca [3.28.0-3ubuntu1 (bionic, now)]                                                                      
30)     osspd-pulseaudio [1.3.2-9 (bionic, now)]                                                                  
31)     pavucontrol [3.0-4 (bionic, now)]                                                                         
32)     pulseaudio [1:12.2-5~bionic1 (now)]                                                                       
33)     pulseaudio-module-bluetooth [1:12.2-5~bionic1 (now)]                                                      
34)     pulseaudio-module-gsettings [1:12.2-5~bionic1 (now)]                                                      
35)     pulseaudio-utils [1:12.2-5~bionic1 (now)]                                                                 
36)     remmina-plugin-rdp [1.2.0-rcgit.29+dfsg-1ubuntu1 (bionic, now)]                                           
37)     speech-dispatcher [0.8.8-1ubuntu1 (bionic, now)]                                                          
38)     speech-dispatcher-audio-plugins [0.8.8-1ubuntu1 (bionic, now)]                                            
39)     speech-dispatcher-espeak-ng [0.8.8-1ubuntu1 (bionic, now)]                                                
40)     ubuntu-desktop [1.417 (bionic, now)]                                                                      
41)     ubuntu-session [3.28.1-0ubuntu3 (bionic-updates, now)]                                                    
42)     unity-control-center [15.04.0+18.04.20180216-0ubuntu1 (bionic, now)]                                      
43)     unity-settings-daemon [15.04.1+18.04.20180413-0ubuntu1.2 (bionic-updates, now)]                           
44)     vlc [4.0.0~rc1~~git20181218+r78706+167~ubuntu18.04.1 (bionic, now)]                                       
45)     vlc-plugin-base [4.0.0~rc1~~git20181218+r78706+167~ubuntu18.04.1 (bionic, now)]                           


      Install the following packages:                                                                             
46)     libmate-panel-applet-4-1 [1.20.1-3ubuntu1 (bionic)]                                                       
47)     mate-power-manager [1.20.1-2ubuntu1 (bionic)]                                                             
48)     mate-power-manager-common [1.20.1-2ubuntu1 (bionic)]                                                      


      Keep the following packages at their current version:                                                       
49)     wine-staging [Not Installed]                                                                              
50)     wine-staging-amd64 [Not Installed]                                                                        
51)     winehq-staging [Not Installed]                                                                            


      Leave the following dependencies unresolved:                                                                
52)     gnome-bluetooth recommends gnome-control-center | unity-control-center                                    
53)     remmina recommends remmina-plugin-rdp                                                                     
54)     rhythmbox recommends gstreamer1.0-pulseaudio                                                              
55)     ubuntu-desktop recommends orca                                                                            
56)     ubuntu-desktop recommends speech-dispatcher                                                               
57)     indicator-applet recommends indicator-sound                                                               
58)     indicator-datetime recommends unity-control-center (>= 14.04.3) | gnome-control-center                    
59)     libopenal1 recommends libpulse0 (>= 0.99.1)                                                               
60)     unity-control-center recommends libcanberra-pulse                                                         
61)     gnome-control-center recommends libcanberra-pulse                                                         
62)     gnome-online-accounts recommends gnome-control-center (>= 3.6.1)                                          
63)     gnome-shell recommends gnome-control-center                                                               
64)     totem recommends gstreamer1.0-pulseaudio                                                                  
65)     wine-staging-amd64 recommends libsdl2-2.0-0                                                               

```

```
Accept this solution? [Y/n/q/?] n
```

```

The following actions will resolve these dependencies:


      Remove the following packages:                                                                              
1)      ffmpeg [7:3.4.4-0ubuntu0.18.04.1 (bionic-security, bionic-updates, now)]                                  
2)      gdm3 [3.28.3-0ubuntu18.04.3 (bionic-updates, now)]                                                        
3)      gnome-control-center [1:3.28.2-0ubuntu0.18.04.2 (bionic-updates, now)]                                    
4)      gnome-initial-setup [3.28.0-2ubuntu6.16.04.4 (bionic-updates, now)]                                       
5)      gnome-settings-daemon [3.28.1-0ubuntu1.1 (bionic-updates, now)]                                           
6)      gnome-shell [3.28.3-0ubuntu0.18.04.3 (bionic-updates, now)]                                               
7)      gnome-tweak-tool [3.28.1-1 (bionic, now)]                                                                 
8)      gnome-tweaks [3.28.1-1 (bionic, now)]                                                                     
9)      gstreamer1.0-plugins-bad [1.14.1-1ubuntu1~ubuntu18.04.1 (bionic-updates, now)]                            
10)     gstreamer1.0-pulseaudio [1.14.1-1ubuntu1~ubuntu18.04.1 (bionic-updates, now)]                             
11)     indicator-bluetooth [0.0.6+17.10.20170605-0ubuntu3 (bionic, now)]                                         
12)     indicator-sound [12.10.2+18.04.20180420.3-0ubuntu1 (bionic, now)]                                         
13)     indicator-sound-gtk2 [12.10.0.1-0ubuntu6 (bionic, now)]                                                   
14)     libasound2-plugins [1.1.1-1ubuntu1 (bionic, now)]                                                         
15)     libavdevice57 [7:3.4.4-0ubuntu0.18.04.1 (bionic-security, bionic-updates, now)]                           
16)     libcanberra-pulse [0.30-5ubuntu1 (bionic, now)]                                                           
17)     libespeak-ng1 [1.49.2+dfsg-1 (bionic, now)]                                                               
18)     libfluidsynth1 [1.1.9-1 (bionic, now)]                                                                    
19)     libfreerdp-client2-2 [2.0.0~git20170725.1.1648deb+dfsg1-7ubuntu0.1 (bionic-security, bionic-updates, now)]
20)     libpcaudio0 [1.0-1 (bionic, now)]                                                                         
21)     libpulse-mainloop-glib0 [1:12.2-5~bionic1 (now)]                                                          
22)     libpulse0 [1:12.2-5~bionic1 (now)]                                                                        
23)     libpulsedsp [1:12.2-5~bionic1 (now)]                                                                      
24)     libsdl-image1.2 [1.2.12-8 (bionic, now)]                                                                  
25)     libsdl1.2debian [1.2.15+dfsg2-0.1 (bionic, now)]                                                          
26)     libsdl2-2.0-0 [2.0.8+dfsg1-1ubuntu1.18.04.1 (bionic-updates, now)]                                        
27)     mpg123 [1.25.10-1 (bionic, now)]                                                                          
28)     mutter [3.28.3-2~ubuntu18.04.2 (bionic-updates, now)]                                                     
29)     orca [3.28.0-3ubuntu1 (bionic, now)]                                                                      
30)     osspd-pulseaudio [1.3.2-9 (bionic, now)]                                                                  
31)     pavucontrol [3.0-4 (bionic, now)]                                                                         
32)     pulseaudio [1:12.2-5~bionic1 (now)]                                                                       
33)     pulseaudio-module-bluetooth [1:12.2-5~bionic1 (now)]                                                      
34)     pulseaudio-module-gsettings [1:12.2-5~bionic1 (now)]                                                      
35)     pulseaudio-utils [1:12.2-5~bionic1 (now)]                                                                 
36)     remmina-plugin-rdp [1.2.0-rcgit.29+dfsg-1ubuntu1 (bionic, now)]                                           
37)     speech-dispatcher [0.8.8-1ubuntu1 (bionic, now)]                                                          
38)     speech-dispatcher-audio-plugins [0.8.8-1ubuntu1 (bionic, now)]                                            
39)     speech-dispatcher-espeak-ng [0.8.8-1ubuntu1 (bionic, now)]                                                
40)     ubuntu-desktop [1.417 (bionic, now)]                                                                      
41)     ubuntu-session [3.28.1-0ubuntu3 (bionic-updates, now)]                                                    
42)     unity-control-center [15.04.0+18.04.20180216-0ubuntu1 (bionic, now)]                                      
43)     unity-settings-daemon [15.04.1+18.04.20180413-0ubuntu1.2 (bionic-updates, now)]                           
44)     vlc [4.0.0~rc1~~git20181218+r78706+167~ubuntu18.04.1 (bionic, now)]                                       
45)     vlc-plugin-base [4.0.0~rc1~~git20181218+r78706+167~ubuntu18.04.1 (bionic, now)]                           


      Install the following packages:                                                                             
46)     libmate-panel-applet-4-1 [1.20.1-3ubuntu1 (bionic)]                                                       
47)     mate-power-manager [1.20.1-2ubuntu1 (bionic)]                                                             
48)     mate-power-manager-common [1.20.1-2ubuntu1 (bionic)]                                                      
49)     wine-staging:i386 [4.0~rc2~bionic (bionic)]                                                               


      Keep the following packages at their current version:                                                       
50)     wine-staging [Not Installed]                                                                              
51)     wine-staging-amd64 [Not Installed]                                                                        


      Leave the following dependencies unresolved:                                                                
52)     gnome-bluetooth recommends gnome-control-center | unity-control-center                                    
53)     remmina recommends remmina-plugin-rdp                                                                     
54)     rhythmbox recommends gstreamer1.0-pulseaudio                                                              
55)     ubuntu-desktop recommends orca                                                                            
56)     ubuntu-desktop recommends speech-dispatcher                                                               
57)     indicator-applet recommends indicator-sound                                                               
58)     indicator-datetime recommends unity-control-center (>= 14.04.3) | gnome-control-center                    
59)     libopenal1 recommends libpulse0 (>= 0.99.1)                                                               
60)     unity-control-center recommends libcanberra-pulse                                                         
61)     gnome-control-center recommends libcanberra-pulse                                                         
62)     gnome-online-accounts recommends gnome-control-center (>= 3.6.1)                                          
63)     gnome-shell recommends gnome-control-center                                                               
64)     totem recommends gstreamer1.0-pulseaudio                                                                  
65)     wine-staging-amd64 recommends libsdl2-2.0-0                                                               


Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.

```

---

### Post by PlazmaKG on 2019-01-19
I have found the solution.
go to the following link [https://dl.winehq.org/wine-builds/ubuntu/dists/bionic/main/binary-amd64/](https://dl.winehq.org/wine-builds/ubuntu/dists/bionic/main/binary-amd64/)
and download the latest one, and install it.
then do 
[COLOR=#ff0000]sudo apt install --install-recommends winehq-staging
[/COLOR][IMG]http://i66.tinypic.com/23rquyg.png[/IMG]

---

### Post by Nullivex on 2019-01-22
> **PlazmaKG said:**
> I have found the solution.
go to the following link [https://dl.winehq.org/wine-builds/ubuntu/dists/bionic/main/binary-amd64/](https://dl.winehq.org/wine-builds/ubuntu/dists/bionic/main/binary-amd64/)
and download the latest one, and install it.
then do 
[COLOR=#ff0000]sudo apt install --install-recommends winehq-staging[/COLOR]


I can confirm this works for me! Nice job.

---

### Post by redy2 on 2019-08-07
If anyone else out there has as much bad luck as me and the above did not work. I fixed it by installing from the xenial repo which is basically the repo for ubuntu 16. Just follow the indications at: [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu) and pretend you have 16.04. I have been using it for a short while now and i haven't had any issues with it.

---

### Post by odhinnsrunes on 2019-08-21
Try the instructions here: [http://ubuntuhandbook.org/index.php/2019/05/nstall-wine-4-8-ubuntu-19-04-18-04/](http://ubuntuhandbook.org/index.php/2019/05/nstall-wine-4-8-ubuntu-19-04-18-04/)

---

### Post by Redsandro on 2019-09-30
I would like to add a guide that worked for me:

[https://www.linuxuprising.com/2019/09/how-to-install-wine-staging-development.html](https://www.linuxuprising.com/2019/09/how-to-install-wine-staging-development.html)

Basically wine recently added dependencies that are not (yet) in the main repos, so it advises to use the OBS repo. Worked for me.

---

