---
title: "usb cam in wine aplication dont work"
date: 2019-03-07
forum: Wine
---

### Post by szprott on 2019-03-07
Hello
I have a problem I  run with wine (the latest version) Windows application (Projekt ARES  shot to click application) the program works correctly in Ubuntu 18.04  but the camera is needed to use it completely and here is the problem wine don't see the camera, in Guvcview the camera (logitech c270) work properly, hence the question  how to "force" wine to detect the camera?

---

### Post by Frogs Hair on 2019-03-07
Moved to* Wine*.

---

### Post by szprott on 2019-03-11
really nobody can help me in this matter,

---

### Post by james.w.krych on 2019-03-14
For what it's worth from me, I thought wine was mostly for gamepads when it came to usb.

---

### Post by szprott on 2019-03-17
```
wine ARES.exe
001c:fixme:mscoree:parse_supported_runtime sku=L".NETFramework,Version=v4.5" not implemented
001c:fixme:mscoree:ConfigFileHandler_startElement Unknown element L"dependentAssembly" in state 0
001c:fixme:mscoree:ConfigFileHandler_startElement Unknown element L"assemblyIdentity" in state 6
001c:fixme:mscoree:ConfigFileHandler_startElement Unknown element L"bindingRedirect" in state 6
001c:fixme:mscoree:ConfigFileHandler_startElement Unknown element L"dependentAssembly" in state 0
001c:fixme:mscoree:ConfigFileHandler_startElement Unknown element L"assemblyIdentity" in state 6
001c:fixme:mscoree:ConfigFileHandler_startElement Unknown element L"bindingRedirect" in state 6
001c:fixme:mscoree:ConfigFileHandler_startElement Unknown element L"dependentAssembly" in state 0
001c:fixme:mscoree:ConfigFileHandler_startElement Unknown element L"assemblyIdentity" in state 6
001c:fixme:mscoree:ConfigFileHandler_startElement Unknown element L"bindingRedirect" in state 6

Unhandled Exception:
System.TypeLoadException: Could not load type of field 'ServiceLayer.CoreService:wssv' (40) due to: Could not load file or assembly 'websocket-sharp, Version=1.0.2.59611, Culture=neutral, PublicKeyToken=5660b08a1845a91e' or one of its dependencies. assembly:websocket-sharp, Version=1.0.2.59611, Culture=neutral, PublicKeyToken=5660b08a1845a91e type:<unknown type> member:<none>
000f:err:service:process_send_command service protocol error - failed to write pipe!
000f:fixme:service:scmdatabase_autostart_services Auto-start service L"nebula" failed to start: 1053
000f:fixme:service:scmdatabase_autostart_services Auto-start service L"SCDEmu" failed to start: 3
0034:fixme:winmm:MXD_GetControlDetails What should the sw-side mixer controls map to?
0009:err:ole:CoGetClassObject class {82c5ab54-c92c-4d52-aac5-27e25e22604c} not registered
0009:err:ole:CoGetClassObject class {82c5ab54-c92c-4d52-aac5-27e25e22604c} not registered
0009:err:ole:create_server class {82c5ab54-c92c-4d52-aac5-27e25e22604c} not registered
0009:err:ole:CoGetClassObject no class object {82c5ab54-c92c-4d52-aac5-27e25e22604c} could be created for context 0x7
0009:fixme:win:EnumDisplayDevicesW ((null),0,0x33f604,0x00000000), stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_HAL, src_format WINED3DFMT_B8G8R8A8_UNORM, dst_format WINED3DFMT_B8G8R8X8_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_HAL, src_format WINED3DFMT_B8G8R8X8_UNORM, dst_format WINED3DFMT_B8G8R8X8_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_HAL, src_format WINED3DFMT_B10G10R10A2_UNORM, dst_format WINED3DFMT_B8G8R8X8_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_HAL, src_format WINED3DFMT_B5G6R5_UNORM, dst_format WINED3DFMT_B8G8R8X8_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_HAL, src_format WINED3DFMT_B5G5R5A1_UNORM, dst_format WINED3DFMT_B8G8R8X8_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_HAL, src_format WINED3DFMT_B5G5R5X1_UNORM, dst_format WINED3DFMT_B8G8R8X8_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_HAL, src_format WINED3DFMT_B8G8R8A8_UNORM, dst_format WINED3DFMT_B5G6R5_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_HAL, src_format WINED3DFMT_B8G8R8X8_UNORM, dst_format WINED3DFMT_B5G6R5_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_HAL, src_format WINED3DFMT_B10G10R10A2_UNORM, dst_format WINED3DFMT_B5G6R5_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_HAL, src_format WINED3DFMT_B5G6R5_UNORM, dst_format WINED3DFMT_B5G6R5_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_HAL, src_format WINED3DFMT_B5G5R5A1_UNORM, dst_format WINED3DFMT_B5G6R5_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_HAL, src_format WINED3DFMT_B5G5R5X1_UNORM, dst_format WINED3DFMT_B5G6R5_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_SW, src_format WINED3DFMT_B8G8R8A8_UNORM, dst_format WINED3DFMT_B8G8R8X8_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_SW, src_format WINED3DFMT_B8G8R8X8_UNORM, dst_format WINED3DFMT_B8G8R8X8_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_SW, src_format WINED3DFMT_B10G10R10A2_UNORM, dst_format WINED3DFMT_B8G8R8X8_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_SW, src_format WINED3DFMT_B5G6R5_UNORM, dst_format WINED3DFMT_B8G8R8X8_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_SW, src_format WINED3DFMT_B5G5R5A1_UNORM, dst_format WINED3DFMT_B8G8R8X8_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_SW, src_format WINED3DFMT_B5G5R5X1_UNORM, dst_format WINED3DFMT_B8G8R8X8_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_SW, src_format WINED3DFMT_B8G8R8A8_UNORM, dst_format WINED3DFMT_B5G6R5_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_SW, src_format WINED3DFMT_B8G8R8X8_UNORM, dst_format WINED3DFMT_B5G6R5_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_SW, src_format WINED3DFMT_B10G10R10A2_UNORM, dst_format WINED3DFMT_B5G6R5_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_SW, src_format WINED3DFMT_B5G6R5_UNORM, dst_format WINED3DFMT_B5G6R5_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_SW, src_format WINED3DFMT_B5G5R5A1_UNORM, dst_format WINED3DFMT_B5G6R5_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_SW, src_format WINED3DFMT_B5G5R5X1_UNORM, dst_format WINED3DFMT_B5G6R5_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_REF, src_format WINED3DFMT_B8G8R8A8_UNORM, dst_format WINED3DFMT_B8G8R8X8_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_REF, src_format WINED3DFMT_B8G8R8X8_UNORM, dst_format WINED3DFMT_B8G8R8X8_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_REF, src_format WINED3DFMT_B10G10R10A2_UNORM, dst_format WINED3DFMT_B8G8R8X8_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_REF, src_format WINED3DFMT_B5G6R5_UNORM, dst_format WINED3DFMT_B8G8R8X8_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_REF, src_format WINED3DFMT_B5G5R5A1_UNORM, dst_format WINED3DFMT_B8G8R8X8_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_REF, src_format WINED3DFMT_B5G5R5X1_UNORM, dst_format WINED3DFMT_B8G8R8X8_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_REF, src_format WINED3DFMT_B8G8R8A8_UNORM, dst_format WINED3DFMT_B5G6R5_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_REF, src_format WINED3DFMT_B8G8R8X8_UNORM, dst_format WINED3DFMT_B5G6R5_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_REF, src_format WINED3DFMT_B10G10R10A2_UNORM, dst_format WINED3DFMT_B5G6R5_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_REF, src_format WINED3DFMT_B5G6R5_UNORM, dst_format WINED3DFMT_B5G6R5_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_REF, src_format WINED3DFMT_B5G5R5A1_UNORM, dst_format WINED3DFMT_B5G6R5_UNORM stub!
0009:fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1594f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_REF, src_format WINED3DFMT_B5G5R5X1_UNORM, dst_format WINED3DFMT_B5G6R5_UNORM stub!

***** VIDEOINPUT LIBRARY - 0.1995 - TFW07 *****

0009:fixme:msvcrt:__clean_type_info_names_internal (0x442e7cc) stub

***** VIDEOINPUT LIBRARY - 0.1995 - TFW07 *****

0009:err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\devenum.dll"
0009:err:ole:CoGetClassObject no class object {62be5d10-60eb-11d0-bd3b-00a0c911ce86} could be created for context 0x1
0009:err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\devenum.dll"
0009:err:ole:CoGetClassObject no class object {62be5d10-60eb-11d0-bd3b-00a0c911ce86} could be created for context 0x1
0009:err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\devenum.dll"
0009:err:ole:CoGetClassObject no class object {62be5d10-60eb-11d0-bd3b-00a0c911ce86} could be created for context 0x1
0009:err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\devenum.dll"
0009:err:ole:CoGetClassObject no class object {62be5d10-60eb-11d0-bd3b-00a0c911ce86} could be created for context 0x1
0009:err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\devenum.dll"
0009:err:ole:CoGetClassObject no class object {62be5d10-60eb-11d0-bd3b-00a0c911ce86} could be created for context 0x1
0009:fixme:d3d:wined3d_query_create Unhandled query type 0x4.
0009:err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\devenum.dll"
0009:err:ole:CoGetClassObject no class object {62be5d10-60eb-11d0-bd3b-00a0c911ce86} could be created for context 0x1
0009:err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\devenum.dll"
0009:err:ole:CoGetClassObject no class object {62be5d10-60eb-11d0-bd3b-00a0c911ce86} could be created for context 0x1
0034:fixme:winmm:MXD_SetControlDetails What should the sw-side mixer controls map to?
0009:fixme:msvcrt:__clean_type_info_names_internal (0x45de7cc) stub

```

---

### Post by dacha on 2019-03-29
Webcams are accessed through DirectShow, one of Windows's most complex APIs.

Try running it with WINEDEBUG=+qcap,+quartz and attach the output.

---

### Post by RedDirtDog on 2019-04-07
I've had huge issues getting Wine to access USB devices.  Keyboard/Mice were OK, but no luck beyond that

---

