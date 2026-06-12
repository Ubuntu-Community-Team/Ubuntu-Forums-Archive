---
title: "How to utilize Wine 64 bit windows emulation."
date: 2016-04-20
forum: Wine
---

### Post by Sasha_Acoiners on 2016-04-20
Hello, my name is Sasha, and I have come across a bit of a problem, with Wine, as of late.

I tried to download and play a game, specifically, Wolfenstein: The New Order. However, I had gotten the error message of: "Cannot run. Missing executable file".

I looked in the game files and, sure enough, there was no .exe to be spoken of.

I looked through the Steam forums and found out that this was due to running a 32 bit version of Windows.

I thought to myself: "But I'm not. My Ubuntu is 64 bit, so I'd imagine that's what Wine is emulating" However, when I looked at my "Windows" system info, through Windows Steam, this is what it stated:

"Computer Information:    Manufacturer:  The Wine Project
    Model:  Wine
    No Touch Input Detected
    
Processor Information:
    CPU Vendor:  GenuineIntel
    CPU Family:  0x6
    CPU Model:  0x2a
    CPU Stepping:  0x7
    CPU Type:  0x0
    Speed:  3400 Mhz
    4 logical processors
    2 physical processors
    HyperThreading:  Supported
    FCMOV:  Supported
    SSE2:  Supported
    SSE3:  Supported
    SSSE3:  Supported
    SSE4a:  Unsupported
    SSE41:  Supported
    SSE42:  Supported
    AES:  Unsupported
    AVX:  Supported
    CMPXCHG16B:  Supported
    LAHF/SAHF:  Supported
    PrefetchW:  Supported
    
Network Information:
    Network Speed:  
    
Operating System Version:
    Windows XP (32 bit)
    Wine Version: wine-1.9.8
    NTFS:  Supported
  
Video Card:
    Driver:  NVIDIA GeForce GTX 660


    DirectX Driver Name:  nv4_disp.dll
    Driver Version:  1.0
    DirectX Driver Version:  6.18.13.4052
    Driver Date Not Detected
    OpenGL Version: 4.5
    Desktop Color Depth: 32 bits per pixel
    DirectX Card: NVIDIA GeForce GTX 660
    Number of Monitors:  1
    Number of Logical Video Cards:  1
    No SLI or Crossfire Detected
    Primary Display Resolution:  1440 x 900
    Desktop Resolution: 1440 x 900
    Primary Display Size: 15.00" x 9.37"  (17.68" diag)
                                            38.1cm x 23.8cm  (44.9cm diag)
    Primary Bus Type Not Detected
    Primary VRAM: 2047 MB
    Supported MSAA Modes:  2x 4x 8x 16x 
    
Sound card:
    Audio device: Pulseaudio
    
Memory:
    RAM:  16003 Mb
    
Miscellaneous:
    UI Language:  English
    Microphone:  Not set
    Media Type:  CD-Rom
    Total Hard Disk Space Available:  2746074 Mb
    Largest Free Hard Disk Block:  986640 Mb
    OS Install Date: May 08 2010
    Game Controller: None detected
    VR Headset: None detected"

Specifically, two lines:

"Windows XP (32 bit)" and "Desktop Color Depth: 32 bits per pixel" Effectively, rendering it a 32 bit system."

And I was wondering if there is any way to have it emulate a 64 bit system, instead. I already know how to change which version of Windows it emulates (meaning: 7, xp, Vista, etc) however, I do not know how to change the bit count. 

Now, I know this question has been asked before, perhaps many times. The latest thread I found on the subject of a 64 bit emulating Wine was posted in 2011, and it stated that you shouldn't emulate 64 bit Windows, as it doesn't work that great. And, the instructions they gave on how to make it emulate 64 bit Windows was a little bit jargon, to me. 

However, as I stated, this was posted back in 2011, so, I feel that it is okay to assume, that things may be just a little bit different, now.

I will go ahead and put all the information about my computer, my Wine and Steam installation, etc, below this that I feel necessary. Hopefully, it is enough, and, if not, please, do not hesitate to ask for more/more specific info.


Information:

OS version: Ubuntu 14.04 64 bits.

Steam version: Wine Lutris Steam

Wine version used to run Steam: WineHQ Devel 1.9.8


I think that's about it, honestly...As I said, if anybody needs more info, I'd be glad to give it.

Anyways, thank you so much for reading.

-Sasha

---

