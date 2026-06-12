---
title: "Wine too confusing? Howto: PlayOnLinux"
date: 2011-08-11
forum: Wine
---

### Post by Paddy Landau on 2011-08-11
[SIZE=4][COLOR=Red]IMPORTANT[/COLOR][/SIZE]

**This thread has been moved to the [Community Wiki]("https://help.ubuntu.com/community/PlayOnLinux"). I shall no longer update this thread (although you are welcome to post queries here); I shall update the Wiki instead.**

A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?p=12062065#post12062065](http://ubuntuforums.org/showthread.php?p=12062065#post12062065)

Thread closed.
__________________________________________________

Many people have posted queries because they struggle to use [Wine]("http://www.winehq.org/"). From a "newbie" point of view, I personally found Wine too confusing to use, and therefore I have never learned to use it &#8212; yet I still manage to use a couple of Windows programs.

How?

I use [PlayOnLinux]("http://www.playonlinux.com/").

This how-to is so that both new users, and other users (such as me) who find Wine too confusing, can nevertheless use it easily.


[CENTER]__________________________________________________[/CENTER]



[SIZE=4][COLOR=DarkRed][FONT=Arial Black]Contents[/FONT][/COLOR][/SIZE]


[LIST=A]
[*]Disclaimers & Warnings
[*]Why use PlayOnLinux?
[*]What are the alternatives are there?
[*]How to install PlayOnLinux
[*]How to install a "supported" Windows program
[*]How to install an "unsupported" Windows program
[*]How to uninstall a Windows program
[/LIST]

 
 [CENTER]__________________________________________________[/CENTER]
 
 
 
 [FONT=Arial Black][SIZE=4][COLOR=DarkRed]A. Disclaimers and Warnings[/COLOR][/SIZE][/FONT]
 

[LIST]
[*]  I am not an expert in Wine nor in running Windows programs under Wine (although I have used PlayOnLinux since 8.04 on both Ubuntu and Lubuntu). However, PlayOnLinux has saved me  plenty of learning and frustration, and this how-to is to share my limited knowledge.
[*]Wine is not a perfect replacement for Windows &#8212; in fact, it is rather limited. Most Windows programs will **not** work under Wine; some will be buggy, and a few will work well. [Refer to the Wine database]("http://appdb.winehq.org/") to find how well your preferred Windows application is likely to work.
[*]Some Windows programs will run slower under Linux, and others faster. It seems to depend on your hardware and available drivers.
[/LIST]
If you have problems, please post a query under [the original thread]("http://ubuntuforums.org/showthread.php?t=1822964") and I'll do my best to answer.

[CENTER]__________________________________________________[/CENTER]



[FONT=Arial Black][COLOR=DarkRed][SIZE=4]B. Why use PlayOnLinux?[/SIZE][/COLOR][/FONT]


[LIST=1]
[*]GUI; no need for the command line interface (CLI).
[*]Hides the complexity of Wine.
[*]Uses "virtual drives" (see notes below).
[*]Some applications are "supported" (e.g. Internet Explorer, Windows Media Player, Microsoft Office, Spore); PlayOnLinux automates their installation.
[*]You can manually install "unsupported" applications.
[/LIST]

[FONT=Arial Black][SIZE=2]What is a "virtual drive"?[/SIZE][/FONT]

Think of each virtual drive as a separate Windows machine. If you install each program in its own virtual drive:

[LIST]
[*]Windows programs don't interfere with each other.
[*]Uninstalling a badly-functioning or unwanted program is a [doddle]("http://dictionary.reference.com/browse/doddle") (PlayOnLinux simply deletes the virtual drive).
[/LIST]

You can, if you want, install several programs on a single virtual drive, but usually it's easier and safer to give each program its own virtual drive.

[FONT=Arial Black][SIZE=2]Cons[/SIZE][/FONT]

What are the cons of using PlayOnLinux?


[LIST]
[*]PlayOnLinux is just a front-end to Wine. Therefore, it has all the same cons as using Wine; many Windows programs don't work, or they work with flaws.
[*]Sometimes, installing a Windows program can be a little buggy. For example, I have previously installed Publisher 2003 without any problem, but when redoing it for this how-to I had a problem.
[*]Some programs may not work on a 64-bit installation.
[/LIST]
  

[CENTER]__________________________________________________[/CENTER]



[FONT=Arial Black][SIZE=4][COLOR=DarkRed]C. What alternatives are there?[/COLOR][/SIZE][/FONT]

Instead of using Wine, which has many imperfections...

[LIST]
[*]You can use [Crossover]("http://www.codeweavers.com/"). Being a commercial company, it does cost, but it is likely to support Windows programs better. There is a great Compatibility search bar at the top of the web page. Crossover "revolves around the Wine project" (its wording) and shares all improvements with Wine.
[*]For the finest results, either dual-boot with Windows, or run Windows in a virtual machine such as [VirtualBox]("http://www.virtualbox.org/") (if your machine can handle it). This gives you 100% compatibility &#8212; well, to the extent that Microsoft products are compatible with Windows ;).
[/LIST]

[CENTER]__________________________________________________[/CENTER]



[FONT=Arial Black][SIZE=4][COLOR=DarkRed]D. How to install PlayOnLinux[/COLOR][/SIZE][/FONT]

PlayOnLinux comes in the default repositories, but I prefer to have the latest version available.

[FONT=Arial Black][SIZE=2]Use the latest available version (optional):[/SIZE][/FONT]

[LIST=1]
[*]Open the Ubuntu Software Centre > Edit > Software Sources > Other Software > Add.
[*]In APT line, type the following (replace "precise" with your distro, e.g. "lucid", if you have an earlier version):```
deb http://deb.playonlinux.com/ precise main
```
[*]Press Add Source.
[*]Close the window; open a terminal and enter the following. (If you don't like the terminal, then open Update Manager instead and select Check.)```
sudo apt-get update
```
[/LIST]
 [FONT=Arial Black][SIZE=2]Install PlayOnLinux:[/SIZE][/FONT]


[LIST=1]
[*]Open the Ubuntu Software Centre.
[*]Search for playonlinux.
[*]Install.
[/LIST]
 
[FONT=Arial Black][SIZE=2]"Initialise" PlayOnLinux[/SIZE][/FONT]

 On Gnome Classic, you will find PlayOnLinux under your Games menu (I'm not sure why it's there!). On Unity, of course, you can just use the Dash.


[LIST=1]
[*]Open PlayOnLinux. Often when you do this, it will "refresh":
[attach]219286[/attach]
[*]But the very first time you run it, PlayOnLinux will lead you through a process to download the Microsoft fonts. You must be connected to the Internet and agree to the license conditions.
[attach]219287[/attach]
Follow the instructions.
[/LIST]


[CENTER]__________________________________________________[/CENTER]



[FONT=Arial Black][SIZE=4][COLOR=DarkRed]E. [/COLOR][/SIZE][/FONT][FONT=Arial Black][SIZE=4][COLOR=DarkRed]How to install a "supported" Windows program[/COLOR][/SIZE][/FONT]

When PlayOnLinux "supports" a program, it automates the process for you.

I will illustrate this through an example: Internet Explorer 8.

[LIST=1]
[*]Start PlayOnLinux > the big **Install** button at the top > Internet > Internet Explorer 8 (or you can use the search bar).
[attach]219288[/attach]
[*]Press Install.
[*]For some programs, e.g. Microsoft Office or Spore, you will need the original (legal) CD, DVD or purchased download.
[*]Follow the instructions.

Remember: when the installation asks if you want to restart your computer, this applies to your **pretend Windows** machine, and **not** to your Ubuntu machine; you can safely go ahead and press the Windows restart button. PlayOnLinux will intelligently realise what is happening and restart your virtual installation without affecting your Ubuntu session.
[*]Once installed, you will see a launcher on your desktop (which you can  delete if you want), and another on the PlayOnLinux window. Double-click either of  them to open and test the application.
[attach]219289[/attach]
[/LIST]


[CENTER]__________________________________________________[/CENTER]



[FONT=Arial Black][SIZE=4][COLOR=DarkRed]F. How to install an "unsupported" Windows program[/COLOR][/SIZE][/FONT]

The process for installing an "unsupported" program is similar to installing a "supported" one. However, you will be given extra options.

[LIST=1]
[*]Start PlayOnLinux > the big **Install** button at the top > Install a non-listed program (at the bottom left of the window).
[*]A wizard appears. Press Next > Install a program in a new virtual drive (unless you want to use an existing virtual drive) > Next. This creates a new, independent, virtual drive (a pretend Windows machine), independently of any other Windows programs you have installed.
[*]Type a suitable short name **without any spaces**, e.g. Quicken.
[*]Press Next, and Next again.
[*]Browse to the installation file, which may be, for example, an [FONT=Courier New]autorun.exe[/FONT] on a CD or a downloaded [FONT=Courier New].exe[/FONT] file.
[attach]219290[/attach]
[*]Follow the prompts, which will depend on the application you are installing.
[*]Once installed, you will see a launcher on your desktop (which you can   delete if you want), and another on the PlayOnLinux window.  Double-click either of  them to open the application.
[/LIST]
 
[CENTER]__________________________________________________[/CENTER]



[FONT=Arial Black][SIZE=4][COLOR=DarkRed]G. How to uninstall a Windows program[/COLOR][/SIZE][/FONT]

Uninstalling a Windows program is easy.

[LIST=1]
[*]Start PlayOnLinux > select the application you want to uninstall > press the big **Remove** button.
[*]A wizard appears > Next.
[*]When asked, "Do you want to delete the virtual drive&#8230;", press Yes > Next.
[/LIST]


[SIZE=2][FONT=Arial Black]What if my application does not appear?[/FONT][/SIZE]

Sometimes, an installation fails (not even the installation process for that application works). Your virtual drive has been created, but you can't see the application. You can delete the virtual drive as follows.


[LIST=1]
[*]Close PlayOnLinux.
[*]Open Nautilus and navigate to your home folder > PlayOnLinux's virtual drives.
[*]Find the virtual drive you wish to delete, and delete it. Do not delete [FONT=Courier New]default[/FONT].
[/LIST]

---

### Post by kyletstrand on 2011-08-13
Very good tutorial.  I was confused with wine at first, so I adopted PlayOnLinux.  But with POL's ease of use, I was able to learn how to configure and use wine with the greatest of ease.  I now no longer require a front end for wine or any wine program uses.

---

### Post by PCaddicted on 2011-08-15
PlayOnLinux can be useful for running various Windows programs under Linux, but it also represents a major security hole.
Wikipedia:
> Because of Wine's ability to run Windows binary code, concerns have been  raised over native Windows viruses and malware affecting Unix-like  operating systems.[[53]]("https://secure.wikimedia.org/wikipedia/en/wiki/Wine_%28software%29#cite_note-52")  Wine can run much malware, but programs running in Wine are confined to  the current user's privileges, restricting some undesirable  consequences. This is one reason Wine should never be run as the [superuser]("https://secure.wikimedia.org/wikipedia/en/wiki/Superuser").[[54]]("https://secure.wikimedia.org/wikipedia/en/wiki/Wine_%28software%29#cite_note-53") Malware research software such as [ZeroWine]("https://secure.wikimedia.org/wikipedia/en/w/index.php?title=ZeroWine&action=edit&redlink=1")[[55]]("https://secure.wikimedia.org/wikipedia/en/wiki/Wine_%28software%29#cite_note-54") runs Wine on Linux in a [virtual machine]("https://secure.wikimedia.org/wikipedia/en/wiki/Virtual_machine"), to keep the malware completely isolated from the host system. PlayOnLinux is just a graphical front-end for Wine, so there's no difference when comes to security.
My recommendation: run Windows on a virtual machine, using a program like VirtualBox.

---

### Post by Paddy Landau on 2011-08-16
> **PCaddicted said:**
> PlayOnLinux can be useful for running various Windows programs under Linux, but it also represents a major security hole.
Thank you for that information. It is useful to know. Of course, there is the advantage that you will run only what you explicitly install; in my case it is exactly two Windows programs, so I have no concern about Windows malware.

> **PCaddicted said:**
> My recommendation: run Windows on a virtual machine, using a program like VirtualBox.
This is true, especially when using VB's excellent Seamless Windows option -- but only when your computer is strong enough to handle running it. In my case, it is not (my RAM is too low).

---

### Post by PCaddicted on 2011-08-16
> **Paddy Landau said:**
> This is true, especially when using VB's excellent Seamless Windows option -- but only when your computer is strong enough to handle running it. In my case, it is not (my RAM is too low).
If the computer is not strong enough to handle that, one can install Wine or PlayOnLinux inside a virtual machine with Linux.

---

### Post by Paddy Landau on 2011-08-16
> **PCaddicted said:**
> If the computer is not strong enough to handle that, one can install Wine or PlayOnLinux inside a virtual machine with Linux.
This is true. However, my computer slows unacceptably when I run a VM, even when the VM is Linux. But why bother when using Wine (or PlayOnLinux) with one or two carefully-selected programs? Especially when my Windows program runs faster under Wine than it did (on the same computer) under native Windows!

I think your point about security is valid only if you're running Internet Explorer without a firewall, or many Windows programs -- in which case you'd probably be better booting directly into Windows!

After all, Wine is useful only when there is a program or two that you have to use (there is no suitable Linux alternative) and you'd really rather use Linux, isn't that so?

---

### Post by MG&amp;TL on 2011-08-17
Great tutorial, I shall have a look. Although to be honest, there's so much on Linux now that it seems very difficult to justify Wine/frontends. :)

---

### Post by Paddy Landau on 2011-08-18
> **MG&TL said:**
> Great tutorial, I shall have a look. Although to be honest, there's so much on Linux now that it seems very difficult to justify Wine/frontends. :)
Thanks, TL. In the main, that is true these days. But some people have requirements for work. In my case, I use Quicken to manage my books and I haven't (yet) found a suitable Linux replacement.

---

### Post by PCaddicted on 2011-08-18
A mod should sticky this thread. :wink:
It's quite useful for PlayOnLinux novices.

---

### Post by alkh3myst on 2012-03-03
**Arr, me Hearties!** Wine be garbage. I'll buy Windows emulation when I can run iTunes, and stream Netflix movies...and not a moment before. [-X **Shiver me timbers!**

---

### Post by cherry316316 on 2012-03-29
i get error message

"PlayOnLinux is unable to find 32bits OpenGL libraries."

and also

"PlayOnLinux is unable to find 64bits OpenGL libraries."

any help will be appreciated.

---

### Post by Paddy Landau on 2012-03-29
> **cherry316316 said:**
> i get error message

"PlayOnLinux is unable to find 32bits OpenGL libraries."

and also

"PlayOnLinux is unable to find 64bits OpenGL libraries."

any help will be appreciated.
I suggest you start a new thread for this. Please include the version of Ubuntu you are using, whether you are using 32-bit or 64-bit Ubuntu, how you installed PlayOnLinux, and when exactly you get the error. Please remember that we cannot see your screen, so you have to be specific and precise.

---

### Post by Paddy Landau on 2012-05-31
> **alkh3myst said:**
> **Arr, me Hearties!** Wine be garbage. I'll buy Windows emulation when I can run iTunes, and stream Netflix movies...and not a moment before. [-X **Shiver me timbers!**
WINE: "[_W_ine _I_s _N_ot an _E_mulator]("http://wiki.winehq.org/Debunking_Wine_Myths#head-a97295d7364a2a87f5769eeff9b5105b61b85761")"

If you want a fully-working emulator, you actually need the real McCoy running in a virtual machine. That involves the cost of an extra Windows license.

---

### Post by nothingspecial on 2012-06-29
This thread is closed.

The information is now held on the community wiki at [https://help.ubuntu.com/community/PlayOnLinux](https://help.ubuntu.com/community/PlayOnLinux)

Thank you for your thread and the work you have done in keeping it current and of use to the community.

A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?t=2012406](http://ubuntuforums.org/showthread.php?t=2012406)


Support threads regarding the wiki and it's content should be created in a suitable forum.

---

