---
title: "how to get NVIDIA drivers working? !?@!$"
date: 2009-01-08
forum: x86 64-bit Users
---

### Post by sshizzle on 2009-01-08
Hello,

I've spent the last 10 hours reading all sorts of guides trying to get my nvidia drivers working with no luck.

Here is my situation:
I have 8.10, I successfully got wine, steam installed, and Team Fortress 2 installed. I'm using an 8800 GTS (320Mb) btw.

When I try to run TF2, ubuntu poops itself and I'm back at the login screen. My intuition told me I didn't have the video driver installed/working, so then I began my trek into n00b hell.

First I tried using the 'restricted hardware drivers' that 8.10 automatically posted. I tried three different ones (79 i think, 173, and 177) all with no luck.

Then I got onto nvidia's website and downloaded their driver 177.82. First of all, Nvidia's instructions are outrageously suck. Anyway, I try intalling 177.82 per their inSUCKtions, and I got a pop-up installer that tells me "You appear to be running X...."

I then spend some time trying to figure out how to turn off X, with no luck. I have alternatively tried: ctrl-alt-backspace, ctrl-alt-F1, and many others' suggestions from other guides or posts. NOTHING WORKS

I've done so many things so many different ways by now that my brain is fried. I'm just going to go drink beer until someone links me a good guide, or knows what exactly I'm doing wrong.

ANYBODY??? Must. Pwn. Noobs...with 64bit Linux...

---

### Post by sonu 1807 on 2009-01-08
Try EnvyNG-:

type in terminal sudo apt-get install envyng-core

Then sudo envyng -t

Follow the instructions... it should work.

---

### Post by sshizzle on 2009-01-08
> **sonu 1807 said:**
> Try EnvyNG-:

type in terminal sudo apt-get install envyng-core

Then sudo envyng -t

Follow the instructions... it should work.

I just tried. I get the error:
 +--------------------------------------------------------+
 |    Error:                                              |
 |                                                        |
 |    EnvyNG has detected that the headers for            |
 |    your kernel are missing and cannot be installed     |
 |                                                        |
 +--------------------------------------------------------+

for all four drivers.

I uninstalled first, then restarted computer, then restarted x, then installed one by one.

When I checked the envyng website, it says it only supports up to ubuntu 8.04...Is my best best to reinstall w/ 8.04 and redo wine, steam, and tf2 just to get the driver working? If there is an easy option here, I would love to try it first.

---

### Post by mgranet on 2009-01-08
It's quite easy to install the Nvidia drivers. First, you need to install some packages to allow the kernel module to be built. Get the build-essential and linux-headers-2.6.*xx-y* packages; (xx-y being the version for the kernel you happen to be running.) You can find this by ```
uname -a
``` While you are in there, uninstall anything related to nvidia graphics (except open source 'nv' drivers).

 I use Kubuntu, and I log out, then select 'Console login' from the menu. Gnome is different, so you may have to Ctrl+F1 to get to a console. Next, (assuming you have driver in home directory) install the drivers with: ```
 sudo sh NVIDIA-Linux-x86_64-177.82.pkg2.run
``` It will prompt you to download kernel module, it will fail, then build it's own. It will ask to overwrite the old driver: Allow it. It will ask permission to recreate the xorg.conf file: allow it. It will ask if you want 32 bit compatability mode: You guessed it, allowed. It will finish up, then drop you off at the command line. ```
sudo reboot
``` to restart, and you should have drivers installed.

If this did work, play your games for a few minutes to make sure everything works, then go grab the beta 180.17 drivers. You won't be disappointed.

---

### Post by sshizzle on 2009-01-08
I found and installed the build-essential package, but the linux-headers-2.6.24-16 is not available to me in synaptic.

All that I can see in synaptice are linux-headers2.6.27-9, linux-headers2.6.27-3,and linux-headers2.6.27-7 with various suffixes like -generic and -server. I think I have all the repositories and software sources enabled.

When I try to run 
sudo sh NVIDIA-Linux-x86_64-177.82-pkg2.run
I get to the first step of building the kernal module and I get an error that says something like, "compiler used to make kernel (gcc 4.2) does not exactly match current compiler (gcc 4.3)"

I try to go on anyway, because that option is available despite the above error, and then I get an error that says something like, "Please make sure you have installed the kernel source files"

Do I still need some 'headers' package that I'm not seeing? Am I missing a repository or something?

---

### Post by sonu 1807 on 2009-01-08
I am using 8.10 64-bit myself and I installed nvidia driver through it. May be the developer have not tested it on 8.10 and so they do not mention it. Its not working because you have installed nvidia driver earlier. Follow these steps 

1. Log out and press CTRL+ALT+F1 (you'll see the command line)

2. Log in 

3. Stop the Xserver by typing:
sudo /etc/init.d/gdm stop

4. Uninstall the driver from nvidia installer:
cd path_to_the_nvidia_installer
sudo sh name_of_the_nvidia_installer --uninstall

5. Run envyng and select the "Install" function. Run EnvyNG's textual installer by typing:
sudo envyng -t

Then follow the instructions

---

### Post by jocko on 2009-01-08
> **sshizzle said:**
> I found and installed the build-essential package, but the [COLOR=Red]linux-headers-2.6.24-16[/COLOR] is not available to me in synaptic.

All that I can see in synaptice are linux-headers2.6.27-9, linux-headers2.6.27-3,and linux-headers2.6.27-7 with various suffixes like -generic and -server. I think I have all the repositories and software sources enabled.

When I try to run 
sudo sh NVIDIA-Linux-x86_64-177.82-pkg2.run
I get to the first step of building the kernal module and I get an error that says something like, "compiler used to make kernel (gcc 4.2) does not exactly match current compiler (gcc 4.3)"

I try to go on anyway, because that option is available despite the above error, and then I get an error that says something like, "Please make sure you have installed the kernel source files"

Do I still need some 'headers' package that I'm not seeing? Am I missing a repository or something?
Your problem is that you are running an old hardy kernel (2.6.24), so there are no headers for you in the intrepid repos (intrepid uses a 2.6.27 kernel).
You have probably only made a partial upgrade from hardy, so try this:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install linux-image-generic linux-headers-generic
```
Reboot to the new kernel, and after that there should be no problem getting the hardware manager to install the nvidia drivers.

---

### Post by sshizzle on 2009-01-08
Since I couldn't see ubuntuforums.org for most of the day, I just went ahead with the reinstall of 8.10, assuming (I think correctly) that I had the 8.04 kernel, since I did the synaptic upgrade 8.04 to 8.10.

Got the driver installed!! Thanks for your help! However, I'm still having issues...

I also got Steam and Team Fortress 2 running, but when I load into a server, I get to the loading screen of a map, then I'm back to the Ubuntu log in screen. Still searching the forum for help, but thought I'd update everyone who has helped out. Thanks again.

---

### Post by mgranet on 2009-01-09
Actually, Nvidia just released the new stable 180.22. You should grab that one to get VDPAU support amongst other things.

---

### Post by sshizzle on 2009-01-09
> **mgranet said:**
> Actually, Nvidia just released the new stable 180.22. You should grab that one to get VDPAU support amongst other things.

mgranet, are you using 8.10? wine? what games are you playing if any?

does anybody out there have TF2 working. I get the impression people have it working, but I've yet to have anyone say, "yes, I have tf2 working in 8.10 with wine."

---

### Post by mgranet on 2009-01-10
> **sshizzle said:**
> mgranet, are you using 8.10? wine? what games are you playing if any?

does anybody out there have TF2 working. I get the impression people have it working, but I've yet to have anyone say, "yes, I have tf2 working in 8.10 with wine."

Yes, running Kubuntu Intrepid. No Windows games, only native Linux games. (Prefer to to my gaming on my 360 anyway). Wine is good, but you might also have luck with VirtualBox. The latest release has support for Windows guests to have access to the host system's 3d acceleration.

---

