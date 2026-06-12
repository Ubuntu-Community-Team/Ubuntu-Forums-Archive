---
title: "wow works awesome in wine, then...."
date: 2007-10-14
forum: Wine
---

### Post by Aesir09 on 2007-10-14
I run wow in wine, works nicd with some below average framerate... then the sound sounds all weird. help?

**here is my terminal after executing wow.exe**

```
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33eda8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ecd0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2cc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a4,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x14a158) call to IWineD3DDevice_CreateQuery failed
fixme:win:EnumDisplayDevicesW ((null),0,0x33f004,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:reg:GetNativeSystemInfo (0x374029c4) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x7a113494) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:d3d:set_tex_op_nvrc >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from set_tex_op_nvrc()
 @ utils.c / 1346
fixme:d3d:set_tex_op_nvrc >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from set_tex_op_nvrc()
 @ utils.c / 1346
fixme:d3d:set_tex_op_nvrc >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from set_tex_op_nvrc()
 @ utils.c / 1346
fixme:d3d:set_tex_op_nvrc >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from set_tex_op_nvrc()
 @ utils.c / 1346
fixme:d3d:set_tex_op_nvrc >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from set_tex_op_nvrc()
 @ utils.c / 1346
fixme:d3d:set_tex_op_nvrc >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from set_tex_op_nvrc()
 @ utils.c / 1346
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x33d1a4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d200,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x14a180) : stub
fixme:imm:ImmAssociateContextEx (0x20024, (nil), 16): stub

```

---

