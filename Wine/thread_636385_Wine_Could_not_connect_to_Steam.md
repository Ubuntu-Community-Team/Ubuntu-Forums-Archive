---
title: "Wine: Could not connect to Steam"
date: 2007-12-09
forum: Wine
---

### Post by tamcdonald on 2007-12-09
I know this issue pops up pretty often, but none of the solutions I've tried have worked for me. When Steam tries to log in it gives me the Could not connect to Steam network error. It was working fine yesterday in Wine 0.9.46. I've tried upgrading to 9.50 and downgrading to older versions with no success. When I try the retrieve lost account option it says my account doesn't exist. I've also tried reinstalling Steam, but nothing. Any suggestions?

Edit: I can log in from Windows just fine and also my account works on the Steam forums.

Edit 2: Terminal output

[email]thomas@tm:~/.wine[/email]/drive_c/Program Files/Steam$ wine Steam.exe
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on C-Media USB Headphone Set  , disabling mixer
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,140,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,140,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30030,0x00000000,118,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30030,0x00000000,118,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30030,0x00000000,118,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30030,0x00000000,219,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30030,0x00000000,219,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30030,0x00000000,135,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30030,0x00000000,135,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30030,0x00000000,0,2): stub!
err:systray:delete_icon invalid tray icon ID specified: 1
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,110,2): stub!
err:ole:RevokeDragDrop invalid hwnd 0x20032
err:ole:RevokeDragDrop invalid hwnd 0x2002a
err:ole:RevokeDragDrop invalid hwnd 0x10034
Shutting down. . .
9fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open

---

