---
title: "Can't get my 32bit drivers working right"
date: 2012-03-14
forum: Wine
---

### Post by otherethe on 2012-03-14
Alright heres my problem, I'm trying to run World of Warcraft on Wine, I've ran it many times before.
Here is my Out put

$ wine wow.exe
err:module:load_builtin_dll failed to load .so lib for builtin L"OPENGL32.dll": libGL.so.1: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library OPENGL32.dll (which is needed by L"C:\\Program Files\\World of Warcraft\\wow.exe") failed (error c000007a).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\wow.exe" failed, status c0000135

I've reinstalled my 32bit drivers about 50 times if not more I don't get why it's still looking at the 64bit one
I've uninstalled all my drivers  and reinstalled via .run file newest from nvida.com

---

### Post by dino99 on 2012-03-14
only use genuine ubuntu packages from synaptic archives

---

### Post by otherethe on 2012-03-15
> **dino99 said:**
> only use genuine ubuntu packages from synaptic archives

I did have them installed at first but thats not the prob the prob is the fact that wine is pulling my drivers from /usr/lib and it needs to pull them from /usr/lib32 I need to know how to change it to make it stop looking in /usr/lib I know this is the prob for a fact because i replaced all my 64 bit with 32bit by hand, I had to reinstall after I rebooted but I had one of my 32 bit games working, Warcraft III was the game I had working but seeings how my computer could not restart with the drivers as is I had to reinstall them to get my gui working again, but lets stick to the topic here, how do I force wine to read from /usr/lib32 and not /usr/lib

---

### Post by cwwilson721 on 2012-03-15
You've already been given the answer, whether you LIKE it or not.

Install the Ubuntu Nvidia drivers, and it will work.

Don't, and in _your_ system (which _you_ borked, somehow, because _you_ know better than every other person getting wine/WoW working perfectly), wine/WoW ain't gonna work.

_Your_ choice.

Get it working, THEN change it.

---

### Post by otherethe on 2012-03-15
> **cwwilson721 said:**
> You've already been given the answer, whether you LIKE it or not.

Install the Ubuntu Nvidia drivers, and it will work.

Don't, and in _your_ system (which _you_ borked, somehow, because _you_ know better than every other person getting wine/WoW working perfectly), wine/WoW ain't gonna work.

_Your_ choice.

Get it working, THEN change it.
 
You must not read very well I clearly stated a moment ago I USED the Drivers that are given by Ubuntu, they do 100% the same thing it's lmfao I just told you what the prob is if you would take 2 sec to read and not think YOU know it all, I don't wanna be a jerk so plz don't comment with your none sense before you read all that's been said

---

### Post by cwwilson721 on 2012-03-15
Believe me. I know EXACTLY how to fix your system.

Step-by-step.

> ...I just told you what the prob is if you would take 2 sec to read and not think YOU know it all...

YOU don't know. I do. I don't know it all. [But I REALLY know my Nvidia/Intel drivers, and what your EXACT issue is.]("http://www.linuxquestions.org/questions/slackware-14/a-guide-enabling-3d-acceleration-in-x11-402003/")

[LIST]
[*]Uninstall the Nvidia driver from Nvidia.com ```
sudo nvidia-installer --uninstall
```
[*]Remove the Nvidia Ubuntu drivers (ignore errors)
[*]Reboot
[*]Reinstall Ubuntu Nvidia drivers.
[*]Listen to advice.

THAT is how you install the Ubuntu Nvidia Drivers after you borked them on your own installing the Nvidia.com drivers. 
[/LIST]

---

### Post by otherethe on 2012-03-15
Ya no thanks you clearly have no Idea what you talking about, also I just fixed my problem fyi, anyone else having the same issue as me put this in a text file and save it as *name.sh *name being what you choice,
after you save it cd to the folder you saved it to type in sudo sh *name.sh 

```
  
if test `uname -o` = Solaris
then
    if test ! -w /
    then
        echo "Usage: pfexec sh $0"
        exit 1
    fi

    if test ! `which pkg`
    then
        echo "Only OpenSolaris is supported at this time."    
        exit 1
    fi

    pkg install SUNWaconf SUNWaudh SUNWbison SUNWcups SUNWflexlex SUNWgcc SUNWgit \
    SUNWGlib SUNWgmake SUNWgnome-common-devel SUNWsane-backend SUNWxorg-headers SUNWxwinc
    exit
fi

if test `uname -s` = 'FreeBSD'
then
    if test ! -w /
    then
        echo "Usage: 'sh $0' as root"
        exit 1
    fi

    pkg_add -r bison cups flex git gsm gstreamer-plugins jpeg lcms libGLU \
    libxslt mpg123 openldap-client sane-backends tiff xorg
    exit
fi

if test `uname -s` = 'NetBSD'
then
    if test ! -w /
    then
        echo "Usage: 'sh $0' as root"
        exit 1
    fi

    pkg_add bison cups flex gsm jpeg lcms libxslt mpg123 openldap-client sane-backends scmgit-base tiff
    exit
fi

if test `uname -s` = 'OpenBSD'
then
    if test ! -w /
    then
        echo "You must run $0 as root"
        exit 1
    fi

    if test ! $PKG_PATH
    then
        echo "\$PKG_PATH is undefined, don't know where to get packages"
        exit 1
    fi

    for pkg in \
        git \
        lcms \
        gsm \
        openldap-client \
        sane-backends \
        gnutls \
        mpg123 \
        jpeg \
        png \
        libxml \
        libxslt \
        bison
    do
        pkg_add $pkg
    done

    if test -d /usr/ports/devel/flex/
    then
        cd /usr/ports/devel/flex
        make
        make install
    else
        echo "Flex wasn't found in ports (or you don't have ports installed)."
        echo "You'll need to build/install flex manually. You need at least version 2.5.33."
        exit 2
    fi

fi

# Regular Linux distros.

if test ! -w /
then
    echo "Usage: sudo sh $0"
    exit 1
fi

#
# Alpine Linux:
alpine_pkgs="\
alsa-lib-dev autoconf automake bison build-base cups-dev flex fontconfig-dev freetype-dev git gnutls-dev gsm-dev \
gst-plugins-base-dev gstreamer-dev jpeg-dev lcms-dev libgphoto2-dev libpng-dev libxcomposite-dev libxcursor-dev \
libxdamage-dev libxinerama-dev libxml2-dev libxrandr-dev libxrender-dev libxslt-dev libxxf86dga-dev mesa-dev \
mpg123-dev ncurses-dev openal-soft-dev openldap-dev openssl-dev paxctl tiff-dev v4l-utils-dev winbind zlib-dev"

#----------------------------------------------------------------------------
# Debian data, common to Debian GNU/kFreeBSD, GNU/Hurd and GNU/Linux:
debian_common_pkgs="\
bison ccache flex fontforge gcc gettext git-core libasound2-dev libaudio-dev libc6-dev libcups2-dev \
libdbus-1-dev libelfg0 libesd0-dev libexif-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev \
libgcrypt11-dev libgif-dev libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev libgnutls-dev \
libgpg-error-dev libgphoto2-2-dev libgsm1-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev \
libhal-dev libhal-storage-dev libice-dev libjpeg62-dev liblcms1-dev libldap2-dev libmad0 libmad0-dev \
libmpg123-dev libncurses5-dev libodbcinstq1c2 libogg-dev  libopenal-dev libopenal1 \
libpng12-dev libpopt-dev libsane-dev libsm-dev libssl-dev libtasn1-3-dev libtiff4-dev libtiffxx0c2 \
libusb-dev libvorbis-dev libvorbisfile3 libx11-dev libxau-dev libxcomposite-dev libxcursor-dev \
libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxml2-dev libxmu-dev \
libxmu-headers libxrandr-dev libxrender-dev libxslt1-dev libxt-dev libxv-dev libxxf86vm-dev m4 make \
mesa-common-dev unixodbc unixodbc-dev x11proto-composite-dev x11proto-core-dev x11proto-fixes-dev \
x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-video-dev x11proto-xext-dev \
x11proto-xf86vidmode-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev"

# Linux specific:
debian_linux_pkgs="\
libcapi20-3 libcapi20-dev libieee1284-3-dev linux-libc-dev prelink"

#----------------------------------------------------------------------------
# Ubuntu data
ubuntu_common_pkgs="\
bison ccache cvs flex fontforge gcc gettext git-core libasound2-dev libaudio-dev libc6-dev \
libcapi20-3 libcapi20-dev libdbus-1-dev libesd0-dev libexif-dev \
libexpat1-dev libfontconfig1-dev libfreetype6-dev libgcrypt11-dev libgl1-mesa-dev \
libglib2.0-dev libglu1-mesa-dev libgnutls-dev libgpg-error-dev libgphoto2-2-dev libgsm1-dev libgstreamer0.10-dev \
libgstreamer-plugins-base0.10-dev libhal-dev libice-dev libieee1284-3-dev liblcms1-dev \
libldap2-dev libmad0 libmad0-dev libmpg123-dev libncurses5-dev \
libogg-dev  libopenal-dev libopenal1 libpng12-dev libpopt-dev \
libsm-dev libssl-dev libtasn1-3-dev libtiffxx0c2 libusb-dev libvorbis-dev \
libvorbisfile3 libx11-dev libxau-dev libxcomposite-dev libxcursor-dev libxdmcp-dev \
libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxml2-dev libxmu-dev \
libxmu-headers libxrandr-dev libxrender-dev libxslt1-dev libxt-dev libxv-dev \
libxxf86vm-dev linux-libc-dev m4 make mesa-common-dev \
unixodbc unixodbc-dev x11proto-composite-dev x11proto-core-dev x11proto-fixes-dev  \
x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-video-dev x11proto-xext-dev \
x11proto-xf86vidmode-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev \
libelfg0 libgif-dev libhal-storage-dev libjack-dev"

ubuntu_gutsy_pkgs="\
cogito \
libcupsys2-dev \
libfreebob0 \
libglib1.2-dev \
libjpeg62-dev \
libltdl3 \
libltdl3-dev \
liblzo-dev \
libodbcinstq1c2 \
libopencdk8-dev \
libsane-dev \
libtiff4-dev \
obcinst1debian1 \
xrender-dev \
x11proto-render-dev \
x-dev \
"

ubuntu_hardy_pkgs="\
libcupsys2-dev \
libfreebob0 \
libglib1.2-dev \
libjpeg62-dev \
libltdl3 \
libltdl3-dev \
liblzo-dev \
libodbcinstq1c2 \
libopencdk10-dev \
libsane-dev \
libtiff4-dev \
odbcinst1debian1 \
x-dev \
"

ubuntu_ibex_pkgs="\
libcups2-dev \
libfreebob0 \
libglib1.2-dev \
libjpeg62-dev \
liblzo-dev \
libltdl7 \
libltdl7-dev \
libodbcinstq1c2 \
libsane-dev \
libtiff4-dev \
odbcinst1debian1 \
x-dev \
"

ubuntu_jaunty_pkgs="\
libcups2-dev \
libfreebob0 \
libglib1.2-dev \
libjpeg62-dev \
liblzo-dev \
libltdl7 \
libltdl7-dev \
libodbcinstq1c2 \
libsane-dev \
libtiff4-dev \
odbcinst1debian1 \
x-dev \
"

ubuntu_karmic_pkgs="\
libcups2-dev \
libfreebob0 \
libjpeg62-dev \
liblzo2-dev \
libltdl7 \
libltdl7-dev \
libgstreamermm-0.10-dev \
libodbcinstq1c2 \
libsane-dev \
libtiff4-dev \
odbcinst1debian1 \
prelink \
x-dev \
"

ubuntu_maverick_pkgs="\
libcups2-dev \
libfreebob0 \
libjpeg62-dev \
liblzo2-dev \
libltdl7 \
libltdl7-dev \
libgstreamermm-0.10-dev \
libodbcinstq1c2 \
libsane-dev \
libtiff4-dev \
odbcinst \
prelink \
"

ubuntu_oneiric_pkgs="\
libcups2-dev \
libjpeg62-dev \
liblzo2-dev \
libltdl7 \
libltdl7-dev \
libgstreamermm-0.10-dev \
libodbcinstq1c2 \
libsane-dev \
libtiff4-dev \
odbcinst \
prelink \
"

ubuntu_precise_pkgs="\
libcups2-dev \
libjpeg-turbo8-dev \
libsane-dev \
libtiff4-dev \
libv4l-dev \
oss4-dev \
prelink \
"

ubuntu_64_ibex_usr_lib32_sos="\
libcapi20.so.3 libcrypto.so.0.9.8 libcups.so.2 libfontconfig.so.1 libfreetype.so.6 \
libGL.so.1 libGLU.so.1 libgnutls.so.26 libgphoto2_port.so.0 libgphoto2.so.2 \
libhal.so.1 libjack.so.0 libjpeg.so.62 libmpg123.so.0.2.4 liblcms.so.1 \
libodbc.so.1 libpng12.so.0 libsane.so.1 \
libssl.so.0.9.8 libX11.so.6 libXcomposite.so.1 libXcursor.so.1 libXext.so.6 \
libXinerama.so.1 libXi.so.6 libxml2.so.2 libXrandr.so.2 libXrender.so.1 \
libxslt.so.1 libXxf86vm.so.1 libz.so.1"

ubuntu_64_ibex_lib32_sos="libdbus-1.so.3"

#----------------------------------------------------------------------------
# rpm-based distros

fedora_pkgs="\
alsa-lib-devel audiofile-devel bison cups-devel dbus-devel esound-devel flex \
fontconfig-devel fontforge freeglut-devel freetype-devel gcc giflib-devel git \
gnutls-devel hal-devel isdn4k-utils-devel lcms-devel libgphoto2-devel \
libICE-devel libjpeg-devel libpng-devel libSM-devel libusb-devel libX11-devel \
libXau-devel libXcomposite-devel libXcursor-devel libXext-devel libXi-devel \
libXinerama-devel libxml2-devel libXrandr-devel libXrender-devel \
libxslt-devel libXt-devel libXv-devel libXxf86vm-devel make mesa-libGL-devel \
mesa-libGLU-devel ncurses-devel openldap-devel openssl-devel patch pkgconfig \
prelink samba-winbind sane-backends-devel xorg-x11-proto-devel"

suse_pkgs="\
alsa-devel audiofile bison capi4linux-devel cups-devel desktop-file-utils flex \
fontconfig-devel freeglut-devel freetype2-devel gcc giflib-devel git-core glibc-devel \
gnutls-devel hal-devel jack-devel libgphoto2-devel libjpeg-devel liblcms-devel \
libpng-devel libxml2-devel libxslt-devel make Mesa-devel ncurses-devel openldap2-devel \
openssl-devel pkgconfig unixODBC-devel update-desktop-files xorg-x11-devel zlib-devel"


#----------------------------------------------------------------------------
# Code

# For some reason, Debian/KFreeBSD has this, but it is broken...
case "`uname -s`" in
    *Linux*) lsb_release_path=`which lsb_release 2>/dev/null`;;
esac

if test "$lsb_release_path" != ""
then
  distro=`lsb_release -i -r -s`
elif test -f /etc/issue
  then
    distro=`head -n 1 /etc/issue`
else
  echo "Don't know how to identify your OS."
fi

case $distro in
*Alpine*Linux*) apk add $alpine_pkgs;;
Ubuntu*7.10) apt-get install $ubuntu_common_pkgs $ubuntu_gutsy_pkgs;;
Ubuntu*8.04) apt-get install $ubuntu_common_pkgs $ubuntu_hardy_pkgs;;
Ubuntu*8.10) apt-get install $ubuntu_common_pkgs $ubuntu_ibex_pkgs;;
Linux*Mint*7|Ubuntu*9.04) apt-get install $ubuntu_common_pkgs $ubuntu_jaunty_pkgs;;
Linux*Mint*8|Ubuntu*9.10) apt-get install $ubuntu_common_pkgs $ubuntu_karmic_pkgs;;
Linux*Mint*9|Ubuntu*10.04) apt-get install $ubuntu_common_pkgs $ubuntu_karmic_pkgs;;
Linux*Mint*10|Ubuntu*10.10) apt-get install $ubuntu_common_pkgs $ubuntu_maverick_pkgs;;
Linux*Mint*11|Ubuntu*11.04) apt-get install $ubuntu_common_pkgs $ubuntu_maverick_pkgs;;
Linux*Mint*12|Ubuntu*11.10) apt-get install $ubuntu_common_pkgs $ubuntu_oneiric_pkgs;;
Ubuntu*12.04) apt-get install $ubuntu_common_pkgs $ubuntu_precise_pkgs;;
Fedora*release*) yum install $fedora_pkgs ;;
SUSE*LINUX*11.1) zypper install $suse_pkgs ;;
Debian*Hurd*) apt-get install $debian_common_pkgs ;;
Debian*Linux*) apt-get install $debian_common_pkgs $debian_linux_pkgs ;;
Debian*6.0.2*) apt-get install $debian_common_pkgs $debian_linux_pkgs ;;
Debian*kFreeBSD*) apt-get install $debian_common_pkgs ;;
*) echo "distro $distro not supported"; exit 1;;
esac

set -x
if test `uname -m` = x86_64
then

# Provide plain old .so names for given libraries
# Usage: linksos dir foo.so.x bar.so.y ...
linksos()
{
    dir=$1
    shift
    for lib
    do
        barename=`echo $lib | sed 's/\.so\..*$/.so/' `
        if test -f $dir/$lib && test ! -f $dir/$barename 
        then
            ln -s $dir/$lib $dir/$barename
        fi
    done
}

    case $distro in
    Linux*Mint*7|Linux*Mint*8|Ubuntu*8.04|Ubuntu*8.10|Ubuntu*9.04|Ubuntu*9.10) 
        apt-get install ia32-libs lib32asound2-dev lib32z1-dev 
        linksos /usr/lib32 $ubuntu_64_ibex_usr_lib32_sos
        linksos /lib32 $ubuntu_64_ibex_lib32_sos
        # Special cases
        test -f /usr/lib32/libpng.so || ln -s /usr/lib32/libpng12.so /usr/lib32/libpng.so
        test -f /usr/lib32/libldap.so || ln -s /usr/lib32/libldap-2.4.so /usr/lib32/libldap.so
        test -f /usr/lib32/liblber.so || ln -s /usr/lib32/liblber-2.4.so.2 /usr/lib32/liblber.so
        test -f /usr/lib32/libldap_r.so || ln -s /usr/lib32/libldap_r-2.4.so.2 /usr/lib32/libldap_r.so
        # For some reason not installed by default
        apt-get install lib32ncurses5-dev
        ;;
    Fedora*release*)
        yum install alsa-lib-devel.i686 audiofile-devel.i686 cups-devel.i686 dbus-devel.i686 esound-devel.i686 \
            fontconfig-devel.i686 freetype.i686 freetype-devel.i686 giflib-devel.i686 hal-devel.i686 \
            lcms-devel.i686 libICE-devel.i686 libjpeg-devel.i686 libpng-devel.i686 libSM-devel.i686 \
            libusb-devel.i686 libX11-devel.i686 libXau-devel.i686 libXcomposite-devel.i686 \
            libXcursor-devel.i686 libXext-devel.i686 libXi-devel.i686 libXinerama-devel.i686 \
            libxml2-devel.i686 libXrandr-devel.i686  libXrender-devel.i686 libxslt-devel.i686 \
            libXt-devel.i686 libXv-devel.i686 libXxf86vm-devel.i686 mesa-libGL-devel.i686  mesa-libGLU-devel.i686 \
            ncurses-devel.i686 openldap-devel.i686 openssl-devel.i686 zlib-devel.i686 sane-backends-devel.i686 \
            xorg-x11-proto-devel glibc-devel.i686 prelink libstdc++-devel.i686 pulseaudio-libs-devel.i686 \
            gnutls-devel.i686 libgphoto2-devel.i686 openal-soft-devel.i686 isdn4k-utils-devel.i686 \
            gsm-devel.i686 libv4l-devel.i686 cups-devel.i686 libtiff-devel.i686
        ;;
    Linux*Mint*9|Linux*Mint*10|Linux*Mint*11|Ubuntu*10.04|Ubuntu*10.10|Ubuntu*11.04|Ubuntu*12.04)
        apt-get install ia32-libs lib32asound2-dev lib32ncurses5-dev lib32v4l-dev lib32z1-dev
        ;;
    *)
        echo "I do not know how to install 32 bit libraries for distro $distro yet"
        ;;
    esac
fi

```

---

### Post by cwwilson721 on 2012-03-15
And doing what I outlined will do the same thing.

PLUS, you get all the things the Nvidia drivers STOPPED putting in their drivers (32bit support, anyone?).

THAT is what your script does. It installs the stuff that the Ubuntu Drivers do, but won't get upgraded through Ubuntu.

So, I will stick to my way.

Plus, it's easier, supported by Ubuntu, and it works for everybody, nor does it install anything that is not needed for 32 driver support.

It comes down to personal preferences: Do you want the distro supplied drivers that do as they are supposed to, and get regular updates/security fixes/support? Or do you want to reinstall stuff every time there is a kernel upgrade, or a new driver comes out from Nvidia (that may or may not have things needed for your distro)?

I like the peace of mind, myself.

---

### Post by pdcant on 2012-04-23
I agree with otherethe's method. Why go back to get old drivers after many years of progress, just so the latest version OS works with third-party apps? Why not solve the problems with the new drivers and keep them working together? 

I don't care about the bean scores here. The "answers" provided, along with snide comments, is what keeps most from switching to Linux. Linux "experts": Get your head out of the sand. This sounded like the service I get from Acer/Gateway when trying to solve a problem. This is the so-called "Gold Standard of Support." At least corporations remain civil when they answer.

Thanks for the solution provided, otherethe. It didn't work for me yet, but my issue is probably slightly different from yours. I think I have to find the real libGL.so.1 32-bit. The final solution should come from nvidia because they seem to have broken it. Have they been notified? I'll be looking there.

---

### Post by cwwilson721 on 2012-04-23
I don't care about the "beans" myself.

The issue is, the OP borked his system by trying something different, that doesn't work.

Using the Ubuntu Drivers WORKS, on 64bit and 32bit, with no "extra" script needed, as long as you stick with them.

I boot Ubuntu, Slackware, and Debian, all as 32bit and 64bit (yes, six separate distros, plus a Windows 7 install. My wife hates how much I spent on hard drives alone), and run WoW thru wine on all the distros (Not 6 separate installs. Actually, I have one dedicated HDD just for WoW, that is shared amongst my Linux distros and Windows. For those counting, that's 8 partitions spread over 4 HDDs).

On Ubuntu, I use the Distro Drivers. Slackware uses the ones from Nvidia.com. Using Nvidia.com drivers, on a 64bit system, you must say "yes" to the part where it asks if you want to install the 32bit libraries, and in 32bit, just normal install.

With Ubuntu, it's "install and done" with the Additional Drivers.

In NO distro, do I need to add the above script.

Remember, this is all volunteer. I'm not getting paid. 

You can either listen to the free help given here, or not. Your choice. And if an OP chooses NOT to take my WORKING advice, then don't say I don't know what I'm talking about. I do know. It's whether you CHOOSE to go the "easy" established route, or go around in circles reinventing the wheel.

Personally, the only reason I use Ubuntu is the "easy" way. Install the drivers, install wine1.3+, install/copy/softlink WoW, and done. Never have an issue except when I "try something new", because it just works on 32/64bit Linux, most any distro.

---

### Post by spando on 2012-09-10
I can confirm otherethe's script works nicely for linux mint 13 (with small changes), I needed to test the more recent nvidia drivers to see if they would clear up some graphical problems I was having. I'm no fan of closed source drivers but if you need to try a thing then it has to be done. Telling the OP to give up on that is not the kind of advice I would come here looking for. Also the tone of some of these replies has been rather rude in my view.

In any case, well done not giving up, otherethe, could you tell me if you wrote this script or where you found it?

---

