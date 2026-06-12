---
title: "Kdeinit, Kstartupconfig missing...."
date: 2006-09-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cariboo1938 on 2006-09-25
Hi everybody,
I have Ubuntu 6.06 AMD64 Version and I also installed KDE Desktop. 
I played/fooled around in /usr/bin (I know, I'm not supposed to do that)
looking for what files are responsible for the KDE Desktop. 
I think I messed up the KDE installation. When I log in and "change sesssion" to KDE, 
I get the message 
[COLOR="Red"]'couldnt find _kstartupconfig_ and _kdeinit_ not found, check installation'[/COLOR] 
on the blue KDE Splash Screen. 
[COLOR="Blue"]Is it possible to get these missing files? 
Where would I find them?[/COLOR]

---

### Post by kuja on 2006-09-25
Fooled around indeed  :O

Rather than screw around with things some more, why not do things the easy way eh?

```

apt-get install --reinstall kubuntu-desktop acpi acpi-support acpid adept akregator amarok anacron ark arts bc bicyclerepair bluez-cups bluez-utils bogofilter brltty cdparanoia cdrdao cdrecord cupsys cupsys-bsd cupsys-client cupsys-driver-gutenprint dbus dc diveintopython doc-base doc-debian dvd+rw-tools example-content foo2zjs foomatic-db foomatic-db-engine foomatic-db-gutenprint foomatic-db-hpijs foomatic-filters foomatic-filters-ppds fortune-mod gs-esp gtk2-engines-gtk-qt gwenview hal hotkey-setup hplip hplip-ppds irssi k3b kaddressbook kaffeine-xine kamera karm katapult kate kaudiocreator kcontrol kcron kde-guidance kde-systemsettings kdeadmin-kfile-plugins kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdesktop kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin landscape-client language-selector-qt lftp libarts1-akode libgl1-mesa libglut3 libnss-mdns libpam-foreground libsasl2-modules libxp6 min12xxw mkisofs openoffice.org pmount pnm2ppa powermanagement-interface powernowd python-adns python-apt python-cddb python-clientcookie python-crypto python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-epydoc python-eunuchs python-examples python-gadfly python-gd python-gdbm python-genetic python-geoip python-gnupginterface python-htmlgen python-htmltmpl python-id3lib python-imaging python-imaging-sane python-jabber python-kjbuckets python-ldap python-mysqldb python-netcdf python-newt python-numeric python-pam python-parted python-pexpect python-pgsql python-pisock python-pqueue python-pyao python-pylibacl python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr python-reportlab python-simpletal python-soappy python-sqlite python-stats python-syck python-unit python-xdg python-xmpp python2.4-dbus python2.4-dictclient python2.4-librdf python2.4-libxml2 python2.4-libxslt1 python2.4-pycurl qca-tls readahead scim-qtimm screen skim slocate smbclient speedcrunch ttf-arabeyes ttf-arphic-uming ttf-baekmuk ttf-bitstream-vera ttf-dejavu ttf-freefont ttf-gentium ttf-indic-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-thai-tlwg unzip usplash vorbis-tools wlassistant wvdial x-ttcidfont-conf x-window-system-core xcursor-themes xkeyboard-config xserver-xorg-input-synaptics xterm zip
```

That will reinstall all packages associated with kubuntu-desktop.

---

### Post by Cariboo1938 on 2006-09-25
> **kuja said:**
> Fooled around indeed  :O
Rather than screw around with things some more, why not do things the easy way eh?```
apt-get install --reinstall....
```
That will reinstall all packages associated with kubuntu-desktop.
Thanks kuja, yeah I know this was not a good idea....
Anyway, I followed your advice and now the error messages are:
> [COLOR="Red"]Could not start kstartupconfig/kdeinit. Check your installation.[/COLOR]So, it seems it helped to get the missing files...but now there is another problem...
[COLOR="Blue"]Any idea what to do now? 
Can I use the Live CD to solve this issue?
...because before I "fooled" around KDE desktop was working fine.[/COLOR]

---

### Post by Cariboo1938 on 2006-09-27
Hi,
I just don't understand why I still can't start KDE desktop.
I uninstalled KDE```
sudo aptitude remove kubuntu-desktop
``` and installed again following [THESE INSTRUCTIONS]("http://www.psychocats.net/ubuntu/kde")
And still the error message> [COLOR="Red"]Could not start kstartupconfig/kdeinit. Check your installation[/COLOR]
[COLOR="Blue"]What else could be responsable for that?[/COLOR]

---

### Post by kuja on 2006-09-27
Well, it is possible that your personal or system settings got borked somehow. 

Try doing this, I've done this a time or two in the past with success (though my problem was related to something else, changing the computers name .... that didn't work out as well as I'd hoped)

```
apt-get remove --purge kubuntu-desktop acpi acpi-support acpid adept akregator amarok anacron ark arts bc bicyclerepair bluez-cups bluez-utils bogofilter brltty cdparanoia cdrdao cdrecord cupsys cupsys-bsd cupsys-client cupsys-driver-gutenprint dbus dc diveintopython doc-base doc-debian dvd+rw-tools example-content foo2zjs foomatic-db foomatic-db-engine foomatic-db-gutenprint foomatic-db-hpijs foomatic-filters foomatic-filters-ppds fortune-mod gs-esp gtk2-engines-gtk-qt gwenview hal hotkey-setup hplip hplip-ppds irssi k3b kaddressbook kaffeine-xine kamera karm katapult kate kaudiocreator kcontrol kcron kde-guidance kde-systemsettings kdeadmin-kfile-plugins kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdesktop kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin landscape-client language-selector-qt lftp libarts1-akode libgl1-mesa libglut3 libnss-mdns libpam-foreground libsasl2-modules libxp6 min12xxw mkisofs openoffice.org pmount pnm2ppa powermanagement-interface powernowd python-adns python-apt python-cddb python-clientcookie python-crypto python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-epydoc python-eunuchs python-examples python-gadfly python-gd python-gdbm python-genetic python-geoip python-gnupginterface python-htmlgen python-htmltmpl python-id3lib python-imaging python-imaging-sane python-jabber python-kjbuckets python-ldap python-mysqldb python-netcdf python-newt python-numeric python-pam python-parted python-pexpect python-pgsql python-pisock python-pqueue python-pyao python-pylibacl python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr python-reportlab python-simpletal python-soappy python-sqlite python-stats python-syck python-unit python-xdg python-xmpp python2.4-dbus python2.4-dictclient python2.4-librdf python2.4-libxml2 python2.4-libxslt1 python2.4-pycurl qca-tls readahead scim-qtimm screen skim slocate smbclient speedcrunch ttf-arabeyes ttf-arphic-uming ttf-baekmuk ttf-bitstream-vera ttf-dejavu ttf-freefont ttf-gentium ttf-indic-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-thai-tlwg unzip usplash vorbis-tools wlassistant wvdial x-ttcidfont-conf x-window-system-core xcursor-themes xkeyboard-config xserver-xorg-input-synaptics xterm zip
```
```
apt-get install --reinstall kubuntu-desktop acpi acpi-support acpid adept akregator amarok anacron ark arts bc bicyclerepair bluez-cups bluez-utils bogofilter brltty cdparanoia cdrdao cdrecord cupsys cupsys-bsd cupsys-client cupsys-driver-gutenprint dbus dc diveintopython doc-base doc-debian dvd+rw-tools example-content foo2zjs foomatic-db foomatic-db-engine foomatic-db-gutenprint foomatic-db-hpijs foomatic-filters foomatic-filters-ppds fortune-mod gs-esp gtk2-engines-gtk-qt gwenview hal hotkey-setup hplip hplip-ppds irssi k3b kaddressbook kaffeine-xine kamera karm katapult kate kaudiocreator kcontrol kcron kde-guidance kde-systemsettings kdeadmin-kfile-plugins kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdesktop kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin landscape-client language-selector-qt lftp libarts1-akode libgl1-mesa libglut3 libnss-mdns libpam-foreground libsasl2-modules libxp6 min12xxw mkisofs openoffice.org pmount pnm2ppa powermanagement-interface powernowd python-adns python-apt python-cddb python-clientcookie python-crypto python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-epydoc python-eunuchs python-examples python-gadfly python-gd python-gdbm python-genetic python-geoip python-gnupginterface python-htmlgen python-htmltmpl python-id3lib python-imaging python-imaging-sane python-jabber python-kjbuckets python-ldap python-mysqldb python-netcdf python-newt python-numeric python-pam python-parted python-pexpect python-pgsql python-pisock python-pqueue python-pyao python-pylibacl python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr python-reportlab python-simpletal python-soappy python-sqlite python-stats python-syck python-unit python-xdg python-xmpp python2.4-dbus python2.4-dictclient python2.4-librdf python2.4-libxml2 python2.4-libxslt1 python2.4-pycurl qca-tls readahead scim-qtimm screen skim slocate smbclient speedcrunch ttf-arabeyes ttf-arphic-uming ttf-baekmuk ttf-bitstream-vera ttf-dejavu ttf-freefont ttf-gentium ttf-indic-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-thai-tlwg unzip usplash vorbis-tools wlassistant wvdial x-ttcidfont-conf x-window-system-core xcursor-themes xkeyboard-config xserver-xorg-input-synaptics xterm zip
```

Then back  up your personal files.

```
sudo mkdir /backup
sudo chown $USER:$USER /backup

```

Then copy your non-setting files to /backup (setting files are usually in the base of your home directory, and are hidden(ie, that start with a dot))

```

cd /
sudo rm -rf $HOME
sudo mkdir $HOME
sudo chown $USER:$USER $HOME
sudo chmod u+rwx $HOME
sudo chmod go=r $HOME
sudo apt-get install kubuntu-desktop
cd /backup
sudo cp * $HOME
```

---

### Post by Cariboo1938 on 2006-09-28
> **kuja said:**
> Well, it is possible that your personal or system settings got borked somehow. 

Try doing this, I've done this a time or two in the past with success (though my problem was related to something else, changing the computers name .... that didn't work out as well as I'd hoped)
 
```
apt-get install --reinstall kubuntu-desktop acpi acpi-sup... 
```
Thank you kuja for the reply...
before I start to follow your instructions I want to know if it would not be better to use "aptitide" instead of "apt-get"? 
I ask because I read [THIS.]("http://www.psychocats.net/ubuntu/kde")

---

### Post by kuja on 2006-09-28
This is a matter of personal preference really. Some people like that aptitude keeps track of what you installed along with  a certain package, some don't. It shouldn't matter which you use, so long as you're consistent. Use whichever you like best.

---

### Post by gcornett on 2006-11-06
Although I am a total newbie, I decided to install kde to check it out.  Of course I got the missing kstartupconfig error box.  Bummer!  

So I read your messages and tried the things suggested. Still didn't work but I also got an error message that said my session lasted less than 10 seconds - too true - and it gave me a log of what happened.  kde was trying to install .kde/share and .kde/share/config in my home directory.  But they were already there!  So I deleted them and tried again.  Worked fine!  I now have kde up and running.  Now to see if Gnome still works.  :)

---

