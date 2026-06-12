---
title: "[WINE CONFLICT]:  Apt/Synaptic tries to 'remove' too much from Ubuntu Mate Jammy"
date: 2024-05-29
forum: Wine
---

### Post by 909mjolnir on 2024-05-29
[SOLVED(?)]:  erased everything and started all over again! 

I get this wierd result when I try to install wine in an otherwise functional Ubuntu...
Scroll down to the 'The following packages will be REMOVED' section.  
I NEED all of those packages!  I can't install wine because if they get removed my system becomes naff.  
I'm on Ubuntu Mate (official).  

```

$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  accountsservice bsdutils fonts-wine gir1.2-javascriptcoregtk-4.0 gstreamer1.0-plugins-base gstreamer1.0-x gtk-update-icon-cache libaccountsservice0 libblkid1
  libcapi20-3 libcurl4 libfaudio0 libgail-3-0 libglib2.0-0 libglib2.0-bin libgnutls30 libgpg-error-l10n libgstreamer-gl1.0-0 libgstreamer-plugins-base1.0-0 libgtk-3-0
  libgtk-3-bin libgtk-3-common libjavascriptcoregtk-4.0-18 libmount1 libnghttp2-14 libodbc2 libstb0 libtiff5 libvkd3d-shader1 libvkd3d1 libwine libxml2 libz-mingw-w64
  notification-daemon pinentry-curses util-linux uuid-runtime wine64 xserver-common
Suggested packages:
  gnome-control-center gnutls-bin libvisual-0.4-plugins odbc-postgresql tdsodbc cups-bsd gstreamer1.0-plugins-bad ttf-mscorefonts-installer pinentry-doc
  util-linux-locales q4wine winbind winetricks playonlinux wine-binfmt dosbox exe-thumbnailer | kio-extras wine64-preloader
Recommended packages:
  vkd3d-compiler libosmesa6 wine32
The following packages will be REMOVED:
  appmenu-gtk3-module apturl arctica-greeter atril ayatana-indicator-application ayatana-indicator-printers ayatana-settings bamfdaemon bleachbit caja caja-admin
  caja-eiciel caja-gtkhash caja-mediainfo caja-open-terminal caja-rename caja-sendto caja-wallpaper engrampa eom ffmpeg folder-color-caja gcr gdebi
  gir1.2-ayatanaappindicator3-0.1 gir1.2-caja-2.0 gir1.2-eom-1.0 gir1.2-gtk-3.0 gir1.2-gtksource-4 gir1.2-handy-1 gir1.2-peas-1.0 gir1.2-pluma-1.0 gir1.2-vte-2.91
  gir1.2-webkit2-4.0 gir1.2-wnck-3.0 gnome-disk-utility gnome-keyring gnome-session-canberra gparted gucharmap language-selector-gnome libappmenu-gtk3-parser0
  libatrildocument3 libatrilview3 libayatana-appindicator3-1 libayatana-ido3-0.4-0 libayatana-indicator3-7 libcaja-extension1 libcanberra-gtk3-0
  libcanberra-gtk3-module libexo-2-0 libflashrom1 libgcr-ui-3-1 libgepub-0.6-0 libgl1-amber-dri libgtk-layer-shell0 libgtk3-perl libgtkmm-3.0-1v5 libgtksourceview-4-0
  libgucharmap-2-90-7 libhandy-1-0 libmarco-private2 libmate-desktop-2-17 libmate-panel-applet-4-1 libmate-slab0 libmate-window-settings1 libmatekbd4 libmateweather1
  libmousepad0 libnma0 libpeas-1.0-0 libplank1 libsasl2-modules libsasl2-modules-gssapi-mit libvte-2.91-0 libwebkit2gtk-4.0-37 libwnck-3-0 libxatracker2
  libxfce4ui-2-0 libyelp0 marco mate-applet-appmenu mate-applet-brisk-menu mate-applets mate-control-center mate-desktop mate-hud mate-indicator-applet mate-media
  mate-notification-daemon mate-optimus mate-panel mate-polkit mate-power-manager mate-screensaver mate-sensors-applet mate-session-manager mate-settings-daemon
  mate-system-monitor mate-terminal mate-tweak mate-user-guide mate-utils mate-window-buttons-applet mate-window-menu-applet mate-window-title-applet
  mesa-vulkan-drivers mousepad mozo network-manager-gnome network-manager-openvpn-gnome network-manager-pptp-gnome onboard onboard-data pavucontrol pinentry-gnome3
  plank pluma python3-aptdaemon.gtk3widgets python3-caja qt5-gtk-platformtheme ristretto software-properties-gtk soundconverter spice-vdagent synaptic tilda
  tumbler-plugins-extra ubuntu-release-upgrader-gtk update-manager update-notifier xdg-desktop-portal-gtk xfce4-screenshooter xorg xserver-xorg xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-libinput xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-amdgpu xserver-xorg-video-ati
  xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-nouveau xserver-xorg-video-qxl xserver-xorg-video-radeon xserver-xorg-video-vesa
  xserver-xorg-video-vmware yelp zenity
The following NEW packages will be installed:
  fonts-wine libcapi20-3 libfaudio0 libgpg-error-l10n libodbc2 libstb0 libvkd3d-shader1 libvkd3d1 libwine libz-mingw-w64 notification-daemon pinentry-curses wine
  wine64
The following packages will be upgraded:
  accountsservice bsdutils gir1.2-javascriptcoregtk-4.0 gstreamer1.0-plugins-base gstreamer1.0-x gtk-update-icon-cache libaccountsservice0 libblkid1 libcurl4
  libgail-3-0 libglib2.0-0 libglib2.0-bin libgnutls30 libgstreamer-gl1.0-0 libgstreamer-plugins-base1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libjavascriptcoregtk-4.0-18 libmount1 libnghttp2-14 libtiff5 libxml2 util-linux uuid-runtime xserver-common
26 upgraded, 14 newly installed, 151 to remove and 59 not upgraded.
Need to get 104 MB of archives.
After this operation, 208 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```

(I snipped out the autoremove reminder the the above code message)

---

### Post by 909mjolnir on 2024-05-29
sorry that post was so long, the main idea is, Synaptic and/or Apt both ask to REMOVE stuff that I NEED.  What can I do to install wine without that problem?

---

### Post by Tadaen_Sylvermane on 2024-05-29
I'm thinking something is wrong with your sources.list because that type of thing tends to happen with external repositories quite often. Just a guess. Use code tags. Not blockquote or whatever that is.
[ code ] stuff [ /code ] minus the spaces

---

### Post by 909mjolnir on 2024-05-30
> **Tadaen_Sylvermane said:**
> I'm thinking something is wrong with your sources.list because that type of thing tends to happen with external repositories quite often. Just a guess.


Hey, thanks very much!  That's an angle I would not have thought of.  The only potential wierd source time I know of is when I was using Debian Mint (Linux Mint, LMDE).  I had switched to a non-conventional Debian source instead of the main site.  But I'm not using that anymore.  This has been a clean install of a totally different OS; I haven't edited any sources or repos at all.  I mostly only installed AppImages, but I'll take a look.  It's still not fixed, though.  I'm not sure what else to check.  I've been using normal 'synaptic' and normal 'apt-get' to install my stuff.  This has been my first problem during this session.  It makes me kinda mad, because there's no documentation about if that error happens.  Maybe the tutorial I saw about how to install wine was flakey.

---

### Post by 909mjolnir on 2024-06-02
I couldn't get it solved so unfortunately I just reformatted the entire hard drive and installed a different Linux OS and also a different Wine from a different source.  
Now it's all OK.

---

