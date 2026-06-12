---
title: "Adobe Flash install information for AMD64 (September 2009 update)"
date: 2009-09-05
forum: x86 64-bit Users
---

### Post by michael37 on 2009-09-05
**this thread has been removed.  Superceeded by [thread="1358591"]new thread[/thread]**

---

### Post by Clancy_s on 2009-09-06
Thank you. :)

---

### Post by bruno9779 on 2009-09-11
I am trying this out as soon as i get home

thanks

---

### Post by bapoumba on 2009-09-12
Stuck thread as a continuation of [http://ubuntuforums.org/showthread.php?p=7938752](http://ubuntuforums.org/showthread.php?p=7938752) that did not look supported by the OP any longer.

---

### Post by DodgeV83 on 2009-09-13
On a brand new install of 64bit with the newest flash alpha I experienced immediate crashes when attempting to view a Hulu video, or an ign.com video.  Youtube was fine.  All sites worked with the normal flash release.

This happened on Firefox 3.0, 3.5 and Opera.

After banging my head on this for a few hours, I enabled the "backports" and "proposed" releases in Synaptic, did a full update and bam, no more crashes :)

Hope this helps someone else with the same problem.

---

### Post by michael37 on 2009-09-13
> **DodgeV83 said:**
> On a brand new install of 64bit with the newest flash alpha I experienced immediate crashes when attempting to view a Hulu video, or an ign.com video.  Youtube was fine.  All sites worked with the normal flash release.

This happened on Firefox 3.0, 3.5 and Opera.

After banging my head on this for a few hours, I enabled the "backports" and "proposed" releases in Synaptic, did a full update and bam, no more crashes :)

Hope this helps someone else with the same problem.
It would be helpful if you specified your version of OS.

---

### Post by DodgeV83 on 2009-09-13
> **michael37 said:**
> It would be helpful if you specified your version of OS.

Ubuntu 9.04 64 bit

---

### Post by vkimball on 2009-09-13
Tried the script on Ubuntu 8.04 AMD64 and flash doesn't work at all anymore.

---

### Post by michael37 on 2009-09-13
> **vkimball said:**
> Tried the script on Ubuntu 8.04 AMD64 and flash doesn't work at all anymore.

could you please post output of command 
```

ldd /usr/lib/mozilla/plugins/libflashplayer.so 

```

---

### Post by skunkfifty on 2009-09-14
> **michael37 said:**
> could you please post output of command 
```

ldd /usr/lib/mozilla/plugins/libflashplayer.so 

```

I'm having the same issue, typing that command gets me "No such file or directory"

---

### Post by skunkfifty on 2009-09-14
> **skunkfifty said:**
> I'm having the same issue, typing that command gets me "No such file or directory"

Out of curiosity I ran the the script line-by-line to see if some step was failing. All steps ran properly, now when i type "ldd /usr/lib/mozilla/plugins/libflashplayer.so" I get:

    linux-vdso.so.1 =>  (0x00007fffb61fe000)
    libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007f51a918a000)
    libpthread.so.0 => /lib/libpthread.so.0 (0x00007f51a8f6e000)
    libX11.so.6 => /usr/lib/libX11.so.6 (0x00007f51a8c66000)
    libXext.so.6 => /usr/lib/libXext.so.6 (0x00007f51a8a54000)
    libXt.so.6 => /usr/lib/libXt.so.6 (0x00007f51a87ee000)
    libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00007f51a8567000)
    libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00007f51a8335000)
    libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0x00007f51a7d39000)
    libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0x00007f51a7a96000)
    libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0x00007f51a7876000)
    libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x00007f51a765a000)
    libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x00007f51a744d000)
    libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x00007f51a7204000)
    libcairo.so.2 => /usr/lib/libcairo.so.2 (0x00007f51a6f81000)
    libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x00007f51a6d3a000)
    libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x00007f51a6b36000)
    libdl.so.2 => /lib/libdl.so.2 (0x00007f51a6932000)
    libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0x00007f51a666c000)
    libnss3.so => /usr/lib/libnss3.so (0x00007f51a6336000)
    libsmime3.so => /usr/lib/libsmime3.so (0x00007f51a610a000)
    libssl3.so => /usr/lib/libssl3.so (0x00007f51a5ed1000)
    libplds4.so => /usr/lib/libplds4.so (0x00007f51a5ccd000)
    libplc4.so => /usr/lib/libplc4.so (0x00007f51a5ac8000)
    libnspr4.so => /usr/lib/libnspr4.so (0x00007f51a588a000)
    libm.so.6 => /lib/libm.so.6 (0x00007f51a5605000)
    libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007f51a53ed000)
    libc.so.6 => /lib/libc.so.6 (0x00007f51a507a000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f51ae0b7000)
    libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007f51a4e5e000)
    libXau.so.6 => /usr/lib/libXau.so.6 (0x00007f51a4c5b000)
    libSM.so.6 => /usr/lib/libSM.so.6 (0x00007f51a4a51000)
    libz.so.1 => /lib/libz.so.1 (0x00007f51a4839000)
    libexpat.so.1 => /usr/lib/libexpat.so.1 (0x00007f51a460f000)
    libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00007f51a4404000)
    libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x00007f51a4202000)
    libXi.so.6 => /usr/lib/libXi.so.6 (0x00007f51a3ff7000)
    libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x00007f51a3ded000)
    libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x00007f51a3be3000)
    libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0x00007f51a39e0000)
    libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x00007f51a37dd000)
    libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x00007f51a35d8000)
    libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0x00007f51a335b000)
    libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x00007f51a312c000)
    libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0x00007f51a2ee7000)
    libdirectfb-1.0.so.0 => /usr/lib/libdirectfb-1.0.so.0 (0x00007f51a2c72000)
    libfusion-1.0.so.0 => /usr/lib/libfusion-1.0.so.0 (0x00007f51a2a69000)
    libdirect-1.0.so.0 => /usr/lib/libdirect-1.0.so.0 (0x00007f51a2853000)
    libpng12.so.0 => /usr/lib/libpng12.so.0 (0x00007f51a262b000)
    libxcb-render-util.so.0 => /usr/lib/libxcb-render-util.so.0 (0x00007f51a2427000)
    libxcb-render.so.0 => /usr/lib/libxcb-render.so.0 (0x00007f51a221e000)
    libpcre.so.3 => /lib/libpcre.so.3 (0x00007f51a1fed000)
    libnssutil3.so => /usr/lib/libnssutil3.so (0x00007f51a1dce000)
    libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007f51a1bc8000)
    libICE.so.6 => /usr/lib/libICE.so.6 (0x00007f51a19ad000)
    libuuid.so.1 => /lib/libuuid.so.1 (0x00007f51a17a8000)
    libselinux.so.1 => /lib/libselinux.so.1 (0x00007f51a158b000)

Flash still does not work however.

---

### Post by PeterBBB on 2009-09-14
> **michael37 said:**
> 

... may cause problems in Hardy ... 



Only problem here is that Flash still does not work. (Script seems to run fine)

"*Hello, you either have JavaScript turned off *[I don't]* or an old version of Adobe's Flash Player. **Get the latest Flash player**.* [For how many more times!?]" 

FWIW my output from that command is

ldd /usr/lib/mozilla/plugins/libflashplayer.so

	linux-vdso.so.1 =>  (0x00007fffd11ef000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007f9ac4236000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007f9ac401a000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00007f9ac3d16000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00007f9ac3b05000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0x00007f9ac38a1000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00007f9ac3623000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00007f9ac33f1000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0x00007f9ac2e22000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0x00007f9ac2b87000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0x00007f9ac2967000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x00007f9ac274d000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x00007f9ac2541000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x00007f9ac22fd000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0x00007f9ac2082000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x00007f9ac1e3c000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x00007f9ac1c39000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007f9ac1a35000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0x00007f9ac1774000)
	libnss3.so => /usr/lib/libnss3.so (0x00007f9ac1442000)
	libsmime3.so => /usr/lib/libsmime3.so (0x00007f9ac1217000)
	libssl3.so => /usr/lib/libssl3.so (0x00007f9ac0fe4000)
	libplds4.so => /usr/lib/libplds4.so (0x00007f9ac0de1000)
	libplc4.so => /usr/lib/libplc4.so (0x00007f9ac0bdd000)
	libnspr4.so => /usr/lib/libnspr4.so (0x00007f9ac09a0000)
	libm.so.6 => /lib/libm.so.6 (0x00007f9ac071f000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007f9ac0508000)
	libc.so.6 => /lib/libc.so.6 (0x00007f9ac01a5000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f9ac915f000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0x00007f9abffa4000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007f9abfd89000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00007f9abfb86000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0x00007f9abf97e000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0x00007f9abf763000)
	libz.so.1 => /usr/lib/libz.so.1 (0x00007f9abf54b000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0x00007f9abf327000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0x00007f9abf125000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x00007f9abef22000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x00007f9abed1d000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00007f9abeb14000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x00007f9abe911000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0x00007f9abe708000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x00007f9abe501000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x00007f9abe2f6000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x00007f9abe0ca000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0x00007f9abde85000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0x00007f9abdc60000)
	libxcb-render-util.so.0 => /usr/lib/libxcb-render-util.so.0 (0x00007f9abda5c000)
	libxcb-render.so.0 => /usr/lib/libxcb-render.so.0 (0x00007f9abd852000)
	libpcre.so.3 => /usr/lib/libpcre.so.3 (0x00007f9abd62c000)
	libnssutil3.so.1d => /usr/lib/libnssutil3.so.1d (0x00007f9abd40e000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007f9abd208000)

---

### Post by PeterBBB on 2009-09-14
**Sorted!!**

Looks to me that /usr/lib/mozilla/plugins is the wrong place.
I moved the library to /usr/firefox-addons/plugins and it works. Amazing!

I have a directory /usr/lib/firefox-3.0.14 which has a symlink subdirectory /plugins.  I guess that needs to point to wherever the library is?  Your mileage may vary, as they say.

---

### Post by Flywaver on 2009-09-14
Thanks a LOT michael37, your fix worked!! :)

---

### Post by Flywaver on 2009-09-15
ok unfortunately I just lost Flash in FF 3.5! :(
I didn't install/modify anything and it was working fine until I installed the patch and up to a few hours ago! :(

Flash works fine in FF 3.14 and Opera!

---

### Post by michael37 on 2009-09-15
> **Flywaver said:**
> ok unfortunately I just lost Flash in FF 3.5! :(
I didn't install/modify anything and it was working fine until I installed the patch and up to a few hours ago! :(

Flash works fine in FF 3.14 and Opera!

Try to run a command
```

sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/

```
and restart Firefox 3.5.  Let me know if it starts working.

---

### Post by Flywaver on 2009-09-15
> **michael37 said:**
> Try to run a command
```

sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/

```
and restart Firefox 3.5.  Let me know if it starts working.

Ok it worked for Youtube but some sites say I don't have Flash Player! :(

---

### Post by acids7n on 2009-09-16
> **michael37 said:**
> ***** This is an updated version of the script since the original maintainer has not updated it in a while.  Provides August 2009's version of 64-bit Adobe Flash *** **

Works very well in Jaunty and Karmic, may cause problems in Hardy (the latter is still being investigated).

1. Download Get64bitFlash-0.2.tar.gz script below (use "Right Click, Save Link As...)
2. Right click on the tar.gz and select "Extract Here"
3. Close all browsers.
4. Inside the folder that extracts is a "Get64bitFlash" file, double click on it.
5. Select "Run in Terminal"
6. When the terminal closes, restart your browser.
7. Your done.

worked great here, thank you, working in chromium and ff 3.1.x

---

### Post by michael37 on 2009-09-16
> **acids7n said:**
> worked great here, thank you, working in chromium and ff 3.1.x

Gotta try a new version of Chromium.  My older version is still 32-bit so it can't execute the plugin.

---

### Post by michael37 on 2009-09-16
> **Flywaver said:**
> Ok it worked for Youtube but some sites say I don't have Flash Player! :(

Consider adding [Mozilla-Security PPA]("https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa") and install Firefox 3.5.3 (Ubuntu-ized version available for Jaunty and Karmic).

---

### Post by Poobanks on 2009-09-16
Alright, I've tried about every recommendation I've found online. I run x86 64-bit Ubuntu 9.04.

I upgraded to Firefox 3.53 about 3 days ago and the Flash player/plugin have not worked with this version. Using the directions above, the script completed successfully. But I still cannot view the video on the link.

I tried creating the soft-link, which worked, but Firefox still does not see this plugin.

Any other ideas?

---

### Post by pyroclastic on 2009-09-16
Thank you was real helpfull

---

### Post by pyroclastic on 2009-09-16
> **Poobanks said:**
> Alright, I've tried about every recommendation I've found online. I run x86 64-bit Ubuntu 9.04.

I upgraded to Firefox 3.53 about 3 days ago and the Flash player/plugin have not worked with this version. Using the directions above, the script completed successfully. But I still cannot view the video on the link.

I tried creating the soft-link, which worked, but Firefox still does not see this plugin.

Any other ideas?


Dude, try to update ur repositories, or loook for flash player in ur synaptic package manager.. i have flash player and i didint looked for them, just selected in SPM:popcorn:

---

### Post by northwestuntu on 2009-09-17
> **bapoumba said:**
> Stuck thread as a continuation of [http://ubuntuforums.org/showthread.php?p=7938752](http://ubuntuforums.org/showthread.php?p=7938752) that did not look supported by the OP any longer.

thanks for updating that.

---

### Post by michael37 on 2009-09-17
> **Poobanks said:**
> Alright, I've tried about every recommendation I've found online. I run x86 64-bit Ubuntu 9.04.

I upgraded to Firefox 3.53 about 3 days ago and the Flash player/plugin have not worked with this version. Using the directions above, the script completed successfully. But I still cannot view the video on the link.

I tried creating the soft-link, which worked, but Firefox still does not see this plugin.

Any other ideas?

Did you use the version from mozilla-security or from mozilla.org?

Please run Help/About and post your User Agent string.  Should look something like Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.3) Gecko/20090902 Ubuntu/9.10 (karmic) Firefox/3.5.3

---

### Post by michael37 on 2009-09-17
> **pyroclastic said:**
> Dude, try to update ur repositories, or loook for flash player in ur synaptic package manager.. i have flash player and i didint looked for them, just selected in SPM

If you use repositories, you are probably running 32-bit version of Flash.  Not 64-bit version.  Does it matter?  Up to you.

---

### Post by Flywaver on 2009-09-17
> **michael37 said:**
> Consider adding [Mozilla-Security PPA]("https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa") and install Firefox 3.5.3 (Ubuntu-ized version available for Jaunty and Karmic).

Thanks Michael! 
All is good to normal with 3.5.3! :)

---

### Post by Flywaver on 2009-09-17
Grrrrr it started to freak out on me again! ](*,)

Once a while there is a light blue rectangle instead of a youtube video....if I hit refresh then the video appears! 
Same issue if I let a video load and go to another tab, then come back to youtube's tab the video dissapears! :(

---

### Post by michael37 on 2009-09-17
> **Flywaver said:**
> Grrrrr it started to freak out on me again! ](*,)

Once a while there is a light blue rectangle instead of a youtube video....if I hit refresh then the video appears! 
Same issue if I let a video load and go to another tab, then come back to youtube's tab the video dissapears! :(

Do you have an Intel video card?

---

### Post by Flywaver on 2009-09-17
> **michael37 said:**
> Do you have an Intel video card?

Nope nVidia 6800 GS TDH

---

### Post by michael37 on 2009-09-17
> **Flywaver said:**
> Nope nVidia 6800 GS TDH

I have a hunch it's a graphics issue rather than Firefox/Flash issue, but I can't tell for sure.  I don't have Nvidia, so I can't really tell.

---

### Post by Tomas79 on 2009-09-18
G'day, is there something I can do to speed up Flash Videos in full screen on my amd64 ubuntu 9.04?? I do have the hardware accelaration ticked, but youtube  and other flash sites run slow in full screen. You tube ren perfectly in Windows??

Thanks
:confused::confused:

---

### Post by wm_brant on 2009-09-18
My system is 64-bit Ubuntu 9.04 and Shiretoko 3.5.2.  

I followed the procedure on the first page of this thread and while I had no errors,  I also had no Flash.  I then restarted my computer, and after the restart, Flash was working.  

...I can't explain this, this is just what worked for me...

  --Bill

---

### Post by Conzo on 2009-09-18
> **michael37 said:**
> ***** This is an updated version of the script since the original maintainer has not updated it in a while.  Provides August 2009's version of 64-bit Adobe Flash *** **

Designed for **64-bit** Hardy, Jaunty and Karmic.

1. Download Get64bitFlash-0.2.1.tar.gz script below (use "Right Click, Save Link As...)
2. Right click on the tar.gz and select "Extract Here"
3. Close all browsers.
4. Inside the folder that extracts is a "Get64bitFlash" file, double click on it.
5. Select "Run in Terminal"
6. When the terminal closes, restart your browser.
7. Test by going to [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/).  Version 10.0.32.18 should show up in "About" box.  

P.S.  Shockwave is not available for Linux (noone uses it anyway).

Changelog.
Version 0.2.1
Adds a symlink to /usr/lib/firefox-addons/plugins
Version 0.2
Updates for the version 10.0.32.18 of Adobe Flash


Thank you So Much Works great easy to do ! 


Conzo

---

### Post by michael37 on 2009-09-19
> **Tomas79 said:**
> G'day, is there something I can do to speed up Flash Videos in full screen on my amd64 ubuntu 9.04?? I do have the hardware accelaration ticked, but youtube  and other flash sites run slow in full screen. You tube ren perfectly in Windows??

Thanks
:confused::confused:

If you have an Intel video card, you may be affected by a bug which severely crippled flash, esp in full screen mode.  See my original post for the updated info.  Additionally, you may want to follow the link in troubleshooting and follow other performance optimizations.

---

### Post by Poobanks on 2009-09-20
Thanks for the suggestion.

I ended up removing the flashplugin-installer and nspluginwrapper, then adding the libflashplayer.so plugin to /usr/lib/mozilla/plugins and restarted Firefox. The plugin is working so far...

Here's a link I used - 
[http://queleimporta.com/en/finally-adobe-releases-native-64-bit-flash-10-for-linux/](http://queleimporta.com/en/finally-adobe-releases-native-64-bit-flash-10-for-linux/)

---

### Post by superark on 2009-09-21
Thanks,though I had installed it:P

---

### Post by Tomas79 on 2009-09-21
> **michael37 said:**
> If you have an Intel video card, you may be affected by a bug which severely crippled flash, esp in full screen mode.  See my original post for the updated info.  Additionally, you may want to follow the link in troubleshooting and follow other performance optimizations.

Thanks, I'll try following the trouble shooting link, as i have a nvidia 6600 GT, with the nvidia driver running perfectly.

---

### Post by arpanaut on 2009-09-22
Thanks, This fresh script worked like a charm on a fresh install of Hardy & was the last piece of the puzzle on a machine I set up for a new Ubuntu user user.
His reaction was WOW! that was easy.... Just had to laugh, hope the rest of his "orientation" goes as well.

Thanks again!

---

### Post by shaunsmith_99 on 2009-09-23
HOLY COW this is good stuff!!!!!! Bump Bump bump and hope someone else gets it too!! :P

---

### Post by DodgeV83 on 2009-09-24
It seemed no matter what I did, flash was incredibly choppy on my dual-core recent Dell laptop.  I had simply given up lately and decided it was just something I'd have to deal with as long as I was with Linux.  This was a contributing factor to me dropping Linux for Windows a while back, but I figured I could do without flash videos...

Well today I had enough and looked again for a solution.  I noticed the video was noticeably better when the laptop is plugged in, even though choppiness was still abundant enough to make me simply not want to watch any flash videos full-screen.

After trying all the beta NVidia drivers and everything else on the forums, I had never thought to check my CPU.

My research brought me here:

[http://maketecheasier.com/how-to-control-your-cpu-frequency-in-ubuntu/2009/04/10](http://maketecheasier.com/how-to-control-your-cpu-frequency-in-ubuntu/2009/04/10)

I simply added the Gnome CPU Frequency Scaling Monitor to my panel and set it to as high as it goes, 2.4GHZ.

FLASH IS PERFECT NOW!

I hope this helps someone out!

---

### Post by merlin666 on 2009-09-26
It worked not too bad in Shiretoko 3.5.2, but now update to 3.5.3 crashes with many flash sites. Hopefully the next version will be more stable.

---

### Post by michael37 on 2009-09-27
> **merlin666 said:**
> It worked not too bad in Shiretoko 3.5.2, but now update to 3.5.3 crashes with many flash sites. Hopefully the next version will be more stable.

All of us, including myself, have occasional trouble with flash, but I have not observed any difference in stability between versions 3.5.2 and 3.5.3.  Check whether you changed anything else while upgrading FF.

Regardless, [Restart Firefox]("https://addons.mozilla.org/addon/3559") is a handy extension to have with Flash in its current _ALPHA_ stage.

---

### Post by FrancoNero on 2009-09-27
wouldn't it make sense to have 64bit Flash by default when I install a 64bit Ubuntu OS? bugs me

---

### Post by jbarzuna on 2009-09-27
Hi 
I'm prety new on ubuntu but I'm having that issue too
I've been about 2 days trying to install the flash and I cant get it to work
I've tryed dowloading it in a tgz and in an rpm and pasing it through the alien so it converts into a dev package but none of them have worked for me, and the dowload of the dev package shows me an error  
[CENTER]**[COLOR=Red]Error: Wrong architecture 'i386'[/COLOR]**
[/CENTER]
and I dont know how to solve it

---

### Post by FrancoNero on 2009-09-28
> **jbarzuna said:**
> 
[CENTER]**[COLOR=Red]Error: Wrong architecture 'i386'[/COLOR]**
[/CENTER]
and I dont know how to solve it

sounds like you're running something 32bit on 64bit or vice versa

---

### Post by VampireSausage on 2009-09-28
Hey I'm using 64 bit Firefox 3.5 on Ubuntu 9.04 64 bit and flash still wont work for me after running your script.
Any ideas what I could be doing wrong?

---

### Post by D3mon_Spawn on 2009-09-28
I followed the exact steps and when the installation finished I got a crashed report. I just ignored it and opened up Firefox and flash was working fine. Very weird.

---

### Post by michael37 on 2009-09-29
> **FrancoNero said:**
> wouldn't it make sense to have 64bit Flash by default when I install a 64bit Ubuntu OS? bugs me

64-bit Flash from Adobe is in the Alpha stage.  There are recognized stability and performance issues; and in general, I would not put the Alpha software by default.

However, 64-bit Flash works for me (and works better than alternatives).  IMHO it's worth trying.

---

### Post by michael37 on 2009-09-29
> **VampireSausage said:**
> Hey I'm using 64 bit Firefox 3.5 on Ubuntu 9.04 64 bit and flash still wont work for me after running your script.
Any ideas what I could be doing wrong?

How did you install Firefox?  This script works only with 64-bit Ubuntu-provided version.   Most common cause of the problem like yours is running 32-bit Firefox 3.5 and not realizing it.

---

### Post by michael37 on 2009-09-29
> **D3mon_Spawn said:**
> I followed the exact steps and when the installation finished I got a crashed report. I just ignored it and opened up Firefox and flash was working fine. Very weird.

I am not sure I understand what exactly crashed... but sounds like all is good.  In general, you must restart Firefox after the script execution.

---

### Post by FrancoNero on 2009-09-29
I think one way to install it is to remove all the ndispluginwrapper stuff and just put the 64bit .so file into the folder where it belongs, right?

---

### Post by BladeMelbourne on 2009-09-29
Thanks @michael37.

I ran this on Xubuntu Karmic (Daily Build - 28th Sept 2009).
On first run, I got this:
> libflashplayer.so
> mv: cannot move `libflashplayer.so' to `/usr/lib/mozilla/plugins/': Not a directory
So I created the directory and re-ran the script.

Flash is now working fine in Firefox 3.5.3 and Opera 10. This was far easier than the hoops I had to jump through for Ubuntu 9.04. Thanks again.

---

### Post by michael37 on 2009-09-29
> **FrancoNero said:**
> I think one way to install it is to remove all the ndispluginwrapper stuff and just put the 64bit .so file into the folder where it belongs, right?

That is correct.  The trick is making sure you remove all ndispluginwrapper from all the relevant directories.

---

### Post by michael37 on 2009-09-29
> **BladeMelbourne said:**
> Thanks @michael37.

I ran this on Xubuntu Karmic (Daily Build - 28th Sept 2009).
On first run, I got this:
> libflashplayer.so
> mv: cannot move `libflashplayer.so' to `/usr/lib/mozilla/plugins/': Not a directory
So I created the directory and re-ran the script.

Flash is now working fine in Firefox 3.5.3 and Opera 10. This was far easier than the hoops I had to jump through for Ubuntu 9.04. Thanks again.
It's highly unusual that you didn't have this directory.  It's created by a number of other useful plugins.  

Here are the packages that create and populate this directory for me:

$ dpkg -S /usr/lib/mozilla/plugins
rhythmbox, totem-mozilla, icedtea6-plugin, acroread, nspluginwrapper, mozilla-plugin-vlc, picasa

---

### Post by VampireSausage on 2009-09-29
> **michael37 said:**
> How did you install Firefox?  This script works only with 64-bit Ubuntu-provided version.   Most common cause of the problem like yours is running 32-bit Firefox 3.5 and not realizing it.
I can't remember how i installed it.

When i click about it says:

Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9.1) Gecko/20090624 Firefox/3.5

that is 64 bit firefox right?

I tried to reinstall it just incase but whenever i try to uninstall it i get this message:

Cannot remove 'firefox-3.0-branding'

One or more applications depend on firefox-3.0-branding. To remove firefox-3.0-branding and the dependent applications, use the Synaptic package manager.

What do i need to do?
I'm relatively new to ubuntu.

---

### Post by michael37 on 2009-09-29
> **VampireSausage said:**
> I can't remember how i installed it.

When i click about it says:

Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9.1) Gecko/20090624 Firefox/3.5

that is 64 bit firefox right?

I tried to reinstall it just incase but whenever i try to uninstall it i get this message:

Cannot remove 'firefox-3.0-branding'

One or more applications depend on firefox-3.0-branding. To remove firefox-3.0-branding and the dependent applications, use the Synaptic package manager.

What do i need to do?
I'm relatively new to ubuntu.

Yeah you got yourself in a pickle.  I also don't know how you installed Firefox 3.5, but it doesn't look quite usable.  

When you are trying to reinstall, you are touching firefox 3.0.  Don't bugger FF 3.0, let it be.  It doesn't really interfere with 3.5 on Ubuntu.

Do this, go to Synaptic and try to install or reinstall package "firefox-3.5" and "firefox-3.5-gnome-support".  Let's see how it works.

---

### Post by VampireSausage on 2009-09-29
> **michael37 said:**
> Yeah you got yourself in a pickle.  I also don't know how you installed Firefox 3.5, but it doesn't look quite usable.  

When you are trying to reinstall, you are touching firefox 3.0.  Don't bugger FF 3.0, let it be.  It doesn't really interfere with 3.5 on Ubuntu.

Do this, go to Synaptic and try to install or reinstall package "firefox-3.5" and "firefox-3.5-gnome-support".  Let's see how it works.
I installed both of those but still nothing.
What if i switch to a different browser?
will it work then?
what's good? Opera?

ok i just tried to install opera using:
```
sudo aptitude install opera
```

It gave me this:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Do you think these things could be related?

---

### Post by michael37 on 2009-09-29
> **VampireSausage said:**
> I installed both of those but still nothing.
What if i switch to a different browser?
will it work then?
what's good? Opera?

I don't use Opera so I can't support it.

Firefox 3.5 is not actually called Firefox, it's called "Shiretoko" under Applications/Internet.

---

### Post by VampireSausage on 2009-09-29
> **michael37 said:**
> I don't use Opera so I can't support it.

Firefox 3.5 is not actually called Firefox, it's called "Shiretoko" under Applications/Internet.

Yes!
It works:)
Thank you so much, i was afraid i would have to go back to vista if i couldn't get it to work.

---

### Post by BladeMelbourne on 2009-09-30
> **VampireSausage said:**
> 
ok i just tried to install opera using:
```
sudo aptitude install opera
```

It gave me this:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


In my experience, this means that another application (Synaptic, Update Manager/Agent) is open, blocking aptitude from working. Only one application can install/update packages at any one time. Try closing all applications except one terminal window and using:
```
sudo apt-get install opera
```

I can confirm that this script plays nicely with Opera - in fact Opera uses the plugins in the Mozilla plugin directory.

> **michael37 said:**
> It's highly unusual that you didn't have this directory.  It's created by a number of other useful plugins.  

Here are the packages that create and populate this directory for me:

$ dpkg -S /usr/lib/mozilla/plugins
rhythmbox, totem-mozilla, icedtea6-plugin, acroread, nspluginwrapper, mozilla-plugin-vlc, picasa

That explains it - I have none of those plugins (minimalistic installation).
```

dpkg -S /usr/lib/mozilla/plugins
dpkg: /usr/lib/mozilla/plugins not found.

```

---

### Post by itsbrad212 on 2009-10-05
if the code originally posted in this thread doesn't work, then try this:

 first, close all firefox windows. then open Applications>Accessories>Terminal and type this in:

```

**sudo apt-get install flashplugin-nonfree**

```

---

### Post by dBuster on 2009-10-06
> **itsbrad212 said:**
> if the code originally posted in this thread doesn't work, then try this:

 first, close all firefox windows. then open Applications>Accessories>Terminal and type this in:

```

**sudo apt-get install flashplugin-nonfree**

```

Is the nonfree plugin you mention a 32bit flash plugin?  I believe it is.  It is not a true 64bit plugin.  Hence the 64bit flash install scripts remove any non 64bit flash which I believe also includes the nonfree plugin you mention.

---

### Post by miegiel on 2009-10-06
> **dBuster said:**
> Is the nonfree plugin you mention a 32bit flash plugin?  I believe it is.  It is not a true 64bit plugin.  Hence the 64bit flash install scripts remove any non 64bit flash which I believe also includes the nonfree plugin you mention.

No it's not, the 64bit flashplayer is not in the repos (unless I missed something ;))

---

### Post by NoaHall on 2009-10-07
Of course it's not in the repos- it's a alpha still. A solid, great alpha, but still. Policies will be policies.

---

### Post by thekat on 2009-10-08
Installed Karmic yesterday..
Found your script today...
Installed today...
Worked without issue... 

Thx
tk

---

### Post by x C0MMAND0 x on 2009-10-08
> **michael37 said:**
> 
P.S.  Shockwave is not available for Linux (noone uses it anyway).


Hello.  I have been trying to get a website to work that I believe uses shockwave and I have not been able to.  The website is [www.calcchat.com](www.calcchat.com)  Go there and then click on "Click HERE for free access".

Any ideas?

---

### Post by MntlWard on 2009-10-09
I am having a lot of trouble with this plugin.  I'm running Ubuntu 9.04 on an AMD64 machine.  I'm using 64-bit Firefox 3.0.14.

Adobe's instructions about how to install didn't work.

Copying libflashplayer.so to the plugins folder didn't work.

A guy told me to download and run the .deb file, but I got the error message  "Error: Wrong architecture 'i386'" when trying that.  he told me to run the code "dpkg -i --force-architecture install_flash_player_10_linux.deb" to force it.  I was told I needed to be a superuser to run that code, so I added "sudo" to the front of it.  It did something, but flash still wouldn't work except for on YouTube, which wasn't perfect.

I had forgotten to uninstall swfdec, and didn't know how until I discovered that the Synaptic Package Manager is different than the Add/Remove tool.  So I removed swfdec and tried installing from the .deb again.  Didn't work.

I uninstalled and reinstalled Firefox.  Tried the .deb again.  Didn't work.

I sort of resigned myself to having to boot up in Windows to watch anything on hulu, and was willing to settle for imperfect YouTube until today when YouTube decided the swfdec wasn't good enough, either.

I was crushed until I found [this lovely set of instructions]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins"), which *worked*!  I enjoyed watching some hulu stuff without having to reboot into Windows, and I tried playing some flash games, but Kongregate kept locking up my browser, so I gave up on gaming.

But later, when I decided I was going to watch Fringe on hulu, the black screen faced me again.  YouTube is acting similarly.  I'm not being told I need Flash, but it's not working, either.

I'm currently interested in uninstalling/reinstalling, but I can't get the damn thing to uninstall.  I've removed everythign that comes up from typing "flash" in the Synaptic Package Manager"  I've removed all instances of libflashplayer.so from every firefox/plugins folder I can find, (and I also removed a file called "flashplugin-alternative"),but "about:plugins" still displays a list which includes Shockwave Flash.

Any help would be greatly appreciated.  :)

---

### Post by MntlWard on 2009-10-10
Ok, I figured out that I hadn't done a thorough enough search for all instances of "libflashplayer.so" so that I could remove them all.

And reinstalling has worked!  I guess (until Adobe provides a better version) flash games aren't going to be available unless I want to break flash again.  However, I'm happy that Adobe has given me the option of watching me some hulu.  :popcorn:

---

### Post by michael37 on 2009-10-11
> **MntlWard said:**
> Ok, I figured out that I hadn't done a thorough enough search for all instances of "libflashplayer.so" so that I could remove them all.

And reinstalling has worked!  I guess (until Adobe provides a better version) flash games aren't going to be available unless I want to break flash again.  However, I'm happy that Adobe has given me the option of watching me some hulu.  :popcorn:

Flash games don't work?  My favorite [http://handdrawngames.com/DesktopTD/Game.asp](http://handdrawngames.com/DesktopTD/Game.asp) is working charmingly well.  Hey, do you really think Hulu was the reason I got flash working :) ?

---

### Post by michael37 on 2009-10-11
> **x C0MMAND0 x said:**
> Hello.  I have been trying to get a website to work that I believe uses shockwave and I have not been able to.  The website is [www.calcchat.com](www.calcchat.com)  Go there and then click on "Click HERE for free access".

Any ideas?

Shockwave doesn't exist for Linux.

---

### Post by internalkernel on 2009-10-14
Great script... I've been try to get flash to work for awhile... Hulu is still crashing - but I think that has something to do with the flash plugin itself. Firefox spits out this error as soon as you navigate to the page: 

(firefox:28384): Gdk-WARNING **: XID collision, trouble ahead

Then a seg fault when you try to play anything, I also tried it in Chromium and it reports that the Flash Plugin crashed. So... I'm blaming it on an alpha release of this 64 bit plugin. 

~~~~~
I made a change to your script before I ran it on my system. I'll copy and paste it in case you want to include this...

```
VARIANTS="iceape iceweasel mozilla firefox xulrunner midbrowser xulrunner-addons"
for p in $VARIANTS; do
sudo update-alternatives --install "/usr/lib/$p/plugins/libflashplayer.so" "$p-flashplugin" /usr/lib/mozilla/plugins/libflashplayer.so 50
done
```

This updates the links in /etc/alternatives/ directory. So any application that relies on flash will reference the libflashplayer.so.

thanks for doing all the hard work!

---

### Post by dk75 on 2009-10-14
Have no problem except for that, than I'm not in US ;PPPp

---

### Post by michael37 on 2009-10-14
> **internalkernel said:**
> Great script... I've been try to get flash to work for awhile... Hulu is still crashing - but I think that has something to do with the flash plugin itself. Firefox spits out this error as soon as you navigate to the page: 

Hulu works for me just fine, with Firefox and with Chromium.  I am also running Compiz and can get FF/Flash/Hulu on the side of a cube.  Not real sure what's happening on your system.
I made a change to your script before I ran it on my system. I'll copy and paste it in case you want to include this...

> **internalkernel said:**
> 
This updates the links in /etc/alternatives/ directory. So any application that relies on flash will reference the libflashplayer.so.

thanks for doing all the hard work!
Thank you for the submission, I'll test and incorporate the code (probably when next version comes out).

---

### Post by internalkernel on 2009-10-14
> **michael37 said:**
> Hulu works for me just fine, with Firefox and with Chromium.  I am also running Compiz and can get FF/Flash/Hulu on the side of a cube.  Not real sure what's happening on your system.

Huh... me too. Compiz & Karmic. Hulu hates me. I've removed all other instances of any flash plugin, including all the symlinks that tend to get installed in /usr/lib/ 

Are you running stock Firefox or a PPA version? and which PPAs if thats the case? 

I have Mozilla Security enabled and that's it for Firefox updates. Currently running 3.5.3 stock out of the karmic repos. And as for Chromium I'm running the daily builds. 

I'd be interested to figure out what the difference is... I think I also recall reading that you don't have an Nvidia card - something else? I have a 9800M... maybe it's Nvidia... 

Thanks

---

### Post by bitspace on 2009-10-14
I've tried everything here (and elsewhere as well) and Youtube seems to be the only thing that doesn't crash libflashplayer.so with a segfault. Nvidia video, AMD64 CPU, Ubuntu 9.04.

At one point months ago I had it working somewhat, except for very laggy video in full-screen. I fixed this at the time by disabling compiz.

Now I can barely navigate the web without firefox crashing. I'm using chromium currently (and a developer release of Chrome) and libflashplayer.so is crashing on pages that don't even have any flash (gmail, for example).

---

### Post by davisch on 2009-10-14
I also have an nvidia card and an AMD64.  I tried the fix suggested in this thread:
[http://ubuntuforums.org/showthread.php?t=1263905](http://ubuntuforums.org/showthread.php?t=1263905)
and it solved my problems - no more Flash crashes!!

---

### Post by michael37 on 2009-10-14
> **internalkernel said:**
> Huh... me too. Compiz & Karmic. Hulu hates me. I've removed all other instances of any flash plugin, including all the symlinks that tend to get installed in /usr/lib/ 

Sounds like you did, the script would have done it for you anyways.
> **internalkernel said:**
> 
Are you running stock Firefox or a PPA version? and which PPAs if thats the case? 

Stock.  Current version is 3.5.3, the same version that was adopted from mozilla-security.
> **internalkernel said:**
> 
I have Mozilla Security enabled and that's it for Firefox updates. Currently running 3.5.3 stock out of the karmic repos. And as for Chromium I'm running the daily builds. 

Same, daily builds from Chromium ppa.

> **internalkernel said:**
> 
I'd be interested to figure out what the difference is... I think I also recall reading that you don't have an Nvidia card - something else? I have a 9800M... maybe it's Nvidia... 

Yep, I have ATI Mobility X1300 card, using ati driver.  Nearly all options are defaults (including composite - it's on by default in Karmic).  The only difference is I configured xorg.conf for EXA acceleration instead of default XAA.  Supposed to work better with composite.  I run Compiz so a lot of graphics is done via OpenGL.

I don't own Nvidia, so I cannot troubleshoot it.

Unfortunately, this is the only computer able to run x64.  My other computers are old 32-bit AMD Athlon and Intel Atom netbooks.

---

### Post by michael37 on 2009-10-14
> **davisch said:**
> I also have an nvidia card and an AMD64.  I tried the fix suggested in this thread:
[http://ubuntuforums.org/showthread.php?t=1263905](http://ubuntuforums.org/showthread.php?t=1263905)
and it solved my problems - no more Flash crashes!!

Thank you for the link.  This is already provided in the OP in the troubleshooting section.

---

### Post by blackjak on 2009-10-19
I installed adobe from the software channel.Do you guys have problems controlling the slide bar of the movie?I can not move the slide bar, can not fast forward or rewind the movie.Sometimes i can not stop it.
It is pissing me off.
Using ubuntu karmic on amd 64 with nvidia grafic card.I tried to remove the nvidia driver.No difference.

---

### Post by miegiel on 2009-10-19
Sorry that I'm nit picking here, but ...
> **blackjak said:**
> I installed adobe from the software channel.
Adobe isn't software, but a software company. And you can't install a company :-?
And *"the software channel"* doesn't mean much to me either.

There are several ways to install flash and when I was still using 64bit ubuntu's all methods but 1 gave me trouble. The method in the 1st post in this thread is basically the method that did work best for me put into a script. I suggest you try it (sounds like you haven't).

---

### Post by typos1 on 2009-10-20
Fianally got iplayer working on ubuntu!! 

Had ubuntu since end of June and despite trying could never get it working. 

Have now!

Ish...got no sound...arghhhhhhh (bangs head against brick wall)

Help!

---

### Post by miegiel on 2009-10-20
> **typos1 said:**
> Fianally got iplayer working on ubuntu!! 

Had ubuntu since end of June and despite trying could never get it working. 

Have now!

Ish...got no sound...arghhhhhhh (bangs head against brick wall)

Help!
Assuming you did all the normal sound trouble shooting, try this :
```
user@machine:~$ asoundconf list
Names of available sound cards:
SB
HDMI
T71Universe
user@machine:~$ asoundconf set-default-card T71Universe
```
Where *T71Universe* was my preferred default soundcard.

---

### Post by Mark76 on 2009-10-20
Is anyone else experiencing problems with the start/pause control in embedded flash on the BBC and youtube sites on 64 bit Ubuntu?

---

### Post by typos1 on 2009-10-20
*****@*****-desktop:~$ user@machine:~$ asoundconf list
bash: user@machine:~$: command not found
*****@*****-desktop:~$ Names of available sound cards:
bash: Names: command not found
*****@*****-desktop:~$ SB
bash: SB: command not found
*****@*****-desktop:~$ HDMI
bash: HDMI: command not found
*****@*****-desktop:~$ T71Universe
bash: T71Universe: command not found
*****@*****-desktop:~$ user@machine:~$ asoundconf set-default-card T71Universe

Got this when typed that in terminal

Got nVidia soundcard and using USB speakers (only one works on ubuntu but both on windows).

Since my ubuntu install, I ve only been able to watch 50% of Flash videos and the ones I could didnt have sound-I had to download stuff to hear it. 

Now iplayer works its the same as any other Flash stuff I can view-ie no sound. Could it be something to do with where Flash player is sending the sound, as I can hear sound for everything else?

---

### Post by dBuster on 2009-10-20
> **typos1 said:**
> *****@*****-desktop:~$ user@machine:~$ asoundconf list
bash: user@machine:~$: command not found
*****@*****-desktop:~$ Names of available sound cards:
bash: Names: command not found
*****@*****-desktop:~$ SB
bash: SB: command not found
*****@*****-desktop:~$ HDMI
bash: HDMI: command not found
*****@*****-desktop:~$ T71Universe
bash: T71Universe: command not found
*****@*****-desktop:~$ user@machine:~$ asoundconf set-default-card T71Universe

Got this when typed that in terminal

Got nVidia soundcard and using USB speakers (only one works on ubuntu but both on windows).

Since my ubuntu install, I ve only been able to watch 50% of Flash videos and the ones I could didnt have sound-I had to download stuff to hear it. 

Now iplayer works its the same as any other Flash stuff I can view-ie no sound. Could it be something to do with where Flash player is sending the sound, as I can hear sound for everything else?

I believe you were not to run that verbatim.

The command you need to run would be:

```
asoundconf list
```

That will give you your information as to the sound card.  Then you would follow up with:

```

asoundconf set-default-card YOUR_SOUND_CARD_NAME
```

Replacing of course YOUR_SOUND_CARD_NAME with the results from the first command.

---

### Post by typos1 on 2009-10-20
Sorry-read it too quickly-bit wound up. Was a PICNIC error (Problem In Chair Not In Computer!)

I get two things listed, nvidia and device (assuming device is my usb speakers)

Set both and it makes no difference. As other sound works I reckon its something to do with were flashplayer is sending the sound, trouble is theres no settings for sound in flashplayer, not that I can find anyway

---

### Post by starscalling on 2009-10-21
working great here! thanks lots - was embarassing for the karmic when friends came over :P

[edit]
ok not so great
apparently the location of flash changes, but not everything knows where it's at.

[update]
apparently its segfaulting. gah.

[update]
now firefox is segfaulting. ~_~;

---

### Post by typos1 on 2009-10-21
Anyone??

No sound in Flashplayer-it wont let me into settings either

---

### Post by michael37 on 2009-10-21
> **typos1 said:**
> Anyone??

No sound in Flashplayer-it wont let me into settings either


1. Does sound work in other applications? 
2. Did you install Flashplayer using this script or some other way?  
3. Settings option within Flash won't help anyway.
4. Your Firefox profile may be bad.  Try to create another profile and see if sound works.

---

### Post by michael37 on 2009-10-21
> **starscalling said:**
> working great here! thanks lots - was embarassing for the karmic when friends came over :P

[edit]
ok not so great
apparently the location of flash changes, but not everything knows where it's at.

[update]
apparently its segfaulting. gah.

[update]
now firefox is segfaulting. ~_~;

See OP, section troubleshooting for segfaulting firefox.

---

### Post by typos1 on 2009-10-21
> **michael37 said:**
> 1. Does sound work in other applications? 
2. Did you install Flashplayer using this script or some other way?  
3. Settings option within Flash won't help anyway.
4. Your Firefox profile may be bad.  Try to create another profile and see if sound works.

I installed it using this thread, when it had finished it was version 9 something not 10 as it was supposed  to be so I tried to update it using plugin finder service but that didnt work-it said no plugin was available. So did something else, cant remember how I did it now, but its 10.0.3 or something now, just wont play sound. 

Sound works with everything else. Before flash 10 about 50% of flash movies worked (the other 50% were just blank screen) but they had no sound, so I supose its a Firefox prob like you said. How do I create another Firefox profile?

Edit: Remembered how I got to version 10-I used Firefox's site and installed the update from there

And looked in Firefox settings to see if I can find sound preferences or something-I cant...

---

### Post by greebo-76 on 2009-10-22
I'm also having problems getting sound to work with flash after installing with this script.  Sound works fine with all other apps I've tested (I'm using ALSA as I can't get pulseaudio to work with HDMI... is that the problem?).
I've tested this with firefox 3.0.14 and 3.5.3 on Jaunty 64bit.

asoundconf list returns with
Names of available sound cards:
NVidia

I've found that if I direct sound output to pulseaudio and open the pulseaudio volume control a new source isn't created on the playback tab when I play a youtube/iplayer video unlike when I play sound from other apps which leads me to think this is maybe a problem with the flash install and not the sound config?

Any help would be great, thanks.

---

### Post by miegiel on 2009-10-22
> **greebo-76 said:**
> I'm also having problems getting sound to work with flash after installing with this script.  Sound works fine with all other apps I've tested (I'm using ALSA as I can't get pulseaudio to work with HDMI... is that the problem?).
I've tested this with firefox 3.0.14 and 3.5.3 on Jaunty 64bit.

asoundconf list returns with
Names of available sound cards:
NVidia
Looks like your HDMI soundout is missing.
> I've found that if I direct sound output to pulseaudio and open the pulseaudio volume control a new source isn't created on the playback tab when I play a youtube/iplayer video unlike when I play sound from other apps which leads me to think this is maybe a problem with the flash install and not the sound config?
This probably means that the flashplayer isn't using pulse but sending the sound to alsa directly. This can also cause problems like "no sound in flash if another application was already using sound" or "no sound in other applications if flash was already using sound"

---

### Post by davidsantosmail on 2009-10-22
deleted

---

### Post by RaveJunkie on 2009-10-23
yes this works for most everything and you tube no problem.  I am on x64bit 9.04 and ext4 with SLI 9800GTX+'s with 8 gigs DDR3 and most everything work BUT HULU crashes and so does "fancast" by comcast but i think they use the same streaming flash..... for the most part works though.  I hope with the 9.10 release this will be addressed.  *crosses fingers*

anyone know a work around for HULU for flash 10 x64 firefox users?

---

### Post by thundaraptor on 2009-10-23
This might be a redundant post so sorry.

I have followed the instructions for 64 bit flash from softpedia and it seems to work. hulu/youtube are all fine. what is the performance difference between and 32/64 bit and how to install the plugin in flock, the other good browser.  

Thanks,

TR

---

### Post by RaveJunkie on 2009-10-23
64 bit flash was a big pain last year for winblowz and ubuntu 64 bit, there was work arounds and they were very glitchy untill flash 10 alpha came out for both, not its WAY easier.

and i still have a few issues with x64bit  like when watching hulu i just found this fix TODAY for hulu

```
For hulu and 64 bit, go to .huludesktop and edit the line flash_location + (null)
It should read the location of your flashplayer.so

In my case:
flash_location = /usr/lib64/mozilla/plugins/libflashplayer.so

Your location may be different. Save and it should work.
```

i have got firefox and never used flock..... but there is big diffrances in flash due to adobe not releasing updates. and there is still not a .deb package installer of flash 10 that im aware of.....

---

### Post by typos1 on 2009-10-23
Can anyone help re my earlier post?

---

### Post by RaveJunkie on 2009-10-23
typos1  if you go into firefox and type in "about:plugins" what version of flash does firefox think your using?
version of java? version of media player/quicktime are you on? and what type of media are you having problems with?

---

### Post by typos1 on 2009-10-23
Shockwave Flash 10.0 r3/ Iced Tea Java Web Browser version 1.4.1 (6b14-1.40ubuntu11/ mplayer plugin 3.55/quicktime plugin7.2.0.

Installed ubuntu end of June, no comp expert but did really well whit most things, needed a little help on here with the odd thing. Couldnt make iplayer work though. About half of Flash movies worked half didnt. The ones that worked didnt have sound though. Tried googling it and searching threads on here, spent months on it, nothing worked. Left it for a few weeks tried again and noticed a flash update to version 10 on this thread. Tried that, it didnt update but I found the update manually and updated and it worked! Finally I could view Flash movies, but still no sound. Searched again and tried a few other things but none worked. I ve done so much over the last 4 months I ve lost track of what I ve done.

Sorry to go on, but its so frustrating. The problem now is no sound in Flash movies

---

### Post by dk75 on 2009-10-23
So why don't post a link for flash movie that don't plays for you. Maybe they won't play for anyone so no need to frustrate?

---

### Post by g63marty on 2009-10-23
FYI 
As of Oct 23 I found that Firefox 3.5 plugin finder for 64bit Ubuntu has a Flash plugin available.
The installed package is from Adobe.
flashplugin-installer 10.0.32.18.ubuntu (amd64)

Hope this helps.:)

---

### Post by RaveJunkie on 2009-10-23
[COLOR="Blue"]g63marty is right and I want am able to play flash no problems so next step is find out what is diff on yours.  your flash and plugins look right.  I dont see whats wrong first glance. Only thing i can think of is along the way of "fixing" it to the point where you are might of tweaked or edited some things along the way. 

Do you have a link of something that is not playing sound?

with the newest flash player install its SOOO much easier now.  I almost want to have you remove flash and install it through symantic.  Im no expert either at all but i had the same issue at first and the newest flash via symantic, with firefox 3.5 it works like a charm  FINALLY......[/COLOR]

---

### Post by miegiel on 2009-10-23
> **g63marty said:**
> FYI 
As of Oct 23 I found that Firefox 3.5 plugin finder for 64bit Ubuntu has a Flash plugin available.
The installed package is from Adobe.
flashplugin-installer 10.0.32.18.ubuntu (amd64)

Hope this helps.:)

That's the infamous 32bit flash player wrapped in the ndiswrapper that is giving many people problems (especially in fullscreen).

> **RaveJunkie said:**
> [COLOR="Purple"]...

with the newest flash player install its SOOO much easier now.  I almost want to have you remove flash and install it through symantic.  Im no expert either at all but i had the same issue at first and the newest flash via symantic, with firefox 3.5 it works like a charm  FINALLY.....[/COLOR]

And the flashplayer in symantic it the 32bit player too.

**The 64bit flashplayer is not in the repo's** you need to get it from adobe's _**dev**_ site (labs.adobe.com). It's still alpha (that's why it's not in the repo's) but in 64bit ubuntu it works better than the wrapped  officially released 32bit player.

If you want to do it all by hand get the 64bit flashplayer here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
If that's to complicated for you (or you're just lazy :D) use the script from the 1st post in this thread.

---

### Post by typos1 on 2009-10-24
Miegel-I m not lazy and its not too complicated-I ve spent 4 months trying to sort this. And I ve done it all "by hand" many many times. I know all that about 32 and 64 bit players and I ve already gone to Adobe and downloaded the 64 bit and the 32 bit and spent hours and hours and hours trying to get them to work for iplayer, they played some flash videos, though only about 50% and never with sound. 

g63marty-I ve got 10.0.32.18 and it has finally sorted flash probs and works great and now, iplayer works, in fact ALL flash videos work now, but still no sound. 

dk75-An example of something that wont play sound is...ANY flash video!-No sound at all in flash

Tried the usual things for no sound in Flash, no help. Sound works for everything else on my pc, but not flash movies, so it seems like its where the sound is being sent to when playing flash stuff

---

### Post by ian2112 on 2009-10-24
This was a very helpful thread - much thanks to those who have contributed.

I ultimately solved my problem by reinstalling Firefox 3.5.3.  I know, nothing special... read on.  This was after running the script on the first page, and creating links for the libflashplayer.so file as recommended in this thread.

What made my problem unique (confess I didn't read the entire thread) was that when I selected "About" the Help Menu I was told I was running Firefox 3.5.3 (64-bit).  But... when I went to Synaptic I could see it wasn't installed (weird!).  I marked it (Shiretoko) for install and that solved my problem.

I believe that somehow trying to change the branding for Shiretoko to Firefox I some how caused this mess.

While I'm confident I'm a unique and special snowflake and no one else could have screwed up their browser like me... if you're reading this... have a look.

Hope this helps!

---

### Post by dk75 on 2009-10-25
then check and replace inside "about:config" ```
general.useragent.extra.firefox   Shiretoko/3.5.3
``` to ```
general.useragent.extra.firefox   Firefox/3.5.3
``` to avoid further Flash/JAVA trouble

---

### Post by typos1 on 2009-10-25
What problems where you having ian2112?

---

### Post by lembatz on 2009-10-27
thanks guys..
i was so frustated on how to make the flash player work on my ubuntu..
but after i follow this tutorial, now i can watch youtube on my ubuntu...:D

---

### Post by KapteinPyn on 2009-10-27
It worked thanks. 

high-five

---

### Post by wolfe on 2009-10-27
I used this script to install flash after removing my previous flash install and all seems to be working with the exception that I can't play embedded youtube videos.  Any idea how to resolve that?

tia

edit:  nevermind, I just installed it manually and it seems resolved now.

---

### Post by D3mon_Spawn on 2009-10-30
Can anyone confirm if this works with 9.10 64?

---

### Post by michael37 on 2009-10-30
> **D3mon_Spawn said:**
> Can anyone confirm if this works with 9.10 64?

I tested it with 9.10 64-bit.

---

### Post by Aname on 2009-10-30
Hi all. First post here :)

I've just done a fresh install of Karmic, which comes with Firefox 3.5.3. Flash seems to be working for everything except BBC iPlayer (the player seems to load but none of the buttons, including Play, do anything). I've tried the method here. Anyone else have this problem or know a remedy?

Thanks :)

EDIT: Actually buttons don't seem to be working on some other sites either such as YouTube, but as they auto-play I'd thought they were working without problem..

---

### Post by mohave on 2009-10-30
I have applied the script on my yesterday upgrade to Karmic AMD64 (obviously the default karmic flash plugin applied didn't work)
The script worked properly in the meaning I can now see all flash in youtube and other pages.

However I can't access to yahoo mail nor gmail. Firefox (Shiretoko 3.5.5pre) closes / crashes suddenly just accessing these pages at least. 
(It is not because the old AMD processor issue commented previously in this thread).

What is going wrong? Is it Firefox/Shiretoko version? No, it is the flash plugin that crashes the Firefox. In gmail it is the chat feature the one who trigers the crash. 

Fortunately in the long meanwhile someone from Adobe will develop the right plugin we can use the useful firefox addon called: [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433")
To be honest I guess somebody from the community will develop the right plugin before Adobe does ;-) INCREDIBLE

Thanks for your time and regards

---

### Post by dardack on 2009-10-30
> **Aname said:**
> Hi all. First post here :)

I've just done a fresh install of Karmic, which comes with Firefox 3.5.3. Flash seems to be working for everything except BBC iPlayer (the player seems to load but none of the buttons, including Play, do anything). I've tried the method here. Anyone else have this problem or know a remedy?

Thanks :)

EDIT: Actually buttons don't seem to be working on some other sites either such as YouTube, but as they auto-play I'd thought they were working without problem..


Are you using the flash from the repo's? or the flash from this script? (the alpha 64bit from adobe labs dev)

---

### Post by dardack on 2009-10-30
Just want to say, sometimes the mms.cfg can help, this forces using the GPU to help with flash, YMMV, and doesn't always improve speed:

cd /etc/
sudo mkdir adobe
sudo nano /etc/adobe/mms.cfg
add this line: OverrideGPUValidation=true

---

### Post by Aname on 2009-10-30
> **dardack said:**
> Are you using the flash from the repo's? or the flash from this script? (the alpha 64bit from adobe labs dev)

From the script, just following the method here. I've actually just tried reinstalling (again using the script) and now the iPlayer and YouTube sites just close Firefox immediately. :(

EDIT: Can the people here who are fine with Flash 64 on Karmic confirm whether this is also from a fresh Karmic install, Firefox 3.5.3? If so I think I might as well reinstall Karmic as it's so quick, I must have somehow messed up with the Flash 64 installation somewhere along the line (I had tried other methods prior to seeing this sticky and trying the method here).

EDIT 2: Or should I downgrade Firefox to 3.5.2?

---

### Post by dardack on 2009-10-30
> **Aname said:**
> From the script, just following the method here. I've actually just tried reinstalling (again using the script) and now the iPlayer and YouTube sites just close Firefox immediately. :(

EDIT: Can the people here who are fine with Flash 64 on Karmic confirm whether this is also from a fresh Karmic install, Firefox 3.5.3? If so I think I might as well reinstall Karmic as it's so quick, I must have somehow messed up with the Flash 64 installation somewhere along the line (I had tried other methods prior to seeing this sticky and trying the method here).

First, you are running 64bit Ubuntu yes?

Let's try outside the script.  First from the script run:
(I remove the wrapper since I dont' need it)

```
sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/mozilla/plugins/npwrapper*flash*so
```

then:
```
cd /
sudo find -name libflashplayer.so
```

Find all instances of this file and then remove them.
so if it finds one in /home/username/.mozilla/plugins/
sudo rm -f /home/username/.mozilla/plugins/libflashplayer.so

Once you removed em all, open firefox, go to youtube and just verifies 1. it doesn't auto close, 2. says you need flash.

Then get the file:
```
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz

tar xvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz

sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/

(I then also add a link in my home directory, not sure if this is still needed):

sudo cp libflashplayer.so /home/[username]/.mozilla/plugins

```

Restart firefox, and see.  If you still crash run firefox from a terminal and post the error message.

---

### Post by Aname on 2009-10-30
Dardack, firstly thanks for the help. :)

However..

I followed your steps, then tried again, Firefox crashed again. Then tried again running Firefox in the terminal.. And YouTube worked, buttons worked as well.. Then tried iPlayer and that crashed Firefox, and since then it just crashes (YouTube as well).

The error message I'm getting is:

> (firefox:4926): Gdk-WARNING **: XID collision, trouble aheadrepeated many times, then:

> Segmentation fault

EDIT: "trouble ahead" funny error message at least :D

---

### Post by dardack on 2009-10-30
> **Aname said:**
> Dardack, firstly thanks for the help. :)

However..

I followed your steps, then tried again, Firefox crashed again. Then tried again running Firefox in the terminal.. And YouTube worked, buttons worked as well.. Then tried iPlayer and that crashed Firefox, and since then it just crashes (YouTube as well).

The error message I'm getting is:

repeated many times, then:



EDIT: "trouble ahead" funny error message at least :D

Yea that was added, aparently the error would occur but no message, usually can be ignored from what i understand.

So we need to understand what's going on here.  First, you say that youtube crashes it as well once you visit iplayer, please go to:

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html)

See if that opens, if so find youtube.com and click never ask again, should make it so it doesn't store anything, find iplayer site (no idea what it is) and do same thing.  Then click delete all sites.  Also, clear firefox's cache/cookies (or just the cookies related to youtube/iplayer at least).

This is to test, that i have had issues with 64bit flash and when it stores data it f's up, but if you don't let it store for some reason it then works.

See if that works in youtube first.  I have no idea if iplayer works in linux.

Again, since you didn't answer, you are using 64bit Ubuntu yes?

If that doesn't work, the sudo -ln up there, we gonna try to move the actual lib, so

sudo rm /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo cp libflashplayer.so /usr/lib/firefox-addons/plugins/

restart firefox, try that, if that doesn't work, remove the /home/username/.mozilla/plugins/libflashplayer.so file


If that doesn't work I have no freaking idea man.  Are you sure iplayer works in linux? Sorry a yank here so don't have access that i know of.  Or i'd try it for you.

---

### Post by Aname on 2009-10-30
Hey, thanks again, but alas no help..

The link you gave did work but YouTube, iPlayer and so on still crash Firefox..

I think one of the other methods I tried must have messed something up somewhere so I'm tempted to just reinstall Karmic and try this method from scratch..

In answer to your questions though yep I'm running Karmic 64 and iPlayer ran fine using Flash 64 on Jaunty 64..

Are you running a fresh Karmic 64 install with the Flash 64 installed from this script as well, Firefox 3.5.3?

Anyway shame you can't get iPlayer over there man, some good stuff there. Can you get 4od? ([http://www.channel4.com/programmes/4od](http://www.channel4.com/programmes/4od)) If so check out Peep Show, very good, perhaps somewhat twisted, comedy there. Maybe there's a way to trick your browser into thinking you're from the UK? Anyhoo, veering way off topic now :D

Anyway, yeah, if you, or anyone here reading this, can confirm they're on a fresh install of Karmic 64, Firefox 3.5.3, used the method posted here to install Flash 64, and it's working fine (YouTube for example, buttons as well working), I'll just assume somewhere along the line I messed up with my previous attempts to install Flash 64 and start over, no biggie.:)

BTW can't remove the /home/username/.mozilla/plugins/libflashplayer.so file, I get this error:

> rm: cannot remove `.mozilla/plugins/libflashplayer.so': Not a directory

The "plugins" in that directory is not a folder but a shared library according to the properties window, the icon is of a file with a padlock.

---

### Post by dardack on 2009-10-30
> **Aname said:**
> Hey, thanks again, but alas no help..

The link you gave did work but YouTube, iPlayer and so on still crash Firefox..

I think one of the other methods I tried must have messed something up somewhere so I'm tempted to just reinstall Karmic and try this method from scratch..

In answer to your questions though yep I'm running Karmic 64 and iPlayer ran fine using Flash 64 on Jaunty 64..

Are you running a fresh Karmic 64 install with the Flash 64 installed from this script as well, Firefox 3.5.3?

Anyway shame you can't get iPlayer over there man, some good stuff there. Can you get 4od? ([http://www.channel4.com/programmes/4od](http://www.channel4.com/programmes/4od)) If so check out Peep Show, very good, perhaps somewhat twisted, comedy there. Maybe there's a way to trick your browser into thinking you're from the UK? Anyhoo, veering way off topic now :D

Anyway, yeah, if you, or anyone here reading this, can confirm they're on a fresh install of Karmic 64, Firefox 3.5.3, used the method posted here to install Flash 64, and it's working fine (YouTube for example, buttons as well working), I'll just assume somewhere along the line I messed up with my previous attempts to install Flash 64 and start over, no biggie.:)

BTW can't remove the /home/username/.mozilla/plugins/libflashplayer.so file, I get this error:



The "plugins" in that directory is not a folder but a shared library according to the properties window, the icon is of a file with a padlock.


Fresh install, this 64bit native crashed firefox on hulu (i would assume close to iplayer in same respect as it blocks outside USA people).  So i went back to the 32bit version/wrapper, and hulu works again.

So you might want to remove all libflashplayer.so from the plugin directories, and try sudo apt-get install flashplugin-nonfree

My only issue is sometimes it doesn't let you click inside the flash, but if you click outside it, hole the button down, move over the button in flash, release and click fast again it works.  So a small annoyance, but can't live without my hulu right now.

---

### Post by Aname on 2009-10-30
> **dardack said:**
> Fresh install, this 64bit native crashed firefox on hulu (i would assume close to iplayer in same respect as it blocks outside USA people).  So i went back to the 32bit version/wrapper, and hulu works again.

So you might want to remove all libflashplayer.so from the plugin directories, and try sudo apt-get install flashplugin-nonfree

My only issue is sometimes it doesn't let you click inside the flash, but if you click outside it, hole the button down, move over the button in flash, release and click fast again it works.  So a small annoyance, but can't live without my hulu right now.

Yep, I've just done a fresh install of Karmic, ran the script first thing, and it runs fine now. :)

Thanks for all your help anyway, and thanks michael37 for the script. :)

---

### Post by jsc_moraga on 2009-10-30
I had a few of the problems listed:

(I'm running 9.10 x64, with x64 firefox v3.5.3, on a dual-quad 5520 and 12GB of RAM)

1. At first, Hulu crashed. Removed the 32-bit stuff, installed x64 flash via the script, problem solved.

2. After installing x64 flash, hulu and youtube videos play, but in the controls(like pause and fullscreen) didn't respond.

3. Removed Nvidia driver 185.xxx. and rebooted. Controls now working properly.

Anyone else have this same problem? Anyone have a way of running x64 flash and the nvidia drivers without this problem?

jsc

---

### Post by jsc_moraga on 2009-10-30
I think I found the problem:

After I installed the latest Nvidia drivers, ubuntu reset my desktop effects from "none" to "normal". When I turned off the desktop effects again, flash video controls worked properly again.

jsc

---

### Post by liveforfunnow on 2009-10-30
> **jsc_moraga said:**
> I think I found the problem:

After I installed the latest Nvidia drivers, ubuntu reset my desktop effects from "none" to "normal". When I turned off the desktop effects again, flash video controls worked properly again.

jsc

I installed the script, and rebooted. I can view YouTube and Hulu, but the Flash controls (play, pause. full screen, etc) do not work. I am on an ATI driver. 

Any ideas?

---

### Post by Aname on 2009-10-30
> **liveforfunnow said:**
> I installed the script, and rebooted. I can view YouTube and Hulu, but the Flash controls (play, pause. full screen, etc) do not work. I am on an ATI driver. 

Any ideas?

I have an ATI driver. I had the same problems you describe, then did a fresh install of Karmic, ran the script, and Flash worked fine (even with the desktop effects enabled with the ATI driver).

Then I was prompted to update Firefox (to 3.5.4 now) and the problem has returned. :mad:

Turning off desktop effects seems to resolve the issue, though. Ideally I'd like to have effects enabled but for now at least it seems the only solution (other than another fresh install perhaps).

People here having the same issue:

[http://ubuntuforums.org/showthread.php?t=1293921](http://ubuntuforums.org/showthread.php?t=1293921)

---

### Post by liveforfunnow on 2009-10-30
I'll try that tonight, later, and post results. Thanks!

---

### Post by michael37 on 2009-10-31
> **jsc_moraga said:**
> I think I found the problem:

After I installed the latest Nvidia drivers, ubuntu reset my desktop effects from "none" to "normal". When I turned off the desktop effects again, flash video controls worked properly again.

jsc

I have ATI video card and I don't have any problems with hulu and youtube.  A LOT of Nvidia users report problems.  Since I don't have hardware, I cannot troubleshoot it, but just letting you know that observing problems with Nvidia graphics is quite common.  If you can troubleshoot it, that would be GREAT!!!

---

### Post by Aname on 2009-10-31
Uh.. Just realised what I'd done. I'd installed Ubuntu restricted extras, which comes bundled with Flash, that must have caused the problem. Reinstalled now, all working fine. D'oh.

---

### Post by Caldavien on 2009-10-31
After following these instructions Firefox crashes everytime I go to gmail. In command line it gives error  "Segmentation fault".

---

### Post by DodgeV83 on 2009-10-31
> **jsc_moraga said:**
> I had a few of the problems listed:

(I'm running 9.10 x64, with x64 firefox v3.5.3, on a dual-quad 5520 and 12GB of RAM)

1. At first, Hulu crashed. Removed the 32-bit stuff, installed x64 flash via the script, problem solved.

2. After installing x64 flash, hulu and youtube videos play, but in the controls(like pause and fullscreen) didn't respond.

3. Removed Nvidia driver 185.xxx. and rebooted. Controls now working properly.

Anyone else have this same problem? Anyone have a way of running x64 flash and the nvidia drivers without this problem?

jsc

I'd guess the only reason removing the Nvidia driver worked, is because that in turn disabled Compiz.  Disabling Compiz (Appearance -> Visual Effects -> None) is a known fix for this problem.

---

### Post by dk75 on 2009-10-31
Oh boy. How many times it needs to be writen that Adobe Flash complains that Compiz breaks Compositing and thus Adobe Flash don't like Compiz and that's why hardware acceration is disabled in Linux Flash and other bad things happen.

64bit user can't do anything about it except to disable GPU detection in Flash and 32bit users could HEX edit "libflashplayer.so" and replace every "COMPIZ" string with "COMPIX" which disables Compiz detection in Adobe Flash player.

It should be sticky.

---

### Post by liveforfunnow on 2009-10-31
I fixed the issue with my ATI card by: 

1. Uninstalling Flash via Software Center;
2. Deleting the ~/.mozilla/plugins folder (that I created when manually installing Flash from the Adobe Labs site). 
3. Uninstalling and reinstalling Firefox via Software Center. 

When I rebooted, Firefox was stable, and Flash controls worked properly. 

I hope this helps.

---

### Post by dardack on 2009-10-31
Yea no idea why with compiz enabled flash controls don't work.  You can get them to work with compiz enabled with a little tricky, click outside the flash window, hold mouse button down, move cursor to the button you want to click, release and click quickly.  This works for me, can get annoying but for a little bit of flash with compiz enabled is fine.

---

### Post by Habboblob on 2009-10-31
I tried that and it didn't work.
:(

I am currently running Ubuntu 9.10 Karmic Koala.
My laptop is a Toshiba A500 / 042 and I do not have a Intel Video Card.

I've tried this and many guides but flash is still not working for me.

Here are my specs of my laptop is this helps:
```
Processor
Processor Brand 	Intel
Processor Type 	Core&#8482;2 Duo
Processor Model 	P7350
Processor Speed 	2.0
Processor QTY 	1
Memory
Installed RAM (GB) 	4
RAM Configuration 	2 x 2GB
RAM Expandable To (GB) 	8
RAM Type 	DDR2
Cache Memory Size (MB) 	3
Disk Drives
Interface Type 	SATA
Hard Drive Size (GB) 	400
Hard Drive Speed (RPM) 	5400
Number of Optical Drives 	1
Optical Drive Type 	DVD Super Multi
Optical Drive Format 	Dual Layer Support, DVD±R/RW
Power
Battery Type 	6-cell Lithium Ion
Screen
Screen Size (cm) 	40.64 (16 in)
Screen Type 	TruBrite Display
Screen Definition 	High Definition
Screen Resolution 	1366 x 768
Audio
Microphone 	External
Speakers 	Premium harman/kardon® Speakers
Networking & Internet
Wireless Networking 	IEEE 802.11a, IEEE 802.11g, IEEE 802.11n
Bluetooth Enabled 	Yes
Networking 	Gigabit Ethernet
Graphics & Video Support
[B]Graphics Card Brand 	ATI
Graphics Card Type 	Radeon&#8482; HD 4650
Graphics Card Memory (MB) 	1024[/B]
Connections and Expansion
Audio Ports 	Headphone 3.5mm jack, Microphone 3.5mm jack
USB Ports 	4
Video Ports 	1 x HDMI, 1 x VGA
PCMCIA Slot 	Express Card
Other Ports 	eSATA
Dimensions
Product Height (cm) 	3.64/4.1
Product Depth (cm) 	38.4
Product Width (cm) 	25.9
Product Weight (kg) 	2.9400
Software
Operating System 	Windows Vista® Home Premium
Included Trial Software 	Norton Internet Security&#8482; 2009 (60-day trial)
Manufacturers Warranty
Manufactures Warranty (months) 	12
Parts Warranty 	1 year
Labour Warranty 	1 year
Back to top

```

---

### Post by HNS-I on 2009-11-01
I've run the script and it works like a charm in firefox, but chrome still has the old behaviour. A can't find any flash libs in the chrome directory however.
EDIT:Also I've doublechecked there is no old plugin installed.

---

### Post by dardack on 2009-11-01
> **HNS-I said:**
> I've run the script and it works like a charm in firefox, but chrome still has the old behaviour. A can't find any flash libs in the chrome directory however.
EDIT:Also I've doublechecked there is no old plugin installed.

What version of chromium/ubuntu?

I'm running 4.0.226.0 (Ubuntu build 30050) without having to move the libflashplayer.so into /usr/lib/chromium-browser/plugins like yyou used to have to.  Now it correctly find's mozilla's.

Also, shoulda asked this,, when starting chromium do you have the enable plugins option?

chromium-browser --enable-plugins --enable-greasemonkey --enable-user-scripts --enable-extensions

Well that's mine, but if you just want flash, the enable plugins is enough.

---

### Post by dardack on 2009-11-01
> **dk75 said:**
> Oh boy. How many times it needs to be writen that Adobe Flash complains that Compiz breaks Compositing and thus Adobe Flash don't like Compiz and that's why hardware acceration is disabled in Linux Flash and other bad things happen.

64bit user can't do anything about it except to disable GPU detection in Flash and 32bit users could HEX edit "libflashplayer.so" and replace every "COMPIZ" string with "COMPIX" which disables Compiz detection in Adobe Flash player.

It should be sticky.

I have hard ware accelartion enabled in my linux flash, and i just put the OverrideGPUValidation=true in the /etc/adobe/mms.cfg file.  And i run full screen hulu/youtube fine.  If i'm watching alot i might disable compiz so i don't have to do the click outside the flash window, hold th emousee button down, move the cursor to the button i want to push, and click release/reclick.  Once it's in fullscreen tho all buttons seem to work with compiz enabled.

---

### Post by dardack on 2009-11-01
Is there a way to tell for sure you have the 64bit installed?

---

### Post by dk75 on 2009-11-01
> **dardack said:**
> I have hard ware accelartion enabled in my linux flash, and i just put the OverrideGPUValidation=true in the /etc/adobe/mms.cfg file.  And i run full screen hulu/youtube fine.  If i'm watching alot i might disable compiz so i don't have to do the click outside the flash window, hold th emousee button down, move the cursor to the button i want to push, and click release/reclick.  Once it's in fullscreen tho all buttons seem to work with compiz enabled.

But "hardware acceration" that is in Flash menu is... only partial slight acceration that Windows have and that Linux had long time ago before Compiz.
I've read it on nVidia forum: user complained to nVidia, nVidia to Adobe and Adobe stated "Because of Compiz we removed full hardware acceration from our Flash plugin for Linux".

---

### Post by JugglinPhil on 2009-11-01
Thanks for the Tutorial, now I finally can watch embedded youtube videos again. :)

---

### Post by jamvegan on 2009-11-01
Thank you!  I just upgraded to 9.10, with NVIDIA driver enabled, and had same flash control problems.  Setting desktop effects to none fixed it.

---

### Post by mohave on 2009-11-01
> 
64bit user can't do anything about it except to disable GPU detection in Flash 

Please how to disable GPU detection in flash ?

---

### Post by dk75 on 2009-11-01
> **mohave said:**
> Please how to disable GPU detection in flash ?

```
sudo su
mkdir /etc/adobe
echo "OverrideGPUValidation=true" > /etc/adobe/mms.cfg
```

---

### Post by promet on 2009-11-01
I tried this and it did not work for me, would this require a reboot? Any way I could be sure that I'm going about that correctly? I checked that the syntax and location are correct.

---

### Post by miegiel on 2009-11-01
> **promet said:**
> would this require a reboot?
No, but restarting firefox won't hurt.
> Any way I could be sure that I'm going about that correctly?
```
about:plugins
``` (in the firefox address bar)

---

### Post by Uncle Spellbinder on 2009-11-01
> **jamvegan said:**
> Thank you!  I just upgraded to 9.10, with NVIDIA driver enabled, and had same flash control problems.  Setting desktop effects to none fixed it.


Indeed. It really is that simple. I have the default Flash from the repo's installed on my 64-Bit Karmic install. Had all kinds of issues. Spesdtest.net, YouTube, MetaCafe and the like were nearly unusable. After yurning desktop effects from 'normal' to 'none', I've had no issues at all with Flash.

While I appreciate the script, and all the suggestions in this (and other) threads about 64-bit flash issues. It seems unnecessary.

Just turn desktop effect to 'none' and all is fixed.

---

### Post by promet on 2009-11-01
If one wanted to have desktop effects ***and*** proper flash?

---

### Post by Uncle Spellbinder on 2009-11-01
> **promet said:**
> If one wanted to have desktop effects ***and*** proper flash?

As was stated earlier, and in other threads about this issue...

That ain't gonna happen. The folks at Adobe are aware of the compatibility issues between Flash and Compiz (desktop effects) in Linux. There is NO fix on the horizon (at least on Adobe's end). Perhaps a fix from Ubuntu devs or Compiz devs?

---

### Post by promet on 2009-11-01
Holy wow, that actually works, lol! Well that'll do until a legit fix comes along, nice one!

---

### Post by Uncle Spellbinder on 2009-11-01
Better than a wonky, unstable Flash, eh? 

:-)

---

### Post by DynastyX on 2009-11-01
> **Uncle Spellbinder said:**
> As was stated earlier, and in other threads about this issue...

That ain't gonna happen. The folks at Adobe are aware of the compatibility issues between Flash and Compiz (desktop effects) in Linux. There is NO fix on the horizon (at least on Adobe's end). Perhaps a fix from Ubuntu devs or Compiz devs?

Why does it work properly with the 32 bit OS if the compatibility issues are between flash and compiz? Before I had to buy a new laptop I ran 32 bit Hardy for almost year with no issues using flash and compiz at the same time.

---

### Post by Uncle Spellbinder on 2009-11-02
> **DynastyX said:**
> Why does it work properly with the 32 bit OS if the compatibility issues are between flash and compiz? Before I had to buy a new laptop I ran 32 bit Hardy for almost year with no issues using flash and compiz at the same time.

Flash/Compiz/64bit - That's the conflict.

Info and interesting posts in the [64-bit + flash + compiz](http://ubuntuforums.org/showthread.php?t=1293921) thread.

---

### Post by klemperal on 2009-11-02
Does anyone know how to uninstall/remove all the things that this script installed (symbolic links and all)?  I wanted to start from scratch since I'm not having any luck with the script.

---

### Post by Uncle Spellbinder on 2009-11-02
Have you tried to disable desktop effects?

---

### Post by miegiel on 2009-11-02
> **klemperal said:**
> Does anyone know how to uninstall/remove all the things that this script installed (symbolic links and all)?  I wanted to start from scratch since I'm not having any luck with the script.

Uninstall whatever you installed and then search your root and home for *libflashplayer.so* and remove it.

---

### Post by klemperal on 2009-11-02
> **miegiel said:**
> Uninstall whatever you installed and then search your root and home for *libflashplayer.so* and remove it.

So the only two things that the script 'installed' so to speak was libflash.so and a sym link?

---

### Post by klemperal on 2009-11-02
Ok, I'm having some very strange problems with 64 bit flash.  I made a plugins directory within my .mozilla folder and moved the latest 64 bit libflashplayer.so there.  Now, whenever I got to youtube.com firefox crashes with a segmentation fault.  However, so long as I don't go to youtube's main page [youtube.com (where firefox seg faults)] I can watch youtube videos--from a hyper link or from my youtube subscriptions page for example.  I'm using Karmic 64bit fully updated with the back-ports and proposed updates.  Anyone know what my problem might be?

---

### Post by i.artiles on 2009-11-02
Woot woot, thanks a bunch for the script, everything working perfect

---

### Post by promet on 2009-11-02
> **klemperal said:**
> Ok, I'm having some very strange problems with 64 bit flash.  I made a plugins directory within my .mozilla folder and moved the latest 64 bit libflashplayer.so there.  Now, whenever I got to youtube.com firefox crashes with a segmentation fault.  However, so long as I don't go to youtube's main page [youtube.com (where firefox seg faults)] I can watch youtube videos--from a hyper link or from my youtube subscriptions page for example.  I'm using Karmic 64bit fully updated with the back-ports and proposed updates.  Anyone know what my problem might be?

You may want to go into Synaptic Package Manager Remove all Flash and use the script provided earlier in this thread. 

Also, you **might** remove your custom created ".mozilla" directory, including the liblflashplayer.so file.

That is just a suggestion. This solved my Firefox crashes in 64-bit Karma with  Firefox.

Good Luck!

---

### Post by dk75 on 2009-11-02
> **promet said:**
> I tried this and it did not work for me, would this require a reboot? Any way I could be sure that I'm going about that correctly? I checked that the syntax and location are correct.

It might have different effect on different configuration. For me it makes Flash to paly twice as fast as without but still it is five time too slow so no love.

As my experience I could say that it have more impact with nVidia 180.x dirvers ( I could watch 480p full screen flash ) than with 190.x ( there I have trouble with minimalised flash even ) and it doing nothing with 185.x nVidia drivers.

---

### Post by klemperal on 2009-11-02
I figured out what the problem was for me.  Gmail, youtube, and Hulu would make firefox crash with a seg fault--but it turned out that flash was not the problem.  According to [this thread]("https://lists.ubuntu.com/archives/ubuntu-mozillateam-bugs/2009-February/068347.html"), pulseaudio was the one causing me all this trouble.  To fix, all I had to do was run the commands 
```
sudo rm -rf /tmp/* 
```
and then
```
sudo reboot
```

---

### Post by michael37 on 2009-11-02
> **klemperal said:**
> I figured out what the problem was for me.  Gmail, youtube, and Hulu would make firefox crash with a seg fault--but it turned out that flash was not the problem.  According to [this thread]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8224372"), pulseaudio was the one causing me all this trouble. 

U got a bad link.  Could you please repost?

---

### Post by xAgnostoSx on 2009-11-03
Thank you...!I will test it...

---

### Post by Uncle Spellbinder on 2009-11-03
I've gotten quite tired of the inability to stream flash video with Compiz (desktop effects) enabled. I decided to install Ubuntu 9.10 32-bit on my 64 bit machine. Other than the fact that all 8 gigs of memory are not utilized, all is back to normal in Ubuntu/Flash/Compiz.

And no noticeable difference in system performance using a 32 bit Ubuntu on a 64 bit machine.

For me.....problem solved.

---

### Post by Habboblob on 2009-11-03
> **Uncle Spellbinder said:**
> Indeed. It really is that simple. I have the default Flash from the repo's installed on my 64-Bit Karmic install. Had all kinds of issues. Spesdtest.net, YouTube, MetaCafe and the like were nearly unusable. After yurning desktop effects from 'normal' to 'none', I've had no issues at all with Flash.

While I appreciate the script, and all the suggestions in this (and other) threads about 64-bit flash issues. It seems unnecessary.

Just turn desktop effect to 'none' and all is fixed.

I tried setting my Desktop Effects to None and then run a script but flash still doesn't work.
When I type in ```
about:plugins
``` into firefox I still receive the:
```
No plugins are installed
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.

```

---

### Post by edantes on 2009-11-04
**Adobe Flash 64bit  works with Firefox but not with Opera and Konqueror!**

After installing Ubuntu 9.10 AMD64, I had problems with the Flash plugin for some sites.  Problems disappeared by purging Karmic packages and manually installing libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz downloaded from the Adobe site.  Something like this (not unlike the script on the top post of this topic)

```
sudo apt-get -y purge flashplugin-installer flashplugin-nonfree
sudo cp libflashplayer.so /usr/lib/mozilla/plugin
sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
```

This seemed to cure the problems I bumped into with Firefox.  For instance, now I can view megavideo.com videos, which didn't work before:

[http://www.megavideo.com/?v=ILK0UKDH](http://www.megavideo.com/?v=ILK0UKDH)

Two question anyway:

1.  What exactly is in the flashplugin-installer flashplugin-nonfree packages that breaks the plugin?

2.  The solution described above does no work for Konqwueror and Opera, even if they use the exactly same plugin as Firefox.

---

### Post by Harold.Gcia on 2009-11-04
I tried using the method mentioned on this thread, but it didn't work for me. Then I went to Google and found this website [http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/](http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/) with instructions on how to install the flash player, this one worked for me and fixed the problem. First, I removed the nonfree version form the ubuntu software center, then fallowed the instructions and thats it.

---

### Post by miegiel on 2009-11-04
> **Harold.Gcia said:**
> I tried using the method mentioned on this thread, but it didn't work for me. 
To bad, but that's not very helpful. If you'd at least post what went wrong the script or instructions could be improved.

> Then I went to Google and found this website [http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/](http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/) with instructions on how to install the flash player, this one worked for me and fixed the problem. First, I removed the nonfree version form the ubuntu software center, then fallowed the instructions and thats it.

That's basically the same as what the script in the 1st post does, though the script also ads links to the flasplayer for other programs then firefox, who might want to know where the flshplayer is located too. :-k

---

### Post by Harold.Gcia on 2009-11-04
I would've but I do not know what went wrong. I just installed Ubuntu 2 days ago, I'm new to this OS and everything around it. I'm learning as I go.

---

### Post by miegiel on 2009-11-04
> **Harold.Gcia said:**
> I would've but I do not know what went wrong. I just installed Ubuntu 2 days ago, I'm new to this OS and everything around it. I'm learning as I go.

My appolozies :) "it didn't work" post get on my nerves to much. I should have taken a chill pill before posting (or read Amy Hoy's "help vampire" artiticle again).

*ps* welcome

---

### Post by miegiel on 2009-11-04
> **edantes said:**
> ...

Two question anyway:

1.  What exactly is in the flashplugin-installer flashplugin-nonfree packages that breaks the plugin?
Not 100% sure, but I think the *flashplugin-installer* downloads adobes 32bit flashplayer and installs it. Both packages will get you some version of the 32bit flashplayer.

> 2.  The solution described above does no work for Konqwueror and Opera, even if they use the exactly same plugin as Firefox.

Maybe opera and konqueror can't find the plugin, or there is a old link to the 32bit flashplayer in their plugin directories. Copying *libflashplayer.so* to their plugin directories or making a link in their plugin directories to */usr/lib/mozilla/plugin/libflashplayer.so* might fix it.

---

### Post by pietro_spina on 2009-11-04
Thanks michael37,

This is a very clear script and useful to many people, myself included. However I would like to suggest that you add uninstall instructions to your original post.

I know that it's incredibly simple but I think it is helpful to know how to (and that you can) revert to a 'clean slate' when one comes across these scripts that take you outside the comfort of 'Software Center' or Synaptic.

Regards,
P

---

### Post by Harold.Gcia on 2009-11-04
> **miegiel said:**
> My appolozies :) "it didn't work" post get on my nerves to much. I should have taken a chill pill before posting (or read Amy Hoy's "help vampire" artiticle again).

*ps* welcome

Don't worry about it. I just wanted to help anyway I can. But next time I have a problem, I will try to explain better and elaborate more than just "it didn't work". 

P.S.
Thanks for the welcome.

---

### Post by edantes on 2009-11-04
> **miegiel said:**
> 

Maybe opera and konqueror can't find the plugin, or there is a old link to the 32bit flashplayer in their plugin directories. Copying *libflashplayer.so* to their plugin directories or making a link in their plugin directories to */usr/lib/mozilla/plugin/libflashplayer.so* might fix it.



Opera (so does Konqueror) uses the Mozilla plugin directly:

Plug-ins
Shockwave Flashapplication/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/mozilla/plugins/libflashplayer.so

Something fails in the communication with megavideo and other sites.

---

### Post by dk75 on 2009-11-04
> **Harold.Gcia said:**
> I tried using the method mentioned on this thread, but it didn't work for me. Then I went to Google and found this website [http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/](http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/) with instructions on how to install the flash player, this one worked for me and fixed the problem. First, I removed the nonfree version form the ubuntu software center, then fallowed the instructions and thats it.

But removing "nonfree" version from Ubuntu is the core of this thread. Without this nothing will work correctly.

**michael37@** add this to the first post because only feew reads full thread to find about needs of uninstalling old plugins.

---

### Post by michael37 on 2009-11-04
> **dk75 said:**
> But removing "nonfree" version from Ubuntu is the core of this thread. Without this nothing will work correctly.

**michael37@** add this to the first post because only feew reads full thread to find about needs of uninstalling old plugins.

I am not sure I understand what is the point of this.  sudo apt-get -y purge flashplugin-nonfree is a part of the script in the OP.

---

### Post by Flywaver on 2009-11-04
For some reason all flash works fine now!
I did install gnome-shell which requires compiz and desktop effects disabled! I have no idea if it's related!

---

### Post by michael37 on 2009-11-04
> **pietro_spina said:**
> Thanks michael37,

This is a very clear script and useful to many people, myself included. However I would like to suggest that you add uninstall instructions to your original post.

I know that it's incredibly simple but I think it is helpful to know how to (and that you can) revert to a 'clean slate' when one comes across these scripts that take you outside the comfort of 'Software Center' or Synaptic.

Regards,
P
@pietro_spina, thank you for suggestion.  Uninstall instructions posted in the OP.

---

### Post by 00ber n00b on 2009-11-04
Whenever I play an embedded youtube video while my laptop is in "ondemand" frequency scale mode I get very glitchy playback, but if I enable performance mode the playback is flawless...but the problem with performance mode is that my laptop over heats and shuts down.  Any suggestions?

---

### Post by samulis on 2009-11-05
I know this is not a fix (nothing on the forums worked for me, save from disabling compositing), but the way I live with the unresponsiveness of mouse commands is using keyboard commands instead. Space to pause/play, "f" for fullscreen, esc to get out of fullscreen. If your playback is choppy in fullscreen, try to move your cursor out of the way to the right and not move it. It seems the choppiness is due to moving cursor over the video. 

Curiously I had the same problem and same fix for choppy fullscreen in with video in my old windows install when my pci-e bus got broken and I had to use a really old pci 3d card.

---

### Post by dk75 on 2009-11-06
> **00ber n00b said:**
> Whenever I play an embedded youtube video while my laptop is in "ondemand" frequency scale mode I get very glitchy playback, but if I enable performance mode the playback is flawless...but the problem with performance mode is that my laptop over heats and shuts down.  Any suggestions?

```

echo 1 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/ignore_nice_load
echo 50 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold

```

try to add this to "/etc/rc.local" just before "end" line
If you have more cores then you must do this for every core ( cpu1, cpu2, cpu3, ...).

---

### Post by Flywaver on 2009-11-06
Grrrr....there was an update to FF this morning and now youtube doesn't display anything, just a big white box where the player used to be :(

---

### Post by wd5gnr on 2009-11-06
I had this working great on Jaunty. However, I upgraded to Kosmic (why do I do this?) and it replaced it with the npwrapper 32-bit version which actually works ok. However, because I like to run 64 bit, I reinstalled. That works too, EXCEPT, that gmail crashes Firefox 3.5 when it starts the gTalk application. Opera crashes too although less spectacularly since it sandboxes the plugins. The 32-bit version works fine. But still.

Googling shows lots of people are having the gTalk problem with 64 bit flash plugin. So step forward some ways and backwards some others.

---

### Post by 00ber n00b on 2009-11-06
> **dk75 said:**
> ```

echo 1 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/ignore_nice_load
echo 50 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold

```

try to add this to "/etc/rc.local" just before "end" line
If you have more cores then you must do this for every core ( cpu1, cpu2, cpu3, ...).

So, since I have a dual core amd processor it should read...

```
echo 1 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/ignore_nice_load
echo 50 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold
echo 1 > /sys/devices/system/cpu/cpu1/cpufreq/ondemand/ignore_nice_load
echo 50 > /sys/devices/system/cpu/cpu1/cpufreq/ondemand/up_threshold
```

And exactly what does this do? 

Thanks.

---

### Post by Flywaver on 2009-11-06
Well, I solved my problem!! I am running FF 3.6 Namoroka and everything is smooth sailing! :D

---

### Post by michael37 on 2009-11-06
> **wd5gnr said:**
> I had this working great on Jaunty. However, I upgraded to Kosmic (why do I do this?) and it replaced it with the npwrapper 32-bit version which actually works ok. However, because I like to run 64 bit, I reinstalled. That works too, EXCEPT, that gmail crashes Firefox 3.5 when it starts the gTalk application. Opera crashes too although less spectacularly since it sandboxes the plugins. The 32-bit version works fine. But still.

Googling shows lots of people are having the gTalk problem with 64 bit flash plugin. So step forward some ways and backwards some others.

What am I missing?  What does Gtalk application has to do with flash?  Are you talking about Gtalk within gmail?

---

### Post by wd5gnr on 2009-11-07
> **michael37 said:**
> What am I missing?  What does Gtalk application has to do with flash?  Are you talking about Gtalk within gmail?

Yes. The little GTalk sidebar, which I guess uses flash or at least interacts with it negatively. It isn't just me. 
[http://www.google.com/search?hl=en&q=flash+crash+gmail+amd64&aq=f&oq=&aqi=](http://www.google.com/search?hl=en&q=flash+crash+gmail+amd64&aq=f&oq=&aqi=)

There is a fix in one of those about ARGB visual disables. I haven't tried that but when I get a chance, I will and will report back.

Update: Nope the ARGB disable does not work, nor does removing the .macromedia directory. So still back to 32 bit.

---

### Post by ian2112 on 2009-11-07
Hello all,

Seeking some assistance here.  I've been here before and successfully followed the steps to get flash working.  Now, after an upgrade to 9.10 and blindly accepting a software update... flash no longer works at all - nothing.

Some info / things I have tried:

1) Help / About Mozilla Firefox returns:

Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-GB; rv:1.9.1.3) Gecko/20090824 Firefox/3.5.3

- so I believe I am correctly running a 64-bit browser.

2) Followed the steps in the first post and ran the script - no errors.

3) I can confirm that in /usr/lib/firefox-addons/plugins is a link to libflashplayer.so, and the file is located in the /usr/lib/mozilla/plugins directory

4) When I type about:plugins I don't see flash

5) Also, in Software Sources I have:
[http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu)

6) I've tried uninstalling and reinstalling firefox 3.5.3.  And I've tried removing the .so file from the two places mentioned above, and re-run the script

7) I should not that I did have a version of ff 3.0.? running, but it's now no longer on my system.  I believe one of my updates removed it (I didn't consciously remove it).  Also, with the removal of earlier ff version, I also noticed that ff 3.5.3 was now called Firefox and not Shiretoko (sp?).


Any other troubleshooting steps I should follow?

---

### Post by dk75 on 2009-11-07
> **00ber n00b said:**
> So, since I have a dual core amd processor it should read...

```
echo 1 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/ignore_nice_load
echo 50 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold
echo 1 > /sys/devices/system/cpu/cpu1/cpufreq/ondemand/ignore_nice_load
echo 50 > /sys/devices/system/cpu/cpu1/cpufreq/ondemand/up_threshold
```

And exactly what does this do?

"ignore_nice_load=1" - ignore processes which has "nice" positive value when counting how much processor is loaded with work.
For example BOINC client ( any other background programs and system daemon ) without this would bash processor to 100% of usage but with "nice=19" it uses processor only when it is free from other task so why to speedup processor for it since it not need it and not consume processor for itself.

"up_treshold=50" - state precentage of processor ocupation above which kernel frequency manager will speedup core to higher frequency.
So if you have processor which could scale his speed from 1GHz to 2GHz when it's counted usage is below 50% stays in 1GHz mode but when it's usage past 50% then it speedup to 2GHz.

My processor will scale on values: 1000MHz, 1600MHz, 1800MHz and 22000MHz.
When it's usage past 50% it speedup to 2200MHz, but at 2200MHz mode when it's usage is below 50% then it slow down to 1800MHz. If it still below 50% then slow down to 1600MHz and so on. That's "OnDemand" kernel processor sheduler.
There's others which make's things differently.

---

### Post by 00ber n00b on 2009-11-07
> **dk75 said:**
> "ignore_nice_load=1" - ignore processes which has "nice" positive value when counting how much processor is loaded with work.
For example BOINC client ( any other background programs and system daemon ) without this would bash processor to 100% of usage but with "nice=19" it uses processor only when it is free from other task so why to speedup processor for it since it not need it and not consume processor for itself.

"up_treshold=50" - state precentage of processor ocupation above which kernel frequency manager will speedup core to higher frequency.
So if you have processor which could scale his speed from 1GHz to 2GHz when it's counted usage is below 50% stays in 1GHz mode but when it's usage past 50% then it speedup to 2GHz.

My processor will scale on values: 1000MHz, 1600MHz, 1800MHz and 22000MHz.
When it's usage past 50% it speedup to 2200MHz, but at 2200MHz mode when it's usage is below 50% then it slow down to 1800MHz. If it still below 50% then slow down to 1600MHz and so on. That's "OnDemand" kernel processor sheduler.
There's others which make's things differently.

So, do I have to edit the processes and give them a value or is it fine how I already have it?

---

### Post by dk75 on 2009-11-07
No. What's could have "nice" set by it's creator.
The only thing you need is to configure "OnDemand" scheduler as I've posted because by default it isn't.

---

### Post by michael37 on 2009-11-07
> **ian2112 said:**
> Hello all,

Seeking some assistance here.  I've been here before and successfully followed the steps to get flash working.  Now, after an upgrade to 9.10 and blindly accepting a software update... flash no longer works at all - nothing.

Some info / things I have tried:

1) Help / About Mozilla Firefox returns:

Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-GB; rv:1.9.1.3) Gecko/20090824 Firefox/3.5.3

- so I believe I am correctly running a 64-bit browser.

2) Followed the steps in the first post and ran the script - no errors.

3) I can confirm that in /usr/lib/firefox-addons/plugins is a link to libflashplayer.so, and the file is located in the /usr/lib/mozilla/plugins directory

4) When I type about:plugins I don't see flash

5) Also, in Software Sources I have:
[http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu)

6) I've tried uninstalling and reinstalling firefox 3.5.3.  And I've tried removing the .so file from the two places mentioned above, and re-run the script

7) I should not that I did have a version of ff 3.0.? running, but it's now no longer on my system.  I believe one of my updates removed it (I didn't consciously remove it).  Also, with the removal of earlier ff version, I also noticed that ff 3.5.3 was now called Firefox and not Shiretoko (sp?).


Any other troubleshooting steps I should follow?

Please run 
ldd /usr/lib/firefox-addons/plugins/libflashplayer.so 

Let's see what you get there.

---

### Post by ian2112 on 2009-11-07
Hello,

Thank-you for volunteering to look at the output.  Here it is.

Thx,
Ian.

ldd /usr/lib/firefox-addons/plugins/libflashplayer.so 
	linux-vdso.so.1 =>  (0x00007fff1edff000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007f7153da2000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007f7153b86000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00007f715384f000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00007f715363d000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0x00007f71533d7000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00007f7153151000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00007f7152f1f000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0x00007f7152914000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0x00007f7152667000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0x00007f7152447000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x00007f715222b000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x00007f715201e000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x00007f7151dd5000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0x00007f7151b52000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x00007f715190a000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x00007f7151706000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007f7151502000)
	libglib-2.0.so.0 => /lib/libglib-2.0.so.0 (0x00007f715123a000)
	libnss3.so => /usr/lib/libnss3.so (0x00007f7150f06000)
	libsmime3.so => /usr/lib/libsmime3.so (0x00007f7150cdb000)
	libssl3.so => /usr/lib/libssl3.so (0x00007f7150aa5000)
	libplds4.so => /usr/lib/libplds4.so (0x00007f71508a1000)
	libplc4.so => /usr/lib/libplc4.so (0x00007f715069c000)
	libnspr4.so => /usr/lib/libnspr4.so (0x00007f7150460000)
	libm.so.6 => /lib/libm.so.6 (0x00007f71501dc000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007f714ffc5000)
	libc.so.6 => /lib/libc.so.6 (0x00007f714fc55000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f7158cd7000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007f714fa39000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00007f714f836000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0x00007f714f62c000)
	libz.so.1 => /lib/libz.so.1 (0x00007f714f415000)
	libexpat.so.1 => /lib/libexpat.so.1 (0x00007f714f1ec000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0x00007f714efe8000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x00007f714ede6000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x00007f714ebe0000)
	libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0x00007f714e935000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x00007f714e70c000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00007f714e502000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x00007f714e2ff000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0x00007f714e0f4000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x00007f714deeb000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x00007f714dce0000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0x00007f714da9b000)
	libdirectfb-1.2.so.0 => /usr/lib/libdirectfb-1.2.so.0 (0x00007f714d80f000)
	libfusion-1.2.so.0 => /usr/lib/libfusion-1.2.so.0 (0x00007f714d605000)
	libdirect-1.2.so.0 => /usr/lib/libdirect-1.2.so.0 (0x00007f714d3ea000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0x00007f714d1c2000)
	libxcb-render-util.so.0 => /usr/lib/libxcb-render-util.so.0 (0x00007f714cfbe000)
	libxcb-render.so.0 => /usr/lib/libxcb-render.so.0 (0x00007f714cdb5000)
	libpcre.so.3 => /lib/libpcre.so.3 (0x00007f714cb86000)
	libnssutil3.so => /usr/lib/libnssutil3.so (0x00007f714c968000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007f714c762000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0x00007f714c547000)
	libuuid.so.1 => /lib/libuuid.so.1 (0x00007f714c342000)
	libresolv.so.2 => /lib/libresolv.so.2 (0x00007f714c128000)
	libselinux.so.1 => /lib/libselinux.so.1 (0x00007f714bf0a000)

---

### Post by michael37 on 2009-11-07
> **ian2112 said:**
> Hello,

Thank-you for volunteering to look at the output.  Here it is.

Thx,
Ian.

ldd /usr/lib/firefox-addons/plugins/libflashplayer.so 



That looks fine.  

Try this, run

firefox -ProfileManager --no-remote

Create a new profile, name it "Test", accept all other defaults.  Go to [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/) and see if Flash plugin works (second one, Shockwave one on the top does not and  should not work, don't worry about Shockwave)

---

### Post by szlwzl on 2009-11-08
> **dk75 said:**
> ```
sudo su
mkdir /etc/adobe
echo "OverrideGPUValidation=true" > /etc/adobe/mms.cfg
```

This worked for me - thank you!!!

S

---

### Post by Flywaver on 2009-11-08
> **dk75 said:**
> ```
sudo su
mkdir /etc/adobe
echo "OverrideGPUValidation=true" > /etc/adobe/mms.cfg
```

Did the same, hope it works!

---

### Post by Flywaver on 2009-11-08
Ok that OverrideGPUValidation=true did NOT work! :(
Now Youtube videos flicker!
I guess I redo the same but I set it to OverrideGPUValidation=false ?

---

### Post by ian2112 on 2009-11-08
> **michael37 said:**
> That looks fine.  

Try this, run

firefox -ProfileManager --no-remote

Create a new profile, name it "Test", accept all other defaults.  Go to [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/) and see if Flash plugin works (second one, Shockwave one on the top does not and  should not work, don't worry about Shockwave)

I tried this and was unsuccessful.  The Adobe site said I needed flash and java (also to confirm, I have java and javascript enabled).

Does it help to know that flash works on Opera?  

I appreciate the help!  Any other thoughts or suggestions?

Ian.

---

### Post by adrian.h on 2009-11-08
This was fun.  Somehow, I lost flash.  Tried just about everything listed.  Only got to page 7 of 21 (last count).  Here is what I did:

From terminal:
```
sudo find /usr -iname libflashplayer.so -exec rm '{}' ';'

```

From SPM: installed flashplugin-installer.

This has been quite a PITA.  Hope it doesn't stop working. :(

I've noticed that the performance, is not as good as on a win box which sucks.  Esp on HD youtube vids running full screen.  This really shouldn't be so.

Video is given running lspci|grep VGA:
```
02:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 LE] (rev a2)

```

Disabled compiz as I found it eating 30% of CPU.  I hope this Ubuntu 64 gets better.  May try Gentoo if I feel brave (and have a day+ to play).

---

### Post by dsbig123 on 2009-11-09
21 pages on trying to get flash to work on 64bit, WOW, this is why Im using 32bit ubuntu

---

### Post by ~aris on 2009-11-10
Thank you! I runned the script on 9.10 and all worked fine!

---

### Post by miegiel on 2009-11-10
> **dsbig123 said:**
> 21 pages on trying to get flash to work on 64bit, WOW, this is why Im using 32bit ubuntu

It's not all that bad, if you don't have nVidia graphics and install the 64bit flashplayer on a clean ubuntu you probably won't have any trouble at all. Even if you do use compiz. Most problems are caused by remnants of the old 32bit flashplayer or bugs that only surface with nVidia graphics.

---

### Post by silvertuna on 2009-11-10
So for those of us with nVidia graphics on 64-bit karmic, what can we do?  will a clean install fix it?

---

### Post by miegiel on 2009-11-10
> **silvertuna said:**
> So for those of us with nVidia graphics on 64-bit karmic, what can we do?  will a clean install fix it?

I don't have a nVidia graphics, but [this seems like a good fix]("http://ubuntuforums.org/showthread.php?p=8215570#post8215570"). There are other things suggested in this thread too and I think there is a *"(64bit) flash with nVidia graphics"* thread somewhere.

---

### Post by Digikid on 2009-11-10
Ran the script...nothing.  Every time I go to Youtube it says that I need to install flash.

EDIT:  Did a complete uninstall and THEN tried the script.  Works now....but not in the 3.6 Beta of Firefox....but that is not your fault so.......

---

### Post by David-IT on 2009-11-10
wow works great ty soo much and i am loving 64 bit 9.10 amazing.

---

### Post by blueridgedog on 2009-11-10
> **dsbig123 said:**
> 21 pages on trying to get flash to work on 64bit, WOW, this is why Im using 32bit ubuntu

I did a clean install to 64 bit from a working 32 bit install.  I installed the Adobe flash alpha and have no issues other than needing a work around for a gmail issue.  I am satisfied with 64 bit at this point.

---

### Post by MasterOfTheHat on 2009-11-11
The alpha installer worked fine for me and flash videos would play, but I couldn't get the buttons on the Hulu player to work. 

The ultimate solution for me, (I found it somewhere, but can't find the post again now), was to run through the alpha install and then uninstall flashplugin-installer. Restart FF after that uninstall, and everything works, including buttons.

Use either Synaptic to search for and remove the package, or run 
```
sudo apt-get remove flashplugin-installer
```
in a terminal.

EDIT: Well, scratch that. It worked after I upgraded from Jaunty to Karmic, but on this clean install of Karmic, it just crashes FF after a few seconds.

---

### Post by silvertuna on 2009-11-11
None of the solutions above restored my flash sound. I have tried many suggestions in the ubuntu 64-bit and other forums to no avail - either i get no sound, or Firefox crashes, the video window is blank or flash fails to install. However, my pulseaudio output volume meter appears to be active, the bars jump, but no sound actually comes out. The other odd thing is i have flash sound through my TV speakers when i connect my latptop via HDMI. Can anyone else confirm that their flash plays in HDMI but not in their built-in laptop speakers? And does that offer a clue as to what to look for?

Karmic 64-bit nVidia Firefox

---

### Post by SolidSilver on 2009-11-11
I'm also having a problem with sound.  All was working fine until I installed Cinelerra and tried several audio options earlier today.  Now, flash does not have any audio.  Kaffeine plays fine.  Amarok plays fine until I try to play a flash movie.  Afterward, Amarok will fail with 'audio device nvidia (...) is not working.  Switching to PulseAudio'.  (not an exact quote)  Amarok then fails to play audio until a restart *after*I play something in Kaffeine.  

This seems to be related to the Cinelerra install, but the Cinelerra startup scripts don't seem to do anything to sound settings.  (FWIW, the Cinelerra Esound option to use PulseAudio didn't work and caused Pulse to consume 94% CPU until killed and restarted)

Karmic amd64 nvidia with the Adobe 64-bit Flash plugin.  Any help will be appreciated.

---

### Post by Flywaver on 2009-11-12
Youtube and all FF flash movies now have flickers and small studders! :mad:
This is getting really ridiculous! :(

---

### Post by Guilden_NL on 2009-11-13
No go for me.  Went through all of the troubleshooting steps across the 21 pages.  I hate Adobe anyway, so I guess it's another reason to kill the beast off and get HTML 5 a-rollin'.

---

### Post by ubernoob on 2009-11-13
There are some flash-elements i cant click on. I'm not sure if it's just some add-on i have installed that doesnt work with this flash version, or if this is a known issue. 

E.g i can't go to the next picture on this screenshot:
[http://www.pfsense.org/screenshots/](http://www.pfsense.org/screenshots/)

---

### Post by SolidSilver on 2009-11-13
Looks like I found my problem.  If Amarok is open, it grabs the sound card such that Pulse can't open it.  Even telling Amarok to use Pulse doesn't help.  Closing Amarok restored sound to flash videos. Exaile doesn't appear to do this.  For now, I'm just not running a music player unless I want to listen to music.

---

### Post by gutierrezfam on 2009-11-13
Tried the Get64bitFlash install.  It executed without errors.  But Firefox doesn't recognize that Flash is installed.  Interestingly, Konquerer (4.3.2) does recognize it.  It states that Version 10,0,32,18 is installed successfully.  Using Konquerer, YouTube and other sites work perfectly.

I first ran the script.  Restarted the browser and computer (several times). No go on Firefox. I removed the "flashplugin-installer-10.0.32.18ubuntu1 (amd64)) via Software Management (KPackageKit).  I then executed the following two commands
[COLOR="Blue"][sudo rm /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so][/COLOR]
and re-ran the script...  still a no go.

Can anyone help out?

I've recently upgraded to Kubuntu Karmic 9.10 - 64-bit version (although I didn't have Flash working with Jaunty, either).  I have 64-bit FireFox 3.5.2 (Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9.1.2) Gecko/20090729 Firefox/3.5.2)

---

### Post by nbv4 on 2009-11-13
I tried the script and it seems to work fine. When I go to the adobe site it tells me I have 10.0.32.18 installed properly. But when I load up a page that contains flash, the terminal fills up with this:

```
(firefox:25528): Gdk-WARNING **: XID collision, trouble ahead

(firefox:25528): Gdk-WARNING **: XID collision, trouble ahead

(firefox:25528): Gdk-WARNING **: XID collision, trouble ahead

(firefox:25528): Gdk-WARNING **: XID collision, trouble ahead

(firefox:25528): Gdk-WARNING **: XID collision, trouble ahead

(firefox:25528): Gdk-WARNING **: XID collision, trouble ahead

(firefox:25528): Gdk-WARNING **: XID collision, trouble ahead

(firefox:25528): Gdk-WARNING **: XID collision, trouble ahead

(firefox:25528): Gdk-WARNING **: XID collision, trouble ahead

(firefox:25528): Gdk-WARNING **: XID collision, trouble ahead

(firefox:25528): Gdk-WARNING **: XID collision, trouble ahead

(firefox:25528): Gdk-WARNING **: XID collision, trouble ahead

(firefox:25528): Gdk-WARNING **: XID collision, trouble ahead
Segmentation fault

```

And then the window closes. Anyone else having this problem?

---

### Post by synapse13 on 2009-11-13
> **dk75 said:**
> ```
sudo su
mkdir /etc/adobe
echo "OverrideGPUValidation=true" > /etc/adobe/mms.cfg
```

Thank you for this!  Helped solve my Karmic Flash troubles.  :P

---

### Post by silvertuna on 2009-11-14
Good News/Bad News - I had to resort to a clean install from the Live CD to get sound restored to Flash in 64-bit Karmic.

---

### Post by mashedbear on 2009-11-14
Am having problems with flash post upgrade to 64 bit 9.10 with firefox 3.5.5. Seems the same as many others - youtube works, but cbbc site crashes firefox so lots of complaints from the kids. 

Have tried runnig this [script]("http://ubuntuforums.org/showthread.php?t=1259102"), and an install of libflashplayer.so and created mms.cfg file above - but neither are solving this problem. 

Help appreciated!

---

### Post by A4orce84 on 2009-11-14
I too am having flash problems. At least on Youtube / Hulu, it seems my videos will play, but I can't interact with the flash-player.

So I can't pause the video, make things full-screen, etc. I'm stuck with whatever size the video was set to on the page.

Anyone out there beaten this 100% yet?

Thanks.

---

### Post by aniplox on 2009-11-15
Thank you this worked> i am drunk right now lol

---

### Post by A4orce84 on 2009-11-15
Which step worked?

---

### Post by Flywaver on 2009-11-15
> **A4orce84 said:**
> Which step worked?

Who knows...he was drunk! :lolflag:

My FF was updated and flash works fine! 
3.5.6pre and 3.6b3pre

---

### Post by A4orce84 on 2009-11-15
how do we update? I'm running FF 3.5.5

---

### Post by mashedbear on 2009-11-15
I seem to have this fixed now. I install 64 bit libflashplayer.so and created mms.cfg file above, but then had to restart ubuntu to get it to work.

---

### Post by Flywaver on 2009-11-15
> **A4orce84 said:**
> how do we update? I'm running FF 3.5.5

Add this in Software Sources: 
[http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu]("http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu")

You will get the daily builds...they are not the official builds but you get an update every week if not more!

---

### Post by 73ckn797 on 2009-11-15
Works like a charm!! Thanks.

---

### Post by poubelle on 2009-11-17
Just to add my little data point: the script in the original post works for me, for Firefox. (Thank you!) But I also have Swiftfox installed, with the hope of switching over to that, and Flash doesn't work on Swiftfox (despite everything else being interchangeable, including browsing history). 

It's not a huge huge issue, but it's a definite annoyance. At this point I browse in Swiftfox and open Firefox if I want to view Youtube. Or else I don't bother going to Youtube. But blank spaces where embedded videos should be are pretty annoying.

I don't understand why this small thing is such a big problem, but then, I don't really know much about 32- vs. 64-bit addressing.

(AMD64, Karmic, most recent FF/SF, crappy thrift-store CRT, NVidiia so I can use Compiz.)

---

### Post by steevelewis on 2009-11-18
Hi michael.
  Just read your post and would like to thank you for the valuable information mentioning in your post. Thanks for providing some useful links for further suggestion, really great work and Ido appreciate your efforts.
 Thanks and stay connect.

---

