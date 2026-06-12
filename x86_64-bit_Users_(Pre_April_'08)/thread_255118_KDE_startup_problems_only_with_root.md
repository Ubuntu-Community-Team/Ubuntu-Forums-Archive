---
title: "KDE startup problems only with root"
date: 2006-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by wgaprotest on 2006-09-11
It's really strange that I'm not having problems with KDE as a user with some root priviledges - just as root. As root, it stops loading, sometimes at the second-to-end section, and sometimes at the very end, the processes part. I read somewhere that dcop had crashed, so how to fix it? The messages vary, too, depending on where it stops loading. I don't remember exactly what the various error messages are, so please don't ask me.

That's what I'm hoping someone can help me with: fixing the dcop. 

I'm anticipating that you ask me why? have a root user, when ubuntu allows another user to have root priviledges and simply use sudo with the same password? I'm still setting things up here, and I got tired of constantly being asked for the password, so I elected to have sysadmin login. And if you're going to ask me why kde instead of gnome, I was trying to solve some cups & samba problems, and so much of my reading references kde. I'd finally gotten the stuff I needed to get my local printer to print across the network by using kdeprint, and now all my local printing facilities are gone. The local printer isn't even detected in gnome, either.

I'm also wondering if I shouldn't have installed kubuntu dapper, server version, but with kde dying on me I'm nervous about going that option and starting from scratch again. It has been sooooooo much work to get my multimedia working, and it was tough to get the printer going locally.

---

### Post by kuja on 2006-09-11
Actually, there are a couple solutions that could be a little bit better *if* you're working in a terminal. You could start a root terminal, or open a regular terminal and type in ```
sudo -s
``` There, that way you only enter the password once. 

As per else, if that won't work out, and you must have a root login, then  you're going to need to supply a bit more information.
Some useful information:

-Version of KDE being used (three are available for Dapper)
-Do you have the kubuntu-desktop package installed?
-Error messages would be nice

If you're using KDE from the default repository, perhaps the more-up-to-date KDE 3.5.4 provides a fix for your problem(s). (repository: deb [http://kubuntu.org/packages/kde-354](http://kubuntu.org/packages/kde-354) main)

Mayhap there was a problem with the install in general? Hard telling, granted the vagueness of information provided, Try this:

```
sudo apt-get install --reinstall kubuntu-desktop acpi acpi-support acpid adept akregator amarok anacron ark arts bc bicyclerepair bluez-cups bluez-utils bogofilter brltty cdparanoia cdrdao cdrecord cupsys cupsys-bsd cupsys-client cupsys-driver-gutenprint dbus dc diveintopython doc-base doc-debian dvd+rw-tools example-content foo2zjs foomatic-db foomatic-db-engine foomatic-db-gutenprint foomatic-db-hpijs foomatic-filters foomatic-filters-ppds fortune-mod gs-esp gtk2-engines-gtk-qt gwenview hal hotkey-setup hplip hplip-ppds irssi k3b kaddressbook kaffeine-xine kamera karm katapult kate kaudiocreator kcontrol kcron kde-guidance kde-systemsettings kdeadmin-kfile-plugins kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdesktop kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin landscape-client language-selector-qt lftp libarts1-akode libgl1-mesa libglut3 libnss-mdns libpam-foreground libsasl2-modules libxp6 min12xxw mkisofs openoffice.org pmount pnm2ppa powermanagement-interface powernowd python-adns python-apt python-cddb python-clientcookie python-crypto python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-epydoc python-eunuchs python-examples python-gadfly python-gd python-gdbm python-genetic python-geoip python-gnupginterface python-htmlgen python-htmltmpl python-id3lib python-imaging python-imaging-sane python-jabber python-kjbuckets python-ldap python-mysqldb python-netcdf python-newt python-numeric python-pam python-parted python-pexpect python-pgsql python-pisock python-pqueue python-pyao python-pylibacl python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr python-reportlab python-simpletal python-soappy python-sqlite python-stats python-syck python-unit python-xdg python-xmpp python2.4-dbus python2.4-dictclient python2.4-librdf python2.4-libxml2 python2.4-libxslt1 python2.4-pycurl qca-tls readahead scim-qtimm screen skim slocate smbclient speedcrunch ttf-arabeyes ttf-arphic-uming ttf-baekmuk ttf-bitstream-vera ttf-dejavu ttf-freefont ttf-gentium ttf-indic-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-thai-tlwg unzip usplash vorbis-tools wlassistant wvdial x-ttcidfont-conf x-window-system-core xcursor-themes xkeyboard-config xserver-xorg-input-synaptics xterm zip
```

---

### Post by wgaprotest on 2006-09-11
Thanks for your help. Now that I'm a bit fresher after getting some sleep:

The last couple of times I rebooted the kde startup process stopped at the last stage: where it's trying to restore the last session, and the error message I get when I'm tired of waiting for it is: "the process for the system protocol died unexpectedly." I will try to find a way for it to start a brand new session, as opposed to restoring the last one.

I also believe that I'm using KDE 3.5.2, which was what was available from synaptic. I suspected the 3.5.2 version was the issue awhile back, but I seemed to have some trouble upgrading it. So far I've attempted to stay away from the debian packages to avoid the bloat, but this install is getting bloated anyway, so that reason doesn't apply anymore. 

However, I'm not using kubuntu at all yet: it's still ubuntu, with kde added when gnome wasn't too easy to use during things like cups/samba configuration. And I don't think it was a problem with the original install, as things were working well for a week - until I installed the kde. So I'm not sure I can or should paste your script into shell while in root-user mode. I have tried actually, but shell hangs: nothing appears from my paste command. Shell (and other app windows) also get hidden behind this mozilla window, and another annoying feature of this kde problem is that the window behavior isn't right: the outside edges, like the title bars, are indistinct, and there are no minimize buttons for me to switch between apps/multitask. I'll now try again while under my user session; I just reentered the root session so that I could double-check the error message again. 

I'm back in gnome now, as root, and it seems to be ok, but another reason why I tried the kde route was that gnome was not behaving itself: I would try to minimize apps, and they seemed to disappear instead. Very annoying to have to constantly reopen packages when I'm trying to flip back and forth between them. I never did ask any of the desktops to hide anything, as I know that's NOT how I want my windows to behave. After all, what's the point of a hidden window? I think the programmers have gotten a little carried away with their own "this is neat' impulses with this feature, as I can't see any utility in it - just problems.

---

### Post by wgaprotest on 2006-09-11
I'm going delete everything to install the ubuntu server ed, and then try to avoid the kde 3.5.2 problem completely, going right to 3.5.4. It makes sense, as we've started using this pc as the entertainment server anyway,  want myth on here and it requires mysql, and another package I may end up using for my volunteer management program also requires the mysql.

and if I'm having problems with kde 3.5.2/printing on the desktop, not having tried to go the whole route with servers (I'm intimidated with servers, frankly) I don't want to have to tackle all the elements of the lamp invidividually.

At least I feel heartened by the fact that  did get the printer going on the desktop, and ALL the music/dvd codecs.

---

### Post by kuja on 2006-09-11
The little script above won't break your GNOME, it just reinstalls all of the packages related to kubuntu-desktop.

Also, debian packages really don't result in bloat, as far as I can tell. The only thing that may end up bloated really is the /var/cache/apt/archives folder, which after enough updates/installed packages can grow into the gig. "sudo apt-get clean" cleans that folder out. 

I think you can problably get it working without doing the reinstall though seriously.

---

