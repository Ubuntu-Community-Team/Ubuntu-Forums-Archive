---
title: "Has anyone  got RealPlayer to work on a ppc computer?"
date: 2005-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by seatea on 2005-10-26
I am using  a desktop PM G4 400 to run Ubuntu. Thankfully, I  now seem to have most of my hardware functioning adequately. One problem that persists in plaguing  me is trying to get RealPlayer to run. Ironically, one of the reasons I have even installed Ubuntu on my computer was to see if I could  get RealPlayer to run on a professional website that I access periodically. I still have Mac OS 9.2.2 on my computer. Since  it is now rendered obsolete by Mac OS X, software makers such as RealPlayer are no longer  providing  updates for it. The website I am trying  to use their software on requires a RealPlayer  update not available for Mac OS 9.2.2.

Today, I thought I had finally gotten RealPlayer to install using the realplay-10.0.0.297-linux-2.2-libc6-gcc32-powerpc.bin file from the  helix website. Following the instructions in the Ubuntu  Starter Guide, I am running Breezy Badger, everything seemed to go smoothly. When I tried to access it in the Applications menu, it  was not there. A search through Add Application shows the  realplayer logo, but the  words video player next to it are grayed out. If I attempt to check the box next to it, I get the message "Application 'realplayer' not available - The  application can not be found  in your  archive. This usually means that it is not  available for your  hardware platform. "

Does this mean because I have a ppc based machine I cannot run  RealPlayer or is there something  else I can do? If anyone has any advice or has RealPlayer running on their ppc based computer I would like to hear about it.

---

### Post by pvz on 2005-10-27
You might want to try a more recent build. I run RealPlayer 10.0.5.756
[https://helixcommunity.org/download.php/1346/realplay-10.0.5.756-linux-2.2-libc6-gcc32-powerpc.bin](https://helixcommunity.org/download.php/1346/realplay-10.0.5.756-linux-2.2-libc6-gcc32-powerpc.bin)
On my iBook with no problems. If the above link doesn't work, get in from the downloadpage at
[https://helixcommunity.org/project/showfiles.php?group_id=154](https://helixcommunity.org/project/showfiles.php?group_id=154)
under RealPlayer for Unix, RealPlayer 10.0.5 Gold Release.

---

### Post by seatea on 2005-10-27
Thanks for your help. I downloaded from the link in your post [https://helixcommunity.org/download...32-powerpc.bin](https://helixcommunity.org/download...32-powerpc.bin) and the file downloaded to my Desktop. I then followed the instructions in the Ubuntu  starter guide and in the Terminal did the following:

"seatea@equipage:~$ cd Desktop
seatea@equipage:~/Desktop$ chmod +x realplay-10.0.5.756-linux-2.2-libc6-gcc32-powerpc.bin
seatea@equipage:~/Desktop$ sudo ./realplay-10.0.5.756-linux-2.2-libc6-gcc32-powerpc.bin
Password:
Extracting files for RealPlayer installation........................

Welcome to the RealPlayer (10.0.5.756) Setup for UNIX
Setup will help you get RealPlayer running on your computer.
Press [Enter] to continue...


Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory:  [/home/seatea/Desktop/RealPlayer]: /usr/bin/RealPlayer

You have selected the following RealPlayer configuration:

Destination:            /usr/bin/RealPlayer

Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]: F


Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: ...y.
enter the prefix for symbolic links [/usr]: .../usr.
Setting up realplay symlinks in /usr...
configuring icons...
configuring document icons...
.configuring pixmaps...
configuring locale...
configuring desktop...
configuring applications...
configuring GNOME mime types...
Configuring realplay script...

RealPlayer installation is complete.
Cleaning up installation files...
Done.

seatea@equipage:~/Desktop$ cd".

After that I went to Applications>Sound &Video and for the first time since I  have been trying to install this program the "RealPlayer 10" icon  was showing. Unfortunately, when I clicked on it nothing  happened. What do you think went wrong?

---

### Post by emendelson on 2005-10-27
Use Automatix to install RealPlayer and save yourself much grief. Search for Automatix in the forums, and you'll find the download.

EDIT - sorry, this probably applies only to x86 systems. Please ignore.

---

### Post by pauljwells on 2005-10-27
Try opening realplayer from a terminal.
/usr/local/bin/RealPlay/whatevertheexecutableiscalled

if this works then you probably just need to update the gnome menu, easiest way is a reboot.

---

### Post by pvz on 2005-10-27
try to run it from a terminal, like pauljwells who just beat me with his post said :-)
On my system just running **realplay** from a terminal is enough to start it. Relogging in your X session or rebooting will probably fix it, otherwise look for the output in the console and post back.

That automatix thingy seems to be i386 only, not for PPC..

---

### Post by seatea on 2005-10-27
I appreciate the help. I have been about ready to throw in the towel on Ubuntu. Here's what I did. I opened  terminal and typed in the path to the executable file on my computer which I presume is realplay.bin and the terminal gave this output;

"seatea@equipage:~$ /usr/bin/RealPlayer/realplay.bin

** (realplay.bin:5715): WARNING **: HXPlayer: Error 0x80004005: "A general error has occurred."

** ERROR **: Could not create helix engine. You must run:
export HELIX_LIBS=<path to your helix libs>
aborting...
Aborted".

I then just typed in  realplay in the terminal and got this:

"seatea@equipage:~$ realplay
/usr/bin/RealPlayer/realplay.bin: symbol lookup error: /usr/bin/RealPlayer/plugins/swfrender.so: undefined symbol: _Z27FlashRendererCreateInstancePP8IUnknown".

I searched for the file HELIX_LIBS and could not find it on my computer.

Do you think if this was installed, I could run realplayer? Also, where would I find these files?

---

### Post by pvz on 2005-10-27
Weird, I never had any of your problems, and I used the same installer as you.. I don't even have the file swfrender.so in the plugins directory.
It's probably some useless shockwave plugin, so try to remove it as suggested here:
[http://lists.debian.org/debian-powerpc/2004/10/msg00144.html](http://lists.debian.org/debian-powerpc/2004/10/msg00144.html)
and see what happens when you try realplay from the terminal again.
In your case, do ```
sudo rm /usr/bin/RealPlayer/plugins/swfrender.so
```
and hopefully it will finally work :-)

And just a thought, did you remove the directory with your previous install from the older version?

When I run pvz@ibook:~$ /usr/local/bin/realplayer/realplay.bin
it gives me the same error message about the HELIX_LIBS, so that's obviously not the way to start it. Just **realplay** should do.

---

### Post by seatea on 2005-10-27
Success! It opened! 

I did as you said: 
"sudo rm /usr/bin/RealPlayer/plugins/swfrender.so" then got another error for  "swfformat.so" , removed it and  RealPlayer  launched. I can't thank  you enough for helping  me with this. Will the plugins be already installed to use with Firefox or do I need to add them manually to Firefox?

Thanks again.

Addendum: I went to the website I was wanting to use RealPlayer with, it launches, starts buffering then  freezes. I have tried to get it to play the video by downloading the .smil file and  then opening it with  RealPlayer as well as opening directly from Firefox, but  same problem. I have to force quit each time. Any thoughts on this?

---

### Post by pvz on 2005-10-28
[QUOTE=seatea]Success! It opened! 

Addendum: I went to the website I was wanting to use RealPlayer with, it launches, starts buffering then  freezes. I have tried to get it to play the video by downloading the .smil file and  then opening it with  RealPlayer as well as opening directly from Firefox, but  same problem. I have to force quit each time. Any thoughts on this?[/QUOTE]

Great you got it working at last..
what is the website you are trying to watch? I can try and see if it works on my computer. Maybe you could try installing the latest Helix player as well, my firefox gives the following plugin information:
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
and it works with realplayer content, at least at [http://3voor12.vpro.nl/3voor12/live/kies.jsp](http://3voor12.vpro.nl/3voor12/live/kies.jsp)

---

### Post by seatea on 2005-10-28
I  tried HelixPlayer on the website, but  it could not play the video at all. I looked in Firefox and there is  no plugin, Helix DNA Plugin: RealPlayer G2 Plug-In Compatible. How could I install it? I searched for the file Helix DNA Plugin, but did not get any results.

The website I was trying to access is <[http://www.unmc.edu/Pediatrics/GrandRounds/](http://www.unmc.edu/Pediatrics/GrandRounds/) >. In the middle of the page there  is a line that  says, Archive Video Link; Click Kere to View the Presentation.

---

### Post by pvz on 2005-10-30
You can check the installed plugins in Firefox by typing
```
about:plugins
```
in the location bar.

I tried to watch the smil-files from the page you linked to, but unfortunately I had no luck either. It starts to buffer the file, but my CPU goes 100% and Realplayer crashes.

I'm out of options, perhaps it's time to head over to the Helix & RealPlayer forums and ask for help there.
[https://helixcommunity.org/forum/?group_id=154](https://helixcommunity.org/forum/?group_id=154)

Good luck..

---

### Post by seatea on 2005-10-30
It was generous of you to take the time to help troubleshoot my RealPlayer problems. It  was a minor consolation to have at least gotten the player installed. It leaves me uncertain about Ubuntu ppc though. It seems a little buggy. although it is appealing, not to mention free; however, I don't mind paying for software that fills my needs. I think I am going to have to get over my  attachment to my PM G4 400 and get another  computer with  a different  architecture and more processing  power in  order to run Linux. I haven't really been able to warm up to Mac OS X. From what I have read from other users posts, Mac OS X would  be too sluggish  on my computer.  With  the potential of Apple switching  to Intel based systems, it  doesn't really make sense to me to stay with the powerpc based  computers either. I owned  a Betamax once and my PM G4 is starting  to remind me of that experience. I was content with Mac OS 9.2.2 even with its limitations on memory management  and multitasking. It runs well on the PM G4 and really is simple to use. It's a shame to see it become obsolete. Have you tried any other operating  systems on your  iBook? Thanks again.

---

### Post by pvz on 2005-10-30
[QUOTE=seatea] Have you tried any other operating  systems on your  iBook? Thanks again.[/QUOTE]
I have OS 10.4 Tiger installed as well, but I never use it. I run the KDE Kubuntu flavor though, [www.kubuntu.org](www.kubuntu.org) Maybe you will like it better than Gnome, if you decide to continue with Linux. Or try the XFCE4 desktop, it's light and fast.
PowerPCs are nice, but probably not the best platform for Linux if you need things like java, flash and full RealPlayer support. I wouldn't mind having a Power Macintosh G4/400 to play with though :-)

---

### Post by calum on 2005-10-31
[QUOTE=seatea]
Addendum: I went to the website I was wanting to use RealPlayer with, it launches, starts buffering then  freezes. I have tried to get it to play the video by downloading the .smil file and  then opening it with  RealPlayer as well as opening directly from Firefox, but  same problem. I have to force quit each time. Any thoughts on this?[/QUOTE]

FWIW, you're not the only one to fall at this final hurdle... I haven't managed to play a video with RealPlayer on Breezy yet; it always freezes.  Worked fine on Hoary.  Plays audio files just fine, just not videos :/

---

### Post by Brian McConnell on 2005-10-31
[QUOTE=calum]FWIW, you're not the only one to fall at this final hurdle... I haven't managed to play a video with RealPlayer on Breezy yet; it always freezes.  Worked fine on Hoary.  Plays audio files just fine, just not videos :/[/QUOTE]
just wanted to chime in with a me-too post. RealPlayer launches, but freezes when I try to play a file.

Here's how I installed mine:

```
$ cd browse_to_your_download_folder
$ chmod +x realplay-10.0.4.750-linux-2.2-libc6-gcc32-powerpc.bin
$ sudo ./realplay-10.0.4.750-linux-2.2-libc6-gcc32-powerpc.bin

Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory:  [/home/chua/RealPlayer]: /opt/RealPlayer

You have selected the following RealPlayer configuration:
Destination:            /opt/RealPlayer
Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]: F

Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: Y

enter the prefix for symbolic links [/usr]: /usr
```

---

