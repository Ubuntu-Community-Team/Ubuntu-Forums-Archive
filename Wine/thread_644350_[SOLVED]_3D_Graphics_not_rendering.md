---
title: "[SOLVED] 3D Graphics not rendering"
date: 2007-12-18
forum: Wine
---

### Post by Felson on 2007-12-18
I have a number of games that were working fine (or mostly fine), and now don't render 3D video at all. My System is an AMD64 running Ubuntu 7.10 (Gutsy) 64bit. 2.8 GH Dual core with 2 GB of ram.

2 things on this system changed since I last tried to run any of these games:
1) Updated to WINE 0.9.51 (auto update)
2) Video card changed from an on board Nvidia based card to an ATI Radeon x1600

I am thinking that he issue is the video card, because if it was the auto update I should have found something on the forums about it by now. It is possible that I am just a noob, and that there is a simple configuration I need to change, but I will be damed if I can find it... Any help would be wonderful.

---

### Post by Felson on 2007-12-18
Here is the output from when I try and run Heroes Of Might And Magic V

```

:-> wine H5_Game.exe
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,9,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,18,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,27,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,36,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,45,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,54,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,63,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,72,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,81,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,90,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,99,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,108,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,117,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,126,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,135,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,144,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,153,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,162,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,171,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,180,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,189,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,198,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,207,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,216,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,225,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,234,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,243,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,252,2): stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f840,0x00000000), stub!
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1653a0) Unhandled query type 4
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x157d70) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1653a0) Event query: Unimplemented, but pretending to be supported
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #536870913: "WARNING: 0:1: extension 'GL_ARB_draw_buffers' is not supported\n"
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #2147483649: " Link successful. The GLSL vertex shader will run in hardware. The GLSL fragment shader will run in hardware."
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1653a0) Unhandled query type 4
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x155290) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1653a0) Event query: Unimplemented, but pretending to be supported
fixme:wininet:InternetSetOptionExA Flags 04000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (1000): STUB
fixme:wininet:InternetSetOptionExA Flags 04000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
No arguments found, but required
No arguments found, but required
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #536870913: "WARNING: 0:1: extension 'GL_ARB_draw_buffers' is not supported\n"
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #2147483649: " Link successful. The GLSL vertex shader will run in hardware. The GLSL fragment shader will run in hardware."
sock_set_error: Success
fixme:wininet:InternetSetOptionExA Flags 04000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (1000): STUB
fixme:wininet:InternetSetOptionExA Flags 04000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1653a0) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1653a0) Event query: Unimplemented, but pretending to be supported
sock_set_error: Success
fixme:wininet:InternetSetOptionExA Flags 04000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (1000): STUB
fixme:wininet:InternetSetOptionExA Flags 04000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
sock_set_error: Success
fixme:wininet:InternetSetOptionExA Flags 04000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (1000): STUB
fixme:wininet:InternetSetOptionExA Flags 04000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
sock_set_error: Success
fixme:wininet:InternetSetOptionExA Flags 04000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (1000): STUB
fixme:wininet:InternetSetOptionExA Flags 04000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
sock_set_error: Success
fixme:wininet:InternetSetOptionExA Flags 04000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (1000): STUB
fixme:wininet:InternetSetOptionExA Flags 04000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #536870914: "WARNING: 0:1: extension 'GL_ARB_draw_buffers' is not supported\n"
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #2147483650: " Link successful. The GLSL vertex shader will run in hardware. The GLSL fragment shader will run in hardware."
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #536870915: "WARNING: 0:1: extension 'GL_ARB_draw_buffers' is not supported\n"
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #2147483651: " Link successful. The GLSL vertex shader will run in hardware. The GLSL fragment shader will run in hardware."
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #536870916: "WARNING: 0:1: extension 'GL_ARB_draw_buffers' is not supported\n"
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #2147483652: "Warning: built-in varying gl_TexCoord[1] has mismatched access semantics between the vertex and fragment shader\nWarning: built-in varying gl_TexCoord[2] has mismatched access semantics between the vertex and fragment shader\n Link successful. The GLSL vertex shader will run in hardware. The GLSL fra"...
sock_set_error: Success
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #536870917: "WARNING: 0:1: extension 'GL_ARB_draw_buffers' is not supported\n"
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #2147483653: " Link successful. The GLSL vertex shader will run in hardware. The GLSL fragment shader will run in hardware."
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #536870918: "WARNING: 0:1: extension 'GL_ARB_draw_buffers' is not supported\n"
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #2147483654: " Link successful. The GLSL vertex shader will run in hardware. The GLSL fragment shader will run in hardware."
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #536870919: "WARNING: 0:1: extension 'GL_ARB_draw_buffers' is not supported\n"
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #2147483655: " Link successful. The GLSL vertex shader will run in hardware. The GLSL fragment shader will run in hardware."
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #536870920: "WARNING: 0:1: extension 'GL_ARB_draw_buffers' is not supported\n"
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #2147483656: "Warning: built-in varying gl_TexCoord[1] has mismatched access semantics between the vertex and fragment shader\n Link successful. The GLSL vertex shader will run in hardware. The GLSL fragment shader will run in hardware."
fixme:wininet:InternetSetOptionExA Flags 04000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (1000): STUB
fixme:wininet:InternetSetOptionExA Flags 04000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
sock_set_error: Success
fixme:wininet:InternetSetOptionExA Flags 04000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (1000): STUB
fixme:wininet:InternetSetOptionExA Flags 04000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
sock_set_error: Success

```

---

### Post by cogadh on 2007-12-18
The solution is simple, go back to the Nvidia video, it will work better than the ATI one. At the moment the ATI Linux drivers are not all that mature and you will likely get better performance and much greater ease of use out of the Nvidia device.

---

### Post by Felson on 2007-12-18
:) Sadly that isn't the answer... My on board video is most definitely NOT better then the card I have in there now. But thanks for a replay all the same.

---

### Post by Felson on 2007-12-21
Still trying to figure this out. If anyone could offer some help, that would be awesome.

---

### Post by Felson on 2008-01-04
bump. (Still looking)

---

### Post by Faud on 2008-01-04
Not to speak for Codagh but I THINK, he isnt talking about the card itself, he is talking about the ease of compatability with the ATI drivers vs the Nvidia drivers..
Which drivers are you using for your ATI card ?

---

### Post by Felson on 2008-01-04
The ATI "restricted" one. Under Graphics Cards, it comes up as "fglrx".

---

### Post by Faud on 2008-01-05
I would make sure that you even have direct rendering with the new card

```

glxinfo | grep direct

```

Are you able to get things like compiz to work ?

---

### Post by Felson on 2008-01-05
Yes, I have direct rendering.
```

-> glxinfo | grep direct
direct rendering: Yes

```

no, compiz doesn't work.
```
> compiz
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

```

---

### Post by Faud on 2008-01-05
Maybe you could try the suggestion found here?

[http://ubuntuforums.org/showthread.php?t=596927](http://ubuntuforums.org/showthread.php?t=596927)

---

### Post by Felson on 2008-01-05
I installed xserver-xgl, and it changed my issues entirely. 

Most interesting... 
Disciples 2 seems to work well, Heroes 5 Loads, has "3d" graphics, but has no texturing at all, and not menu text, and Oblivion doesn't load (not that it worked well when it did load).

Any other ideas? (And thanks for the help BTW.)

---

### Post by Felson on 2008-01-05
ok, I figured out the problem..
I had to uncheck "Allow Pixel Shader". That works without xserver-xgl installed.

---

