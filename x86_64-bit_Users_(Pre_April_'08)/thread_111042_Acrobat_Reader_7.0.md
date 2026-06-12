---
title: "Acrobat Reader 7.0"
date: 2006-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-01-01
Ubuntu Breezy-64 on Compaq R3240 Laptop (AMD64)

Have tried and tried to install Acrobat Reader 7.0. Read everything I can find here, but nothing works. I run the INSTALL script and it appears to install everything OK. (Had to do it as sudo.) The executable file is acroread in /usr/local/Adobe/Acrobat7.0/intellinux/bin. It did not install a launcher in the Gnome panel Applications menu, but I can fix that later. The problem is getting it to launch.

What does not work:
[LIST=1]
[*]Double-clicking on the acroread executable file in Nautilus
[*]Typing "acroread" or "sudo acroread" from the command line
[*]Navigating via the command line to the above directory where the executable is located and then typing "acroread" or "sudo acroread."
[*]Double-clicking on a PDF file (it opens in Gnome PDF Viewer).
[/LIST]

I'm out of ideas. I think others have gotten it running on Breezy-64, but I'm too new to Linux to know all the tricks. Any suggestions?

---

### Post by bryanl on 2006-01-01
first thought is permissions. make sure all users have execute permission to acroread and read permission for all the necessary program files.

After that, what is the error or behavior?

---

### Post by rplantz on 2006-01-01
[QUOTE=John Jason Jordan]Ubuntu Breezy-64 on Compaq R3240 Laptop (AMD64)

I'm out of ideas. I think others have gotten it running on Breezy-64, but I'm too new to Linux to know all the tricks. Any suggestions?[/QUOTE]

Some searching on this forum convinced me that the only way to do it is with a chroot to provide a 32-bit environment.

As I recall, I tried downloading from Adobe's site and installing. I don't think they provide the sources, just the 32-bit binaries. That, of course, requires a 32-bit chroot.

Installing a chroot is a little tedious, but once it has been done, it works quite well and is easy to use. For example, you can use syanapic32 to easily install acroread.

---

### Post by John Jason Jordan on 2006-01-01
[QUOTE=rplantz]Some searching on this forum convinced me that the only way to do it is with a chroot to provide a 32-bit environment.

As I recall, I tried downloading from Adobe's site and installing. I don't think they provide the sources, just the 32-bit binaries. That, of course, requires a 32-bit chroot.

Installing a chroot is a little tedious, but once it has been done, it works quite well and is easy to use. For example, you can use syanapic32 to easily install acroread.[/QUOTE]
OK, I did it. I found instructions at 
[URL="http://doc.ubuntu-fr.org/installation/chroot32bits"]
And I followed the instructions. Amazingly, I succeeded in getting chroot installed and I can open Synaptic32. And Acrobat Reader 7.0 is listed in Synaptic32. I marked it for installation and clicked on Apply. It took a long time, but it seems to have installed it.

However, the last bit of the instructions are unclear to me. I can't figure out how to launch it. The instructions used Flash as an example. The last bit of the instructions say:

Fermez synaptic32
Entrez dans l’environnement 32 bits et créez les liens nécessaires à l’exécution depuis l’environnement 64 bits:
```
dchroot -d
sudo ln -s /usr/bin/firefox /usr/bin/firefox32

```
Quittez et créez les liens suivants
```
exit
sudo ln -s /usr/local/bin/do_dchroot /usr/local/bin/firefox32
```
Assurez-vous d’avoir fermé toutes les instances de Firefox sinon firefox32 lancera simplement une nouvelle instance 64 bits
```
firefox32
```
Visitez un site avec du flash puis installer le greffon par la procédure automatisée de Firefox.
Attention il se peut qu’il manque la librairie libXmu6 nécessaire à la bonne execution du plugin flash, si c’est le cas, installez-la avec synaptic32.

I couldn't figure out how to adapt those instructions for Acrobat Reader 7.0. It didn't help that when it comes to French, I suck.

I think I'm almost there. Can someone help me with the last bit?

---

### Post by Suger on 2006-01-02
Once Acrobat is installed through synaptic32, all you have to do is

```
sudo ln -s /usr/local/bin/do_dchroot /usr/local/bin/acroread
```

---

### Post by John Jason Jordan on 2006-01-02
[QUOTE=Suger]Once Acrobat is installed through synaptic32, all you have to do is

```
sudo ln -s /usr/local/bin/do_dchroot /usr/local/bin/acroread
```[/QUOTE]
YAY!

I knew I was close. That was the last bit I needed. It is working fine now. A thousand thanks!

---

### Post by rplantz on 2006-01-02
[QUOTE=John Jason Jordan]It didn't help that when it comes to French, I suck.
[/QUOTE]

Me too. I had a French teacher once ask me if I have a hearing deficit. :-)

I did realize the other day that seeing instructions in French can be helpful, though. It makes it easier to see what I need to copy verbatim and where I need to fill in my own information.

Glad you got it working. Within my chroot I was also able to install realplayer. So now I can listen to npr while I play on my computer.

---

### Post by John Jason Jordan on 2006-01-02
[QUOTE=rplantz]Glad you got it working. Within my chroot I was also able to install realplayer. So now I can listen to npr while I play on my computer.[/QUOTE]
That's what I'm working on right now!

I have installed RealPlayer, also via Synaptic32, but can't get it to run. First, I did:
```
sudo ln -s /usr/local/bin/do_dchroot /usr/bin/realplay
```
But that just got me an error message that the file exists.

Then I just typed "realplay" from the command line. The screen flickered and it appeared an application was going to appear on the panel, but then it stopped and nothing happened. Ditto for if I clicked on a RealPlayer link on a streaming web site.

So then I read some more and learned I could just type "dchroot" to enter the chroot environment. I did so, and then typed "realplay." This time I got:
```
jjj@Devil5:~$ realplay
** ERROR **: Unable to open display
aborting...
/usr/bin/realplay: line 75:  9972 Aborted                 $REALPLAYBIN "$@"
```

Now I see why it started to appear and then disappeared.

I know zero about programming, so I am clueless about what that means.

How did you get it working?

---

### Post by rplantz on 2006-01-07
[QUOTE=John Jason Jordan]That's what I'm working on right now!

I know zero about programming, so I am clueless about what that means.

How did you get it working?[/QUOTE]

Sorry to take so long to respond.

I've been prorgramming for forty years, and I don't know what that error message means.  :-)

Anyway, here's what I did.
```

sudo ln -s /usr/local/bin/do_dchroot /usr/local/bin/realplay32
sudo ln -s /chroot/usr/local/bin/realplay /chroot/usr/local/bin/realplay32

```

The second ln command assumes that the realplay program got installed in your /chroot/usr/local/bin/ directory. You should double-check where it got installed with
```

bob@ubuntu:/usr/local/bin$ dchroot -d
Executing shell in 'breezy' chroot.
bob@ubuntu:/usr/local/bin$ which realplay
/usr/local/bin/realplay
bob@ubuntu:/usr/local/bin$ exit
exit
bob@ubuntu:/usr/local/bin$

```

For example, when I installed acroread, it got placed in /chroot/usr/bin/. So I had to use the commands
```

sudo ln -s /usr/local/bin/do_dchroot /usr/local/bin/acroread32
sudo ln -s /chroot/usr/bin/realplay /chroot/usr/bin/realplay32

```

The general idea is:
1. Use synaptic32 to install the 32-bit program in the chroot world.
2. Determine where the program was installed (somewhere in the /chroot/ tree) and link program_name32 to program_name in that same directory.
3. Link program_name32 to do_dchoot in the (normal 64-bit world) /usr/local/bin/ directory.

As I understand it, when you type program_name32 in the 64-bit world, it goes to the do_chroot script, which switches to the 32-bit chroot world and passes program_name32 along. Within the chroot world, it follows the link you made from program_name32 to program_name.

The part that I had to figure out is that when using synaptic32 to install programs in the chroot world, different programs may be placed in different locations. You need to figure out where they are placed so you can make a link to them.

Hope this helps.

---

### Post by John Jason Jordan on 2006-01-07
[QUOTE=rplantz]As I understand it, when you type program_name32 in the 64-bit world, it goes to the do_chroot script, which switches to the 32-bit chroot world and passes program_name32 along. Within the chroot world, it follows the link you made from program_name32 to program_name.[/QUOTE]
That isn't exactly what happened for me. Getting RealPlayer installed in chroot was easy, because it was just listed in Synaptic32. But it still wouldn't launch. After reading other threads I figured out how to do it -- "dchroot -d realplay." Then I added that as a menu item and now I can launch it any time I want. Works perfectly.

Well, perfectly except for one problem. If I click on a web page link to a streaming audio source and the source expects RealPlayer, RealPlayer pops up for a moment, then disappears, and Firefox disappears along with it. No warning, no error messages, nada. 

This is exactly the behavior it edhibited before installing it into chroot, only before if I tried to launch it standalone it did the same thing -- appeared for a moment, then disappeared. 

I think Firefox is trying to call the version I installed in my 64-bit world. I'd delete it except it didn't come with an uninstall utility. Furthermore, it appears it scattered files from hell to breakfast all over my computer. There is a log file somewhere that says what it installed, but I haven't bothered to figure out how to get rid of the original installation.

In the Firefox about : plugins page there are several references to RealPlayer, but I don't understand any of them. None of them says anything clear like "ok, when the user clicks on a link to streaming audio open realplayer in /x/x folder and run it." 

Anyway, I've got it running. Now all I have to do is inform Firefox of that fact. I posted the question on the Firefox general forum, this morning, but only five people have even read the message and there are no replies.

Anyway, thanks for your detailed reply. I'm sure it helps others as well. That's the nature of these forums -- you never know who will benefit from your experiences. Maybe someone else knows the answer to my Firefox problem. In the meantime, I'm happy that I'm making progress, even if it is slow.

---

### Post by rplantz on 2006-01-08
[QUOTE=John Jason Jordan]
Well, perfectly except for one problem. If I click on a web page link to a streaming [/QUOTE]

I had similar problems.

So I tried something different. In Firefox I went to one of my favorite radio station web pages, [www.kqed.org](www.kqed.org) (public radio in San Francisco area) and clicked on their live play link. That brought up a dialog that told me I was missing plugins. But down at the bottom there's a link for "Still no audio?" I clicked on "Click here" which brought up another dialog. This one allowed me to select realplay32 to play all files of this type. I chose realplay32 in my 64-bit environment because that one is linked to do the chroot for me. I tried another station, and it worked.

By the way, I'm running the 32-bit version of Firefox that I installed following the instructions found here [http://ubuntuforums.org/showthread.php?t=112418](http://ubuntuforums.org/showthread.php?t=112418).

---

### Post by John Jason Jordan on 2006-01-08
[QUOTE=rplantz]I had similar problems.

So I tried something different. In Firefox I went to one of my favorite radio station web pages, [www.kqed.org](www.kqed.org) (public radio in San Francisco area) and clicked on their live play link. That brought up a dialog that told me I was missing plugins. But down at the bottom there's a link for "Still no audio?" I clicked on "Click here" which brought up another dialog. This one allowed me to select realplay32 to play all files of this type. I chose realplay32 in my 64-bit environment because that one is linked to do the chroot for me. I tried another station, and it worked.

By the way, I'm running the 32-bit version of Firefox that I installed following the instructions found here [http://ubuntuforums.org/showthread.php?t=112418](http://ubuntuforums.org/showthread.php?t=112418).[/QUOTE]
OK, the first thing I tried was your kqed site. It did behave differently than allclassical.org, which tries to run RealPlayer, which then disappears and takes Firefox with it. On kqed.org it popped up a window with the options to listen with RealPlayer (dialup) or with Windows Media Player (dialup). If I select RealPlayer and hit Continue it closes (crashes) Firefox and the popup window, launches gxine, and gxine then seems to go through a "buffering" routine. Gxine never produces any sound in the speakers.

If I select Windows Media, when I hit Continue it just crashes Firefox and the popup window. Interestingly, in the lower right corner of the popup window there is a little double-note icon. Hovering over it the bubble popup says it is to "restore FoxyTunes." whatever that is.

In neither case do I get an option for "still no audio?" and I never got a notice that I was missing plugins.

I have tried other stations, but none work, although the results vary. I went to [http://mikesradioworld.com/ft_classical.html](http://mikesradioworld.com/ft_classical.html) and tried several. Even if I clicked on ones whose icon indicated they required ReaPlayer, I would get Totem, Gxine or something else, or everything would crash, including Firefox. Totem and Gxine just announce they can't play the media.

Firefox is trying to launch the wrong thing. I think I need to remove all references in Firefox to all media players and then add RealPlayer. But I don't know how to do that. I've asked in a Firefox forum, but no replies after over a day.

This is kind of off-topic for the subject line (Acrobat Reader 7.0). If I don't make any more progress I'll start a new thread.

---

