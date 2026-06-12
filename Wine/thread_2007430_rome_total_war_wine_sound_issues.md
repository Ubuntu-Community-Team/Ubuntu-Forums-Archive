---
title: "rome total war wine sound issues"
date: 2012-06-20
forum: Wine
---

### Post by linuxman72 on 2012-06-20
I am having issues running rome total war in wine.
I am running ubuntu precise and wine 1.5.6
I have a copy of Rome total war gold edition
Installation went smoothly

when I run the game I get errors of several varieties (and the game crashes at startup), I have corrected some of them, which were related to incorrect sound drivers (miles sound system), and finally got the initial splashscreen to show up, which was followed by this terminal output and a game crash:

```
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000003 not handled
fixme:win:EnumDisplayDevicesW ((null),0,0x32dce0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ded8,0x00000000), stub!
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
Failed to initialise 3D audio!
```

I believe that only the last two lines are fatal errors as the others all printed before the game crashed. I then tried using different sound outputs in winecfg-audio and then the game would not even load the splashscreen, even if I changed the winecfg-audio back to what it was. then when I launched the game this printed to the terminal:

```
wine: Unhandled page fault on write access to 0xe6aed29a at address 0x6670ea50 (thread 003e), starting debugger...
Can't attach process 003d: error 5
```

and a window appeared with a message about invalid parameters.

a few minutes later I ran the game again (no changes) and for some reason the splashscreen appeared again, but this time the terminal printed:

```
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000003 not handled
fixme:win:EnumDisplayDevicesW ((null),0,0x32dce0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ded8,0x00000000), stub!
err:ntdll:RtlpWaitForCriticalSection section 0x110060 "heap.c: main process heap section" wait timed out in thread 0030, blocked by 0009, retrying (60 sec)
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc3495a
err:ntdll:RtlpWaitForCriticalSection section 0x110060 "heap.c: main process heap section" wait timed out in thread 0030, blocked by 0009, retrying (60 sec)
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc3495a
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x62e5dc,0x64a14a): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x133968,0x64a14a): stub
err:eventlog:ReportEventW L"3"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x62e5dc,0x64a1c2): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x133968,0x64a1c2): stub
err:eventlog:ReportEventW L"6"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x000002cc,0x62e5dc,0x651a62): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x000002cc,0x133968,0x651a62): stub
err:eventlog:ReportEventW L"7"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x62e5dc,0x651d4a): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x133968,0x651d4a): stub
err:eventlog:ReportEventW L"3"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x62e5dc,0x651dc2): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x133968,0x651dc2): stub
err:eventlog:ReportEventW L"6"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x000002cc,0x62e5dc,0x651e3a): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x000002cc,0x133968,0x651e3a): stub
err:eventlog:ReportEventW L"7"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
```

Note: this time the game runs for a few minutes (invisibly, the only indication that it is running is the terminal and the wine symbol in the unity sidebar) before all of this appears.

Please Help, I consider myself somewhat computer capable, but  I have no idea what is going on other than that it involves audio.

---

### Post by linuxman72 on 2012-08-24
I have been installing new versions of wine whenever they are released hoping that RTW will start working. It still does not work, but it continues longer before crashing now. this is the terminal output I get now:

```
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000003 not handled
fixme:win:EnumDisplayDevicesW ((null),0,0x33dce0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ded8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3331e0,0x00000000), stub!
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:wined3d_buffer_preload Too many declaration changes or converting dynamic buffer, stopping converting
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000003 not handled
fixme:win:EnumDisplayDevicesW ((null),0,0x332a88,0x00000000), stub!
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000003 not handled
fixme:win:EnumDisplayDevicesW ((null),0,0x332a40,0x00000000), stub!
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000003 not handled
fixme:win:EnumDisplayDevicesW ((null),0,0x332fec,0x00000000), stub!
fixme:d3d_surface:surface_convert_format Cannot find a conversion function from format WINED3DFMT_B5G6R5_UNORM to WINED3DFMT_B8G8R8A8_UNORM.

(process:4008): GThread-WARNING **: GThread system no longer supports custom thread implementations.
fixme:gstreamer:init_new_decoded_pad Linking: 0
fixme:gstreamer:no_more_pads Done
fixme:gstreamer:event_sink 0x7ec41950 stub tag
fixme:gstreamer:event_sink 0x7ec41980 stub tag
fixme:gstreamer:got_data_sink Triggering 0x7ec03cc0 0x200
fixme:gstreamer:GST_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:strmbase:TransformFilterImpl_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:VideoRendererInner_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:VideoRendererInner_QueryInterface No interface for {56a86897-0ad4-11ce-b03a-0020af0ba770}!
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xeee977
fixme:gstreamer:no_more_pads Done
fixme:gstreamer:event_sink 0x7ec41a00 stub tag
fixme:gstreamer:event_sink 0x7ec41a30 stub tag
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x62e5dc,0x6527d2): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x133420,0x6527d2): stub
err:eventlog:ReportEventW L"6"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x000002cc,0x62e5dc,0x65284a): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x000002cc,0x133420,0x65284a): stub
err:eventlog:ReportEventW L"7"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub


```

please help!

---

### Post by linuxman72 on 2012-09-09
Bump

---

