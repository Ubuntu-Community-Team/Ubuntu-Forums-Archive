---
title: "Intuit Quicken 2011 and 2012 Deluxe"
date: 2012-06-07
forum: Wine
---

### Post by Welly Wu on 2012-06-07
I have an ASUS N61JV-X2 notebook PC with 8 GB of dual-channel DDR3 PC-8500 SDRAM and an Intel 2nd Generation MLC NAND FLASH X25-M 160 GB Solid State Drive running Ubuntu 12.04 64 bit Long Term Support. I installed WINE 1.5.5 64 bit and Wine (Gecko) 32 bit. I purchased Intuit Quicken Deluxe 2011 and 2012 from Amazon. I keep getting an error 1063 message stating that I may not have the correct permissions in the target folder in which I am trying to install Quicken Deluxe. I read the WineHQ documentation for Intuit Quicken Deluxe 2011 and 2012 and it says that it has Gold and Silver support respectively.

How do I get Intuit Quicken Deluxe 2011 or 2012 (which I prefer to install) to install correctly?

How do I get Quicken Deluxe to run under WINE?

---

### Post by Mark Phelps on 2012-06-07
You have to install it first.  But ... how well it will work depends on the version you have.

See the link to the WineHQ website page on Quicken below:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=107]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=107")

A gold rating means nearly everyting works; a bronze rating means you're wasting your time trying to install it.

Details can be read by clicking on the test results on the right side of the page.

---

### Post by Toz on 2012-06-07
Here are a set if detailed instructions for installing Quicken 2011. ([http://blog.jdpfu.com/2010/11/29/solved-quicken-2011-working-on-linux]("http://blog.jdpfu.com/2010/11/29/solved-quicken-2011-working-on-linux")). Give them a try.

---

### Post by Welly Wu on 2012-06-07
I set my WINE environment to 32 bit and I tried to install winetricks dotnet20, but it keeps telling me that the ProgramFiles returned an empty string. When I switch back to 64 bit mode, it tells me that 64 bit is not supported.

I still get the same error message while trying to install Intuit Quicken Deluxe 2011.

How do I install dotnet20 using WINE 1.5.5 so that I can install Intuit Quicken Deluxe 2011?

---

### Post by oldos2er on 2012-06-07
Moved to Wine.

---

### Post by Toz on 2012-06-07
> **Welly Wu said:**
> I set my WINE environment to 32 bit and I tried to install winetricks dotnet20, but it keeps telling me that the ProgramFiles returned an empty string. When I switch back to 64 bit mode, it tells me that 64 bit is not supported.

I still get the same error message while trying to install Intuit Quicken Deluxe 2011.

How do I install dotnet20 using WINE 1.5.5 so that I can install Intuit Quicken Deluxe 2011?

Sorry but I don't have a 64-bit install to test this.

To install dotnet20 in wine, assuming the default prefix, from a command line the following should work (though it isn't for you).
```
winetricks dotnet20
```

Can you post the exact commands you are running and the exact wording of the error message? You're not using sudo are you?

---

### Post by Welly Wu on 2012-06-08
This is my exact terminal output:

wellywu@N61JV-X2:~$ winetricks dotnet20
/home/wellywu/bin/winetricks: line 1: syntax error near unexpected token `newline'
/home/wellywu/bin/winetricks: line 1: `<html>'
wellywu@N61JV-X2:~$ wine --version
wine-1.5.5
wellywu@N61JV-X2:~$

I have Ubuntu 12.04 64 bit Long Term Support installed as my default and primary host operating system on my ASUS N61JV-X2 notebook PC.

This is my exact terminal output when I invoke the sudo command:

wellywu@N61JV-X2:~$ sudo winetricks dotnet20
[sudo] password for wellywu: 
------------------------------------------------------
wine cmd.exe /c echo '%ProgramFiles%' returned empty string
------------------------------------------------------
wellywu@N61JV-X2:~$ 


I set env WINEARCH=win32 prior to invoking the sudo command.

WINE HQ tells me that Intuit Quicken Deluxe 2011 has a gold rating for support. It tells me that everything should work right out of the box.

How do I fix this problem so that I can synchronize with my Sovereign Santander and PNC Bank accounts using Intuit Quicken Deluxe 2011 or 2012?

GNUCash does not support Sovereign Santander Bank which is my primary bank. Intuit Quicken Deluxe 2011 and 2012 are much more robust and they support nearly every financial institution.

I need this to work. I can't just rely on Sovereign Santander or PNC Bank's websites to manage my personal finances and investment and savings portfolios. It's too cumbersome and I need a centralized software application to manage my finances.

---

### Post by Welly Wu on 2012-06-08
I typed in set env WINEARCH=win64 and this is my exact output:

wellywu@N61JV-X2:~$ env WINEARCH=win64
SSH_AGENT_PID=3987
GPG_AGENT_INFO=/home/wellywu/.cache/keyring-EWZR6d/gpg:0:1
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=3035fdc45b7555795e599ab80000027a-1339086669.95524-1449046291
WINDOWID=132120582
GNOME_KEYRING_CONTROL=/home/wellywu/.cache/keyring-EWZR6d
USER=wellywu
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lz=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0
XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
SSH_AUTH_SOCK=/home/wellywu/.cache/keyring-EWZR6d/ssh
SESSION_MANAGER=local/N61JV-X2:@/tmp/.ICE-unix/3944,unix/N61JV-X2:/tmp/.ICE-unix/3944
DEFAULTS_PATH=/usr/share/gconf/ubuntu.default.path
XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu:/etc/xdg
PATH=/home/wellywu/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
DESKTOP_SESSION=ubuntu
PWD=/home/wellywu
GNOME_KEYRING_PID=3931
LANG=en_US.UTF-8
MANDATORY_PATH=/usr/share/gconf/ubuntu.mandatory.path
UBUNTU_MENUPROXY=libappmenu.so
COMPIZ_CONFIG_PROFILE=ubuntu
GDMSESSION=ubuntu
HOME=/home/wellywu
SHLVL=2
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=wellywu
XDG_DATA_DIRS=/usr/share/ubuntu:/usr/share/gnome:/usr/local/share/:/usr/share/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-Cp67QOORwH,guid=68387e843829646611a106fe0000002e
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=:0
XDG_CURRENT_DESKTOP=Unity
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/home/wellywu/.Xauthority
OLDPWD=/home/wellywu/Downloads
_=/usr/bin/env
WINEARCH=win64
wellywu@N61JV-X2:~$ set env WINEARCH=win64
wellywu@N61JV-X2:~$ winetricks dotnet20
/home/wellywu/bin/winetricks: line 1: syntax error near unexpected token `newline'
/home/wellywu/bin/winetricks: line 1: `<html>'
wellywu@N61JV-X2:~$

---

### Post by Toz on 2012-06-08
> **Welly Wu said:**
> wellywu@N61JV-X2:~$ sudo winetricks dotnet20
[sudo] password for wellywu: 
------------------------------------------------------
wine cmd.exe /c echo '%ProgramFiles%' returned empty string
------------------------------------------------------

You should not run wine with sudo. See: 7.11 at [http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014]("http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014") and 7.12 to fix.

You also seem to have a problem with your winetricks application. I also notice that it is in your bin directory. I suggest renaming the existing winetricks (so it doesn't interfere) and installing the winetricks from the repositories:
```
mv /home/wellywu/bin/winetricks /home/wellywu/bin/winetricks.BAK
sudo apt-get install winetricks
```
After you've fixed the permission errors, try again without using sudo.

> How do I fix this problem so that I can synchronize with my Sovereign Santander and PNC Bank accounts using Intuit Quicken Deluxe 2011 or 2012?

GNUCash does not support Sovereign Santander Bank which is my primary bank. Intuit Quicken Deluxe 2011 and 2012 are much more robust and they support nearly every financial institution.

I need this to work. I can't just rely on Sovereign Santander or PNC Bank's websites to manage my personal finances and investment and savings portfolios. It's too cumbersome and I need a centralized software application to manage my finances.
I'm not sure about the synchronization piece. I guess once quicken gets installed, you can try and see if it works,

---

### Post by Welly Wu on 2012-06-08
It still does not work. Intuit Quicken Deluxe 2011 keeps telling me  error 1063. It says that I might not have the correct permissions to install into the target folder. I already fixed WINE by following WINE HQ FAQ 7.12.

Here is my output when I type in winetricks dotnet20:

This product does not support 64 bit installations. Setup will now exit.

wellywu@N61JV-X2:~/Ubuntu 64 bit Software Repository$ winetricks dotnet20
Executing w_do_call dotnet20
Executing load_dotnet20
Executing w_do_call fontfix
Executing load_fontfix
Setting Windows version to win2k
Executing winetricks_early_wine regedit C:\windows\Temp\_dotnet20\set-winver.reg
Executing mkdir -p /home/wellywu/.cache/winetricks/dotnet20
Executing unzip -o -q -d /home/wellywu/.wine/dosdevices/c:/windows/syswow64 l_intl.zip
Executing mkdir -p /home/wellywu/.cache/winetricks/dotnet20
Executing wine dotnetfx.exe
fixme:advapi:DecryptFileA "C:\\users\\wellywu\\Temp\\IXP000.TMP\\" 00000000
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:advapi:LsaOpenPolicy ((null),0x33f31c,0x00000001,0x33f344) stub
fixme:advapi:LsaClose (0xcafe) stub
------------------------------------------------------
Note: command 'wine dotnetfx.exe' returned status 26.  Aborting.
------------------------------------------------------
wellywu@N61JV-X2:~/Ubuntu 64 bit Software Repository$

I am getting closer to the solution. How do I get dotnet20 to install correctly now that I have fixed WINE?

---

### Post by Toz on 2012-06-08
> p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
Looks like a known bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/885492]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/885492"). 

Fortunately, there is a workaround: [http://askubuntu.com/questions/127848/wine-cant-find-gnome-keyring-pkcs11-so]("http://askubuntu.com/questions/127848/wine-cant-find-gnome-keyring-pkcs11-so").

---

### Post by Welly Wu on 2012-06-09
I am still getting the same error message:

wellywu@N61JV-X2:~/Ubuntu 64 bit Software Repository$ clear

wellywu@N61JV-X2:~/Ubuntu 64 bit Software Repository$ winetricks dotnet20
Executing w_do_call dotnet20
Executing load_dotnet20
Executing w_do_call fontfix
Executing load_fontfix
Setting Windows version to win2k
Executing winetricks_early_wine regedit C:\windows\Temp\_dotnet20\set-winver.reg
Executing mkdir -p /home/wellywu/.cache/winetricks/dotnet20
Executing unzip -o -q -d /home/wellywu/.wine/dosdevices/c:/windows/syswow64 l_intl.zip
Executing mkdir -p /home/wellywu/.cache/winetricks/dotnet20
Executing wine dotnetfx.exe
fixme:advapi:DecryptFileA "C:\\users\\wellywu\\Temp\\IXP000.TMP\\" 00000000
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:advapi:LsaOpenPolicy ((null),0x33f31c,0x00000001,0x33f344) stub
fixme:advapi:LsaClose (0xcafe) stub
------------------------------------------------------
Note: command 'wine dotnetfx.exe' returned status 26.  Aborting.
------------------------------------------------------
wellywu@N61JV-X2:~/Ubuntu 64 bit Software Repository$

---

### Post by Welly Wu on 2012-06-09
I solved this problem.

I downloaded and I installed CrossOver for Linux from the Ubuntu Software Center. I am using the free 15 day trial. I installed Intuit Quicken Deluxe 2011 successfully. I disabled registration by following the tips and tricks section for Intuit Quicken Deluxe 2011 on the Code Weavers CrossOver Linux website. I synchronized my Sovereign Santander Bank accounts and I backed up my Intuit Quicken Deluxe 2011 file with a unique, strong, complex password. It works.

This works for me. I plan to purchase Code Weavers CrossOver for Linux for $59.99 USD in the next two weeks. This is much easier and simpler than WINE 1.5.5 64 bit. I can afford it.

This thread is solved.

---

### Post by kurt18947 on 2012-06-09
Now if Codeweavers could work their magic with recent versions of Quickbooks they might sell some subscriptions ..............

---

### Post by WhiteSphinx on 2012-07-16
I had Quicken working perfectly but updates were always a problem.  I tied GnuCash, Homebank, and all the other personal finance programs that I could find and none of them felt like quicken until I got MoneyDance.  MoneyDance installs in Linux and it works perfectly. Best of all, it feels like Quicken. I've been using MoneyDance since November, 2011.

---

