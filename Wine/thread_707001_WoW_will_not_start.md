---
title: "WoW will not start"
date: 2008-02-25
forum: Wine
---

### Post by lhardyl on 2008-02-25
Starting WoW from terminal, game crashes.... I have sound but no picture and this is the output from term...
```
lhardyl@lhardyl-desktop:~$ wine "C:\Program Files\World of Warcraft\WoW.exe"
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
fixme:advapi:SetSecurityInfo stub
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias -720, std (d/m/y): 6/04/2008, dlt (d/m/y): 28/09/2008
fixme:powrprof:DllMain (0x7bf30000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7bf30000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x34edd8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f21c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f340,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f5e0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f5e0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f744,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x135398) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x34f050,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
lhardyl@lhardyl-desktop:~$ fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias -720, std (d/m/y): 6/04/2008, dlt (d/m/y): 28/09/2008

```

What the?

---

### Post by lhardyl on 2008-02-25
bumpedy bump

---

### Post by Faud on 2008-02-26
I would just make sure that you have direct rendering and you could try running it in open GL mode.
Has it worked for you before and just gave out this time ?

---

### Post by Dojan5 on 2008-02-26
Are you sure that your graphics card is workin?
I mean, sure i might have worked perfect on windox, but maybe not on Ubuntu.

---

