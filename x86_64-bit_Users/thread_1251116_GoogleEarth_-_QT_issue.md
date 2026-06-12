---
title: "GoogleEarth - QT issue?"
date: 2009-08-27
forum: x86 64-bit Users
---

### Post by danteuk on 2009-08-27
I installed googleearth today on Kubuntu 9.04(64bit) using synaptic.
It seems it's installed the 32bit binary, with all the libraries required ( I guess ) but it doesn't run.

$ googleearth
Segmentation fault

root@Borodin:/usr/lib32/googleearth# file googleearth-bin
googleearth-bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.0, stripped
root@Borodin:/usr/lib32/googleearth# export LD_LIBRARY_PATH=.
root@Borodin:/usr/lib32/googleearth# ldd googleearth-bin 
        linux-gate.so.1 =>  (0xf7f27000)                  
        libgcc_s.so.1 => ./libgcc_s.so.1 (0xf7f19000)     
        libstdc++.so.6 => ./libstdc++.so.6 (0xf7e3f000)   
        libQtCore.so.4 => /usr/lib32/libQtCore.so.4 (0xf7be1000)
        libQtGui.so.4 => /usr/lib32/libQtGui.so.4 (0xf71f2000)  
        libQtNetwork.so.4 => /usr/lib32/libQtNetwork.so.4 (0xf70d6000)
        libQtWebKit.so.4 => ./libQtWebKit.so.4 (0xf69e3000)           
        libgoogleearth_lib.so => ./libgoogleearth_lib.so (0xf68cb000) 
        libm.so.6 => /lib32/libm.so.6 (0xf68a5000)                    
        libc.so.6 => /lib32/libc.so.6 (0xf6742000)                    
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf6729000)        
        libbase.so => ./libbase.so (0xf6675000)                       
        libge_net.so => ./libge_net.so (0xf6626000)                   
        libgeobase.so => ./libgeobase.so (0xf6303000)
        libz.so.1 => ./libz.so.1 (0xf62ec000)
        libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf62e6000)
        librt.so.1 => /lib32/librt.so.1 (0xf62dc000)
        libglib-2.0.so.0 => /usr/lib32/libglib-2.0.so.0 (0xf6224000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf6220000)
        libaudio.so.2 => /usr/lib32/libaudio.so.2 (0xf6208000)
        libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf61e2000)
        libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf616a000)
        libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf612c000)
        libSM.so.6 => /usr/lib32/libSM.so.6 (0xf6123000)
        libICE.so.6 => /usr/lib32/libICE.so.6 (0xf610b000)
        libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf6101000)
        libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf60d4000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf60c3000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf5fd4000)
        libXi.so.6 => /usr/lib32/libXi.so.6 (0xf5fca000)
        libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf5fc2000)
        libIGCore.so => ./libIGCore.so (0xf5eca000)
        libIGUtils.so => ./libIGUtils.so (0xf5ea3000)
        libapiloader.so => ./libapiloader.so (0xf5e9f000)
        libauth.so => ./libauth.so (0xf5e08000)
        libcommon.so => ./libcommon.so (0xf5d23000)
        libcomponentframework.so => ./libcomponentframework.so (0xf5d18000)
        libmath.so => ./libmath.so (0xf5ce3000)
        libmoduleframework.so => ./libmoduleframework.so (0xf5cd5000)
        libport.so => ./libport.so (0xf5ccb000)
        librender.so => ./librender.so (0xf5c36000)
        /lib/ld-linux.so.2 (0xf7f28000)
        libIGMath.so => ./libIGMath.so (0xf5bec000)
        ./libminizip.so (0xf5be5000)
        libfusioncommon.so => ./libfusioncommon.so (0xf5be0000)
        libcurl.so.4 => ./libcurl.so.4 (0xf5bac000)
        libpcre.so.3 => /lib32/libpcre.so.3 (0xf5b7a000)
        libXt.so.6 => /usr/lib32/libXt.so.6 (0xf5b27000)
        libuuid.so.1 => /lib32/libuuid.so.1 (0xf5b22000)
        libexpat.so.1 => /usr/lib32/libexpat.so.1 (0xf5afa000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf5af6000)
        libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf5adc000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0xf5a22000)
        libGLU.so.1 => ./libGLU.so.1 (0xf59a4000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf599e000)
        libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0xf4a88000)
        libnvidia-tls.so.1 => /usr/lib32/libnvidia-tls.so.1 (0xf4a86000)

Any idea ?

---

### Post by Yellow Pasque on 2009-08-27
Are you using the version from medibuntu?
[http://packages.medibuntu.org/jaunty/googleearth.html](http://packages.medibuntu.org/jaunty/googleearth.html)

---

