---
title: "64-bit Firefox + Flash + Pulse = no sound"
date: 2008-08-29
forum: x86 64-bit Users
---

### Post by Linux-Leach on 2008-08-29
I'm (I think) using the wrapper options to support flash.  Flash itself works.

I'm using the OSS drivers - have to since I'm using an X-Fi.

Pulse is installed, and seems to be working.

Alsa has been configured to use pulse - tests look good.

All of my normal sound operations are fine - I now am trying to support sound from flash.

libflashsupport.so has been compiled.  Watching the pulseaudio verbose output, it appears the npviewer.bin is constantly connecting/disconnecting. A small section follows:

[...]
I: client.c: Created 82 "Native client (UNIX socket client)"                                                                         
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1                                                                   
I: protocol-native.c: Enabled SHM for new connection                                                                                 
I: client.c: Client 82 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [npviewer.bin]"                       
I: module-volume-restore.c: Restoring sink for <pulsecore/protocol-native.c$ALSA plug-in [npviewer.bin]>                             
I: module-volume-restore.c: Restoring volume for <pulsecore/protocol-native.c$ALSA plug-in [npviewer.bin]>                           
I: sink-input.c: Created input 82 "ALSA Playback" on output with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
D: memblockq.c: memblockq requested: maxlength=132300, tlength=88200, base=4, prebuf=84672, minreq=3528                              
D: memblockq.c: memblockq sanitized: maxlength=132300, tlength=88200, base=4, prebuf=84672, minreq=3528                              
I: sink-input.c: Freeing output 82 "ALSA Playback"                                                                                   
I: client.c: Freed 82 "ALSA plug-in [npviewer.bin]"                                                                                  
I: protocol-native.c: connection died.                                                                                               
I: client.c: Created 83 "Native client (UNIX socket client)"                                                                         
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1                                                                   
I: protocol-native.c: Enabled SHM for new connection                                                                                 
I: client.c: Client 83 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [npviewer.bin]"                       
I: module-volume-restore.c: Restoring sink for <pulsecore/protocol-native.c$ALSA plug-in [npviewer.bin]>                             
I: module-volume-restore.c: Restoring volume for <pulsecore/protocol-native.c$ALSA plug-in [npviewer.bin]>                           
I: sink-input.c: Created input 83 "ALSA Playback" on output with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
D: memblockq.c: memblockq requested: maxlength=132300, tlength=88200, base=4, prebuf=84672, minreq=3528                              
D: memblockq.c: memblockq sanitized: maxlength=132300, tlength=88200, base=4, prebuf=84672, minreq=3528                              
I: sink-input.c: Freeing output 83 "ALSA Playback"                                                                                   
I: client.c: Freed 83 "ALSA plug-in npviewer.bin]"                                                
I: protocol-native.c: connection died.
[...]

Any ideas?

---

### Post by Yellow Pasque on 2008-08-29
> Alsa has been configured to use pulse - tests look good.
Did you mean OSS?

- Did you install OSS4.0 from a .deb or compile the OSS4.1 beta mercurial code?
- When you compiled libflashupport.so, did you edit it to #define OSS and use the -m32 and -fPIC flags when compiling?
- Did you place the resulting library in /usr/lib32?

---

### Post by Crafty Kisses on 2008-08-29
Weird, may I see the following ouptut? lspci -v

---

### Post by Linux-Leach on 2008-08-29
*OSS from .deb downloaded from 4front.
*compile...both commented out the #define OPENSSL and tried leaving it in with libssl-dev installed.
*-m32 and -fPIC - yes
*Place library in /usr/lib32 - yes.

---

### Post by Linux-Leach on 2008-08-29
Catch!

00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
        Subsystem: nVidia Corporation Unknown device c55e       
        Flags: bus master, 66MHz, fast devsel, latency 0        
        Capabilities: [40] HyperTransport: Host or Secondary Interface

00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Subsystem: nVidia Corporation Unknown device c55e            
        Flags: 66MHz, fast devsel                                    

00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Subsystem: nVidia Corporation Unknown device c55e            
        Flags: 66MHz, fast devsel                                    

00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Subsystem: nVidia Corporation Unknown device c55e            
        Flags: bus master, 66MHz, fast devsel, latency 0             

00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Subsystem: nVidia Corporation Unknown device c55e            
        Flags: bus master, 66MHz, fast devsel, latency 0             

00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
        Subsystem: nVidia Corporation Unknown device c55e            
        Flags: bus master, 66MHz, fast devsel, latency 0             

00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Subsystem: nVidia Corporation Unknown device c55e            
        Flags: 66MHz, fast devsel                                    

00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Subsystem: nVidia Corporation Unknown device c55e            
        Flags: 66MHz, fast devsel                                    

00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Subsystem: nVidia Corporation Unknown device c55e            
        Flags: 66MHz, fast devsel                                    

00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Subsystem: nVidia Corporation Unknown device c55e            
        Flags: 66MHz, fast devsel                                    

00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Subsystem: nVidia Corporation Unknown device c55e            
        Flags: 66MHz, fast devsel                                    

00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Subsystem: nVidia Corporation Unknown device c55e            
        Flags: 66MHz, fast devsel                                    

00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Subsystem: nVidia Corporation Unknown device c55e            
        Flags: 66MHz, fast devsel                                    

00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Subsystem: nVidia Corporation Unknown device c55e            
        Flags: 66MHz, fast devsel                                    

00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Subsystem: nVidia Corporation Unknown device c55e            
        Flags: 66MHz, fast devsel                                    

00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Subsystem: nVidia Corporation Unknown device c55e            
        Flags: 66MHz, fast devsel                                    

00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Subsystem: nVidia Corporation Unknown device c55e            
        Flags: bus master, 66MHz, fast devsel, latency 0             

00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Subsystem: nVidia Corporation Unknown device c55e            
        Flags: 66MHz, fast devsel                                    

00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0                                                  
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0                               
        I/O behind bridge: 00009000-00009fff                                                       
        Memory behind bridge: cc000000-ceffffff                                                    
        Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff                       
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0c55                       
        Capabilities: [48] Power Management version 2                                              
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+            
        Capabilities: [60] HyperTransport: MSI Mapping                                             
        Capabilities: [80] Express Root Port (Slot+) IRQ 0                                         

00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
        Subsystem: nVidia Corporation Unknown device c55e              
        Flags: bus master, 66MHz, fast devsel, latency 0               
        Capabilities: [44] HyperTransport: Slave or Primary Interface  
        Capabilities: [dc] HyperTransport: MSI Mapping                 

00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
        Subsystem: nVidia Corporation Unknown device c55e       
        Flags: bus master, 66MHz, fast devsel, latency 0        
        I/O ports at fc00 [size=128]                            

00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
        Subsystem: nVidia Corporation Unknown device c55e
        Flags: 66MHz, fast devsel, IRQ 255               
        I/O ports at f800 [size=64]                      
        I/O ports at f400 [size=64]                      
        I/O ports at f000 [size=64]                      
        Capabilities: [44] Power Management version 2    

00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: nVidia Corporation Unknown device c55e                                   
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20                            
        Memory at cffff000 (32-bit, non-prefetchable) [size=4K]                             
        Capabilities: [44] Power Management version 2                                       

00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: nVidia Corporation Unknown device c55e                                   
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23                            
        Memory at cfffe000 (32-bit, non-prefetchable) [size=256]                            
        Capabilities: [44] Debug port                                                       
        Capabilities: [80] Power Management version 2                                       

00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1) (prog-if 8a [Master SecP PriP])
        Subsystem: Unknown device f0de:c55e                                                 
        Flags: bus master, 66MHz, fast devsel, latency 0                                    
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]         
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]         
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]         
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]         
        I/O ports at ec00 [size=16]                                                         
        Capabilities: [44] Power Management version 2                                       

00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
        Subsystem: nVidia Corporation Unknown device c55e                                               
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23                                        
        I/O ports at 09f0 [size=8]                                                                      
        I/O ports at 0bf0 [size=4]                                                                      
        I/O ports at 0970 [size=8]                                                                      
        I/O ports at 0b70 [size=4]                                                                      
        I/O ports at d800 [size=16]                                                                     
        Memory at cfffd000 (32-bit, non-prefetchable) [size=4K]                                         
        Capabilities: [44] Power Management version 2                                                   
        Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-                 
        Capabilities: [cc] HyperTransport: MSI Mapping                                                  

00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
        Subsystem: nVidia Corporation Unknown device c55e                                               
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22                                        
        I/O ports at 09e0 [size=8]                                                                      
        I/O ports at 0be0 [size=4]                                                                      
        I/O ports at 0960 [size=8]                                                                      
        I/O ports at 0b60 [size=4]                                                                      
        I/O ports at c400 [size=16]                                                                     
        Memory at cfffc000 (32-bit, non-prefetchable) [size=4K]                                         
        Capabilities: [44] Power Management version 2                                                   
        Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-                 
        Capabilities: [cc] HyperTransport: MSI Mapping                                                  

00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
        Subsystem: nVidia Corporation Unknown device c55e                                               
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21                                        
        I/O ports at c000 [size=8]                                                                      
        I/O ports at bc00 [size=4]                                                                      
        I/O ports at b800 [size=8]                                                                      
        I/O ports at b400 [size=4]                                                                      
        I/O ports at b000 [size=16]                                                                     
        Memory at cfffb000 (32-bit, non-prefetchable) [size=4K]                                         
        Capabilities: [44] Power Management version 2                                                   
        Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-                 
        Capabilities: [cc] HyperTransport: MSI Mapping                                                  

00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0                                          
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32                             
        I/O behind bridge: 00008000-00008fff                                                      
        Memory behind bridge: c4000000-cbffffff                                                   
        Capabilities: [b8] Subsystem: nVidia Corporation Unknown device cb84
        Capabilities: [8c] HyperTransport: MSI Mapping

00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
        Subsystem: nVidia Corporation Unknown device c55e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 509
        Memory at cfffa000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ac00 [size=8]
        Memory at cfff9000 (32-bit, non-prefetchable) [size=256]
        Memory at cfff8000 (32-bit, non-prefetchable) [size=16]
        Capabilities: [44] Power Management version 2
        Capabilities: [70] MSI-X: Enable- Mask- TabSize=8
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable+
        Capabilities: [6c] HyperTransport: MSI Mapping

00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
        Subsystem: nVidia Corporation Unknown device c55e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 510
        Memory at cfff7000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at a800 [size=8]
        Memory at cfff6000 (32-bit, non-prefetchable) [size=256]
        Memory at cfff5000 (32-bit, non-prefetchable) [size=16]
        Capabilities: [44] Power Management version 2
        Capabilities: [70] MSI-X: Enable- Mask- TabSize=8
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable+
        Capabilities: [6c] HyperTransport: MSI Mapping

01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GT] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: eVga.com. Corp. Unknown device c635
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at cc000000 (32-bit, non-prefetchable) [size=16M]
        Memory at b0000000 (64-bit, prefetchable) [size=256M]
        Memory at cd000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at 9c00 [size=128]
        [virtual] Expansion ROM at ce000000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint IRQ 0

02:09.0 Multimedia audio controller: Creative Labs SB X-Fi
        Subsystem: Creative Labs Unknown device 002c
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at 8c00 [size=32]
        Memory at cbe00000 (64-bit, non-prefetchable) [size=2M]
        Memory at c4000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

---

### Post by Linux-Leach on 2008-08-29
New messages.  Using "find /usr -iname 'libflashsupp*'", I deleted all instances. I re-compiled using the m32 and commented out the ssl.

I copied the result to /usr/lib32, and placed links from /usr/lib/mozilla/plugins and /usr/lib/firefox/plugins.  Now, firefox gives me the following errors:

*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Message type invalid
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Message type invalid
*** NSPlugin Viewer  *** ERROR: NPN_GetURLNotify() invoke: Message type invalid
*** NSPlugin Viewer  *** ERROR: NPN_GetURLNotify() invoke: Message type invalid

---

### Post by Linux-Leach on 2008-08-29
output of "ldd libflashsupport.so"

        linux-gate.so.1 =>  (0xffffe000)
        libc.so.6 => /lib32/libc.so.6 (0xf7e0a000)
        /lib/ld-linux.so.2 (0xf7f72000)

---

### Post by Linux-Leach on 2008-08-29
Ok - new update.  After continuing to try all kinds of combinations, I tried something different.  I updated to the latest OSS, and activated "softoss".  After re-configuring several applications, I now have sound from just about everywhere - without any sound servers required.  Much better.

---

