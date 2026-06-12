---
title: "GTA San Andreas freezes after logos"
date: 2012-11-10
forum: Wine
---

### Post by csergiu on 2012-11-10
Hello, first of all I want to say that I have searched over the internet and on AppDB and couldn't find a fix or someone else having the same problem as mine.

What I'm trying to do is get San Andreas Multiplayer to run in Wine using [this]("http://forum.ls-rp.com/viewtopic.php?f=63&t=239950") guide. I am stuck at step 13, after I launch the game through wine the logos appear and dissapear the screen just remains black and nothing else happens.

This is what the terminal gave me:
> csergiu@csergiu-F3Sc:~/.wine/drive_c/Program Files/Rockstar Games/GTA San Andreas$ wine gta_sa.exe
fixme:d3d:init_driver_info Unable to find a driver/device info for vendor_id=0x10de device_id=0x421 for driver_model=2
fixme:win:EnumDisplayDevicesW ((null),0,0x177f638,0x00000000), stub!
fixme:d3d:init_driver_info Unable to find a driver/device info for vendor_id=0x10de device_id=0x421 for driver_model=2
fixme:win:EnumDisplayDevicesW ((null),0,0x177f628,0x00000000), stub!
fixme:d3d:init_driver_info Unable to find a driver/device info for vendor_id=0x10de device_id=0x421 for driver_model=2
fixme:win:EnumDisplayDevicesW ((null),0,0x177f2e0,0x00000000), stub!
fixme:d3d:init_driver_info Unable to find a driver/device info for vendor_id=0x10de device_id=0x421 for driver_model=2
fixme:win:EnumDisplayDevicesW ((null),0,0x177f778,0x00000000), stub!
fixme:d3d:resource_check_usage Unhandled usage flags 0x28.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:d3d:wined3d_buffer_preload Too many declaration changes or converting dynamic buffer, stopping converting
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x28.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:wined3d_buffer_preload Too many declaration changes or converting dynamic buffer, stopping converting
fixme:d3d:wined3d_buffer_preload Too many declaration changes or converting dynamic buffer, stopping converting
fixme:d3d:wined3d_buffer_preload Too many declaration changes or converting dynamic buffer, stopping converting
fixme:d3d:wined3d_buffer_preload Too many declaration changes or converting dynamic buffer, stopping converting

(process:3740): GThread-WARNING **: GThread system no longer supports custom thread implementations.
fixme:gstreamer:init_new_decoded_pad Linking: 0
fixme:gstreamer:init_new_decoded_pad Linking: 0
fixme:gstreamer:no_more_pads Done
fixme:gstreamer:event_sink 0x78910860 stub tag
fixme:gstreamer:event_sink 0x7bd0d9b0 stub tag
fixme:gstreamer:event_sink 0x78910200 stub tag
fixme:gstreamer:event_sink 0x78910230 stub tag
fixme:gstreamer:event_sink 0x78910260 stub tag
fixme:gstreamer:got_data_sink Triggering 0x7bd203e8 0xe4
fixme:gstreamer:got_data_sink Triggering 0x7bd20320 0xe0
fixme:quartz:VideoRendererInner_QueryInterface No interface for {56a86897-0ad4-11ce-b03a-0020af0ba770}!
wine client error:9: read: Bad address
wine client error:9: read: Bad file descriptor
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 75 requests (75 known processed) with 0 events remaining.
^Cfixme:console:CONSOLE_DefaultHandler Terminating process 8 on event 0
err:mmtime:TIME_MMTimeStop Timer still active?!


Any help is appreciated, thanks.

---

### Post by csergiu on 2012-11-14
EDIT: Nevermind, I got it working by disabling winegstreamer.dll from Wine Config.

---

