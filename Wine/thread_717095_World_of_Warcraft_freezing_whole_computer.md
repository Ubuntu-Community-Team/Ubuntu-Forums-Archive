---
title: "World of Warcraft freezing whole computer"
date: 2008-03-06
forum: Wine
---

### Post by A Hemlocks Lie on 2008-03-06
For about two days, I've searched the Internet and tested anything I've come across that looks like it might help, but nothing has helped. Every time I play, after 5-15 minutes, my entire computer freezes. I have to turn off my computer and turn it back on to fix this.

I've updated to the latest version of Wine. I've added anything suggested to my config file. I've been running with the -opengl command on the end. I've tried Cedega, running the Cedega install through Wine, and copying my WoW folder from my Windows partition. I've gotten rid of all my extra addons. I've updated my video drivers. I've probably tried a half dozen other things I can't recall off the top of my head.

When I run the game through the terminal, I get the following, which outputs about until I get fully logged in and have loaded the area and a character. Then, it seems to stop until the crash. Maybe it tries to output something right at the crash, but I can't catch it.
```
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed78,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34eccc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f29c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f400,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f57c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f574,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f4fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f4ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34efd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f118,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:reg:GetNativeSystemInfo (0x374027e4) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x724733d4) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x34d198,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34d1f4,0x00000000), stub!
```

Here's the system hardware info from Cedega (I don't run it through Cedega, that works even worse than Wine, but it has the system info handy):
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz
CPU GHz: 3.0
Memory (MB): 757
Video card:
   Manufacturer: ATI Technologies Inc.
   Type: ATI Radeon 9550 / X1050 Series (It's a 9550)
   Video RAM (MB): 128
   AGP Mem Avaiable (MB): N/A
   Driver Version: 2.0.6473 (8.37.6)
Sound Card
   Name: Audigy SE [SB0570] at 0xb000 irq 1
   Driver: ALSA Version 1.0.14
Kernel: 2.6.22-14-generic
X Version: Xorg Version 1.3.0
Distribution: Debian lenny/sid (Really Ubuntu 7.10)

My Wine version is 0.9.56

EDIT: Oh, I forgot something. I recently tried to run Ventrilo through Wine, and that didn't work entirely. It did start up and stuff, but I couldn't talk/hear others talk. It also gave me a potentially relevant error claiming my video card doesn't support hardware video overlay. More signs pointing to video card problems, maybe?

EDIT 2: New development. I was playing a few minutes ago, trying to test it again, when I noticed that some of the trees weren't working properly. They weren't getting their textures or something because they were basically just tree-shaped holes in the environment. I wouldn't even see what was behind them, it was a hole right through the whole environment. I saw what looked like sky through them, sort of.

---

### Post by DM was on fire! on 2008-03-06
Hmm. Sounds like a video card. ATI's known to have problems on Ubuntu. I had an ATI Radeon 7000 until today when it finally gave up the ghost, to which I am eternally grateful. XD

Have you always had this problem, or has it just started?

---

### Post by A Hemlocks Lie on 2008-03-06
> **DM was on fire! said:**
> Hmm. Sounds like a video card. ATI's known to have problems on Ubuntu. I had an ATI Radeon 7000 until today when it finally gave up the ghost, to which I am eternally grateful. XD

Have you always had this problem, or has it just started?

I just started using Ubuntu recently, so I dunno if it's persistent or the result of something I've done recently.

---

### Post by DM was on fire! on 2008-03-06
> **A Hemlocks Lie said:**
> I just started using Ubuntu recently, so I dunno if it's persistent or the result of something I've done recently.

If it's been doing this since you started running WoW on Ubuntu, then it is most likely the video card.
ATI, as I said before, is known for not being the best things in the world for Ubuntu. NVIDIA is typically the best, and the most expensive.
Check the compatibility and incompatibilty list for your video card, and that should help you out. I don't play WoW, so I can't really help you, but I've had enought video card incompatibility issues for a lifetime.

---

### Post by A Hemlocks Lie on 2008-03-06
> **DM was on fire! said:**
> If it's been doing this since you started running WoW on Ubuntu, then it is most likely the video card.
ATI, as I said before, is known for not being the best things in the world for Ubuntu. NVIDIA is typically the best, and the most expensive.
Check the compatibility and incompatibilty list for your video card, and that should help you out. I don't play WoW, so I can't really help you, but I've had enought video card incompatibility issues for a lifetime.

My card is most likely compatible with WoW. I used to play on Windows all the time, and I never had any problems like this. The system requirements on the WoW site just says "Recommended: 64MB VRAM 3D graphics processor with Vertex and Pixel Shader capability, such as an NVIDIA GeForce FX 5700 class card or above", so I guess I can't be 100% positive.

EDIT: Whoops, copied the recommended. Here's the minimum. "Minimum: 32MB 3D graphics processor with Hardware Transform and Lighting, such as an NVIDIA GeForce 2 class card or above"

---

### Post by A Hemlocks Lie on 2008-03-06
Oh, I forgot something. I recently tried to run Ventrilo through Wine, and that didn't work entirely. It did start up and stuff, but I couldn't talk/hear others talk. It also gave me a potentially relevant error claiming my video card doesn't support hardware video overlay. More signs pointing to video card problems, maybe?

---

