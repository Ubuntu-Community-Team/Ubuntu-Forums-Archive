---
title: "nvidia drivers!!"
date: 2006-05-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by s_spiff on 2006-05-01
i'm using a Dapper Drake installtion of ubuntu.. beta 2.. i know wrong forum ..but i didnt get a solution to my problem in Dapper Drake Dev. and the Hardware section..so i apologise. I want to install drivers for my nvidia chipset 430. I dont know how to do it. can someone please help? Because of this i cant even connect to the net on ubuntu..have to boot into winxp to post my query! please help!

---

### Post by Imexius on 2006-05-01
I don't see how not having nvidia drivers prevents you from connecting to the internet


If you in the terminal type

```
sudo apt-get install nvidia-glx

sudo nvidia-glx-config enable

startx
```

---

### Post by s_spiff on 2006-05-01
well i would have done that but u c ... i need to have my internet connection working for that, and to have my nternet connection working, I need to have the drivers which willl get the nvidia chipset working :D

---

### Post by MartinG on 2006-05-01
But you don't need nvidia drivers to work in a terminal, in fact you don't need X at all.  How are you trying to do this?:???:

---

### Post by s_spiff on 2006-05-01
umm i have my graphical interface working an all..but u c..when i tried lsmod command ..used for the ethernet card......i didnt get response..and according to a how-to i don have the drivers installed..so now i need to install them..but without net workin i cant install them by sudo..so i need to know if there is some other way ..like a .deb package that i can download ..burn to a cd and use in linux..

---

### Post by MartinG on 2006-05-01
This sounds like you are needing network card drivers, but the only nvidia drivers I know of are graphics card drivers -- ISTM you're looking for the wrong thing?

Networking problems are a bit beyond me, but we can check what card you've got. Run ```
lspci | grep Ethernet
``` and see what it says.  Then we can tackle drivers (or you can ask elsewhere with a different title!).

---

### Post by kaffeine on 2006-05-01
boot into windows, and download the nForce drivers here
[http://www.nvidia.com/object/linux_nforce_amd64_1.0-0310.html](http://www.nvidia.com/object/linux_nforce_amd64_1.0-0310.html)

these are nvidia's drivers for your chipset, including onboard ethernet controller (NOT GRAPHICS driver, but i guess you figured that out by now).

boot into linux and copy the nforce driver package from wherever you stored it (from mounted windows partition or USB stick, whichever is easier for you)

change it to exectable 
```
chmod a+x NFORCE-Linux-x86_64-1.0-0310-pkg1.run
``` 

run it as root, and reboot. (you may need to ifup eth0 if it's not done after the reboot)

p.s: make sure you download the correct nforce drivers for your chipset/CPU.

---

### Post by s_spiff on 2006-05-02
well did that as u said... put it on a cd and copied to linux and tried running it..but at the start itself it says : Please check if you have the package binutils installed, if you have, then please make sure that 'ld' is in the PATH.
something of that sort, dont remember properly. what to do now? where do i download that package from?

---

### Post by kaffeine on 2006-05-02
ok that appears very suspicious. let's do this step-by-step: check if binutils is really not installed or if it's just a path issue (dapper should install binutils by default that's why it's better to make sure)

1. type ```
ls /usr/bin/ld
```. if you get 'No such file...', go to step 3. if you get '/usr/bin/ld' (ld exists in /usr/bin) - 

2. do ```
echo $PATH
``` if you see '/usr/bin/' in the output, then go to step 3. if you don't, add this to your .bashrc file

```
PATH="$PATH:/usr/bin:"
```

close terminal and reopen, repeat echo $PATH and check if you now see /usr/bin in the output. try 'ld' and if you get 'no input files' then ld is working - go ahead and install he Nforce driver. 

3. now that you know you don't have 'ld', install the binutils package. get it from [here ]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Fmain%2Fb%2Fbinutils%2Fbinutils_2.16.1cvs20060117-1ubuntu2_amd64.deb&md5sum=99ff87daccd61de40537e032825b7b15&arch=amd64&type=main")
 while in windows, put it on CD/USB/mount and go into linux. install it by typing 

```
sudo dpkg -i binutils*.deb
```

hopefully the install goes without any additional dependencies to be downloaded. if it barfs then make a list of all dependencies it needs, boot into windows, download their .deb packages from packages.ubuntu.com and install them with dpkg -i like before.

once you get ld working, you could get back to installing NForce drivers.

---

### Post by s_spiff on 2006-05-02
rocking dude! thanks..will try it out immediately! and amazing singnature :P

---

### Post by s_spiff on 2006-05-02
well had to take binutils from windows to linux..anyways.. well when i i started the driver indtallations this is what error it gave me :

error 1 : No precompiled kernel interface was found to match your kernel, this means that the installer will need to complile a new interface.
[clicked ok on this ]

error 2: [ which came when i pressed ok for the above error ] Unable to find kernel source for the currently running kernel. Please make sure you have a installed kernel source files for your kernel. [ it gives the examsple of a redhat system ] If you know the correct kernel source files are installed, you may specify the path with the ' -- kernel-source-path ' commandline option

so now what to do? whats wrong with my kernel? and how do i set that path! damn..this is very very frustrating!

---

### Post by Jason_25 on 2006-05-02
Error 1 is not an error.  Error 2 means you need your kernel headers installed.

---

### Post by s_spiff on 2006-05-02
ok..how do i do that?

---

### Post by Jason_25 on 2006-05-02
```

sudo apt-get install linux-headers-`uname -r`

```

---

### Post by s_spiff on 2006-05-03
well ... net isnt working u c! so i cant get it from apt-get...any other method?

---

### Post by Jason_25 on 2006-05-03
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

```

uname -r

```
will tell you your kernel version.

---

### Post by s_spiff on 2006-05-03
thanks man...but well where do i search in the packages site? as in which section? and whats the name of the package?

---

### Post by Jason_25 on 2006-05-03
I'm not sure what to tell you if you can't find the search box.  Also, I don't know your kernel version, and thus your kernel header version because I am not psychic.

---

### Post by s_spiff on 2006-05-03
lol sorry.. ok..i'll figure out something. thanks.

---

### Post by s_spiff on 2006-05-03
can someone tell me how to install the headers? same sudo dpkg -i ..... or some other command?

---

### Post by Jason_25 on 2006-05-03
If you have found the matching headers for your kernel, then yes, install them like any other deb.

---

### Post by kaffeine on 2006-05-03
spiff, i expected you would run into that error - it's very common. as before, always check if you have stuff already installed (may save you loads of time) - find out your running kernel with 'uname -r' and then look in 'ls /usr/src/' to find the folder 'linux-headers-...' where ... is your kernel. if you don't, then get the packages as before (a google search always works:) ) - dapper linux headers are [here]("http://packages.ubuntu.com/dapper/devel/"). 

do dpkg as you did before, and check /usr/src/ to make sure they are installed.

then start your nForce installation - with this option:

```
sh ./NFORCE-***.run --kernel-source-path=/usr/src/linux-headers-...
```

(replace ... with your version, of course)

a couple of other preemptive suggestions: if it says "kernel was compiled using a different version of gcc...", do this:

```
export $CC="gcc-3.4"
``` 

if it throws up a 'kernel output path' not found, add this option to installation:

```
sh ./NFORCE-***.run --kernel-source-path=/usr/src/linux-headers-... --kernel-output-path=/lib/modules/2.6..../ 
``` (... is your version)

good luck!

---

### Post by s_spiff on 2006-05-04
kaffine u rock dude..thanks a lot..will try i out immediately... was just abt to give up on dapper actually! gettin really frustrated... and was hoping breezy for amd54 wont be as much as a pain as DD. cuz for a noob like me..it really is madness!

---

