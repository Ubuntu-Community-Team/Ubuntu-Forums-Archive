---
title: "Howto: Lineage 2 - C6 in Ubuntu 7.10"
date: 2007-12-08
forum: Wine
---

### Post by eledh on 2007-12-08
This is a detailed howto about installing Lineage 2 Chronicle 6. I recommend you to configure to play in L2Dimensions server ([www.l2dimensions.com](www.l2dimensions.com)), built in L2J, also free software, running in a Linux. Is one of the bests L2J servers. I also post some screenshots to show you the results about it. Hope this guide will be useful to you guys. You can get more information in wine webpage. I just show how it worked to me ;D

[[img]http://img136.imageshack.us/img136/3153/screenshot2bw1.png[/img]](http://imageshack.us)

My config:

  - Ubuntu 7.10 for AMD64
  - NVIDIA 6600GT - Installed drivers **nvidia-glx-new + nvidia-kernel-common**
  - Wine Version: **wine-0.9.49** (last tested on wine-0.9.50 also works)
  - How?
     1. Install Wine (recommended for ubuntu, the same version i used). You can find information about how to install it for each distribution in **[http://www.winehq.org/site/download](http://www.winehq.org/site/download)**
     2. Download L2 Game Installer, and install it by using the command:  wine setup,exe
     3. After got the game installed in wine and updated using Lineage2.exe (it will tell you to install a plugin, just accept and let it update the game). Download this patch: **[http://www.megaupload.com/?d=0WDDHZ1D](http://www.megaupload.com/?d=0WDDHZ1D)**
     4. Add patch system folder files to your lineage system folder (do not replace patch folder for lineage folder, just copy the file inside the patch folder and replace for the lineage folder files... otherwise you'll miss some files)
     5. Update WIne's DirectX. How? Copy **dpmodemx.dll, dpnet.dll, dpwsock.dll, dpwsockx.dll **from any windows to your wine drive_c/windows/system32/ (i copied from Windows XP - Professional updated to SP2 and to DirectX 9.0c, and those files can be found in your **<label>:/Windows/system32/** folder)
     6. To disable GameGuard, add in your linux **/etc/security/limits.conf** file the following line at the end of the file. It should look like following:
**        *      hard    nofile      16383**
        # End of file 
     7. Run the command **winecfg**.Go to "Application" and:
              - add l2.exe (from wine LineageII/system) and set Windows Vista as O.S. Version
              - add LineageII.exe (from the main wine Linage II Folder) and set Windows Vista as O.S. Version.
              - I also have modified Default Settings to Windows Vista, but seems isn't needed. 
              - Example: 

[[img]http://img114.imageshack.us/img114/5324/screenshotwineconfiguraem9.png[/img]](http://imageshack.us)
     8. Edit your linux /etc/hosts and add the following line at any part of the file:
     **209.190.93.178  l2authd.lineage2.com**

     9. Sometimes you can get the following message:

You have triggered a bug in the DirectX 9.0c runtime. Please install DirectX 8.1b (or later) for a fix. See Release Notes for instructions on how to obtain it.

If so open a terminal and run:     **wineserver -k **  After it finishes to run, launch game again.

     10. If you got problems in camera, disable **Tracking** option in L2 options  (in game, or you can also edit **option.ini** file)

---

### Post by Sugi on 2007-12-10
amazing Howto.  I wish there was one when I needed it in the beginning of 2007.  I don't know if this will work for everyone, but

 - I just installed Lineage 2 C4 on a windows partition and 
 - copy it over to Ubuntu.  
 - run L2.exe wihtin wine 
 - and bam!  it worked.

I did have some problems with the camera.  Thanks for the tip. :)

---

### Post by eXXy on 2007-12-25
i tried to run lineage in ubuntu 7.10 with wine 0.9.51 and system32 fully copied from windows xp sp2 one, and this is what i have:
```
exxy@exxy-desktop:~/lineage/system$ wine l2.exe
fixme:reg:GetNativeSystemInfo (0x1ef424b) using GetSystemInfo()
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1f4b35e): Stub!
fixme:reg:GetNativeSystemInfo (0x3015dcdb) using GetSystemInfo()
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x301b3a0a): Stub!
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x34f078,0x34f074): stub
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x34e8d8,0x00000000), stub!
fixme:imm:ImmReleaseContext (0x2003c, 0x138078): stub
fixme:imm:ImmGetDefaultIMEWnd (0x2003c - (nil) 0x138078 ): semi-stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aba0, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aba0, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aba0, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aba0, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab8c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab8c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab8c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab8c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab8c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab8c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab8c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab8c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab8c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab8c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab8c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab8c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aac8, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aac8, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aac8, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aac8, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab8c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab8c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab8c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab8c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab64, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab64, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab64, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab64, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab64, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab64, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab64, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab64, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa3c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa3c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa3c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa3c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa3c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa3c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa3c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa3c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa40, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa40, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa40, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa40, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa20, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa20, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa20, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa20, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa20, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa20, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa20, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa20, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa20, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa20, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa20, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34aa20, 259): stub
fixme:advpack:write_predefined_strings SYS_MOD_PATH needs more work
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab44, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab44, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab44, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab44, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab44, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab44, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab44, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ab44, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abb8, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abb8, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abb8, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abb8, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34abec, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34ac2c, 259): stub
fixme:process:IsWow64Process (0xffffffff 0x349b44) stub!
fixme:d3d:state_patchedgestyle (WINED3DRS_PATCHEDGESTYLE,1065353216) not yet implemented
wine: Unhandled exception 0x80000003 at address 0x109169e2 (thread 0009), starting debugger...
0x109169e2: int $3
Modules:
Module  Address                 Debug info      Name (137 modules)
PE        350000-  35f000       Deferred        ogg
PE        360000-  39f000       Deferred        vorbis
PE        3a0000- 2099000       Deferred        engine
PE       20a0000- 20b4000       Deferred        dsetup
PE       28e0000- 291b000       Deferred        ifc23
PE       3e00000- 3fbd000       Deferred        d3ddrv
PE       4150000- 455b000       Deferred        nwindow
PE       4560000- 45c8000       Deferred        npkcrypt
PE       45d0000- 45de000       Deferred        npkpdb
PE       68c0000- 6917000       Deferred        alaudio
PE      10000000-1001c000       Deferred        vorbisfile
PE      10100000-10352000       Deferred        core
PE      10500000-10551000       Deferred        fire
PE      10900000-109ac000       Export          l2
PE      11000000-110ba000       Deferred        window
PE      11100000-1119e000       Deferred        windrv
PE      30000000-30207000       Deferred        binkw32
ELF     79003000-7901b000       Deferred        usp10<elf>
  \-PE  79010000-7901b000       \               usp10
ELF     79298000-792e2000       Deferred        dsound<elf>
  \-PE  792a0000-792e2000       \               dsound
ELF     792e2000-79303000       Deferred        mpr<elf>
  \-PE  792f0000-79303000       \               mpr
ELF     79303000-79350000       Deferred        wininet<elf>
  \-PE  79310000-79350000       \               wininet
ELF     79350000-793b6000       Deferred        setupapi<elf>
  \-PE  79360000-793b6000       \               setupapi
ELF     795c7000-795fe000       Deferred        dinput<elf>
  \-PE  795d0000-795fe000       \               dinput
ELF     795fe000-79617000       Deferred        dinput8<elf>
  \-PE  79600000-79617000       \               dinput8
ELF     79983000-79a24000       Deferred        oleaut32<elf>
  \-PE  799a0000-79a24000       \               oleaut32
ELF     7b800000-7b92b000       Deferred        kernel32<elf>
  \-PE  7b820000-7b92b000       \               kernel32
ELF     7b933000-7b979000       Deferred        riched20<elf>
  \-PE  7b940000-7b979000       \               riched20
ELF     7b979000-7b98d000       Deferred        riched32<elf>
  \-PE  7b980000-7b98d000       \               riched32
ELF     7b98d000-7b9de000       Deferred        libgcrypt.so.11
ELF     7bc00000-7bca3000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca3000       \               ntdll
ELF     7bca5000-7bcb0000       Deferred        libgcc_s.so.1
ELF     7bcb0000-7bcde000       Deferred        libcrypt.so.1
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf08000-7bf78000       Deferred        libgnutls.so.13
ELF     7bf78000-7c000000       Deferred        libkrb5.so.3
ELF     7c146000-7c156000       Deferred        libtasn1.so.3
ELF     7c156000-7c15e000       Deferred        libkrb5support.so.0
ELF     7c15e000-7c183000       Deferred        libk5crypto.so.3
ELF     7c183000-7c1ac000       Deferred        libgssapi_krb5.so.2
ELF     7c1ac000-7c1e1000       Deferred        libcups.so.2
ELF     7d460000-7d492000       Deferred        uxtheme<elf>
  \-PE  7d470000-7d492000       \               uxtheme
ELF     7d492000-7d4b9000       Deferred        msacm32<elf>
  \-PE  7d4a0000-7d4b9000       \               msacm32
ELF     7d4b9000-7d4d1000       Deferred        msacm32<elf>
  \-PE  7d4c0000-7d4d1000       \               msacm32
ELF     7d740000-7d755000       Deferred        midimap<elf>
  \-PE  7d750000-7d755000       \               midimap
ELF     7d755000-7d791000       Deferred        wineoss<elf>
  \-PE  7d760000-7d791000       \               wineoss
ELF     7d791000-7d79a000       Deferred        libxcursor.so.1
ELF     7d79a000-7d7b8000       Deferred        imm32<elf>
  \-PE  7d7a0000-7d7b8000       \               imm32
ELF     7d7b8000-7d7bd000       Deferred        libxfixes.so.3
ELF     7d7bd000-7d7c0000       Deferred        libxcomposite.so.1
ELF     7d7c0000-7d7c6000       Deferred        libxrandr.so.2
ELF     7d7c6000-7d7ce000       Deferred        libxrender.so.1
ELF     7d7cf000-7d7d3000       Deferred        libgpg-error.so.0
ELF     7d7d3000-7d7d5000       Deferred        libkeyutils.so.1
ELF     7d7d5000-7d7d8000       Deferred        libcom_err.so.2
ELF     7d876000-7e20e000       Deferred        libglcore.so.1
ELF     7e20e000-7e2a4000       Deferred        libgl.so.1
ELF     7e2a4000-7e2a9000       Deferred        libxdmcp.so.6
ELF     7e2a9000-7e39a000       Deferred        libx11.so.6
ELF     7e39a000-7e3a8000       Deferred        libxext.so.6
ELF     7e3a8000-7e3ad000       Deferred        libxxf86vm.so.1
ELF     7e3ad000-7e3c5000       Deferred        libice.so.6
ELF     7e3c5000-7e3cd000       Deferred        libsm.so.6
ELF     7e3d9000-7e466000       Deferred        winex11<elf>
  \-PE  7e3f0000-7e466000       \               winex11
ELF     7e4f8000-7e518000       Deferred        libexpat.so.1
ELF     7e518000-7e543000       Deferred        libfontconfig.so.1
ELF     7e543000-7e558000       Deferred        libz.so.1
ELF     7e558000-7e5c8000       Deferred        libfreetype.so.6
ELF     7e5c8000-7e5f5000       Deferred        ws2_32<elf>
  \-PE  7e5d0000-7e5f5000       \               ws2_32
ELF     7e5f5000-7e60f000       Deferred        wsock32<elf>
  \-PE  7e600000-7e60f000       \               wsock32
ELF     7e60f000-7e623000       Deferred        lz32<elf>
  \-PE  7e620000-7e623000       \               lz32
ELF     7e623000-7e63d000       Deferred        version<elf>
  \-PE  7e630000-7e63d000       \               version
ELF     7e63d000-7e693000       Deferred        ddraw<elf>
  \-PE  7e650000-7e693000       \               ddraw
ELF     7e693000-7e780000       Deferred        wined3d<elf>
  \-PE  7e6b0000-7e780000       \               wined3d
ELF     7e780000-7e7ae000       Deferred        d3d9<elf>
  \-PE  7e790000-7e7ae000       \               d3d9
ELF     7e7ae000-7e7e3000       Deferred        winspool<elf>
  \-PE  7e7c0000-7e7e3000       \               winspool
ELF     7e7e3000-7e885000       Deferred        comdlg32<elf>
  \-PE  7e7f0000-7e885000       \               comdlg32
ELF     7e885000-7e898000       Deferred        libresolv.so.2
ELF     7e898000-7e89b000       Deferred        libxau.so.6
ELF     7e8a4000-7e8c2000       Deferred        iphlpapi<elf>
  \-PE  7e8b0000-7e8c2000       \               iphlpapi
ELF     7e8c2000-7e91e000       Deferred        rpcrt4<elf>
  \-PE  7e8d0000-7e91e000       \               rpcrt4
ELF     7e91e000-7e9c1000       Deferred        ole32<elf>
  \-PE  7e930000-7e9c1000       \               ole32
ELF     7e9c1000-7ea7f000       Deferred        comctl32<elf>
  \-PE  7e9d0000-7ea7f000       \               comctl32
ELF     7ea7f000-7ead8000       Deferred        shlwapi<elf>
  \-PE  7ea90000-7ead8000       \               shlwapi
ELF     7ead8000-7ebdd000       Deferred        shell32<elf>
  \-PE  7eaf0000-7ebdd000       \               shell32
ELF     7ebdd000-7ec29000       Deferred        advapi32<elf>
  \-PE  7ebf0000-7ec29000       \               advapi32
ELF     7ec29000-7ecc2000       Deferred        gdi32<elf>
  \-PE  7ec40000-7ecc2000       \               gdi32
ELF     7ecc2000-7edff000       Deferred        user32<elf>
  \-PE  7ece0000-7edff000       \               user32
ELF     7edff000-7ee8d000       Deferred        winmm<elf>
  \-PE  7ee10000-7ee8d000       \               winmm
ELF     7efac000-7efb7000       Deferred        libnss_files.so.2
ELF     7efb7000-7efcf000       Deferred        libnsl.so.1
ELF     7efcf000-7eff4000       Deferred        libm.so.6
ELF     7eff4000-7eff6000       Deferred        libnvidia-tls.so.1
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c65000-b7c6e000       Deferred        libnss_compat.so.2
ELF     b7c6f000-b7c73000       Deferred        libdl.so.2
ELF     b7c73000-b7dbd000       Deferred        libc.so.6
ELF     b7dbe000-b7dd6000       Deferred        libpthread.so.0
ELF     b7de2000-b7ef6000       Deferred        libwine.so.1
ELF     b7ef8000-b7f14000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000022 
        00000024    0
        00000023    0
00000008 (D) Z:\home\exxy\lineage\system\l2.exe
        00000042   15
        00000040    0
        0000003f    0
        0000003e    0
        0000003d    2
        0000003c    2
        0000003b    2
        0000003a    2
        00000039    2
        00000038    2
        00000037    2
        00000036    2
        00000035    2
        00000034    2
        00000033    2
        00000032    2
        00000031    2
        00000030    2
        0000002f    2
        0000002e    2
        0000002d    0
        0000002c    0
        0000002b    0
        0000002a    0
        00000029    0
        00000028    0
        00000027    0
        00000026    0
        00000025    0
        00000021    2
        00000020    2
        0000001f    2
        0000001e    2
        0000001d    2
        0000001c    2
        0000001b    2
        0000001a    2
        00000019    2
        00000018    2
        00000017    2
        00000016    2
        00000015    2
        00000014    2
        00000013    2
        00000012    2
        00000011    0
        00000010    0
        0000000f    0
        0000000e    0
        0000000d    0
        0000000c    0
        0000000b    0
        0000000a    0
        00000009    0 <==
Backtrace:
=>1 0x109169e2 in l2 (+0x169e2) (0x0034fe70)
  2 0x10922471 in l2 (+0x22471) (0x0034ff08)
  3 0x7b8759fe in kernel32 (+0x559fe) (0x0034ffe8)
  4 0xb7de98f7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc8fce4 "loader.c: loader_section" wait timed out in thread 000b, blocked by 0027, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7e4635e0 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 0027, blocked by 0009, retrying (60 sec)

```
help me plz :(

---

### Post by eledh on 2008-01-04
Which gfx do you have?

---

### Post by eXXy on 2008-01-06
> **eledh said:**
> Which gfx do you have?
GeForce 8800 GTS 320mb

---

### Post by bagde on 2008-01-15
a cant still run lineage2,settings i do it a perfect,but when I runnig lineage2 eject
error "An internal exception occured(Adress :0x1f33677)".If you have some ideas,please whrite it.

---

### Post by eledh on 2008-01-28
About 
rr:ntdll:RtlpWaitForCriticalSection section 0x7e4635e0 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 0027, blocked by 0009, retrying (60 sec)
error, try to modify your Option.ini in your L2 system folder to 32 bit or 16 bit, or directly delete option.ini to let the game reconfigure this file automatically.
Dunno where can be the problem but maybethis can help.

---

### Post by dragonhunter on 2008-02-09
Hi Guys

I play Lineage 1, and I tried to install it in my ubuntu. Everything runs fine, but when I get the screen to log in I got an error message saying 

**¨File initialization error related to nProtect has ocurred. Log in through the administrator account and run the game. Thank you.**"
 
Well I tried to run lineage using sudo and I got  this error on my console
```



ronald@ronald-laptop:~/.wine/drive_c/Program Files/Lineage$ sudo wine lineage.exe 
ronald@ronald-laptop:~/.wine/drive_c/Program Files/Lineage$ fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x10a3c50) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x219330)->(0x30024,00000011)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d_surface:IWineGDISurfaceImpl_Blt Can't handle DDBLT_WAIT flag right now.
err:d3d_surface:IWineGDISurfaceImpl_LockRect (0x10f2860) Surface already locked
err:d3d_surface:IWineGDISurfaceImpl_LockRect (0x10f2860) Surface already locked
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x4839b7

```

Could anyone help me to fix it?

---

### Post by Duelmaster on 2008-02-24
FANTASTIC HOW TO. I'll try it and tell you if it works on 7600 GS 512mb.:popcorn:

---

### Post by Duelmaster on 2008-02-25
When I go to loading screen it turns me this.

2008.2.25 16:57:59
OS : Windows Vista 6.0 (Build: 6000)
CPU : GenuineIntel Unknown processor @ 3416 MHz with 1519MB RAM
Video : Direct3D HAL (10014)

Failed to load 'Level None.MyLevel': Can't find file '21_16.unr'

History: UObject::SafeLoadError <- UObject::StaticLoadObject <- (Engine.Level None.MyLevel 21_16.unr) <- LoadLevel <- UGameEngine::LoadMap <- LocalMapURL <- UGameEngine::Browse <- ClientTravel <- UGameEngine::Tick <- UpdateWorld <- MainLoop

Ok i got it, thanks. Sorry for double posting.

---

### Post by Sugi on 2008-02-27
I am still having issus with the camera. 
> "10. If you got problems in camera, disable Tracking option in L2 options (in game, or you can also edit option.ini file)"

I did both the System Options and the option.ini, but I am still having problems with the camera.  What Should I do?


By the way, has anyone got a fix for the hotkeys issus with ubuntu's hotkeys (like IE: alt + F1 for menu, or alt + F4 for close :()???


Sugi

---

### Post by Quid on 2008-03-16
Hi..
in  installtion I get it asking for the disk due to missing files?
Anyone see that?
Also what is the patch for?
The second post implied it was not being used by him?

---

### Post by Omnibilion on 2008-03-30
Im having problems to run Lineage2 on wine. I follow every step that i read in the porst, but, when i launch L2, a window message appears that says "the game may not be consistant because AGP is deactivated. Please activate AGP for consistancy" Im new with Ubuntu, so i dont know what is missing. The wine version is 0.9.46 and th Ubuntu 7.10. How do i fix this?:confused:

---

### Post by Sugi on 2008-04-22
**Omnibilion**
> Im having problems to run Lineage2 on wine. I follow every step that i read in the porst, but, when i launch L2, a window message appears that says "the game may not be consistant because AGP is deactivated. Please activate AGP for consistancy" Im new with Ubuntu, so i dont know what is missing. The wine version is 0.9.46 and th Ubuntu 7.10. How do i fix this?

Omnibilion and anyone else reading this,
I don't mean to be rude, but he clearly stated to use 0.9.49 and 0.9.50 because they both work with Lineage 2 and have been tested.  Everyone troubleshooting Lineage 2, please use version 0.9.49 or 0.9.50 and then come back here and post your issues, but do not post your problems if you are not following the step by step order eledh posted for us.  I can truely say, you need to listen eledh, because I know after wine 0.9.51 Lineage 2 broke for me.

Try PlayOnLinux for different wine version at the same (I am not going to go into details on this because this thread is base on Linux and Lineage 2 = LL)

**Omnibilion**
> "The game may not be consistant because AGP is deactivated. Please activate AGP for consistancy"

For this fix, just check OK and leave Linux and Lineage 2 alone when Lineage 2 is loading up.  I notice if I don't do anything with Lineage 2 when it is loading up, the game loads faster and it does not give me any errors.  But I mean, I do not do anything when Lineage 2 is loading up.  I just sit there and wait for it to load.  I have to wait about 5 minutes for the game to load, but it's does load.  And In-Game is fast as hell with max settings on.

**Quid**
> Hi..
in installtion I get it asking for the disk due to missing files?
Anyone see that?
Also what is the patch for?
The second post implied it was not being used by him?

Huh?  If I understand you correctly, when you are installing Lineage 2 it says you are missing files during the installation?  If so, I had this same problem within Windows for probably a few weeks.  I had a corrupted compression of Lineage 2 (lineage2.rar)  and I was trying to find a uncorrupted winrar compression of Lineage 2 and it was a pain in my butt. I also had to find a correct version of Winrar to unzip the compression Lineage 2.  

"Also what is the patch for?" It's for playing Lineage 2 C6 on the same server as eledh plays on.

**dragonhunter**
> Hi Guys

I play Lineage 1, and I tried to install it in my ubuntu. Everything runs fine, but when I get the screen to log in I got an error message saying 

¨File initialization error related to nProtect has ocurred. Log in through the administrator account and run the game. Thank you."

Well I tried to run lineage using sudo and I got this error on my console

I have not played Lineage 1 before but I have heard of it.  nProtect sounds like it is referring to GameGuard or something like it, but I am not sure if Lineage 1 used GameGuard back then, but if you can find a patch for GameGuard within Linux for Lineage 1 you are set.  And, if you are using sudo with wine that is not a good thing at all even for a game.  Sudo can mess up the permission of wine and how it runs games.   You might to reinstall wine, but I think there is better fixes out there for correcting the permission of wine. >.<

This may help though,
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=687]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=687")

**bagde**
> a cant still run lineage2,settings i do it a perfect,but when I runnig lineage2 eject
error "An internal exception occured(Adress :0x1f33677)".If you have some ideas,please whrite it.

**eledh**
> try to modify your Option.ini in your L2 system folder
This does work for a number of errors during Lineage 2 booting up.  I backed up of my original Lineage 2 option.ini file from Windows, the option.ini file is within the Lineage 2/system/option.ini.  When ever I get that "An internal exception occurred" or any other error, I just replace the options.ini file with my original Windows back up and everything runs fine.

Note:  The error happens after you have seen the Splash screen of Lineage 2 on your desktop and it starts loading the actually window of Lineage 2 (the black box), but then crashes and the error appears.  Just replace your option.ini file with your original Window's backup of the option.ini.
Remember Lineage 2 is in the directory of Lineage 2/system/option.ini.


**Sugi**
> I am still having issus with the camera. 
Quote:"10. If you got problems in camera, disable Tracking option in L2 options (in game, or you can also edit option.ini file)" 

I did both the System Options and the option.ini, but I am still having problems with the camera. What Should I do?

To reply to my older post, I did get the Tracking (camera) working into lineage 2 on Linux.  I sometimes have to go into system options and enable Tracking.
In-Game > Alt + X > Options > System Tab > check Tracking





Spec:
Dual Core 2.0 GHz
2 gigs DDR2
7700 go
Lineage 2 C4
Wine 0.9.50

Played Lineage 2 on Windows since 2004
Played Lineage 2 on Linux since 2006



I hope this helps someone and Please fell free to post any more problems,
Sugi

---

### Post by DaveBG on 2008-05-05
I managed to run the game but i do not have sound? Does anyone know how to enable the sound?

---

### Post by bagde on 2008-05-13
hi,sorry for my bad english, I have a problem,when I play I can't teleport,when I teleporting i get error or stay where i was before teleport.This problem isn't in the patch,because i try a many patch and this problem not disappear.

---

### Post by VinisLentoje on 2008-05-15
Hello,
I have a problem: Lineage2 stucks on character loading. I log in, choose a character, click "Start", than I see the loading screen and in a sec or two I start hearing the character creation screen sounds. But it refuses to load, the HDD indicator shows that there's no HHD activity. Than I have the only option, but to kill the program. I've spent long hours trying to fix this, but no luck.

Anyone has an idea?

Thank You!

And sorry for my bad English.

---

### Post by VinisLentoje on 2008-05-25
bump

---

### Post by Sugi on 2008-06-10
VinisLentoje,
Try creating a Character within a Windows Box.  There is a known bug for creating Human Characters within Lineage 2 on wine.  The bug crashes Lineage 2, but sorry I do not have more help for you.

DaveBG, There is two things you can do.  First, try the sound options tab within Lineage 2.  Alt + X (I am not sure if this is the right hotkey, sorry. I am not on my ubuntu box right now.) Next, click system option and then Sound tab.  Second, make sure your wine has configed sound driver.  This is probably it.  Open up wine (
Terminal > winecfg
) and then click on the sound tab to see if sound is enable.  Sometimes to enable it, is just clicking on the sound tab.

bagde, This sounds like Lineage 2 is sucking up all your processing power.  This happen on windows sometimes on older machine (at least it happen to me).  But are you on a older machine?  Does the teleporting takes a long time to process and then gives error?  Please, can you fill me in with more details of your errors?  Like what is the actual error.  Run Lineage 2 through the terminal and give me the final output when it crashes.  What patches are you refering to?  Like c2, c3, c4 kind of patches?

I am truely sorry for my late reply, I did not think anyone was still posting on this thread.  I was checking it, but no new posts.  Sorry for my poor english as well.  Let me know if I need to example anything farer.

Cheers,
Sugi

---

### Post by VinisLentoje on 2008-06-10
> **Sugi said:**
> VinisLentoje,
Try creating a Character within a Windows Box.  There is a known bug for creating Human Characters within Lineage 2 on wine.  The bug crashes Lineage 2, but sorry I do not have more help for you.


Cheers,
Sugi

I can't log in with the characters I already have for a long time.
Some of them are humans, but they were created on windows.
So, anyone else has any ideas?

---

### Post by Darkshade on 2008-06-12
I'm having some trouble with Lineage II too. When I first installed Ubuntu and couldn't make it run I just dualbooted windows for L2 (the only game I play, and the only thing I needed windows for) but now my other hard disk died and I'm trying to get it work on Ubuntu. I tried tons of different configurations and nothing turned to work. Now I seem to have the best setup so far but 4 different things happen when I run the game:
1. The game crashes before the login screen.
2. The game freezes after entering my login info and selecting the server.
3. The game crashes after selecting the character.
4. The game just works fine for some time but crashes in places with more people.
All 4 options include an "AGP is deactivated..." error at launching the game.
When the game crashes I get an "You have outdated nvidia drivers, please update to version ...". The thing is that I have an ATI Radeon 9250 card and I'm using the default Ubuntu drivers, not nvidia. I also tried removing all the visual effects (compiz, window fx, etc) but nothing seems to change.

I looked all over the internet for a solution, seems like most people using ATI cards have the same issues. Should I get an nvidia gfx card or there's still hope for ati?

Any help is appreciated.

---

### Post by hellramza on 2008-09-08
I know this post is a bit old but I'm trying to run L2 on my gutsy and I can't make it work. I get to run my server's updater, but when I try to run L2.exe (or click the "Start" button on the updater) it just doesn't work. I tried deleting Option.ini and also leaving it more than 5 minutes to see if it came back to life but nothing, the process goes "zombie" and does nothing, not even suck up my processor or RAM.

This is my terminal output:

```
fixme:reg:GetNativeSystemInfo (0x1ef9526) using GetSystemInfo()
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1f522d6): Stub!
wine: Unhandled page fault on write access to 0x00e7d7e4 at address 0x101091c9 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x00e7d7e4 in 32-bit code (0x101091c9).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:101091c9 ESP:0034f574 EBP:0034f5b8 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00000000 EBX:0034fe5c ECX:00e7d7e0 EDX:00000004
 ESI:00e7d798 EDI:109686b4
Stack dump:
0x0034f574:  00000004 007b8c96 00000004 00000000
0x0034f584:  109686b4 0034fe5c 0034fe5c 0034fe68
0x0034f594:  10916062 1096b008 0011043c 10970448
0x0034f5a4:  10996f10 0034f584 0034fe5c 008ccab0
0x0034f5b4:  ffffffff 0034fe68 10916970 656e694c
0x0034f5c4:  32656761 75527349 6e696e6e 46744167
Backtrace:
=>1 0x101091c9 in core (+0x91c9) (0x0034f5b8)
  2 0x10916970 in l2 (+0x16970) (0x0034fe68)
  3 0x10922471 in l2 (+0x22471) (0x0034ff00)
  4 0x00000000 (0x0034fee0)
  5 0xcd02eb3e (0x00000000)
0x101091c9: movl        $0x0,0x4(%ecx)
Modules:
Module  Address                 Debug info      Name (113 modules)
PE        350000-  35f000       Deferred        ogg
PE        360000-  39f000       Deferred        vorbis
PE        3a0000- 20a3000       Deferred        engine
PE       20b0000- 20c4000       Deferred        dsetup
PE       20d0000- 217d000       Deferred        nvidia
PE       29a0000- 29db000       Deferred        ifc23
PE      10000000-1001c000       Deferred        vorbisfile
PE      10100000-10352000       Export          core
PE      10900000-10a01000       Export          l2
PE      11000000-110ba000       Deferred        window
ELF     7b800000-7b92a000       Deferred        kernel32<elf>
  \-PE  7b820000-7b92a000       \               kernel32
ELF     7bc00000-7bca2000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c301000-7c352000       Deferred        libgcrypt.so.11
ELF     7c352000-7c356000       Deferred        libgpg-error.so.0
ELF     7c356000-7c366000       Deferred        libtasn1.so.3
ELF     7c366000-7c36e000       Deferred        libkrb5support.so.0
ELF     7c36e000-7c39c000       Deferred        libcrypt.so.1
ELF     7c39c000-7c40c000       Deferred        libgnutls.so.13
ELF     7c40c000-7c431000       Deferred        libk5crypto.so.3
ELF     7c431000-7c4b9000       Deferred        libkrb5.so.3
ELF     7c4b9000-7c4e2000       Deferred        libgssapi_krb5.so.2
ELF     7c4e2000-7c517000       Deferred        libcups.so.2
ELF     7e002000-7e004000       Deferred        libkeyutils.so.1
ELF     7e004000-7e036000       Deferred        uxtheme<elf>
  \-PE  7e010000-7e036000       \               uxtheme
ELF     7e036000-7e04b000       Deferred        midimap<elf>
  \-PE  7e040000-7e04b000       \               midimap
ELF     7e04b000-7e072000       Deferred        msacm32<elf>
  \-PE  7e050000-7e072000       \               msacm32
ELF     7e072000-7e08a000       Deferred        msacm32<elf>
  \-PE  7e080000-7e08a000       \               msacm32
ELF     7e08a000-7e150000       Deferred        libasound.so.2
ELF     7e150000-7e153000       Deferred        libcom_err.so.2
ELF     7e163000-7e199000       Deferred        winealsa<elf>
  \-PE  7e170000-7e199000       \               winealsa
ELF     7e199000-7e1a2000       Deferred        libxcursor.so.1
ELF     7e1a2000-7e1bf000       Deferred        imm32<elf>
  \-PE  7e1b0000-7e1bf000       \               imm32
ELF     7e1bf000-7e1c2000       Deferred        libxcomposite.so.1
ELF     7e1c2000-7e1c8000       Deferred        libxrandr.so.2
ELF     7e1c8000-7e1d0000       Deferred        libxrender.so.1
ELF     7e1d0000-7e1d3000       Deferred        libxinerama.so.1
ELF     7e1d3000-7e1dd000       Deferred        libdrm.so.2
ELF     7e1dd000-7e1e2000       Deferred        libxfixes.so.3
ELF     7e1e2000-7e1e5000       Deferred        libxdamage.so.1
ELF     7e1e5000-7e1ea000       Deferred        libxxf86vm.so.1
ELF     7e1ea000-7e24b000       Deferred        libgl.so.1
ELF     7e24b000-7e250000       Deferred        libxdmcp.so.6
ELF     7e250000-7e253000       Deferred        libxau.so.6
ELF     7e253000-7e344000       Deferred        libx11.so.6
ELF     7e344000-7e352000       Deferred        libxext.so.6
ELF     7e365000-7e3f6000       Deferred        winex11<elf>
  \-PE  7e370000-7e3f6000       \               winex11
ELF     7e444000-7e464000       Deferred        libexpat.so.1
ELF     7e464000-7e48f000       Deferred        libfontconfig.so.1
ELF     7e48f000-7e4a4000       Deferred        libz.so.1
ELF     7e4a4000-7e514000       Deferred        libfreetype.so.6
ELF     7e514000-7e5b4000       Deferred        oleaut32<elf>
  \-PE  7e530000-7e5b4000       \               oleaut32
ELF     7e5b4000-7e5c9000       Deferred        psapi<elf>
  \-PE  7e5c0000-7e5c9000       \               psapi
ELF     7e5c9000-7e5f6000       Deferred        ws2_32<elf>
  \-PE  7e5d0000-7e5f6000       \               ws2_32
ELF     7e5f6000-7e610000       Deferred        wsock32<elf>
  \-PE  7e600000-7e610000       \               wsock32
ELF     7e610000-7e624000       Deferred        lz32<elf>
  \-PE  7e620000-7e624000       \               lz32
ELF     7e624000-7e63e000       Deferred        version<elf>
  \-PE  7e630000-7e63e000       \               version
ELF     7e63e000-7e693000       Deferred        ddraw<elf>
  \-PE  7e650000-7e693000       \               ddraw
ELF     7e693000-7e777000       Deferred        wined3d<elf>
  \-PE  7e6b0000-7e777000       \               wined3d
ELF     7e777000-7e7a6000       Deferred        d3d9<elf>
  \-PE  7e780000-7e7a6000       \               d3d9
ELF     7e7a6000-7e7db000       Deferred        winspool<elf>
  \-PE  7e7b0000-7e7db000       \               winspool
ELF     7e7db000-7e87c000       Deferred        comdlg32<elf>
  \-PE  7e7e0000-7e87c000       \               comdlg32
ELF     7e87c000-7e88f000       Deferred        libresolv.so.2
ELF     7e8a2000-7e8c0000       Deferred        iphlpapi<elf>
  \-PE  7e8b0000-7e8c0000       \               iphlpapi
ELF     7e8c0000-7e91a000       Deferred        rpcrt4<elf>
  \-PE  7e8d0000-7e91a000       \               rpcrt4
ELF     7e91a000-7e9bc000       Deferred        ole32<elf>
  \-PE  7e930000-7e9bc000       \               ole32
ELF     7e9bc000-7ea7b000       Deferred        comctl32<elf>
  \-PE  7e9d0000-7ea7b000       \               comctl32
ELF     7ea7b000-7ead4000       Deferred        shlwapi<elf>
  \-PE  7ea90000-7ead4000       \               shlwapi
ELF     7ead4000-7ebd7000       Deferred        shell32<elf>
  \-PE  7eaf0000-7ebd7000       \               shell32
ELF     7ebd7000-7ec23000       Deferred        advapi32<elf>
  \-PE  7ebe0000-7ec23000       \               advapi32
ELF     7ec23000-7ecbb000       Deferred        gdi32<elf>
  \-PE  7ec30000-7ecbb000       \               gdi32
ELF     7ecbb000-7edf8000       Deferred        user32<elf>
  \-PE  7ece0000-7edf8000       \               user32
ELF     7edf8000-7ee86000       Deferred        winmm<elf>
  \-PE  7ee00000-7ee86000       \               winmm
ELF     7efa5000-7efb0000       Deferred        libnss_files.so.2
ELF     7efb0000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efed000       Deferred        libm.so.6
ELF     7efed000-7eff7000       Deferred        libnss_nis.so.2
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     f7cc2000-f7cc6000       Deferred        libdl.so.2
ELF     f7cc6000-f7e10000       Deferred        libc.so.6
ELF     f7e11000-f7e29000       Deferred        libpthread.so.0
ELF     f7e3c000-f7f50000       Deferred        libwine.so.1
ELF     f7f52000-f7f70000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000022 
        00000023    0
00000008 (D) C:\Program Files\Lineage II\system\L2.exe
        00000025    0
        00000024    0
        00000021    2
        00000020    2
        0000001f    2
        0000001e    2
        0000001d    2
        0000001c    2
        0000001b    2
        0000001a    2
        00000019    2
        00000018    2
        00000017    2
        00000016    2
        00000015    2
        00000014    2
        00000013    2
        00000012    2
        00000011    0
        00000010    0
        0000000f    0
        0000000e    0
        0000000d    0
        0000000c    0
        0000000a    0
        00000009    0 <==
```

Any help would be appreciated.

EDIT: Forgot my pc specs:
Dual Core 2.0 GHz
2 gigs DDR2
Intel x3100 GPU (integrated)
Ubuntu Gutsy
Wine 0.9.49

---

### Post by Sugi on 2008-10-28
VinisLentoje,
This could also be an issue with the Option.ini.  But to tell you the truth, I still can't find enough information on your bug or any kind of fixes for it either.

Darkshade,
I would say try to look into a Nvidia card.  I have done some work with ATI cards, and to tell you the trust it was complete hell. First I can't couldn't my video card drivers install, next I couldn't get 3D supprt, and latest I couldn't get games working. They would always spit out the weirdest errors within my terminal. >.< It was hell.  Getting a nvidia could help... a lot.  Also you maybe running into issues with the Option.ini within the system folder of Lineage 2 directory.  I found a lot of my crashes was being caused by this file.  If you are still trying to get Lineage 2 running. Let me know and I can give you some tips on howto get Lineage 2 running without issues from the Option.ini.

hellramza, I was talking to you through PMs a while back, and you stated that you gave up on trying to get Lineage 2 to work through Ubuntu.  For people with the same issues, I will report what we try to do to get it working on Ubuntu.  He tried, wine 1.0, wine 1.0.1, wine, 1.1.3, wine 1.1.4, and versions before wine 1.0.  It seemed the core issue of his problems was his graphic card.  Intel x3100 GPU (integrated) Intel isn't known for making great Linux drivers that support 3D acceleration.

Good Luck,
Sugi

---

### Post by Darkshade on 2008-10-29
Thank you for your reply, Sugi.
I gave up on ATI as soon as I started to understand Ubuntu (when I first posted a couple of months ago I had just installed it for the first time).
I talked to some people who are playing L2 on Linux, all of them were using Nvidia and the ones that tried with ATI had the same issues.
I'm getting a Nvidia soon - something that I had to do long ago, and it'll hopefully solve all my problems (and not only with games, since my current video card is driving me crazy with all kind of stuff).
If I have any trouble with it after that I'll post here.

---

### Post by Sugi on 2008-10-29
Darkshade, I am sorry it took me soo long to reply back to you.  I keep thinking this thread is dead, but when I check on it. It's alive and kicking.  I am currently playing Lineage 2 again on Ubuntu about 5+ hours a day. >.< I'm that addicted to this game :-/  If you need anything, please feel free to ask away.

Sugi

---

### Post by smo0th on 2008-11-05
I get stuck in the server selection screen, I click on either server and it does not advance anymore further than that window, any idea :confused:

---

### Post by Sugi on 2008-11-10
smo0th, I think your problme is the host file and incorrect IP address for your sever.  

```
sudo nano /etc/hosts
```
Open /etc/hosts as root and add the following line:EXAMPLE
127.0.0.1 your.server.l2.com
(^Please remember that is only an exmple, you will have to input the correct ip and server name most likely found on your server's website.)

Remember most Lineage 2 server's has their own server (computer) just for login screen connections and then another server just for their actually Lineage 2 game.

Sugi


PS: The image is from my siege just over the weeken.  To tell you the truth, the siege was terrible, but I got some oh kay screen shots.
(VIEW: Front person mode without interface.)

---

### Post by smo0th on 2008-11-10
hey Sugi, thanks for replying, however that is not my problem, I have done the following:

[LIST]
[*]checked very well my hosts file
[*]installed most recent nvidia drivers (8200GT card)
[*]wine version is 1.0
[*]downloaded tweaked system folder from wine's website
[*]updated wine's directx files (dpmodemx.dll, dpnet.dll, dpwsock.dll, dpwsockx.dll)
[*]disabled gameguard by adding '* hard nofile 16383' inside '/etc/security/limits.conf'
[*]added l2.exe and LineageII.exe to applications list using winecfg
[/LIST]

any ideas will be appreciated T-T

---

### Post by Sugi on 2008-11-10
smo0th, You should check with your admin of your server to see if the gameguard is disable. A lot of servers disable it by default.  If it is disable, you should roll back to the original limits.conf file to make sure that is not one of your issues.

Tweak system files?  For your Wine's Windows's system directory or your Lineage 2 system directory?

Also, it seems like your Lineage 2 server's connection servers is either: under a lot of pressure, because of most logins (prime hour) or the conntection server is down or your Lineage 2 game server is down or an incorrect host file.  Have you tried loging in other times and other days?  My old Lineage 2 server was done all the time. I ended up just leaving for another server.

Please note, L2j servers are bugging as hell and crash a lot.  Find a nice serever with hand coded game clients and good hardware. :D

Sugi

---

### Post by nackgr on 2008-11-11
Hello I am Trying To  Open L2.exe I have  A Critical Saying General Protection Fault and i Have Edited the Line     * hard nofile 16383
So what may be The Problem Anyone KnowS plz Respond ,,, :D
EDIT 
 Ok All Problems SolVed :D

---

### Post by nackgr on 2008-11-12
Ok I Logged in the Game But For 30 Secs and then the Game Closes  Without any warnings... I have Apllied A GG Killer Patch ... So what maybe The Problem ?? Can Anyone Answer Me PLZ

---

### Post by smo0th on 2009-01-18
> **nackgr said:**
> Ok I Logged in the Game But For 30 Secs and then the Game Closes  Without any warnings... I have Apllied A GG Killer Patch ... So what maybe The Problem ?? Can Anyone Answer Me PLZ

hi nackgr

I never had that problem but from what I've read from several different places your problem is related to Game Guard, so the patch that you applied may not be working, is it a windows patch? if it is, it will try to apply the patch over wine but wine networking is owned by linux so I doubt that kind of patches would work, try to apply linux based GG patches ie. editing the limits.conf file by adding the following line at the end

```
* hard nofile 16383
# End of file

```

---

### Post by Darkshade on 2009-02-05
Finally got a new GeForce 6800XT, L2 runs fine now except for some minor bugs - shaders not working, weird graphics on the bottom left corner when shadows are turned on (and not always)... nothing important really.
My only problem left are screenshots - they're completely black. Tried messing around with stuff - virtual desktop on/off, allow the window manager to control/decorate the windows on/of, fullscreen, window mode, compositing on/off, nothing seems to change. Tried in both Gnome and KDE4.2, same result.
Any ideas?


p.s. I just had to do this:
[[img]http://i40.tinypic.com/fe1361_th.png[/img]](http://i40.tinypic.com/fe1361.png)
:lolflag:

---

### Post by Sugi on 2009-02-20
Darkshade, Put Lineage 2 in Windows mode and then take a screen shot.  It should take the screen without a problem.  Btw, what serever are you playing on?

Sugi

---

### Post by Zaitsev on 2009-03-13
hello everyone
I'm newbie to use Ubuntu and I'm just trying to lunch Lineage II on Wine.
I've done all the passes of this topic but when I'm going to lunch the L2.exe file it appears this error msg
1- Agp Deactiveted
2- Themida (An internal exception occured)
3- 

2009.3.13 16:52:34
OS : Windows Vista 6.0 (Build: 6000)
CPU : GenuineIntel Celeron M Processor @ 1729 MHz with 1007MB RAM
Video : Direct3D HAL (6764)
PosCode : LS1:0:0:0 2/0

General protection fault!

History: TSFImpl:: Disable <- NTSFIME:: DisableIME <- NCIME:: DisableIME <- NCIME::SetIME <- NTSFIME::SetIME <- NCIMEManager::SetIME <- NCEditBox::SetFocus <- NCAuthWnd::ShowWindow <- UIGameStateManager::ShowUI <- UIGameState::ShowUI <- UIGameState::OnEnter <- UILoginState::OnEnter <- UIGameStateManager::SetState <- NConsoleWnd::Initialize <- NConsoleWnd::Init <- UGameEngine::Init <- InitEngine



what I've to do??

Thank you all and sorry for the bad english.. :) ;)

---

### Post by Sugi on 2009-03-13
Please provide us with more information: Wine version, Lineage 2 version, Hardware, Ubutnu version, and do you have working video drivers?

Try changing wine OS to Windows XP
terminal: $ winecfg
Change the OS from Windows Vista to Windows XP


Sugi

---

### Post by Zaitsev on 2009-03-13
> **Sugi said:**
> Please provide us with more information: Wine version, Lineage 2 version, Hardware, Ubutnu version, and do you have working video drivers?

Try changing wine OS to Windows XP
terminal: $ winecfg
Change the OS from Windows Vista to Windows XP


Sugi

Wine Version: Wine 1.1.16
Lineage 2 version: the last one, Gracia part 2
Hardware: I've a Toshiba Satellite core duo, 1 GB RAM, VideoBoard= Ati Mobility Radeon x1600
Ubuntu 8.10 version

I've just installed correctly the official video drivers

I've tryed to change the OS from Vista to XP but it doesn't work..

If you need some other info please tell it to me..

Thank you very much

Zaitsev

---

### Post by Sugi on 2009-03-13
You have may two problems.  ATI cards could be causes you some issues.  It **MAY** prevent you from running Lineage 2.  And your second issues, is most likely your option.ini file within your system folder of Lineage 2 directory.  Try tweaking the option.ini to match your Desktop's resolution, force the game to start up in Windows Mode, and force Lineage 2 in low details.

Sugi

---

### Post by Zaitsev on 2009-03-13
I've tried to do what you saied and the result is this other error

2009.3.13 19:29:32
OS : Windows XP 5.1 (Build: 2600)
CPU : GenuineIntel Celeron M Processor @ 1729 MHz with 1007MB RAM
Video : Direct3D HAL (6764)
PosCode : LS1:0:0:0 2/0

You have triggered a bug in the DirectX 9.0 runtime. Please install DirectX 8.1b (or later) for a fix. See Release Notes for instructions on how to obtain it.
IsShadow=0,PrimitiveType=0,IndexBuffer=0xF683160,Base=0,Min=289,Max=48959,First=0,NumPrimitives=68896

History: FD3DRenderInterface::DrawPrimitive <- ATerrainInfo::Render <- this=Lobby01.TerrainInfo0 <- RenderTerrain <- RenderLevel <- FLevelSceneNode::Render <- FPlayerSceneNode::Render <- UGameEngine::Draw <- UWindowsViewport::Repaint <- UWindowsClient::Tick <- ClientTick <- UGameEngine::Tick <- UpdateWorld <- MainLoop


can I play or I must leave this idea? :/
Thank's,
Zaitsev

---

### Post by Sugi on 2009-03-23
BTW Darkshade, I like your subbed Light Elf as Doom Cryer :D  In your server do you have to do the subclass quest?

Zaitsev, you have not gotten back to me with your Lineage 2 issues.

Sugi

---

### Post by bartty on 2009-03-30
Same problem here.
Notebook: HP9339, DualCore T5500, 4Gb RAM, Nvidia Go7600 256DDR2
OS Ubuntu 8.10 / Wine 1.1.18
Lineage2 Gracia2 - installed with Wine and updated.
DirectX 9.0c, NVIDIA-Linux-x86-180.22-pkg1.run (also tried with 177 from Ubuntu Add/Remove driver)
Wine configured corectly setted up for WinXP, L2.exe added, etc.
Tahoma font added, L2.ini edited and configured corectlly.
When i start L2.exe it's turning off itself in 2 seconds without any error. I tried with different patched systems but doing the same.
Any suggestion?

---

### Post by Sugi on 2009-03-30
Please include your terminal output when lineage 2 crashes.  When does it crash?  At login screen?  At server select? Character Select? In-game?  Or during the Lineage 2 splash screen?

Sugi

---

### Post by sp77 on 2009-04-01
General Server Features
x15 rates
* Lineage 2 Interlude [C6]
* L2Walker/L2Phx protection & detection
* Fully working augmentation system
* Flawless Geodata
* Level 80 function fixed, % works as well
* Shadow weapons obtainable
* Siege system working as designed
* Original Interlude NPCs with original locations and stats
* Olympiad system working correctly with stack sub
* All Interlude skills 100% functional
* Enchant system working with original % success chance
* Appropriate shop boundaries applied
* Clan privileges working as intended
* Clan war system working as intended
* Entire Interlude knight clan system & halls working
# Newbie NPCs available with weapon coupons system for faster beginner leveling
# CP system and potions working as normal
# Balanced mana potions available for players
# Hero skills and weapons granted to monthly Olympiad victors

[www.l2reign.com](www.l2reign.com)

---

### Post by Rrv on 2009-04-24
> **Sugi said:**
> Please include your terminal output when lineage 2 crashes.  When does it crash?  At login screen?  At server select? Character Select? In-game?  Or during the Lineage 2 splash screen?
Sugi

How do i do that put a terminal output.

PC: P4 755 3.0 Ghz / 
OS Ubuntu 8.04 / Wine 1.1.19 and 1.05  RC5
VC: Nvidia 8400 BFG 512 MB
Lineage2 Gracia part 2 
DirectX 9.0c, NVIDIA-Linux-x86-180.22-pkg1.run 
Wine configured corectly setted up for WinXP, L2.exe added, etc.
Tahoma font added, L2.ini edited and configured corectlly.

when i try to run L2, it says an error later says this on 1. 1.19 

2009.4.24 07:22:32
OS : Windows XP 5.1 (Build: 2600)
CPU : GenuineIntel Pentium 4 Processor @ 3191 MHz with 2026MB RAM
Video : Direct3D HAL (7341)
PosCode : LS1:0:0:0 2/0

agp error deactivate agp bla bla the same in all

and later on black screen 
You have triggered a bug in the DirectX 9.0 runtime. Please install DirectX 8.1b (or later) for a fix. See Release Notes for instructions on how to obtain it.
IsShadow=0,PrimitiveType=0,IndexBuffer=0x106124E0,Base=0,Min=0,Max=63936,First=0,NumPrimitives=109664

History: FD3DRenderInterface::DrawPrimitive <- ATerrainInfo::Render <- this=Lobby01.TerrainInfo0 <- RenderTerrain <- RenderLevel <- FLevelSceneNode::Render <- FPlayerSceneNode::Render <- UGameEngine::Draw <- UWindowsViewport::Repaint <- UWindowsClient::Tick <- ClientTick <- UGameEngine::Tick <- UpdateWorld <- MainLoop

1.05  RC5
Agp error
even not the black screen start it freeze on the image of the character when is starting.
sorry for my english xD

---

### Post by NexusGS on 2009-06-07
Hi guys,

I am trying to run Linux through Ubuntu 8.04. I am using Wine 1.1.22 and also I have Nvidia card. It gets me to login prompt but then a small box comes up (without any text) and i can only click it and that closes the client. Box is on L2's framework (it's the client message) and I see that it has to be a GG error.I want to login to official L2 server and not private...Any ideas????

Also there is ULL (Universal Linux Launcher for NCSoft games) but nothing better there too..Any idea acceptable...

---

### Post by ReZeeR on 2010-01-04
L2 launches perfectly apart from AGP error but when i try to log in critical error pops up 
> 2010.1.4 13:27:08
OS : Windows Vista 6.0 (Build: 6000)
CPU : GenuineIntel PentiumPro-class processor @ 2400 MHz with 2047MB RAM
Video : Direct3D HAL (16921)

General protection fault!

History: NConsoleWnd::RequestAuthLogin <- NCAuthWnd::OnLoginBtnClick <- NCAuthWnd::OnPasswordDone <- NControl::SendEventMessage <- NCEditBox::OnKeyDown <- NCVirtualWndMain::PassToFocusedWindow <- NCVirtualWndMain::PassToFocusedWindow <- NCVirtualWndMain::PassToFocusedWindow <- NCVirtualWndMain::DispatchWndMsg <- NConsoleWnd::DispatchWndMsgX <- NConsoleWnd::DispatchWndMsg <- UWindowsViewport::ViewportWndProc <- WWindow::StaticProc <- DispatchMessage <- 00020042 256 <- MessagePump <- MainLoop

---

### Post by Gheazu on 2010-02-16
Hello i know this is old 
First im a noob when it comes to Linux  this is first time i install and hell i love it. 
Now i try to run L2 on Ubuntu 9  with wine all ok but when i start lineage II exe nothing happens   can some one help me ? i find on wine it works but no guide  ty for understanding

---

### Post by Eternal_Light on 2010-10-29
Hello, I have kubuntu 10.10 and wine 1.3.5. I have installed L2 epilogue to play on a private server. I have added l2.exe and lineage2.exe on that list thingy and have edited my option.ini to have all graphic options on lowest, run on fullscreen and on my original screen resolution. Here is the deal. after i run l2.exe from inside the system folder, the splash screen appears and after a few seconds disappears as it ought to do but then nothing happens. The main lineage2 window fails to initiate. No flashing of the screen, no errors, no nothing. It's as if the l2.exe is designed to show only the splash screen and nothing else...

I'm so close to playing L2 again after such a long time... All help is welcome. Thank you in advance. :P

---

### Post by Sugi on 2010-11-14
> **Rrv said:**
> ...Wine configured corectly setted up for WinXP, L2.exe added, etc.  Tahoma font added, L2.ini edited and configured corectlly...

I would try the newest wine version, and l2.ini editted? Do you mean option.ini? Just copy and paste the output from the terminal when you run L2.exe within the terminal. [ctrl+shift+c] :D


> **NexusGS said:**
> 
...and I see that it has to be a GG error.I want to login to official L2 server....

I was able to connect to retail with noGGpatch and it's quite easy.  Use fyyre's patch, fyyre has done amazing work!!!
[http://fyyre.ivory-tower.de/](http://fyyre.ivory-tower.de/)


> **ReZeeR said:**
> ...L2 launches perfectly apart from AGP error but when i try to log in critical error pops up...

It would be extremely helpful if you posted your terminal output.  What video card are you on? Version of ubuntu? Wine version?  Though, it's most likely an issue with your option.ini file or you trying to connect to the host.


> **Gheazu said:**
> ....but when i start lineage II exe nothing happens...

This mostly like is linked to your option.ini file, try deleting it and restart Lineage 2.


> **Eternal_Light said:**
> ...No flashing of the screen, no errors, no nothing. It's as if the l2.exe is designed to show only the splash screen and nothing else...

This could be a couple of problems, either an issue with your graphical settings / graphical card or your option.ini file.  I can't say for sure, without more details.


> **Sugi]X Error of failed request: BadWindow (invalid Window parameter)
Major opcode of failed request: 1 (X_CreateWindow)
Resource id in failed request: 0x5200007
Serial number of failed request: 26
Current serial number in output stream: 32
[/QUOTE]

I have found a new issue, which is directly linked to emulate desktop environment [wine explorer /desktop].  The best way to workaround this is just load up L2.exe without emulate desktop environment. [wine L2.exe]

Ubuntu 10.10 x64
Wine 1.3.7
Lineage 2 Gracia Final


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Update:
Here is a list of error messages linked with their Solutions.  These are issues linked to the client, errors which may not be conflicting with WINE it's self.

[QUOTE]Common Critical Errors and their Solutions

Error: History: FL2GameData::ObsceneDataLoad <- FL2GameData::Load() <- UGameEngine::Init <- InitEngine

Cause: The client cannot properly load banned messages.

Solution: Delete obscene-e.dat in your C:\Program Files\Lineage II\system folder and run L2.exe again.

--------------------------------------------------

Error: General protection fault! History: UOrcMove::CalculateCRC32 <- UGameEngine::Init <- InitEngine

Cause: The client is missing one or more vital files that are required to load the game. You have not installed the patch or updater properly, you have accidently deleted files, or you are not using the right Chronicle.

Solutions: 1. Make sure none of your folders are empty said:**
> .
--------------------------------------------------

Error: Negative delta time! History: UGameEngine::Tick <- UpdateWorld <- MainLoop

Cause: Your Lineage 2 client could not properly read your CPU clock speeds. This usually only happens with AMD processors.

Solutions: 1. Download the [AMD Dual Core Optimizer] program and install it.
&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608; 2. Download this >XP ONLY< hotfix from the official Windows website (Genuine Windows XP required). [Link 1]

--------------------------------------------------

Error: Failed to enter Entry: Can't find file 'Entry'. History: UGameEngine::Init <- InitEngine

Cause: Your client is missing one or more required files to launch the game. This may also occur if you install the L2 Server patch onto the wrong version of the game (Hellbound, Gracia, C5, etc).

Solutions: 1. Install the patch in the MAIN Lineage II folder, not the system folder or anywhere else. Installing it in the wrong place can cause this error.
&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608; 2. Update your video card drivers to the latest stable ones.

--------------------------------------------------

Error: Application failed to initialize properly

Cause: This usually appears when you are using modded video card drivers, very outdated video card drivers, do not have the .NET Framework installed, or any combination of the three.

Solutions: 1. Update your video card drivers to the latest stable ones.
&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608; 2. Download and install the .NET Framework 2.0 [Link 1] (Genuine Windows XP/Vista required).

--------------------------------------------------

Error: General protection fault! History: UObject:: DissociateImports <- UObject::EndLoad <- UObject::StaticLoadObject <- (Engine.SkeletalMesh =anything can be here=) <- IsLoadedResource <- User::SetPawnResource <- UNetworkHandler::Tick <- Function Name=NpcInfoPacket <- UGameEngine::Tick <- UpdateWorld <- MainLoop

Cause: This is 99% of the time caused by video card drivers being unable to load textures, or it can be very rarely caused by a missing texture.

Solutions: 1. Update your video card drivers to the latest stable ones.
&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608; 2. If step 1 does not work, do some searching to find out what driver versions work best for your video card. In my case and many others, the latest drivers have caused issues, and older drivers work much better.

--------------------------------------------------

Error: History: FArchiveFileReader::Seek <- ULinkerLoad::Seek <- TLazyArray<< <- FMipmap<< <- SerializeMips <- UTexture::Serialize <- LoadObject <- (Texture LineageMonstersTex.death_knight.death_knight_t00 99684524==99684524/133323252 99683358 132383) <- ULinkerLoad::Preload <- PreLoadObjects <- UObject::EndLoad <- UObject::StaticLoadObject <- (Engine.Texture LineageMonstersTex.Death_Knight_T00 NULL) <- UOrcMove::CalculateCRC32 <- UGameEngine::Init <- InitEngine

Cause: You have a corrupt texture, potentially from another private server that doesn't know how to create a proper patch or from an action you have done yourself.

Solutions: 1. download a fresh Lineage2 installer from [Link 1].
&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608; 2. If step 1 does not work, reinstall DirectX 9.0c and update your video card drivers to the latest stable ones.

--------------------------------------------------

Error: History: NConsoleWnd::RequestAuthLogin <- NCAuthWnd::OnLoginBtnClick <- NCAuthWnd::OnPasswordDone <- NControl::SendEventMessage <- NCEditBox::OnKeyDown <- NCVirtualWndMain::PassToFocusedWindow <- NCVirtualWndMain::PassToFocusedWindow <- NCVirtualWndMain::PassToFocusedWindow <- NCVirtualWndMain:ispatchWndMsg <- NConsoleWnd:ispatchWndMsgX <- NConsoleWnd:ispatchWndMsg <- UWindowsViewport::ViewportWndProc <- WWindow::StaticProc <- DispatchMessage <- 006903B0 256 <- MessagePump <- MainLoop

Cause: Another program is intercepting your connection with the Auth server when you click 'Login'. This can be from almost anything.

Solutions: 1. If you have an anti-virus program such as AVG, disable all active protection while logging in and enable it again only once you are ingame.
&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608; 2. If you have another Lineage 2 client open of a different chronicle (ex. logged into a Gracia Final Part 2 server while trying to login to Interlude one), close the other client and restart your client. Also close any other games that utilise an anti-cheat program, whether it be Gameguard, nProtect, etc. You should now be able to login.
&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608; 3. Go to C:\WINDOWS\system32\drivers\etc and open the file 'hosts' with notepad. Other than all lines starting with the character '#', make sure that this is the only line there:
Code:

Unless you have added other lines there and know what you are doing, you can leave those, but delete all lines with L2authd.lineage2.com, L2testauthd.lineage2.com, auth.lineage2.com.tw, auth.lineage2.jp, L2auth.Lineage2.in.th, L2auth.Lineage2.ph, or anything else you see that relates to Lineage 2 Auth.
[http://forum.pmfun.com/viewtopic.php?p=121793]("http://forum.pmfun.com/viewtopic.php?p=121793")

Cheers,
Sugi

---

### Post by Alexandr0 on 2011-05-16
Hello i'm new here i do everythink in the guide i dont copy the dlls files beacuse i don't find the drive_c folder ine the wine folder haven't drive_c or program files...
OK i run l2.exe and nothink comes up..i trie from console and i got this error:
> alex@Alex:~/Desktop/Lineage][/system$ wine l2.exe
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 0025, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 0026, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 0027, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 0028, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 0029, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 002a, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 002b, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 002c, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 002e, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 002d, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 002f, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 0030, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 0031, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 0032, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 0033, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 0034, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 0035, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 0036, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 0037, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 0038, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 0039, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 003a, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 003b, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 003c, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bca68e4 "loader.c: loader_section" wait timed out in thread 003d, blocked by 0009, retrying (60 sec)
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc33bca
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc33bca
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc33bca
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc33bca
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc33bca
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc33bca



What i do wrong??please answer me :)

---

### Post by Inoki on 2011-07-24
If anyone could provide a fix for the mouse fixed to the center of the screen when launching the game I'd be grateful.

Running Linux Mint 10 x64 bit (based on Maverick Meerkat), latest Wine 1.3.24 and Lineage II. Freya client.

---

