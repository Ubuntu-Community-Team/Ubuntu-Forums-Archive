---
title: "Problem with vmware-player"
date: 2006-12-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by leona on 2006-12-09
Hi
I've been having crashing problems with VMplayer 1.0.4, so decided maybe s reinstall would fix it.
Tried to uninstall it and got the messages
"The following problems were found on your s"
"E: vmware-player: Package is in a very bad inconsistent state - you should"

Ya I should what!?  The message just ended!  What this some sort of "complete the sentence" game?

Anyway how can I fix this and get the package reinstalled and working again.

Thanks

Leona.

---

### Post by John.Michael.Kane on 2006-12-11
Most members here use vmware-server

Heres a guide for vmware-server
[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+howto](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+howto)


Heres two guides for vmware-player.
[https://help.ubuntu.com/community/VMware/Player?action=show&redirect=VMWarePlayerAndWindowsHOWTO](https://help.ubuntu.com/community/VMware/Player?action=show&redirect=VMWarePlayerAndWindowsHOWTO)

[http://www.ubuntuforums.org/showthread.php?t=84275&highlight=vmware-player+howto](http://www.ubuntuforums.org/showthread.php?t=84275&highlight=vmware-player+howto)

As for howto remove VMWare Player (if you installed it from the Ubuntu repositories) you must select “Mark for Complete Removal” in Synaptic

Also make sure your also completely remove the /etc/vmware directory and all files beneath it as well.

---

### Post by leona on 2006-12-11
Thank you for your reply.
I've never used the vmware server, don't know how that would benifit me.
I'm unable to completely remove it, it keeps complaingin there is a problem as listed above, I don't know what is wrong because it will not give me the whole message, maybe there is another way i can remove it ?

Arr I ran an apt-get for something else and got this.

```

not fully installed or removed.
Need to get 0B/11.8MB of archives.
After unpacking 0B of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package vmware-player.
(Reading database ... 89130 files and directories currently installed.)
Preparing to replace vmware-player 1.0.1-4 (using .../vmware-player_1.0.1-4_amd64.deb) ...
/etc/init.d/vmware-player: line 171: vmware_product_name: command not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/etc/init.d/vmware-player: line 171: vmware_product_name: command not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/vmware-player_1.0.1-4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
/etc/init.d/vmware-player: line 171: vmware_product_name: command not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/vmware-player_1.0.1-4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by tszanon on 2006-12-12
The message is something like: "You should run 'dpkg --configure -a'..."
But running this command only allows to me run synaptic again. I've got the same problem and I don't know how to solve it. I thought about removing the packages "by hand", but I don't know where apt keeps its files. Besides, I think that would be kinda dangerous.

Because of this and some other problems, I've already decided to reinstall Dapper. But...if I'm gonna reinstall Dapper, why don't I try to remove vmplayer by hand?:-k

---

### Post by leona on 2006-12-18
I'm still having this problem, I seem unable to clear the problem, ever time I try an install something, it give me this error, can someone tell me how I can clear this problem out?

---

### Post by jms830 on 2006-12-19
I too am having this problem. I believe it arose from trying to install both vmware server and vmware-player or installing one and removing the other or something. Now I'm just stuck with these error msgs

any time i run apt,
```
1 not fully installed or removed.
Need to get 0B/11.9MB of archives.
After unpacking 0B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 142741 files and directories currently installed.)
Preparing to replace vmware-player 1.0.2-2 (using .../vmware-player_1.0.2-2_i386.deb) ...
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/vmware-player_1.0.2-2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/vmware-player_1.0.2-2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

so then I try to remove vmware-player
```

jordan@jordan-ubuntu:~$ sudo apt-get remove --purge vmware-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  vmware-player vmware-player-kernel-modules
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  vmware-player*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.1MB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: error processing vmware-player (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Errors were encountered while processing:
 vmware-player
Aborted (core dumped)

```

then if I try to "apt-get --reinstall vmware-player" I get the same first apt error message

---

### Post by tszanon on 2006-12-19
> **jms830 said:**
> I believe it arose from trying to install both vmware server and vmware-player or installing one and removing the other or something.

Although I have already reinstalled Dapper, I forgot to mention: everything started after I tried to install VMPlayer while VMServer was already installed.
I believe they are conflicting with each other, because I couldn't run the Server after installing the Player. And that's why I tried to uninstall the Player.
After that, as I didn't have time to remove Player by hand, I just reinstalled the whole system.

Unfortunately, I think that I can't be of any help. :neutral:

---

### Post by leona on 2007-01-04
anyone else have ideas how I can clear / clean this up, I don't really want to ahve to reinstall Ubuntu, if I was to do that, I'd go back to 32 bit :)

---

### Post by beamo on 2007-01-04
I had similar problems. You need to remove a folder from your previous vmware player installation:

 /etc/vmware

I couldn't install vmware server myself until I did this. Now that it is installed, it works beautifully.

---

### Post by leona on 2007-01-04
checked, I don't have a /etc/vmware dir.

---

### Post by beamo on 2007-01-05
Did you try uninstalling vmware player and then searching your filesystem for the term "vmware" and then deleting every directory and file that the search finds?

---

### Post by leona on 2007-01-07
err ya, was this the wrong thing to do?  One of the early posts told me to delete stuff out of my etc/ folder.

---

### Post by mlamelas on 2007-01-09
I had the same problem with installing vmware, which did not install correctly (apparently the problem is that the installation routine requires user acceptance of a EULA, and apt-get has no ability to obtain user input). I also had the same problems trying to uninstall the imcomplete installation, and had the same error messages. What finally worked to get rid of vmware-player was:

sudo dpkg --remove --force-remove-reinstreq vmware-player

That got rid of the bad installation. I am still trying to figure out how to get just the player installed.

Mel

---

### Post by leona on 2007-01-10
> **mlamelas said:**
> I had the same problem with installing vmware, which did not install correctly (apparently the problem is that the installation routine requires user acceptance of a EULA, and apt-get has no ability to obtain user input). I also had the same problems trying to uninstall the imcomplete installation, and had the same error messages. What finally worked to get rid of vmware-player was:

sudo dpkg --remove --force-remove-reinstreq vmware-player

That got rid of the bad installation. I am still trying to figure out how to get just the player installed.

Mel
Hi mlamelas, was really hoping this would fix it but instead I got this 
> 
leona@leona-amd64-3Ghz:~$ sudo dpkg --remove --force-remove-reinstreq vmware-player
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 90056 files and directories currently installed.)
Removing vmware-player ...
/etc/init.d/vmware-player: line 171: vmware_product_name: command not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
/etc/init.d/vmware-player: line 171: vmware_product_name: command not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player

It doesn't want to go !

---

### Post by dj1120 on 2007-01-10
I am having the same problem uninstalling vmware in additon when I try to delete the vmware folder out of etc I get a msg say I don't have pemission anyone know how to change permissions for this folder?

---

### Post by leona on 2007-01-11
you can remove the directory as root "su root" or "sudo rmdir" but that'll not fix the problem, well it didn't for me anyway.  Seems to be a problem with the removal script.

---

### Post by beamo on 2007-01-13
leona, now that you have searched for and removed all vmware files/directories you are still unable to do a new install? I had vmware player installed via automatix and couldn't get vmware server to install until I removed all that stuff. Once I did that, it installed without a problem. Even though the uninstall script gives you errors have you tried to do a new install over it?

---

### Post by leona on 2007-01-13
Oh dear, I thought I had cleared them all out, would appear I have some left, can you tell me if these are safe to remove.
```

/etc/init.d/vmware-player
/etc/rc0.d/K20vmware-player
/etc/rc1.d/K20vmware-player
/etc/rc2.d/S20vmware-player
/etc/rc3.d/S20vmware-player
/etc/rc4.d/S20vmware-player
/etc/rc5.d/S20vmware-player
/etc/rc6.d/K20vmware-player
/usr/bin/vmware-config-network.pl
/usr/bin/vmware-ping
/usr/lib/xorg/modules/drivers/vmware_drv.so
/usr/lib/vmware-player
/usr/lib/vmware-player/bin-debug/vmware-vmx
/usr/lib/vmware-player/bin/vmware-vmx
/usr/lib/vmware-player/messages/ja/vmware.vmsg
/usr/lib/vmware-player/share/pixmaps/vmware-player.png
/usr/share/app-install/desktop/vmware-player.desktop
/usr/share/app-install/icons/_usr_share_pixmaps_vmware-player.png
/usr/share/applications/vmware-player.desktop
/usr/share/doc/vmware-player-kernel-modules-2.6.15-26
/usr/share/doc/vmware-player-kernel-modules
/usr/share/doc/xserver-xorg-driver-vmware
/usr/share/doc/vmware-player-kernel-modules-2.6.15-27
/usr/share/doc/vmware-player
/usr/share/icons/hicolor/48x48/apps/vmware-player.png
/usr/share/icons/hicolor/48x48/mimetypes/gnome-mime-application-x-vmware-snapshot.png
/usr/share/icons/hicolor/48x48/mimetypes/application-x-vmware-snapshot.png
/usr/share/icons/hicolor/48x48/mimetypes/gnome-mime-application-x-vmware-team.png
/usr/share/icons/hicolor/48x48/mimetypes/application-x-vmware-team.png
/usr/share/icons/hicolor/48x48/mimetypes/application-x-vmware-vmfoundry.png
/usr/share/icons/hicolor/48x48/mimetypes/application-x-vmware-vmdisk.png
/usr/share/icons/hicolor/48x48/mimetypes/gnome-mime-application-x-vmware-vmfoundry.png
/usr/share/icons/hicolor/48x48/mimetypes/gnome-mime-application-x-vmware-vmdisk.png
/usr/share/icons/hicolor/48x48/mimetypes/application-x-vmware-vm.png
/usr/share/icons/hicolor/48x48/mimetypes/gnome-mime-application-x-vmware-vm.png
/usr/share/man/man4/vmware.4.gz
/usr/share/mime/application/x-vmware-vmdisk.xml
/usr/share/mime/application/x-vmware-vm.xml
/usr/share/mime/application/x-vmware-vmfoundry.xml
/usr/share/mime/application/x-vmware-snapshot.xml
/usr/share/mime/application/x-vmware-team.xml
/usr/share/mime/packages/vmware-player.xml
/var/lib/dpkg/info/vmware-player-kernel-modules-2.6.15-26.postinst
/var/lib/dpkg/info/vmware-player-kernel-modules-2.6.15-26.list
/var/lib/dpkg/info/vmware-player-kernel-modules-2.6.15-26.postrm
/var/lib/dpkg/info/vmware-player-kernel-modules-2.6.15-26.md5sums
/var/lib/dpkg/info/vmware-player-kernel-modules.md5sums
/var/lib/dpkg/info/vmware-player-kernel-modules.list
/var/lib/dpkg/info/vmware-player.templates
/var/lib/dpkg/info/vmware-player.list
/var/lib/dpkg/info/vmware-player.postinst
/var/lib/dpkg/info/vmware-player.preinst
/var/lib/dpkg/info/vmware-player.prerm
/var/lib/dpkg/info/vmware-player.postrm
/var/lib/dpkg/info/vmware-player.conffiles
/var/lib/dpkg/info/vmware-player.md5sums
/var/lib/dpkg/info/xserver-xorg-driver-vmware.list
/var/lib/dpkg/info/xserver-xorg-driver-vmware.md5sums
/var/lib/dpkg/info/vmware-player-kernel-modules-2.6.15-27.postinst
/var/lib/dpkg/info/vmware-player-kernel-modules-2.6.15-27.list
/var/lib/dpkg/info/vmware-player-kernel-modules-2.6.15-27.postrm
/var/lib/dpkg/info/vmware-player-kernel-modules-2.6.15-27.md5sums

```
Oh and is there a way I can remove them in one go without having to do it file by file?
Thanks,.

---

### Post by arnieboy on 2007-01-15
This is a case of a broken post installation file. Try the following:
```
sudo rm -f /var/lib/dpkg/info/vmware-player.postinst
sudo apt-get remove vmware-player
```
and check to see if the error appears again.
If its **not fixed**, try the following:```

sudo rm -f /var/lib/dpkg/info/vmware-player.postrm
sudo apt-get remove vmware-player
```
The vmware-player package is broken in Ubuntu Multiverse.

---

### Post by gmr on 2007-01-17
Hi, I have the same problem. I try all the things that have been wrote in the topic. 

What else can I do?

---

### Post by arnieboy on 2007-01-17
if u have followed the directions in my last post, try the following:
```
sudo rm -f /var/lib/dpkg/info/vmware-player.prerm
sudo apt-get remove vmware-player
sudo apt-get update
```

---

### Post by gmr on 2007-01-17
Oh, great it works! Thank you very much :)

---

### Post by leona on 2007-01-19
I'm sorry this still is not working my end.  This is the output I get
```

** sudo rm -f /var/lib/dpkg/info/vmware-player.prerm**
>
**sudo apt-get remove vmware-player**
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  vmware-player
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.0MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing vmware-player (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
leona@leona-amd64-3Ghz:~$ Errors were encountered while processing:
 vmware-player

```

---

### Post by arnieboy on 2007-01-19
what version of ubuntu are you using? (Dapper/Edgy) amd64/i386 ?

---

### Post by arnieboy on 2007-01-19
you need to make sure you have removed all the files listed below:
```
sudo rm -f /var/lib/dpkg/info/vmware-player.prerm
sudo rm -f /var/lib/dpkg/info/vmware-player.postinst
sudo rm -f /var/lib/dpkg/info/vmware-player.postrm
```
and then do
```
sudo apt-get remove vmware-player
```
If it still doesnt work, we will try something else.

---

### Post by John Jason Jordan on 2007-01-19
I have decided I want to try vmware-player, but I'm not sure which modules to install. On my Dapper amd-64 computer Synaptic lists:

vmware-player
vmware-player-kernel-modules 2.6.15.10-10 (dependency package)
vmware-player-kernel-modules 2.6.15.10-6
vmware-player-kernel-modules 2.6.15.10-7
vmware-player-kernel-modules 2.6.15.10-9
vmware-player-kernel-modules 2.6.15.10-10
vmware-player-kernel-source

I'm guessing I want vmware-player, and the two module packages ending in -10. But, considering the number of people here with messed up installations, I thought it would be intelligent to ask first. ;)

---

### Post by leona on 2007-01-19
> **arnieboy said:**
> you need to make sure you have removed all the files listed below:
```
sudo rm -f /var/lib/dpkg/info/vmware-player.prerm
sudo rm -f /var/lib/dpkg/info/vmware-player.postinst
sudo rm -f /var/lib/dpkg/info/vmware-player.postrm
```
and then do
```
sudo apt-get remove vmware-player
```
If it still doesnt work, we will try something else.
Sorry Arnieboy still no joy.
```

leona@leona-amd64-3Ghz:/$ sudo rm -f /var/lib/dpkg/info/vmware-player.prerm
leona@leona-amd64-3Ghz:/$ sudo rm -f /var/lib/dpkg/info/vmware-player.postinst
leona@leona-amd64-3Ghz:/$ sudo rm -f /var/lib/dpkg/info/vmware-player.postrm
leona@leona-amd64-3Ghz:/$ sudo apt-get remove vmware-player
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  vmware-player
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.0MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing vmware-player (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
leona@leona-amd64-3Ghz:/$ Errors were encountered while processing:
 vmware-player

```
it just hangs at this point.  If I press return it goes back to a prompt.
I'm using 6.06 LTS  64bit Ubuntu.

---

### Post by arnieboy on 2007-01-19
ok try the following:
```
wget http://mirrors.kernel.org/ubuntu/pool/multiverse/v/vmware-player/vmware-player_1.0.1-4_amd64.deb
sudo dpkg -i vmware-player_1.0.1-4_amd64.deb
sudo rm -f /var/lib/dpkg/info/vmware-player.prerm
sudo rm -f /var/lib/dpkg/info/vmware-player.postrm
sudo apt-get remove vmware-player
sudo apt-get update
```

---

### Post by leona on 2007-01-20
> **arnieboy said:**
> ok try the following:
```
wget http://mirrors.kernel.org/ubuntu/pool/multiverse/v/vmware-player/vmware-player_1.0.1-4_amd64.deb
sudo dpkg -i vmware-player_1.0.1-4_amd64.deb
sudo rm -f /var/lib/dpkg/info/vmware-player.prerm
sudo rm -f /var/lib/dpkg/info/vmware-player.postrm
sudo apt-get remove vmware-player
sudo apt-get update
```

Hey thanks muchy arnieboy, that seemed to do the trick.  Much thanks to you I have 1 less problem to deal with :) thanks! :)

---

### Post by hellmet on 2007-02-05
> **beamo said:**
> I had similar problems. You need to remove a folder from your previous vmware player installation:

 /etc/vmware

I couldn't install vmware server myself until I did this. Now that it is installed, it works beautifully.

Thanks for that tip beamo. Worked here):P

---

### Post by tszanon on 2007-02-05
> **John Jason Jordan said:**
> I have decided I want to try vmware-player, but I'm not sure which modules to install. On my Dapper amd-64 computer Synaptic lists:

vmware-player
vmware-player-kernel-modules 2.6.15.10-10 (dependency package)
vmware-player-kernel-modules 2.6.15.10-6
vmware-player-kernel-modules 2.6.15.10-7
vmware-player-kernel-modules 2.6.15.10-9
vmware-player-kernel-modules 2.6.15.10-10
vmware-player-kernel-source

I'm guessing I want vmware-player, and the two module packages ending in -10. But, considering the number of people here with messed up installations, I thought it would be intelligent to ask first. ;)

After having these problems myself, I would not install vmware-player until it is updated in the repositories. I suggest that you download vmware-server from [www.vmware.com]("http://www.vmware.com") (around 100MB) and install from the tarball. It works perfectly, but does not have any hardware accelaration (no 3D games :( )

---

### Post by Saubazi on 2007-02-09
My vmware-player has some problem:

This sort of hints me that it did not go all right:

Starting VMware services:
Virtual machine monitor done
Virtual ethernet done
Bridged networking on /dev/vmnet0 failed
Host-only networking on /dev/vmnet1 (background) done
Host-only networking on /dev/vmnet8 (background) done
NAT service on /dev/vmnet8 failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by vince1027 on 2007-02-12
I also had the same problem. What I did was, uninstall vmware player(as stated) including the /etc/vmware folder.

Then to make the installation successful, download the .tar package from vmware's official site. And follow the guide provided above:
which is also here:
[https://help.ubuntu.com/community/VMware/Player?action=show&redirect=VMWarePlayerAndWindowsHOWTO](https://help.ubuntu.com/community/VMware/Player?action=show&redirect=VMWarePlayerAndWindowsHOWTO)

---

### Post by joesnow on 2007-02-14
I had same issue as Saubazi

i just did  
rm -rf /var/lib/dpkg/info/vm*  
then 
apt-get remove vmware-player

and then it worked, cuz it had vmware-player-kernel-module*  files in /var/lib/dpkg/info/ causing all the fuss.

now it's finally gone

---

### Post by leona on 2007-02-22
my VMplayer has been working fine, but now I get the following error when I try to load it
[quote=vmplayer]"Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded."
What does this mean and how can I fix it?[/quote]
Arr, I think this might have something to do with the new kernal update, I'll try an uninstall and reinstall.

---

### Post by tszanon on 2007-02-23
> **leona said:**
> my VMplayer has been working fine, but now I get the following error when I try to load it

Arr, I think this might have something to do with the new kernal update, I'll try an uninstall and reinstall.

Before trying to reinstall it, try reconfiguring vmware. I think the command is:
```
sudo vmware-configure.pl
```

Or something like that, I don't really remember. It's the same configuration script that is run after installation.
This configuration script must be rerun after each kernel-update, so it will recompile the modules to fit in the current kernel.

---

### Post by leona on 2007-02-24
When I try to install I get
```

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player

```
also can not fine that 'configure' script anywhere :(

---

### Post by tszanon on 2007-02-24
Sorry, I didn't notice you were talking about vmware PLAYER, not vmware SERVER. The configure script surely is available for the server, but I think that the player does not have it.

---

### Post by leona on 2007-03-01
It doesn't work with the latest kernal, so I run it with .27 not .28 and it works fine.  So guess will have to wait till vmware bring out a player that works with kernal .28.

---

### Post by helliewm on 2007-03-02
> just did
rm -rf /var/lib/dpkg/info/vm*
then
apt-get remove vmware-player

This works thanks ever so much.

Helen

---

### Post by kevpatts on 2007-03-04
I've finally got it fully removed. Where can I find a version that doesn't give me an error about /dev/vmmon?

---

### Post by joselin on 2007-03-06
This is how i solve it. 

I changed in /usr/bin/vmware-config-network.pl the line 4337:
```
db_add_answer('VNET_' . $vHubNr . '_INTERFACE', $ethIf);
```
with the following:
```
db_add_answer('VNET_' . $vHubNr . '_INTERFACE', **'eth0'**);
```

With this change I ensure that eth0 will be the interface that vmware will use instead of ath0 that were selected by default and that didn't work.

After that, you should apt-get upgrade without errors.

---

### Post by worapongni on 2007-03-12
First I am newbie of Ubuntu. If I suggest anything wrong, please advise me. I also have the same problem with everyone. But I solve by using these commands.

1. Check VMware in your machine including the configuration by using this command.
- dpkg -l| grep vmware-player

2. Delete all the file inside.
- apt-get remove vmware-player

3. Also, remove config file inside too. (rc)
- dpkg --purge vmware-player
Maybe this step you have to remove /etc/vmware

4. Install vmware-player again, and everything is running fine.

---

### Post by kevpatts on 2007-03-12
If I do:
sudo apt-get remove vmware-player
it removes my X.org too. Not wanted!

---

### Post by Skeletron on 2007-03-16
If you edit /var/lib/dpkg/info/vmware-player.prerm and just comment out all the lines, or put "exit" as the first line in it, then you will be able to remove vmware-player completely using the package manager.

---

### Post by kevpatts on 2007-03-16
thanks man, but having bigger problems at the moment!
[http://ubuntuforums.org/showthread.php?t=385790](http://ubuntuforums.org/showthread.php?t=385790)

---

### Post by ahmatti on 2007-03-16
> **joesnow said:**
> 

rm -rf /var/lib/dpkg/info/vm*  
then 
apt-get remove vmware-player



This did the trick for me as well ! :)

---

