---
title: "Amd64 and 32 bit applications that are a *must*"
date: 2006-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by joefie on 2006-05-27
Hello all,

I hope all of you are in good shape of health. I recently bought a 64 bit computer after running 32 bit for a while with debian. I found out, that I need to run firefox(incl plugins like nonfree-flashplugin) mplayer(incl codecs) openoffice, and all other good 32 bit applications that won't work fully or that arn't compliant on 64 compared to 32 bit). Is there a way for me to only use the 32 bit applications, system wide installed, nicely intergrated in a gnome menu or debian menu?


Thanks in advance


Joe

---

### Post by Kilz on 2006-05-27
[QUOTE=joefie]Hello all,

I hope all of you are in good shape of health. I recently bought a 64 bit computer after running 32 bit for a while with debian. I found out, that I need to run firefox(incl plugins like nonfree-flashplugin) mplayer(incl codecs) openoffice, and all other good 32 bit applications that won't work fully or that arn't compliant on 64 compared to 32 bit). Is there a way for me to only use the 32 bit applications, system wide installed, nicely intergrated in a gnome menu or debian menu?


Thanks in advance


Joe[/QUOTE]

So far I have been messing around trying to get 32 bit applications running on Ubuntu. Im by no means an expert and have done things by trial and error. So far wine and mplayer has ran pretty good when I force installed them with sudo dpkg --force-architecture -i <packagename>
Im running Dapper 64 bit and [This thread]("http://www.ubuntuforums.org/showthread.php?t=112418") is great for setting up Firefox 32 with flash and java. Open office 32 bit is a default install so not a problem. 
What I understand is the next version Edgy will have a better 32/64 bit ability, but that is far off as Dapper is just about to be released.

---

### Post by John Jason Jordan on 2006-05-27
[QUOTE=joefie]I found out that I need to run firefox (incl plugins like nonfree-flashplugin) mplayer (incl codecs) openoffice, and all other good 32 bit applications that won't work fully or that aren't compliant on 64 compared to 32 bit). Is there a way for me to only use the 32 bit applications, system wide installed, nicely intergrated in a gnome menu or debian menu?[/QUOTE]
Yes, you can, although you won't need to run all of them as 32-bit applications. For example, OpenOffice.org runs just fine in 64-bit. The main problem applications are Firefox plugins, Realplayer and Adobe Reader 7.0. Firefox itself runs fine in 64-bit; it's just that it's hard to get the Flash and Realplayer plugins to work.

To accomplish what you want you need to install a 32-bit chroot environment. This is basically a 32-bit version of Ubuntu running inside 64-bit Ubuntu. Installation is simple -- just do it from Synaptic. When I did it the installation went without a hitch. It sets up the 32-bit chroot environment in /chroot/breezy/32-bits. After installing chroot you can browse into that folder and you will see essentially everything the same as you have in your 64-bit Ubuntu, except no programs will be installed yet.

Next, you need to install programs in your 32-bit chroot environment. This is also pretty easy. All you need to do is launch the 32-bit version of Synaptic. To do this, open a terminal and type "sudo dchroot -d synaptic32." The 32-bit version of Synaptic will open and you can choose what programs you want to install. Everything installed with 32-bit Synaptic will automatically be installed in the 32-bit chroot environment. I used Synaptic32 to install Firefox, then Realplayer, then Adobe Reader 7.0. I can't remember how I got the Flash plugin going in my 32-bit Firefox -- I think I went to a site with 32-bit Firefox and installed it from there. In any event, they are all working just fine.

Finally, you need a way to launch these apps in your 32-bit chroot environment from your 64-bit world. This is super-easy. Just right-click on Applications in your panel and choose Edit Menus. Create a new menu item for each application you installed in 32-bit chroot. But instead of just giving it the command, add "dchroot -d" in front of the command. For example, the command to launch my 32-bit Firefox is "dchroot -d firefox %u."

One final problem: Any application in your 32-bit chroot environment that needs to connect to the internet may not be able to find your internet DNS servers. If your computer is always at the same place, this is a problem that you need to fix only once. Just find the /etc/resolv.conf file in your 64-bit world and copy it over the /chroot/breezy/32-bits/etc/resolv.conf file. This file tells things like Firefox where the DNS servers are.

If your computer is a laptop and you connect from different locations you will have to copy over the 64-bit resolv.conf file every time you change locations. If you need to do this, holler back and I'll explain the simple solution I created to automate this.

---

