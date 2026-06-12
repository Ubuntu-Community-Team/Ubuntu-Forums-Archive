---
title: "KDE Issues"
date: 2006-08-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Complitric on 2006-08-13
I have recently installed KDE to my Ubuntu install.  I have a couple of issues with this.  The first issue is that I can not change any display settings.  When I select Display from System Settings, I receive the message:

The module Display could not be loaded.

Possible reasons:
    An error occurred in your last KDE upgrade leaving an orphaned control module.
    You have old third-party modules lying around.

The second issue, is that I am unable to logout,restart, and shut down the machine.  Anytime I select one of these options, my monitor goes into idle mode and hangs.

---

### Post by kuja on 2006-08-13
Interesting, try running ```
sudo apt-get install --reinstall kubuntu-desktop acpi acpi-support acpid adept akregator amarok anacron ark arts avahi-daemon bc bluez-cups bluez-utils bogofilter brltty cdparanoia cdrdao cdrecord cupsys cupsys-bsd cupsys-client cupsys-driver-gutenprint dbus dc diveintopython doc-base dvd+rw-tools example-content foo2zjs foomatic-db foomatic-db-engine foomatic-db-gutenprint foomatic-db-hpijs foomatic-filters foomatic-filters-ppds fortune-mod gs-esp gtk2-engines-gtk-qt gwenview hal hotkey-setup hpijs-ppds hplip k3b kaddressbook kaffeine-xine kamera karm katapult kate kaudiocreator kcontrol kcron kde-guidance kde-systemsettings kdeadmin-kfile-plugins kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdesktop kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscd kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin landscape-client language-selector-qt lftp libarts1-akode libgl1-mesa libglut3 libnss-mdns libpam-foreground libsasl2-modules libxp6 min12xxw mkisofs openoffice.org pmount pnm2ppa powermanagement-interface powernowd qca-tls readahead scim-qtimm screen skim slocate smbclient speedcrunch ttf-arabeyes ttf-arphic-uming ttf-baekmuk ttf-bitstream-vera ttf-dejavu ttf-freefont ttf-gentium ttf-indic-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-thai-tlwg unzip usplash vorbis-tools wlassistant wvdial x-ttcidfont-conf xcursor-themes xkeyboard-config xorg xterm zip
``` in a terminal. Some package is probably missing, or might have had an error during installation. Afterwards, run this command in a terminal. (Hopefully this will still work for you for shutting down.) ```
sudo shutdown -h now
```

---

### Post by Complitric on 2006-08-13
Kuja, first, I will say that I have not tried your previous suggestion yet.


Update to the problem:

I started up SuperTux, and clicked openGL, monitor also went idle doing this.  (Driver issue?)

---

### Post by Complitric on 2006-08-13
Package hpijs-ppds is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Something I need to add to sources.list?

---

### Post by kuja on 2006-08-13
Hmm, not likely, try removing it, and any other such offenders, from the list of packages I gave you and installing without them. The version of Kubuntu-desktop I grabbed that list from was probably just a different version is all.

If interested in the other source on my list though, it would be the one for the latest version of KDE
deb [http://kubuntu.org/packages/kde-354](http://kubuntu.org/packages/kde-354) dapper main

---

### Post by Complitric on 2006-08-13
It is going, what do I do if it wont shutdown properly?

---

### Post by kuja on 2006-08-13
Oh, I'd hold in the power button, but I suppose you already knew that.

---

### Post by Complitric on 2006-08-13
Haha, doesn't an improper shut-down lose all the changes?  Or will it still update everything?

---

### Post by kuja on 2006-08-13
In general, changes don't require a reboot, and you shouldn't lose anything through an improper shutdown. The only updates that really require a reboot if I do recall, is a kernel update.

As per why not to do an improper shutdown, I do believe there is a(n albeit very, very small) risk of data loss/corruption/etc. It hasn't ever happened to me, and as far as I know it's not very common for it to happen with modern hardware/filesystems, but hey, better safe than sorry I'd suppose.

---

### Post by Complitric on 2006-08-13
Is there a way for me to check my ATI install?  I have installed the ATI 
drivers, but it seems to be a video issue.  I can log-out, but can't 
restart/shutdown.  SuperTux openGL mode puts me to idle as well.  Display 
still wont work after the reinstall of KDE, and I found that if I try to go 
to console login, it goes idle as well.

---

### Post by kuja on 2006-08-13
I've tested ATIs FGLRX driver for Linux on my brother's computer, frankly, I'm really disappointed with it. It's not all that stable, and there are multiple ways to make it hang or crash. I'd wait until after the other thing is done first though, really.

---

### Post by Complitric on 2006-08-13
Well, I am not really impressed with their Windows drivers either.  I am using standard Windows drivers there because of a game that ATI has trouble with.  But in Linux, I had to use them, because the standard Linux driver for it was freezing my computer when doing something as simple as looking at an OpenGL screensaver.

---

### Post by kuja on 2006-08-13
Hm, I didn't really have any trouble with it in Windows, but yeah, their drivers seem to need A LOT of work. Granted, in Linux, you're right, there's not a lot of choice. I don't see why it would freeze/hang the system... but a complete lack of performance on the other hand would be typical. Oh well, at least I no longer have to worry about it... Nvidia puts out quality drivers.

---

### Post by Complitric on 2006-08-13
Well, it seems ATI is having some issues with the x800 series, which happens to be what I have (X850 XT)  And, while it runs Windows great, and even games such as Half-Life2, and Heroes of Might and Magic 5.  It fails with a small-time game I run, freezing my computer after very short play-time.  So sadly, I am kind of stuck with this ATI stuff...

---

### Post by kuja on 2006-08-15
Figured I 'd follow up. Did that fix (at least the majority) of the problems you were having with KDE? (Orphaned modules and the like)

I believe your computer hanging on shutdown/logout is indeed a driver issue though. (I had similar issues on my brothers computer with logout/shutdown and switching view terminals). The ati and vesa drivers are probably more stable, but your 3d performances would be garbage. I guess it's one of those pick or choose things... stability, or 3d. Whichever you want yeah?

---

