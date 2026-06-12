---
title: "Steins;Gate crashes on start up"
date: 2011-10-20
forum: Wine
---

### Post by Zienthe on 2011-10-20
[SIZE=2]When I first installed it, it crashed with the error "gstreamer: mpeg plugin missing", or something to that effect. I installed the required plugins, but now it crashes with this: [/SIZE]
 
```
 
[tons of these "Unhandled usage flags" errors] 
fixme:d3d:resource_check_usage Unhandled usage flags 0x8. 
fixme:d3d:resource_check_usage Unhandled usage flags 0x8. 
fixme:d3d:resource_check_usage Unhandled usage flags 0x8. 
fixme:gstreamer:init_new_decoded_pad Linking: 0 
fixme:gstreamer:no_more_pads Done 
fixme:gstreamer:got_data_sink Triggering 0x79b42e48 0xb2c 
err:d3d:resource_init Out of memory! 
fixme:d3d_texture:texture_init Failed to create surface 0x10d20c48, hr 0x8876017c 
wine: Unhandled page fault on read access to 0x00000000 at address 0x4a44a7 (thread 0009), starting debugger... 
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x004a44a7). 
 
[Register dump, a stack dump and backtrace follows - I don't know whether it's of any importance, so I didn't include it, as it's quite long] 
 
zsh: segmentation fault wine STEINSGATE.exe

```
 
[SIZE=2]Any idea on how to fix this? I'm on wine 1.3.29.[/SIZE]

---

