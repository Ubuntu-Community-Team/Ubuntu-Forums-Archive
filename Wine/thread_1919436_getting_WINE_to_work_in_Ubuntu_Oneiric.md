---
title: "getting WINE to work in Ubuntu Oneiric"
date: 2012-02-02
forum: Wine
---

### Post by dimas869 on 2012-02-02
i dont want anything to be with windows but i really miss this game which i had play for a long time and i am trying to make it work in wine but i dont know what happens so i am going to post what the terminal give when i run it and hope someone could help me with it
> ramon@mycompisawhore:~/.wine/drive_c/Programs/AirAttack$ wine AAStart.exe
fixme:advapi:GetCurrentHwProfileA (0x32a348) semi-stub
fixme:ntdll:NtSetInformationToken unimplemented class 4
fixme:advapi:ImpersonateLoggedOnUser ((nil))
fixme:ntdll:NtQueryVolumeInformationFile 0x11c: volume info not supported
--17:13:03--  [https://server1.ketsujin.com/wicketaa3/logininfo2.php?u=&p=&lang=ENU&pa=paaafO%60pgrdrercabhqghumeaylnlfdxfircvscxggbwkfnqduxwfnfozvsrtkjprepggxrpnrvystmwcysyycqpevikeffmznimkkasvwsrenzkycxfxtlsgypsfadpooefxzbcoejuvpvaboygpoeylfpbnpljvrvipyamyehwqnqrqpmxujjloovaowuxwhmsncbxcoksfzkvatxdknlyjyhfixjswnkkufnuxxzrzbmnmgqooketlyhn&ra=wtacblcjflajdkdkcrgrahfoeobhdpbifidjczpvscmpsajlfvgubfaaovlzylntrkdcpwsrtesjwhdizcobzcnfwlqijtvdwvxhrcbldvgylwgbusbmborxtlhcsmpxohgmgnkeufdxotogbgxpeyanfetcukepzshkljugggekjdqzjenpevqgxiepjsrdzjazujllchhbfqmkimwzobiwybxduunfsksrsrtekmqdcyzjeeuhmsrqcozi&bo=cnaedicobiaodnfhbibhbkbqfrbkeqcodrdP%5EQ%5Crgrdreqanfqeqfrbpcjdpeieofiddgbazuxmhecthlegrpunkdmbppweqtgjoparmowzdqyoxytjbbhawdydcprjbxphoohpkwqyuhrqzhnbnfuvqnqqlrzjpxiogvliexdzuzosrkrusvojbrzmwzpowkjilefraamdigpnpuuhgxpqnjwjmwaxxmnsnhhlqqrzudltfzotcjtnzxugl&li=lbafdocheibibhegghchbkcqfkekekakaqejgkbkbkfqfjdjdkakapdifjcjcififjcjclelehahakbqdT_bbcpxifbxvfbcgkcfqckcotzgkubmjrmbsztsshfroefwsjrxjhguzyupzwweiqurpixiqflduuveoowqcudhnefnjhaimuczfskuiduburiswtbrecuykabfcvkdzeztoidukuhjzefczzzbfkqdpqzikfobucdhthxdjgkj&tu=hhaabjfY]xwwkmfxdyygmdcaszsgovsodkjghcwmbmxrmhuyfyqgajqkcklznayxqkqoyzwmyubzazcpkhktkydzivcuypurfmbisgekyrgzvxdhpoamvafyrarxsvkhtqdihersigbhzjzujxmmyspnaraewkegjccvhhrjvbjtsqdjootgpknfpfycgfieowqrwwwpzsqmetogepspxnvjiupalyynmkmnuvklhsecdwracgfmzkgipdfo](https://server1.ketsujin.com/wicketaa3/logininfo2.php?u=&p=&lang=ENU&pa=paaafO%60pgrdrercabhqghumeaylnlfdxfircvscxggbwkfnqduxwfnfozvsrtkjprepggxrpnrvystmwcysyycqpevikeffmznimkkasvwsrenzkycxfxtlsgypsfadpooefxzbcoejuvpvaboygpoeylfpbnpljvrvipyamyehwqnqrqpmxujjloovaowuxwhmsncbxcoksfzkvatxdknlyjyhfixjswnkkufnuxxzrzbmnmgqooketlyhn&ra=wtacblcjflajdkdkcrgrahfoeobhdpbifidjczpvscmpsajlfvgubfaaovlzylntrkdcpwsrtesjwhdizcobzcnfwlqijtvdwvxhrcbldvgylwgbusbmborxtlhcsmpxohgmgnkeufdxotogbgxpeyanfetcukepzshkljugggekjdqzjenpevqgxiepjsrdzjazujllchhbfqmkimwzobiwybxduunfsksrsrtekmqdcyzjeeuhmsrqcozi&bo=cnaedicobiaodnfhbibhbkbqfrbkeqcodrdP%5EQ%5Crgrdreqanfqeqfrbpcjdpeieofiddgbazuxmhecthlegrpunkdmbppweqtgjoparmowzdqyoxytjbbhawdydcprjbxphoohpkwqyuhrqzhnbnfuvqnqqlrzjpxiogvliexdzuzosrkrusvojbrzmwzpowkjilefraamdigpnpuuhgxpqnjwjmwaxxmnsnhhlqqrzudltfzotcjtnzxugl&li=lbafdocheibibhegghchbkcqfkekekakaqejgkbkbkfqfjdjdkakapdifjcjcififjcjclelehahakbqdT_bbcpxifbxvfbcgkcfqckcotzgkubmjrmbsztsshfroefwsjrxjhguzyupzwweiqurpixiqflduuveoowqcudhnefnjhaimuczfskuiduburiswtbrecuykabfcvkdzeztoidukuhjzefczzzbfkqdpqzikfobucdhthxdjgkj&tu=hhaabjfY]xwwkmfxdyygmdcaszsgovsodkjghcwmbmxrmhuyfyqgajqkcklznayxqkqoyzwmyubzazcpkhktkydzivcuypurfmbisgekyrgzvxdhpoamvafyrarxsvkhtqdihersigbhzjzujxmmyspnaraewkegjccvhhrjvbjtsqdjootgpknfpfycgfieowqrwwwpzsqmetogepspxnvjiupalyynmkmnuvklhsecdwracgfmzkgipdfo)           => `logininfo.txt'Resolving server1.ketsujin.com... 66.135.38.41Connecting to server1.ketsujin.com|66.135.38.41|:443... connected.WARNING: Certificate verification error for server1.ketsujin.com: self signed certificateHTTP request sent, awaiting response... 200 OKLength: 930 [text/plain] 0% [                                     ] 0             --.--K/s             100%[====================================>] 930           --.--K/s             17:13:05 (920.69 KB/s) - `logininfo.txt' saved [930/930]fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x321c24,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:winmm:MXD_SetControlDetails What should the sw-side mixer controls map to?
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:gstreamer:init_new_decoded_pad Linking: 0
fixme:gstreamer:no_more_pads Done
fixme:gstreamer:event_sink 0x7db366a0 stub tag
fixme:gstreamer:event_sink 0x7db3b478 stub tag
fixme:gstreamer:event_sink 0x7db3b4a0 stub tag
fixme:gstreamer:event_sink 0x7db3b4c8 stub tag
fixme:gstreamer:event_sink 0x7db3b518 stub tag
fixme:gstreamer:got_data_sink Triggering 0x7db50008 0xc0
fixme:gstreamer:watch_bus mpegaudioparse0: GStreamer encountered a general stream error.
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:gstreamer:GST_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:DSoundRender_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
err:ntdll:RtlpWaitForCriticalSection section 0x1129d98 "gstdemux.c: GSTImpl.csFilter" wait timed out in thread 002d, blocked by 0009, retrying (60 sec)
wine: Critical section 01129d98 wait failed at address 0x7bc3489a (thread 002d), starting debugger...
Unhandled exception: wait failed on critical section 0x01129d98 in 32-bit code (0x7bc3489a).
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc3489a
Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
[email]ramon@mycompisawhore:~/.wine[/email]/drive_c/Programs/AirAttack$ 0000000e services.exe
        00000020    0
        0000001f    0
        00000015    0
        00000010    0
        0000000f    0
00000012 winedevice.exe
        0000001d    0
        0000001a    0
        00000014    0
        00000013    0
0000001b plugplay.exe
        00000021    0
        0000001e    0
        0000001c    0
00000022 explorer.exe
        00000023    0
winedbg: Internal crash at 0x6821c29a
err:ntdll:RtlDeleteResource Deleting active MRSW lock (0x111bfc), expect failure
wine: Unhandled page fault on read access to 0x0000001c at address 0x682725a9 (thread 0031), starting debugger...
err:ntdll:RtlDeleteResource Deleting active MRSW lock (0x112504), expect failure

---

### Post by oldos2er on 2012-02-02
Moved to Wine.

---

### Post by Toz on 2012-02-02
I followed the instructions from here: [http://www.airattack-central.com/faq.php?action=readfaq&faqid=39]("http://www.airattack-central.com/faq.php?action=readfaq&faqid=39") and was able to get the game to work. What was most important were the winetricks instructions to add the necessary components.

I'm also using the latest version of wine from [https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/~ubuntu-wine/+archive/ppa").

---

### Post by dimas869 on 2012-02-02
> **Toz said:**
> I followed the instructions from here: [http://www.airattack-central.com/faq.php?action=readfaq&faqid=39]("http://www.airattack-central.com/faq.php?action=readfaq&faqid=39") and was able to get the game to work. What was most important were the winetricks instructions to add the necessary components.

I'm also using the latest version of wine from [https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/~ubuntu-wine/+archive/ppa").

thank you for the post but i already did that
installed wine with a ppa (wine 1.4-rc1) and follow the instructions from airattack-central.com to install the game
and i still have the problem

---

### Post by Toz on 2012-02-02
Hmmm. Have you tried a separate prefix for the game?

```

WINEPREFIX=~/.wineAA winecfg
```
...and on "Graphics" tab select "Emulate a virtual desktop" and set it to 1024x768. Then:
```

WINEPREFIX=~/.wineAA wine /path/to/AAInstaller21.exe
```
...and install the game. Don't run it, but instead:
```
WINEPREFIX=~/.wineAA winetricks d3dx9 d3dx9_26 d3dx9_28 d3dx9_31 dinput8 directmusic directplay dsound
```
...then run the game ala:
```
WINEPREFIX=~/.wineAA wine ~/.wineAA/drive_c/Program\ Files/Air\ Attack/AAStart.exe
```

---

### Post by dimas869 on 2012-02-03
Hello Toz, thank you very much for the explanation but i am installing wine only for this game so i dont have nothing else but that game in the original directory although i did give it a try to your suggestion and i get the same error and took in consideration all the suggests i found in other pages and documentations as no leaving spaces between the name of the directories

---

### Post by Toz on 2012-02-03
It looks like it might be related to this bug: [http://bugs.winehq.org/show_bug.cgi?id=26796]("http://bugs.winehq.org/show_bug.cgi?id=26796"). Does it work if you use padsp?
```
WINEPREFIX=~/.wineAA padsp wine ~/.wineAA/drive_c/Program\ Files/Air\ Attack/AAStart.exe
```
...or if you have only one prefix:
```
padsp wine /path/to/executable
```

Note: you might have to:
```
padsp winecfg
```
...and setup audio on Audio tab.

---

### Post by dimas869 on 2012-02-03
> **Toz said:**
> It looks like it might be related to this bug: [http://bugs.winehq.org/show_bug.cgi?id=26796]("http://bugs.winehq.org/show_bug.cgi?id=26796"). Does it work if you use padsp?
```
WINEPREFIX=~/.wineAA padsp wine ~/.wineAA/drive_c/Program\ Files/Air\ Attack/AAStart.exe
```
...or if you have only one prefix:
```
padsp wine /path/to/executable
```

Note: you might have to:
```
padsp winecfg
```
...and setup audio on Audio tab.

hello Toz, this last post i don understand what i suppose to do, would you explain that again like i am a dommie? :D

thank you

---

### Post by Toz on 2012-02-03
Open a terminal window and type (or copy/paste) this command and press enter:
```
padsp wine ~/.wine/drive_c/Program\ Files/Air\ Attack/AAStart.exe
```
...this should try running the program and sending the OSS stream to the pulseaudio server. Might be worth a try.

If you followed the instructions from post #5, you might also want to try:
```
WINEPREFIX=~/.wineAA padsp wine ~/.wineAA/drive_c/Program\ Files/Air\ Attack/AAStart.exe
```

Post back any error messages that you may get.

---

