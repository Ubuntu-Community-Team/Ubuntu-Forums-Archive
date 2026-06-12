---
title: "I can't apt-get install acroread."
date: 2006-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hoffmann on 2006-03-24
Hello,

I would like to install Adobe Acroread on my system. However, after running the command $ sudo apt-get install acroread, I got the error:

Reading package lists... Done
Building dependency tree... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  acroread-debian-files
E: Package acroread has no installation candidate

Ok. After trying to install acroread-debian-files by using Synaptic, I got the (pop up) message:

acroread-debian-files:
Depends: acroread  but it is not installable

Important to say that I have multiverse repositories available on Synaptic.
Could anyone, please, help me?

Thanks!
Hoffmann

---

### Post by aysiu on 2006-03-24
The Multiverse has Acroread for only i386, not AMD64.

---

### Post by Hoffmann on 2006-03-24
So, there is no way to install Acroread on AMD64. Right?

---

### Post by aysiu on 2006-03-24
[This](http://ubuntuforums.org/showthread.php?t=91035) may help.

---

### Post by John Jason Jordan on 2006-03-24
[QUOTE=Hoffmann]So, there is no way to install Acroread on AMD64. Right?[/QUOTE]
As far as I know, you can't install it in 64-bit. People have said that you can if you have the 32-bit libraries installed, which Breezy-64 does by default, but it still didn't work for me. In fact, I don't think I have ever seen anyone say they got it installed and working in 64-bit withut chrooting it.

The instructions on the link aysiu gave you is what I used. However, I should add that if you want RealPlayer as well, and to have it working in Firefox, then you need to install in order: Acroread, RealPlayer, Firefox. Otherwise Firefox doesn't seem to get the plugins straight.

By using chroot I now have all three installed and working fine. And Flash, too. There is just one little problem. I have this installed on a laptop. Naturally, the laptop moves around. When I connect at the university I cannot go anywhere on the internet because the DNS server addresses are different from my ISP at home. So every time I change location I have to copy the /etc/resolv.conf file from the 64-bit world to the chroot world. The command to do this is

sudo ln -f /etc/resolv.conf /chroot/breezy/32bits/etc/resolv.conf

I've explored the possibilities of automating this, but it would require scripting and I know zero about programming. So I created an icon to launch an application and installed it on the Gnome panel. The "launch" command is the above link command. I also told it to run the "program" in a terminal. Now, whenever I am in a different location all I have to do is click on the icon, a terminal window pops up asking for my password, I type it in and hit enter, and it's done. I know there are probaly more elegant ways of doing this, but I'm hoping I won't need this much longer anyway. Eventually there will be 64-bit versions of all this stuff and I can just delete the chroot environment and forget about it.

---

### Post by Hoffmann on 2006-03-25
Hi aysiu,

Many thanks for the link. I will read it carefully and, if I feel confortable with "chroot", I will do that. 
Best,
Hoffmann

---

### Post by Hoffmann on 2006-03-25
[QUOTE=John Jason Jordan]As far as I know, you can't install it in 64-bit. People have said that you can if you have the 32-bit libraries installed, which Breezy-64 does by default, but it still didn't work for me. In fact, I don't think I have ever seen anyone say they got it installed and working in 64-bit withut chrooting it.

The instructions on the link aysiu gave you is what I used. However, I should add that if you want RealPlayer as well, and to have it working in Firefox, then you need to install in order: Acroread, RealPlayer, Firefox. Otherwise Firefox doesn't seem to get the plugins straight.

By using chroot I now have all three installed and working fine. And Flash, too. There is just one little problem. I have this installed on a laptop. Naturally, the laptop moves around. When I connect at the university I cannot go anywhere on the internet because the DNS server addresses are different from my ISP at home. So every time I change location I have to copy the /etc/resolv.conf file from the 64-bit world to the chroot world. The command to do this is

sudo ln -f /etc/resolv.conf /chroot/breezy/32bits/etc/resolv.conf

I've explored the possibilities of automating this, but it would require scripting and I know zero about programming. So I created an icon to launch an application and installed it on the Gnome panel. The "launch" command is the above link command. I also told it to run the "program" in a terminal. Now, whenever I am in a different location all I have to do is click on the icon, a terminal window pops up asking for my password, I type it in and hit enter, and it's done. I know there are probaly more elegant ways of doing this, but I'm hoping I won't need this much longer anyway. Eventually there will be 64-bit versions of all this stuff and I can just delete the chroot environment and forget about it.[/QUOTE]

Hi John Jason Jordan,

Thanks for the detailed explanation. I my case, the machine is a EM64T desktop. So, it isn't going to move around so frequently. :-D 
I am not "worry" about Acroread anymore, since I decided to install GNOME PDF Viewer 2.10.0 for reading pdf files. Moreover, I don't need Real Player, since I use XMMS for listen to my musics, etc. I have also followed a nice trick for getting flash plugin running on Firefox32 on my 64-bits environment ([https://wiki.ubuntu.com/FirefoxAMD64FlashJava)](https://wiki.ubuntu.com/FirefoxAMD64FlashJava)). What I have realized is that I have had problems with some "32-bits" libraries for programs that I consider to be important to me (for working).
Ok. I have never used chroot before. Is it complicated? Do you think I should install it? How do you move from you 64-bits environment to the 32-bits environment, and vice-versa?
Could I hear from you again?

Thanks, once again.
Hoffmann

---

### Post by John Jason Jordan on 2006-03-25
[QUOTE=Hoffmann]Ok. I have never used chroot before. Is it complicated? Do you think I should install it? How do you move from you 64-bits environment to the 32-bits environment, and vice-versa?  Hoffmann[/QUOTE]
To install chroot is super-easy. Just open Synaptic and there it is. Select it to install and it will install itself perfectly. At least it did for me.

It is important to understand what chroot does. It is another copy of Ubuntu, a 32-bit copy, inside your 64-bit installation. It will make a folder for this new installation -- /chroot/breezy/32bits. Once you look at what is in that new folder you will realize that it is essentially the same set of files and folders that you have in your 64-bit world.

Once you have chroot installed you need to learn a couple commands to use from the terminal:

dchroot -- this command will move you into the chroot environment. Every command you enter after this will be in 32-bit Ubuntu. To get out of it and back to your 64-bit world type Ctrl-c. (Wait ... I'm not sure, maybe you have to sudo the dchroot command.)

To launch a chrooted program from the 64-bit world change the launch command by adding "dchroot -d" in front of it. For example, to launch the 64-bit version of Firefox the command is "firefox %U." To launch the copy I have installed in 32-bit chroot the command is "dchroot -d firefox %U." You can do this easily just by editing your Applications menu.

To install programs in your new chroot environment, just open the copy of Synaptic that is in there. To do so from the 64-bit world just type "sudo dchroot -d synaptic32." Anything installed by Synaptic32 will automatically be installed in the chroot world.

If you have any other questions, just holler back. :)

---

### Post by Hoffmann on 2006-03-25
[QUOTE=John Jason Jordan]To install chroot is super-easy. Just open Synaptic and there it is. Select it to install and it will install itself perfectly. At least it did for me.

It is important to understand what chroot does. It is another copy of Ubuntu, a 32-bit copy, inside your 64-bit installation. It will make a folder for this new installation -- /chroot/breezy/32bits. Once you look at what is in that new folder you will realize that it is essentially the same set of files and folders that you have in your 64-bit world.

Once you have chroot installed you need to learn a couple commands to use from the terminal:

dchroot -- this command will move you into the chroot environment. Every command you enter after this will be in 32-bit Ubuntu. To get out of it and back to your 64-bit world type Ctrl-c. (Wait ... I'm not sure, maybe you have to sudo the dchroot command.)

To launch a chrooted program from the 64-bit world change the launch command by adding "dchroot -d" in front of it. For example, to launch the 64-bit version of Firefox the command is "firefox %U." To launch the copy I have installed in 32-bit chroot the command is "dchroot -d firefox %U." You can do this easily just by editing your Applications menu.

To install programs in your new chroot environment, just open the copy of Synaptic that is in there. To do so from the 64-bit world just type "sudo dchroot -d synaptic32." Anything installed by Synaptic32 will automatically be installed in the chroot world.

If you have any other questions, just holler back. :)[/QUOTE]

Hello John,

Thanks fot the prompt reply!
Defenitely, I will install chroot, so. One more question, if you don't mind:
In your email, you told me: "...Just open Synaptic and there it is. Select it to install and it will install itself perfectly...". Ok. I opened Synaptic, and used the "search" icon to look for the program. I got a lot options. Which one should I install? Is it "cdhoot"?

Thanks!
Hoffmann

---

### Post by John Jason Jordan on 2006-03-25
[QUOTE=Hoffmann]Ok. I opened Synaptic, and used the "search" icon to look for the program. I got a lot options. Which one should I install? Is it "cdhoot"?  Hoffmann[/QUOTE]
I'm sorry. I thought it was "chroot" but I just looked and it is "dchroot." 

Of course! How stupid of me! That's the command to go to the chroot environment! Duh!

---

### Post by Hoffmann on 2006-03-25
[QUOTE=John Jason Jordan]I'm sorry. I thought it was "chroot" but I just looked and it is "dchroot." 

Of course! How stupid of me! That's the command to go to the chroot environment! Duh![/QUOTE]

Hi John,

I just installed dchroot, so. However, I realized that I didn't make any folder for (a) new installation -- /chroot/breezy/32bits.
Am I missing anythin here? What is the procedure? Sorry if this question seems to be "stupid", but I have no experience with chroot.
Thanks!
Hoffmann

---

### Post by John Jason Jordan on 2006-03-25
[QUOTE=Hoffmann]I just installed dchroot, so. However, I realized that I didn't make any folder for (a) new installation -- /chroot/breezy/32bits.
Am I missing anythin here? What is the procedure? Sorry if this question seems to be "stupid", but I have no experience with chroot.  Hoffmann[/QUOTE]
I think it installs the folders automatically. I have the folders and I don't remember creating them. Look in your file manager (Nautilus or whatever you use) and go to the root (/). You should see folders like /bin, /boot, /cdrom, /chroot, /dev, etc. It's the /chroot folder that you are looking for. It should be:

/chroot/breezy/32bits/ ... and a whole bunch more folders.

Is that what you see? If not, what do you see?

---

### Post by Hoffmann on 2006-03-25
[QUOTE=John Jason Jordan]I think it installs the folders automatically. I have the folders and I don't remember creating them. Look in your file manager (Nautilus or whatever you use) and go to the root (/). You should see folders like /bin, /boot, /cdrom, /chroot, /dev, etc. It's the /chroot folder that you are looking for. It should be:

/chroot/breezy/32bits/ ... and a whole bunch more folders.

Is that what you see? If not, what do you see?[/QUOTE]

Unfortunately, I see no /chroot directory at all. :( 
Are you sure you just installed dchroot program? Didn't you install any other program, as well?
Hoffmann

---

### Post by John Jason Jordan on 2006-03-26
[QUOTE=Hoffmann]Unfortunately, I see no /chroot directory at all. :( 
Are you sure you just installed dchroot program? Didn't you install any other program, as well? [/QUOTE]
I'm sorry, it has been over a month and I don't recall for sure. I do know I installed dchroot because it is marked in Synaptic (64 bit) as installed. 

Is dchroot marked as installed in Synaptic? What happens if you open a terminal and type "sudo dchroot"? And if that works, what happens if you type "sudo dchroot -d synaptic32"? If it's marked in Synaptic as installed, the two commands should work.

---

### Post by Hoffmann on 2006-03-26
[QUOTE=John Jason Jordan]I'm sorry, it has been over a month and I don't recall for sure. I do know I installed dchroot because it is marked in Synaptic (64 bit) as installed. 

Is dchroot marked as installed in Synaptic? What happens if you open a terminal and type "sudo dchroot"? And if that works, what happens if you type "sudo dchroot -d synaptic32"? If it's marked in Synaptic as installed, the two commands should work.[/QUOTE]

I just got the following link: [http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit](http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit)
I think all I need to do is to follow that link, but changing "hoary" to "breezy".

Hoffmann

---

