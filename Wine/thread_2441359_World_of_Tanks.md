---
title: "World of Tanks"
date: 2020-04-22
forum: Wine
---

### Post by warhawk472 on 2020-04-22
I downloaded WOT( World of tanks) in ubuntu using Lutris. Now, on clicking the Wargaming icon opens the game but after that when I click on the play button on the main WOT screen. The game launches and it shows the World of tanks game logo and after a few seconds, the game crashes with no error showing on the screen. Wine and play on Linux are already installed and updated. How can I fix this issue I just want to play the game. I am using ubuntu 20.04 LTS.

---

### Post by howefield on 2020-04-22
Thread moved to the "Wine" forum.

---

### Post by mastablasta on 2020-04-23
you need wine staging and old launcher more here: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=36493](https://appdb.winehq.org/objectManager.php?sClass=version&iId=36493)

it also says mouse sticks to center after certain wine version, so it might be worth using older wine-staging version (easy to do on PoL). 

also using DXVk the game seems to be hanging a lot.

> [COLOR=#000000][FONT=monospace]As Mirecc21 points out, DXVk solves all graphics issues. Make sure you have all 32 bit libraries as well as 64 installed, even for 64 bit systems.[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]However...it is not gold. The game keeps hanging, and always at the same few points:[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]1) Starting WGC. Very rarely you just get a medium size black rectangle.[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]2) Battle loading screen. You usually realise this when you notice some of your tanks are dead and you haven't even entered the battle yet.[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]3)Exiting battle. This takes forever. As does synchronising garage etc. WG really need to work on their networking. Very rarely you just get the progress indicator circling for ever.[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]4) Returning to garage. After "Exiting battle" finishes, returning to garage (or whatever it is called) hangs. Sometimes the background is blank, but sometimes (mostly I think if you saw the battle to the end) you can see the garage in the background with the results screen overlaid, but the game is hung.[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]If you are very unlucky you can get hang 2 and hang 4 for the same battle. I find that I can get an hour or two play before it goes wrong for the first time and after that it goes wrong every other battle or so.[/FONT][/COLOR]

good luck.

---

### Post by warhawk472 on 2020-04-23
I tried running the game using the above method but it didn't work. Also, I would like to tell you that earlier while using ubuntu 18.04 LTS the game worked perfectly fine when run using Lutris. What I actually did at that time was to just download Lutris and then installed the preferred world of tanks client to run the game. But in the same version i.e. 18.04 LTS after installing AMD graphics card from AMD website the Ubuntu failed to boot after which I reinstalled ubuntu and then installed WOT games using the above method again but it didn't work.

Now, after a fresh install of Ubuntu 20.04 LTS I tried to install the game again using Lutris the same way I did in 18.04 LTS but this time in Lutris wargaming game center is opening and the game is downloaded successfully but when I click the play button it shows the WOT screen (the first screen where WOT logo is visible) for few seconds and then closes.

Wargaming game center keeps running and did not crash this whole time but WOT game crashes.

---

### Post by warhawk472 on 2020-04-23
This is the log file that was generated on running the Wargaming client [COLOR=#ff0000]the red part came after I click on the stop button in Lutris since the game already crashed. (World of tank window opens and its logo was visible  on-screen and then the window closes after that I click on the stop  button in Lutris ).
[/COLOR]
```
Running  /home/aseem/.PlayOnLinux/wine/linux-amd64/5.1-staging/bin/wine  /home/aseem/Games/wargaming-game-center/drive_c/Program Files  (x86)/Wargaming.net/GameCenter/wgc.exe
Initial process has started with pid 30509
Game is considered started.
[0424/042232.275:ERROR:network_change_notifier_win.cc(141)] WSALookupServiceBegin failed with: 0
info:  Game: wgc_renderer.exe
info:  DXVK: v1.6.1+
info:  Built-in extension providers:
info:    Win32 WSI
info:    OpenVR
warn:  OpenVR: Failed to locate module
info:  Enabled instance extensions:
info:    VK_KHR_surface
info:    VK_KHR_win32_surface
[0424/042234.648:ERROR:network_change_notifier_win.cc(141)] WSALookupServiceBegin failed with: 0
info:  Intel(R) HD Graphics 620 (KBL GT2):
info:    Driver: 20.0.99
info:    Vulkan: 1.2.131
info:    Memory Heap[0]: 
info:      Size: 5592 MiB
info:      Flags: 0x1
info:      Memory Type[0]: Property Flags = 0xf
info:  Adapter LUID 0: 0:3fc
info:  Game: wgc_renderer.exe
info:  DXVK: v1.6.1+
info:  Built-in extension providers:
info:    Win32 WSI
info:    OpenVR
warn:  OpenVR: Failed to locate module
info:  Enabled instance extensions:
info:    VK_KHR_surface
info:    VK_KHR_win32_surface
info:  Intel(R) HD Graphics 620 (KBL GT2):
info:    Driver: 20.0.99
info:    Vulkan: 1.2.131
info:    Memory Heap[0]: 
info:      Size: 5592 MiB
info:      Flags: 0x1
info:      Memory Type[0]: Property Flags = 0xf
info:  D3D11CoreCreateDevice: Probing D3D_FEATURE_LEVEL_11_1
info:  D3D11CoreCreateDevice: Using feature level D3D_FEATURE_LEVEL_11_1
info:  Device properties:
info:    Device name:     : Intel(R) HD Graphics 620 (KBL GT2)
info:    Driver version   : 20.0.99
info:  Enabled device extensions:
info:    VK_EXT_depth_clip_enable
info:    VK_EXT_host_query_reset
info:    VK_EXT_shader_demote_to_helper_invocation
info:    VK_EXT_shader_stencil_export
info:    VK_EXT_shader_viewport_index_layer
info:    VK_EXT_transform_feedback
info:    VK_EXT_vertex_attribute_divisor
info:    VK_KHR_create_renderpass2
info:    VK_KHR_depth_stencil_resolve
info:    VK_KHR_draw_indirect_count
info:    VK_KHR_driver_properties
info:    VK_KHR_image_format_list
info:    VK_KHR_sampler_mirror_clamp_to_edge
info:    VK_KHR_swapchain
info:  Device features:
info:    robustBufferAccess                     : 1
info:    fullDrawIndexUint32                    : 1
info:    imageCubeArray                         : 1
info:    independentBlend                       : 1
info:    geometryShader                         : 1
info:    tessellationShader                     : 1
info:    sampleRateShading                      : 1
info:    dualSrcBlend                           : 1
info:    logicOp                                : 1
info:    multiDrawIndirect                      : 1
info:    drawIndirectFirstInstance              : 1
info:    depthClamp                             : 1
info:    depthBiasClamp                         : 1
info:    fillModeNonSolid                       : 1
info:    depthBounds                            : 0
info:    multiViewport                          : 1
info:    samplerAnisotropy                      : 1
info:    textureCompressionBC                   : 1
info:    occlusionQueryPrecise                  : 1
info:    pipelineStatisticsQuery                : 1
info:    vertexPipelineStoresAndAtomics         : 1
info:    fragmentStoresAndAtomics               : 1
info:    shaderImageGatherExtended              : 1
info:    shaderStorageImageExtendedFormats      : 1
info:    shaderStorageImageReadWithoutFormat    : 0
info:    shaderStorageImageWriteWithoutFormat   : 1
info:    shaderClipDistance                     : 1
info:    shaderCullDistance                     : 1
info:    shaderFloat64                          : 1
info:    shaderInt64                            : 1
info:    variableMultisampleRate                : 1
info:  VK_EXT_conditional_rendering
info:    conditionalRendering                   : 1
info:  VK_EXT_depth_clip_enable
info:    depthClipEnable                        : 1
info:  VK_EXT_host_query_reset
info:    hostQueryReset                         : 1
info:  VK_EXT_memory_priority
info:    memoryPriority                         : 0
info:  VK_EXT_shader_demote_to_helper_invocation
info:    shaderDemoteToHelperInvocation         : 1
info:  VK_EXT_transform_feedback
info:    transformFeedback                      : 1
info:    geometryStreams                        : 1
info:  VK_EXT_vertex_attribute_divisor
info:    vertexAttributeInstanceRateDivisor     : 1
info:    vertexAttributeInstanceRateZeroDivisor : 1
info:  Queue families:
info:    Graphics : 0
info:    Transfer : 0
info:  DXVK: Read 0 valid state cache entries
info:  DXVK: Using 2 compiler threads
err:   Failed to create surface
[0424/042235.402:ERROR:angle_platform_impl.cc(47)]  reset(615): Could not create additional swap chains or offscreen  surfaces, HRESULT: 0x80070057
[0424/042235.402:ERROR:gl_surface_egl.cc(612)] EGL Driver message (Critical) eglCreateWindowSurface: Bad allocation.
[0424/042235.402:ERROR:gl_surface_egl.cc(1176)] eglCreateWindowSurface failed with error EGL_BAD_ALLOC
[0424/042235.403:ERROR:in_process_command_buffer.cc(593)] ContextResult::kSurfaceFailure: Failed to create surface.
[0424/042235.445:ERROR:command_buffer_proxy_impl.cc(124)]  ContextResult::kTransientFailure: Failed to send  GpuChannelMsg_CreateCommandBuffer.
[0424/042235.445:WARNING:ipc_message_attachment_set.cc(49)] MessageAttachmentSet destroyed with unconsumed attachments: 0/1
[0424/042235.826:INFO:CONSOLE(1)] "[webChannel] connection established.", source: qrc:/ui/main.8f06b6d2a19e324299e3.js (1)
info:  Game: wgc.exe
info:  DXVK: v1.6.1+
info:  Built-in extension providers:
info:    Win32 WSI
info:    OpenVR
warn:  OpenVR: Failed to locate module
info:  Enabled instance extensions:
info:    VK_KHR_surface
info:    VK_KHR_win32_surface
info:  Intel(R) HD Graphics 620 (KBL GT2):
info:    Driver: 20.0.99
info:    Vulkan: 1.2.131
info:    Memory Heap[0]: 
info:      Size: 5592 MiB
info:      Flags: 0x1
info:      Memory Type[0]: Property Flags = 0xf
info:  Adapter LUID 0: 0:3fd
info:  Game: wgc.exe
info:  DXVK: v1.6.1+
info:  Built-in extension providers:
info:    Win32 WSI
info:    OpenVR
warn:  OpenVR: Failed to locate module
info:  Enabled instance extensions:
info:    VK_KHR_surface
info:    VK_KHR_win32_surface
warn:  D3D9: VK_FORMAT_D16_UNORM_S8_UINT -> VK_FORMAT_D24_UNORM_S8_UINT
info:  Intel(R) HD Graphics 620 (KBL GT2):
info:    Driver: 20.0.99
info:    Vulkan: 1.2.131
info:    Memory Heap[0]: 
info:      Size: 5592 MiB
info:      Flags: 0x1
info:      Memory Type[0]: Property Flags = 0xf
info:  Process set as DPI aware
[COLOR=#ff0000]Caught signal 15
passing along signal to PID 30509
passing along signal to PID 30554
passing along signal to PID 30609
passing along signal to PID 30627
passing along signal to PID 30631
passing along signal to PID 30749
--terminated processes--
Game is considered exited.
Initial process has exited.
All monitored processes have exited.
Exit with returncode 15
[/COLOR]
```

---

### Post by mastablasta on 2020-04-24
since you are using PoL here. what happens if you use older version of wine-staging? le.g. 4.0 or something. the one with least issues reported. make sure you have all necessary libraries installed (32 and 64bit) as well as try older launcher.

i forgot how WoT looks like when it starts up. i stopped playing it quite some time ago after realising that it was a pay to win game. you could pay for shells that provided instant penetration and kill. it was fun in early stages though. also too many angry trolls.

---

### Post by warhawk472 on 2020-04-24
this is the link for output file generated when running cmd vulkaninfo in terminal 

[https://paste.ubuntu.com/p/Bkd2z3MCpT/](https://paste.ubuntu.com/p/Bkd2z3MCpT/)

the top two lines show wrong ELF class for both graphic cards AMD and intel 
```
 
ERROR: [Loader Message] Code 0 : /usr/lib/i386-linux-gnu/libvulkan_radeon.so: wrong ELF class: ELFCLASS32
ERROR: [Loader Message] Code 0 : /usr/lib/i386-linux-gnu/libvulkan_intel.so: wrong ELF class: ELFCLASS32

```

not exactly sure what it means.
I will also try to check if i have all libraries 32 bit and 64 bit but not really sure which libraries to look for.

---

