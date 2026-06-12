---
title: "PlayonLinux stuck at creating virtual drive (Ubuntu 18.04)"
date: 2018-08-19
forum: Wine
---

### Post by monkeybrain20122 on 2018-08-19
POL appears to be completely broken in Bionic. 

When creating a new virtual drive with any wine version other than default, POL got stuck in creating virtual drive with these errors even though all freetype packages are installed (including i386 ones)

```
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
http://www.freetype.org
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
http://www.freetype.org
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
http://www.freetype.org
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
http://www.freetype.org
err:ole:marshal_object couldn't get IPSFactory buffer for interface {00000131-0000-0000-c000-000000000046}
err:ole:marshal_object couldn't get IPSFactory buffer for interface {6d5140c1-7436-11ce-8034-00aa006009fa}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80004002
err:ole:CoMarshalInterface Failed to marshal the interface {6d5140c1-7436-11ce-8034-00aa006009fa}, 80004002
err:ole:get_local_server_stream Failed: 80004002
err:ole:marshal_object couldn't get IPSFactory buffer for interface {00000131-0000-0000-c000-000000000046}
err:ole:marshal_object couldn't get IPSFactory buffer for interface {6d5140c1-7436-11ce-8034-00aa006009fa}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80004002
err:ole:CoMarshalInterface Failed to marshal the interface {6d5140c1-7436-11ce-8034-00aa006009fa}, 80004002
err:ole:get_local_server_stream Failed: 80004002
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
http://www.freetype.org
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
http://www.freetype.org
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
http://www.freetype.org
err:syslink:SYSLINK_SetFont Failed to create link font!
```

Following this[ thread]("https://forum.manjaro.org/t/solved-playonlinux-stuck-at-please-wait-while-the-virtual-drive-is-being-created/21924") I removed all libz.so* from POL's wine versions, the FreeType not found errors are gone, but wine crashes 100% when creating new virtual drive
```

wine: Unhandled page fault on read access to 0x00000004 at address 0x7e83f211 (thread 0013), starting debugger...
err:seh:start_debugger Couldn't start debugger ("winedbg --auto 18 84") (2)
Read the Wine Developers Guide on how to set up winedbg or another debugger
wine: Unhandled page fault on read access to 0x00000004 at address 0x7e8c5211 (thread 000b), starting debugger...
err:seh:start_debugger Couldn't start debugger ("winedbg --auto 10 100") (2)
Read the Wine Developers Guide on how to set up winedbg or another debugger
err:ole:marshal_object couldn't get IPSFactory buffer for interface {00000131-0000-0000-c000-000000000046}
err:ole:marshal_object couldn't get IPSFactory buffer for interface {6d5140c1-7436-11ce-8034-00aa006009fa}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80004002
err:ole:CoMarshalInterface Failed to marshal the interface {6d5140c1-7436-11ce-8034-00aa006009fa}, 80004002
err:ole:get_local_server_stream Failed: 80004002
/home/bee/.PlayOnLinux//wine/linux-x86/1.9.4/bin//wineserver
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
wine: Unhandled page fault on read access to 0x00000004 at address 0x7e678211 (thread 001b), starting debugger...
Could not load wine-gecko. HTML rendering will be disabled.
[POL_LoadVar_PROGRAMFILES] Message: Getting Program Files name
[POL_Wine] Message: Running wine-1.9.4 cmd /c echo %ProgramFiles% (Working directory : /usr/share/playonlinux/python)
[POL_Wine] Message: Notice: PlayOnLinux deliberately disables winemenubuilder. See http://www.playonlinux.com/fr/page-26-Winemenubuilder.html
[POL_Wine] Message: Wine return: 0
[POL_Wine] Message: Running wine-1.9.4 winecfg (Working directory : /home/mb/.PlayOnLinux/wineprefix/zbrush)
[POL_Wine] Message: Notice: PlayOnLinux deliberately disables winemenubuilder. See http://www.playonlinux.com/fr/page-26-Winemenubuilder.html
wine: Unhandled page fault on read access to 0x00000004 at address 0x7e849211 (thread 0022), starting debugger...
wine: Unhandled page fault on read access to 0x00000004 at address 0x7e487211 (thread 0009), starting debugger...
winedbg: Internal crash at 0x7e6eb211
[POL_Wine] Error: Wine seems to have crashed
```

So POL is completely useless in 18.04. In 16.04 it works with no issue on same machine.

Any idea?

Thanks.

---

### Post by TheFu on 2018-08-20
Is POL a snap?

---

### Post by kc1di on 2018-08-20
the problem is that 18.04 needs the 32 bit libs which are missing 
you need to go to a terminal and enter this command ```
sudo dpkg --add-architecture i386
``` 
Then ```
sudo apt udate
```
and install ```
sudo apt install wine32
```
try running playonlinux again. 

The problem is that ubuntu 18.04 removed the 32bit libraries from the default wine install. Good luck.

---

### Post by monkeybrain20122 on 2018-08-20
> **TheFu said:**
> Is POL a snap?

No, it is not a snap.

---

### Post by monkeybrain20122 on 2018-08-20
> **kc1di said:**
> the problem is that 18.04 needs the 32 bit libs which are missing 
you need to go to a terminal and enter this command ```
sudo dpkg --add-architecture i386
``` 
Then ```
sudo apt udate
```
and install ```
sudo apt install wine32
```
try running playonlinux again. 

The problem is that ubuntu 18.04 removed the 32bit libraries from the default wine install. Good luck.

wine32 and all relevant 32 bit libs are already installed.

---

### Post by tnt533 on 2018-08-25
Piling on here. I have the same exact situation above. Seems to be somewhat of a larger issue than just us two as there is a ton of stuff on other forums suggesting various fixes. I have tried with both the version of Playonlinux from the repo and also downloaded directly from the website. I have the architecture set and all the required things above done and still no joy.

---

### Post by Babaian on 2018-09-19
I had this problem and had the fonts correctly installed.

In PlayOnLinux I selected Excel 2010, clicked Configure, changed Wine version from `1.7.48` to `System`.

Now the fonts are being detected and Office is working.

---

### Post by monkeybrain20122 on 2018-09-20
> **Babaian said:**
> I had this problem and had the fonts correctly installed.

In PlayOnLinux I selected Excel 2010, clicked Configure, changed Wine version from `1.7.48` to `System`.

Now the fonts are being detected and Office is working.

Yeah I know that it works for system version of wine, but it seems that it is the only wine version that works. That kind of defeats the purpose of POL, which is to let you use different versions of wine. Otherwise you can just use wine and do away with POL.

---

### Post by Gedagtes on 2019-01-02
> **tnt533 said:**
> Piling on here. I have the same exact situation above. Seems to be somewhat of a larger issue than just us two as there is a ton of stuff on other forums suggesting various fixes. I have tried with both the version of Playonlinux from the repo and also downloaded directly from the website. I have the architecture set and all the required things above done and still no joy.

Same problem here. 16.04 worked fine . Ubuntu 18.04 screaming for  fonts

```
PlayOnLinux debugging tool (v4.2.12)
-----------------------------------------------
Debugging: Microsoft Pinball

Warning: This is a PlayOnLinux script logfile. It does not contain everything that happened in your program\'s virtual drive (wineprefix)
Please do not use this logfile on winehq forum, this logfile is not interesting for wine debugging.

Date: 01/02/19 20:50:04

> uname -a
  Linux coenraad-All-Series 4.15.0-43-generic #46-Ubuntu SMP Thu Dec 6 14:45:28 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
> lsb_release -a
  
> wine --version (Be careful; this version might not be the version used
in the script. Read the content of this file for more information)
  wine-3.0 (Ubuntu 3.0-1ubuntu1)
> glxinfo \| grep rendering
  direct rendering: Yes
> glxinfo \| grep renderer
      GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
Extended renderer info (GLX_MESA_query_renderer):
OpenGL renderer string: Mesa DRI Intel(R) Haswell 
> OpenGL libs
  check_dd_x86 missing, test skipped
  check_dd_amd64 missing, test skipped
> export
  declare -x AMD64_COMPATIBLE="True"
declare -x APPLICATION_TITLE="PlayOnLinux"
declare -x CLUTTER_IM_MODULE="xim"
declare -x COLORTERM="truecolor"
declare -x DBUS_SESSION_BUS_ADDRESS="unix:path=/run/user/1000/bus"
declare -x DEBIAN_PACKAGE="TRUE"
declare -x DESKTOP="/home/coenraad/Desktop"
declare -x DESKTOP_SESSION="ubuntu"
declare -x DISPLAY=":0"
declare -x DONT_MONITOR="1"
declare -x DYLDPATH_ORIGIN=""
declare -x DYLD_LIBRARY_PATH=""
declare -x GDMSESSION="ubuntu"
declare -x GECKO_SITE="http://wine.playonlinux.com/gecko"
declare -x GJS_DEBUG_OUTPUT="stderr"
declare -x GJS_DEBUG_TOPICS="JS ERROR;JS LOG"
declare -x GNOME_DESKTOP_SESSION_ID="this-is-deprecated"
declare -x GNOME_SHELL_SESSION_MODE="ubuntu"
declare -x GNOME_TERMINAL_SCREEN="/org/gnome/Terminal/screen/01f58952_514e_412c_aa1e_d5c68856611b"
declare -x GNOME_TERMINAL_SERVICE=":1.246"
declare -x GNUPGHOME="/home/coenraad/.PlayOnLinux//gpg"
declare -x GPG_AGENT_INFO="/run/user/1000/gnupg/S.gpg-agent:0:1"
declare -x GTK_IM_MODULE="ibus"
declare -x GTK_MODULES="gail:atk-bridge"
declare -x G_FILENAME_ENCODING="UTF-8"
declare -x HOME="/home/coenraad"
declare -x IGNORE_ICON_DIR="false"
declare -x IM_CONFIG_PHASE="2"
declare -x LANG="en_ZA.UTF-8"
declare -x LD_32_PATH_ORIGIN=""
declare -x LD_LIBRARY_PATH=""
declare -x LD_PATH_ORIGIN=""
declare -x LESSCLOSE="/usr/bin/lesspipe %s %s"
declare -x LESSOPEN="| /usr/bin/lesspipe %s"
declare -x LOGNAME="coenraad"
declare -x LS_COLORS="rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.zst=01;31:*.tzst=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.wim=01;31:*.swm=01;31:*.dwm=01;31:*.esd=01;31:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:"
declare -x MACHTYPE="x86_64-pc-linux-gnu"
declare -x MD5_COMMAND="md5sum"
declare -x MONO_SITE="http://wine.playonlinux.com/mono"
declare -x OLDPWD="/home/coenraad/.PlayOnLinux/plugins"
declare -x OS_NAME="linux"
declare -x OpenGL32="1"
declare -x OpenGL64="1"
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/usr/lib/wine"
declare -x PATH_ORIGIN="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/usr/lib/wine"
declare -x PLAYONLINUX="/usr/share/playonlinux"
declare -x POL_ARCH="x86"
declare -x POL_COOKIE="IdCqkj5VwfvVw8kxAiPM"
declare -x POL_CURL="curl"
declare -x POL_DNS="playonlinux.com"
declare -x POL_HOST="127.0.0.1"
declare -x POL_ID="54412089"
declare -x POL_LANG="en"
declare -x POL_OS="Linux"
declare -x POL_PORT="30000"
declare -x POL_PYTHON="python"
declare -x POL_SetupWindow_ID="27072"
declare -x POL_TERM="x-terminal-emulator"
declare -x POL_UPTODATE="FALSE"
declare -x POL_USER_ARCH="x86"
declare -x POL_USER_ROOT="/home/coenraad/.PlayOnLinux/"
declare -x POL_WGET="env LD_LIBRARY_PATH=\"\" wget --prefer-family=IPv4 -q"
declare -x PWD="/usr/share/playonlinux/python"
declare -x QT4_IM_MODULE="xim"
declare -x QT_ACCESSIBILITY="1"
declare -x QT_IM_MODULE="ibus"
declare -x REPERTOIRE="/home/coenraad/.PlayOnLinux/"
declare -x SCRIPTID="Microsoft Pinball"
declare -x SED="sed"
declare -x SESSION_MANAGER="local/coenraad-All-Series:@/tmp/.ICE-unix/908,unix/coenraad-All-Series:/tmp/.ICE-unix/908"
declare -x SETUPWINDOW_INIT="true"
declare -x SHELL="/bin/bash"
declare -x SHLVL="4"
declare -x SITE="http://repository.playonlinux.com"
declare -x SSH_AGENT_PID="1014"
declare -x SSH_AUTH_SOCK="/run/user/1000/keyring/ssh"
declare -x TERM="xterm-256color"
declare -x TEXTDOMAIN="pol"
declare -x TEXTDOMAINDIR="/usr/share/locale/"
declare -x TITLE="Microsoft Pinball"
declare -x TITRE="PlayOnLinux"
declare -x UBUNTU_MENUPROXY="0"
declare -x USER="coenraad"
declare -x USERNAME="coenraad"
declare -x VERSION="4.2.12"
declare -x VTE_VERSION="5202"
declare -x WGETRC="/home/coenraad/.PlayOnLinux//configurations/wgetrc"
declare -x WINDOWPATH="1"
declare -x WINEDLLOVERRIDES="winemenubuilder.exe=d"
declare -x WINEPREFIX="/home/coenraad/.PlayOnLinux//wineprefix/default"
declare -x WINE_SITE="http://wine.playonlinux.com/binaries"
declare -x WorkingDirectory="/home/coenraad"
declare -x XAUTHORITY="/run/user/1000/gdm/Xauthority"
declare -x XDG_CONFIG_DIRS="/etc/xdg/xdg-ubuntu:/etc/xdg"
declare -x XDG_CURRENT_DESKTOP="ubuntu:GNOME"
declare -x XDG_DATA_DIRS="/usr/share/ubuntu:/usr/local/share:/usr/share:/var/lib/snapd/desktop"
declare -x XDG_MENU_PREFIX="gnome-"
declare -x XDG_RUNTIME_DIR="/run/user/1000"
declare -x XDG_SEAT="seat0"
declare -x XDG_SESSION_DESKTOP="ubuntu"
declare -x XDG_SESSION_ID="1"
declare -x XDG_SESSION_TYPE="x11"
declare -x XDG_VTNR="1"
declare -x XMODIFIERS="@im=ibus"


01/02/19 20:50:07 - [POL_Wine_SelectPrefix] Message: Selecting prefix: MicrosoftPinball
01/02/19 20:50:07 - [POL_System_SetArch] Message: POL_ARCH set to x86
01/02/19 20:50:07 - [POL_Wine_PrefixCreate] Message: Setting POL_WINEVERSION to 1.7.37
01/02/19 20:50:07 - [POL_Wine_PrefixCreate] Message: Creating prefix (1.7.37)...
01/02/19 20:50:07 - [POL_Wine_PrefixCreate] Message: Prefix already exists
01/02/19 20:50:17 - [POL_SetupWindow_menu] Message: menu answer: Erase (virtual drive content will be lost)
01/02/19 20:50:17 - [POL_Wine_PrefixCreate] Message: Erase Prefix
01/02/19 20:50:17 - [POL_Wine_PrefixCreate] Message: Using wine 1.7.37
01/02/19 20:50:17 - [POL_Wine_InstallVersion] Message: Installing wine version path: 1.7.37, x86
01/02/19 20:50:18 - [POL_Config_PrefixWrite] Message: Prefix config write: ARCH x86
01/02/19 20:50:18 - [POL_Config_PrefixWrite] Message: Prefix config write: VERSION 1.7.37
01/02/19 20:50:18 - [POL_Wine] Message: Running wine-1.7.37 --version (Working directory : /home/coenraad/.PlayOnLinux/shortcuts)
01/02/19 20:50:18 - [POL_Wine] Message: Notice: PlayOnLinux deliberately disables winemenubuilder. See [http://www.playonlinux.com/fr/page-26-Winemenubuilder.html](http://www.playonlinux.com/fr/page-26-Winemenubuilder.html)
wine-1.7.37
01/02/19 20:50:18 - [POL_Wine] Message: Wine return: 0
01/02/19 20:50:27 - [POL_LoadVar_PROGRAMFILES] Message: Getting Program Files name
01/02/19 20:50:27 - [POL_Wine] Message: Running wine-1.7.37 cmd /c echo %ProgramFiles% (Working directory : /home/coenraad/.PlayOnLinux/shortcuts)
01/02/19 20:50:28 - [POL_Wine] Message: Notice: PlayOnLinux deliberately disables winemenubuilder. See [http://www.playonlinux.com/fr/page-26-Winemenubuilder.html](http://www.playonlinux.com/fr/page-26-Winemenubuilder.html)
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
[http://www.freetype.org](http://www.freetype.org)
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
[http://www.freetype.org](http://www.freetype.org)
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
[http://www.freetype.org](http://www.freetype.org)
C:\Program Files
01/02/19 20:50:28 - [POL_Wine] Message: Wine return: 0
01/02/19 20:50:31 - [POL_Call] Message: Calling POL_Install_LunaTheme
01/02/19 20:50:31 - [POL_Call] Message: ----- Starting function POL_Install_LunaTheme -----
01/02/19 20:50:31 - [POL_GPG_auth_script] Message: Checking signature of POL_Install_LunaTheme
01/02/19 20:50:31 - [POL_GPG_install_key] Message: Importing PlayOnLinux public key
01/02/19 20:50:31 - [POL_Source] Message: POL GPG : Good signature
01/02/19 20:50:31 - [POL_Download_Resource] Message: Downloading resource [http://repository.playonlinux.com/divers/luna.msstyles](http://repository.playonlinux.com/divers/luna.msstyles)
01/02/19 20:50:31 - [POL_Download_Resource] Message: Resource already present
01/02/19 20:50:31 - [POL_Download_Resource] Message: Downloading resource [http://repository.playonlinux.com/divers/luna.reg](http://repository.playonlinux.com/divers/luna.reg)
01/02/19 20:50:31 - [POL_Download_Resource] Message: Resource already present
01/02/19 20:50:31 - [POL_Wine] Message: Running wine-1.7.37 regedit /home/coenraad/.PlayOnLinux//ressources/luna.reg (Working directory : /home/coenraad/.PlayOnLinux/ressources)
01/02/19 20:50:31 - [POL_Wine] Message: Notice: PlayOnLinux deliberately disables winemenubuilder. See [http://www.playonlinux.com/fr/page-26-Winemenubuilder.html](http://www.playonlinux.com/fr/page-26-Winemenubuilder.html)
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
[http://www.freetype.org](http://www.freetype.org)
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
[http://www.freetype.org](http://www.freetype.org)
01/02/19 20:50:32 - [POL_Wine] Message: Wine return: 0
01/02/19 20:50:32 - [POL_Call] Message: ----- Ending function POL_Install_LunaTheme -----
01/02/19 20:50:32 - [POL_Download] Message: Downloading [https://www.dropbox.com/s/2qgtjp7lyegps1w/3d_pinball_for_windows_-_space_cadet.exe?dl=1](https://www.dropbox.com/s/2qgtjp7lyegps1w/3d_pinball_for_windows_-_space_cadet.exe?dl=1)
01/02/19 20:50:47 - [POL_Download] Message: Download MD5 matches
01/02/19 20:50:47 - [POL_System_CheckFS] Message: Checking filesystem for 3d_pinball_for_windows_-_space_cadet.exe
01/02/19 20:50:47 - [POL_Wine] Message: Running wine-1.7.37 3d_pinball_for_windows_-_space_cadet.exe (Working directory : /home/coenraad/.PlayOnLinux/wineprefix/MicrosoftPinball/drive_c)
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
[http://www.freetype.org](http://www.freetype.org)
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
[http://www.freetype.org](http://www.freetype.org)
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
[http://www.freetype.org](http://www.freetype.org)
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
[http://www.freetype.org](http://www.freetype.org)
wine: Unhandled division by zero at address 0x7e96617b (thread 0009), starting debugger...
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
[http://www.freetype.org](http://www.freetype.org)
err:syslink:SYSLINK_SetFont Failed to create link font!
```

---

### Post by mastablasta on 2019-01-19
ok so just tried to install a few things in Pol and since i couldn't google led me here. i am glad i am not the only one. fonts are installed but PoL still wants them. looks like a broken app to me since it is not working as it should. perhaps it should get either get removed from software center or fixed.  also looks like Manjaro has similar issues.

---

### Post by mastablasta on 2019-02-18
Acoording to PoL devs, this happens due to items not working with older wine versions. Apparently updating the script to a working wine version should work. how can we confirm this is due to the script? did anyone manage to troubleshoot this? e.g. manually install with older wine version.

i am still a bit unsure that this is a script issue. particularly since i had exact same issue with different apps. i also see users having same issue with different apps. and if older wine version used to work the script that would use that same older version should still work, right?

[https://www.playonlinux.com/en/topic-16051-POL_stuck_at_creating_virtual_drive_Ubuntu_1804.html](https://www.playonlinux.com/en/topic-16051-POL_stuck_at_creating_virtual_drive_Ubuntu_1804.html)

i found out that as long as i use manual install and latest/default wine version. things would install rather well so far. but i didn't have a need for scripts, so far since i installed gold/platinum rating stuff. was there a major change in wine?

---

