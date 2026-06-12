---
title: "Dell Precision 690"
date: 2006-09-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Amalaye on 2006-09-07
Hello,

I have a Dell Precision 690. *The Dell Precision 690 is equipped with up to two 64-bit Dual-Core Intel®  Xeon®  5000/5100 series processors.* ... All other specs can be seen here: [http://www.dell.com/content/products/productdetails.aspx/precn_690?c=us&cs=555&l=en&s=biz&~section=specs#tabtop](http://www.dell.com/content/products/productdetails.aspx/precn_690?c=us&cs=555&l=en&s=biz&~section=specs#tabtop)

I would like to install a 64bit enabled version Ubuntu on it. Can someone please give some guidance and pointers ... I am currently downloading the desktop-amd64.iso ... I just want to make sure that the it takes advantages of my dual-core CPU, sees my drives, firewire and usb ports and likes my monitor (Dell 24 incher). I also want to disable any default firewall type stuff ...

I am an Ubuntu first timer, so any grace extended would be very appreciated.

Thanks!

---

### Post by Kilz on 2006-09-08
> **Amalaye said:**
> Hello,

I have a Dell Precision 690. *The Dell Precision 690 is equipped with up to two 64-bit Dual-Core Intel®  Xeon®  5000/5100 series processors.* ... All other specs can be seen here: [http://www.dell.com/content/products/productdetails.aspx/precn_690?c=us&cs=555&l=en&s=biz&~section=specs#tabtop](http://www.dell.com/content/products/productdetails.aspx/precn_690?c=us&cs=555&l=en&s=biz&~section=specs#tabtop)

I would like to install a 64bit enabled version Ubuntu on it. Can someone please give some guidance and pointers ... I am currently downloading the desktop-amd64.iso ... I just want to make sure that the it takes advantages of my dual-core CPU, sees my drives, firewire and usb ports and likes my monitor (Dell 24 incher). I also want to disable any default firewall type stuff ...

I am an Ubuntu first timer, so any grace extended would be very appreciated.

Thanks!

Dont be suprised if you need to install a driver to get higher resolutions on the monitor. That isnt a 64bit or Ubuntu centric issue. The driver will need to be installed after the os is installed. I dont recommend disabling the iptabels, the firewall. It will alow most things you install through. Disabeling it is inviting attacks. After you install you may want to use the xeon kernel. You wont have to do anything to enable the multi processor support, all 64bit kernels are smp enabled.

---

### Post by monach on 2006-12-13
**Building Ubuntu Linux on Dell Precision 690**

This page describes how I built a desktop using Ubuntu on the Dell Precision 690 workstation.

**Ubuntu Version**

The Dell Precision 690 workstation was configured with two dual-core Intel Xeon processors. Being 64-bit capable I decided to use an amd64 version of the linux distribution from [Ubuntu]("http://www.ubuntu.com/") (AMD designed the first 64 bit processor instruction set and Intel adopted this set, that is why the 64 bit version of distributions are known as the "amd64" set).

Installing Ubuntu 6.06LTS (long-term support) was unsuccessful, however, due to the fact that the [FONT="Courier New"]mptsas[/FONT] module failed to recognise any hard drives. The SAS (serial SATA) controller is a relatively recent technology and the [FONT="Courier New"]mptsas[/FONT] module has had to mature.

Installing Ubuntu 6.10 did the trick, finding the SAS RAID-1 drives with no problems at all.


**Dual Monitor**

With a graphics card of type nVidia N44 the package [FONT="Courier New"]linux-restricted-modules-2.6.17-10-generic[/FONT] had to be removed (by typing [FONT="Courier New"]apt-get remove linux-restricted-modules-2.6.17-10-generic[/FONT] from the command-line) as they contained an old [FONT="Courier New"]nvidia[/FONT] driver. A more modern driver could be downloaded from [nVidia's](http://www.nvidia.com) "Download Drivers" page. The particular page navigated to was [http://www.nvidia.com/object/linux_display_amd64_1.0-9631.html](http://www.nvidia.com/object/linux_display_amd64_1.0-9631.html).

After downloading the file [FONT="Courier New"]NVIDIA-Linux-x86_64-1.0-9631-pkg2.run[/FONT] I installed the [FONT="Courier New"]xorg-dev[/FONT]package and the [FONT="Courier New"]libc6-dev[/FONT] package to ensure the nVidia module could be built.

It was executed with [FONT="Courier New"]sh NVIDIA-Linux-x86_64-1.0-9631-pkg2.run[/FONT]. This built and installed a new kernel module and x-server module. It is important that the kernel and x-server modules have the same version number, this is why the restricted-modules had to be removed, as they contained a clashing kernel module version that would have been loaded by default.

Some updates to the [FONT="Courier New"]/etc/X11/xorg.conf[/FONT] file had to be made for dual-monitor support. Firstly the [FONT="Courier New"]Device[/FONT], [FONT="Courier New"]Screen[/FONT], and [FONT="Courier New"]Monitor[/FONT] sections had to be duplicated (in all cases it was a matter of adding a "2" to the second [FONT="Courier New"]Identifier[/FONT] section, and referring [FONT="Courier New"]Device[/FONT]/[FONT="Courier New"]Screen[/FONT]/[FONT="Courier New"]Monitor[/FONT] keywords). Importantly the [FONT="Courier New"]Device[/FONT] section was a little different (with an additional [FONT="Courier New"]Screen[/FONT] keyword):

```

Section "Device"
    Identifier     "NVIDIA Corporation NV44 [Quadro NVS 285]"
    Driver         "nvidia"
    BusID          "PCI:7:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV44 [Quadro NVS 285] 2"
    Driver         "nvidia"
    BusID          "PCI:7:0:0"
    Screen          1
EndSection

```

Lastly the [FONT="Courier New"]ServerLayout[/FONT] section had to be changed to support [FONT="Courier New"]Xinerama[/FONT] mode (one big screen across multiple monitors):

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    Screen      1  "Default Screen 2" RightOf "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    Option         "Xinerama"
EndSection

```

For the sake of completeness just one example of the [FONT="Courier New"]Monitor[/FONT] and [FONT="Courier New"]Screen[/FONT] sections will be given:

```

Section "Monitor"
    Identifier     "DELL 2007FP"
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV44 [Quadro NVS 285]"
    Monitor        "DELL 2007FP"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

Note, some applications do not work well with nVidia cards. One notable such application is [FONT="Courier New"]gnome-terminal[/FONT]. A work around is to start the application with the [FONT="COURIER NEW"]XLIB_SKIP_ARGB_VISUALS[/FONT] environment variable set to 1 (true). e.g.
[LIST]
   [*] [FONT="Courier New"]XLIB_SKIP_ARGB_VISUALS=1 gnome-terminal &[/FONT] (see also [gentoo-wiki]("http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency"))
[/LIST]


**Apt Configuration**

In [FONT="Courier New"]/etc/apt/sources.list[/FONT] I added the University of Kent local UK mirror:

```

deb http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/ edgy main restricted universe
deb-src http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/ edgy main restricted universe

```


**Macromedia Flash for Ubuntu/amd64 and Firefox 2.0**

(from [http://marius.scurtescu.com/?p=139]("http://marius.scurtescu.com/?p=139"))

[LIST=1]
   [*] Get [nspluginwrapper]("http://gwenole.beauchesne.info/en/projects/nspluginwrapper")
   [*] Download the Plugin and the Viewer
   [*] Install [FONT="Courier New"]alien[/FONT] and [FONT="Courier New"]linux32[/FONT], if not already installed.
   [*] Convert the downloaded rpm's to deb's
      [FONT="Courier New"]$ sudo alien -d *.rpm[/FONT]
   [*] Install the newly created debs:
      [FONT="Courier New"]$ sudo dpkg -i nspluginwrapper-i386_0.9.90-2_amd64.deb[/FONT]
      [FONT="Courier New"]$ sudo dpkg -i nspluginwrapper_0.9.90-2_amd64.deb[/FONT]
   [*] Download the plugin you want to install, and extract the .so file. For example, to install flash, grab the tar.gz file from Macromedia's website, and extract [FONT="Courier New"]libflashplayer.so[/FONT].
   [*] Move the plugin ([FONT="Courier New"]libflashplayer.so[/FONT]) to [FONT="Courier New"]/usr/lib/mozilla/plugins[/FONT]. This is where [FONT="Courier New"]nspluginwrapper[/FONT] stores the main plugin, so it's probably a nice folder to keep them.
   [*] Now we need [FONT="Courier New"]nsplugwrapper[/FONT] to make the new plugin, so call:
      [FONT="Courier New"]$ sudo /usr/lib/nspluginwrapper/x86_64/npconfig -i /usr/lib/mozilla/plugins/libflashplayer.so[/FONT]
      It will either end up in /usr/lib/mozilla/plugins. Copy the generated plugin to the main plugins folder:
      [FONT="Courier New"]$ sudo cp /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla-firefox/plugins/[/FONT]
[/LIST]

That's what someone else says should be done. Here's what I did:

[LIST=1]
   [*] Get nspluginwrapper [FONT="Courier New"]plugin[/FONT] rpm and [FONT="Courier New"]viewer[/FONT] rpm packages from [http://gwenole.beauchesne.info/en/projects/nspluginwrapper](http://gwenole.beauchesne.info/en/projects/nspluginwrapper)
   [*] Install [FONT="Courier New"]alien[/FONT] and [FONT="Courier New"]linux32[/FONT] using [FONT="Courier New"]apt-get install alien linux32[/FONT]
   [*] Convert downloaded rpm's to deb's
      [FONT="Courier New"]$ alien -d *.rpm[/FONT]
   [*] Install newly created deb packages:
      [FONT="Courier New"]$ dpkg -i nspluginwrapper-i386_0.9.90-2_amd64.deb[/FONT]
      [FONT="Courier New"]$ dpkg -i nspluginwrapper_0.9.90-2_amd64.deb[/FONT]
   [*] Download macromedia flash from [http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4](http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4)
   [*] Extract the [FONT="Courier New"].tar.gz[/FONT] and copy [FONT="Courier New"]flashplayer.xpt[/FONT] and [FONT="Courier New"]libflashplayer.so[/FONT] into [FONT="Courier New"]/usr/lib/mozilla/plugins[/FONT].
   [*] Run [FONT="Courier New"]npconfig -v -a -i[/FONT]. You should see
      [FONT="Courier New"]Looking for plugins in /usr/lib/mozilla/plugins[/FONT]
      [FONT="Courier New"]Install plugin /usr/lib/mozilla/plugins/libflashplayer.so[/FONT]
      [FONT="Courier New"]  into /usr/lib64/mozilla/plugins/npwrapper.libflashplayer.so[/FONT]
   [*] Copy [FONT="Courier New"]npwrapper.so[/FONT], [FONT="Courier New"]npwrapper.libflashplayer.so[/FONT], [FONT="Courier New"]libflashplayer.so[/FONT], [FONT="Courier New"]flashplayer.xpt[/FONT] from [FONT="Courier New"]/usr/lib64/mozilla/plugins[/FONT] into [FONT="Courier New"]/usr/lib/firefox/plugins[/FONT].
   [*] Install the 32 bit libraries
      [FONT="Courier New"]apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux32[/FONT]
   [*] Restart firefox.
   [*] Visit [noparse]about:plugins[/noparse] to check that Shockwave Flash is listed.
[/LIST]

Now I can visit [http://www.youtube.com/](http://www.youtube.com/) successfully (as well as other flash-enabled sites).

---

