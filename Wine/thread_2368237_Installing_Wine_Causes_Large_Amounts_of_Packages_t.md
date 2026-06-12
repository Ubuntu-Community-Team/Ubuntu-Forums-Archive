---
title: "Installing Wine Causes Large Amounts of Packages to be Uninstalled"
date: 2017-08-08
forum: Wine
---

### Post by temmie19 on 2017-08-08
As shown in the title, every time I try to install Wine Development it will cause a large amount of packages to be uninstalled. Most I wish not to be. 

Take for example, this Synaptics screenshot.

[IMG]http://imgur.com/7OpsfuHl.png[/IMG]

I'm currently on Xubuntu 16.04 LTS and am currently trying to figure out some way to install Wine without uninstalling over 80 packages including some like Xfce itself. If I try installing normal Wine, it has significantly less packages to be uninstalled but every time I try to apply in Synaptics it will give me an error saying there are held packages and will refuse to start the installation process even after I've selected fix broken packages many times. If any of you could help, that would be greatly appreciated.

---

### Post by deadflowr on 2017-08-08
Sorry, but the screenshot gives us nothing to work with.
Perhaps to get a better idea of what packages will be removed or installed is to open a terminal and run
```
sudo apt-get install wine-development
```
then copy and paste the output into this thread.
(you can press n for no to abort)

Please use code tags when pasting the output from any terminal commands 
(To use code tags: Open a new post with the Reply to Thread button and paste the output into the thread, then highlight the output in the post and press the # symbol in the editor tool bar.
This will encapsulate the output in code tags.
Code tags retain the proper formatting, making it easier to read)

---

### Post by temmie19 on 2017-08-08
I'm not a new user to Linux (so don't worry about explaining basic things like how to abort an apt command) and have successfully installed Wine to  Ubuntu 14.04 LTS, my friend's copy of Lubuntu 17.04, and copy of  Manjaro. Having done these before and not being able to now is why I'm confused.

As for the terminal output:
```
temmie19@temmie-comp:~$ sudo apt install wine-development
[sudo] password for temmie19: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine-development : Depends: wine64-development (>= 1.9.6-1) but it is not going to be installed or
                             wine32-development (>= 1.9.6-1)
                    Depends: wine64-development (< 1.9.6-1.1~) but it is not going to be installed or
                             wine32-development (< 1.9.6-1.1~)
E: Unable to correct problems, you have held broken packages.

```

I am unsure as to why it says I have broken packages, because I get this when trying to fix it:

```
temmie19@temmie-comp:~$ sudo apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

When I try to install wine-development through aptitude it outputs:

```
open: 532; closed: 11705; defer: 168; conflict: 219
The following actions will resolve these dependencies:

      Remove the following packages:                                            
1)      apt-file                                                                
2)      blueman                                                                 
3)      curl                                                                    
4)      espeak                                                                  
5)      gconf-service                                                           
6)      gconf-service-backend                                                   
7)      gconf2                                                                  
8)      gdebi                                                                   
9)      gksu                                                                    
10)     gstreamer1.0-pulseaudio                                                 
11)     indicator-sound                                                         
12)     libasn1-8-heimdal                                                       
13)     libasound2-plugins                                                      
14)     libcurl3-gnutls                                                         
15)     libespeak1                                                              
16)     libgksu2-0                                                              
17)     libgssapi3-heimdal                                                      
18)     libhcrypto4-heimdal                                                     
19)     libheimntlm0-heimdal                                                    
20)     libhx509-5-heimdal                                                      
21)     libkrb5-26-heimdal                                                      
22)     libldap-2.4-2                                                           
23)     libpulse-mainloop-glib0                                                 
24)     libpulse0                                                               
25)     libpulsedsp                                                             
26)     libroken18-heimdal                                                      
27)     libsndfile1                                                             
28)     libwind0-heimdal                                                        
29)     libwine-development                                                     
30)     pavucontrol                                                             
31)     playonlinux                                                             
32)     pulseaudio                                                              
33)     pulseaudio-module-x11                                                   
34)     pulseaudio-utils                                                        
35)     python3-pycurl                                                          
36)     python3-software-properties                                             
37)     software-properties-common                                              
38)     steam-launcher                                                          
39)     xfce4-volumed                                                           
40)     xubuntu-core                                                            
41)     xubuntu-desktop                                                         

      Keep the following packages at their current version:                     
42)     gstreamer1.0-plugins-base:i386 [Not Installed]                          
43)     libasound2-plugins:i386 [Not Installed]                                 
44)     libdbus-1-3:i386 [Not Installed]                                        
45)     libfontconfig1:i386 [Not Installed]                                     
46)     libfreetype6:i386 [Not Installed]                                       
47)     libgcrypt20:i386 [Not Installed]                                        
48)     libglib2.0-0:i386 [Not Installed]                                       
49)     libgnutls30:i386 [Not Installed]                                        
50)     libgssapi3-heimdal:i386 [Not Installed]                                 
51)     libgstreamer-plugins-base1.0-0:i386 [Not Installed]                     
52)     libgstreamer1.0-0:i386 [Not Installed]                                  
53)     libheimbase1-heimdal:i386 [Not Installed]                               
54)     libheimntlm0-heimdal:i386 [Not Installed]                               
55)     libhogweed4:i386 [Not Installed]                                        
56)     libhx509-5-heimdal:i386 [Not Installed]                                 
57)     libicu55:i386 [Not Installed]                                           
58)     libidn11:i386 [Not Installed]                                           
59)     libkrb5-26-heimdal:i386 [Not Installed]                                 
60)     libldap-2.4-2:i386 [Not Installed]                                      
61)     libnettle6:i386 [Not Installed]                                         
62)     libp11-kit0:i386 [Not Installed]                                        
63)     libpulse0:i386 [Not Installed]                                          
64)     libsasl2-modules:i386 [Not Installed]                                   
65)     libssl1.0.0:i386 [Not Installed]                                        
66)     libsystemd0:i386 [Not Installed]                                        
67)     libtasn1-6:i386 [Not Installed]                                         
68)     libwine-development:i386 [Not Installed]                                
69)     libxml2:i386 [Not Installed]                                            
70)     wine-development [Not Installed]                                        
71)     wine32-development:i386 [Not Installed]                                 
72)     wine64-development [Not Installed]                                      

      Leave the following dependencies unresolved:                              
73)     libgconf-2-4 recommends gconf-service                                   
74)     libgstreamer-plugins-base1.0-0:i386 recommends gstreamer1.0-plugins-base
75)     libsasl2-2:i386 recommends libsasl2-modules:i386 (>= 2.1.26.dfsg1-14buil
76)     libopenal1 recommends libpulse0 (>= 0.99.1)                             
77)     pavucontrol recommends pulseaudio                                       
78)     wine64-development recommends wine32-development (>= 1.9.6-1)           
79)     wine64-development recommends wine32-development (< 1.9.6-1.1~)         
80)     xfce4-settings recommends xfce4-volumed                                 
81)     xfce4-volumed recommends pulseaudio                                     
82)     xubuntu-core recommends indicator-sound                                 
83)     xubuntu-core recommends pavucontrol                                     
84)     xubuntu-core recommends xfce4-volumed                                   
85)     xubuntu-desktop recommends espeak                                       
86)     xubuntu-desktop recommends indicator-sound                              
87)     xubuntu-desktop recommends pavucontrol                                  
88)     xubuntu-desktop recommends xfce4-volumed                                
89)     libopenal1:i386 recommends libpulse0:i386 (>= 0.99.1)                   
90)     pidgin recommends gstreamer1.0-alsa | gstreamer1.0-pulseaudio           


Accept this solution? [Y/n/q/?] 

```

This, however doesn't make sense as it will not install wine-development and its dependancies while still trying to uninstall other packages. However, it seems aptitude wishes to remove less packages from my computer than Synaptics.

---

### Post by sccman on 2017-08-11
Does it happen because of Wine only though?

I'm thinking not because it says "conflict: 219" at the top, which probably means you have conflicting dependencies somewhere. It may be trying to fix the problem for you by removing packages.

But to be sure try running:
```
sudo apt-get update
sudo apt-get upgrade --full-resolver
```

**--full-resolver** should give you the same message as above.

[https://askubuntu.com/questions/216354/sudo-aptitude-full-upgrade-420-conflicts](https://askubuntu.com/questions/216354/sudo-aptitude-full-upgrade-420-conflicts)

---

