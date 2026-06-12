---
title: "Wine + Steam unresponsive"
date: 2008-04-11
forum: Wine
---

### Post by mmillman on 2008-04-11
Ok, so I've gotten wine set up and running, and I used it to install Steam... but now whenever I try to run it, nothing happens... If i use the icon on my desktop, it just says "starting steam" in the taskbar, but then disappears...

So I tried to run it from the terminal... and this is what I get:

[email]michael@michael-desktop:~/.wine[/email]/drive_c/Valve/Steam$ wine Steam.exe
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Valve\Steam\bin\ *.mix
dir: C:\Valve\Steam\bin\ *.asi
dir: C:\Valve\Steam\bin\ *.flt
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
[email]michael@michael-desktop:~/.wine[/email]/drive_c/Valve/Steam$ 


Also, the first time I ran winecfg, it told me that i didn't have an audio driver selected, and it would select one for me... It selected the Alsa one by default...  When I try to click "test" it locks up and I have to end the process... same thing happens if I select OSS and click test, same freeze...

Also, when I select OSS, and click apply, the next time i try to run winecfg, it freezes completely as soon as I click the audio tab... so I had to uninstall and reinstall wine to revert back to alsa...

Any ideas??

I'm running Ubuntu 7.10

My box is
Asus a8n32-sli deluxe
XFX GeForce 9600 GT
Athlon 64 x2 4400+ (socket 939, toledo core)
Apevia Beastpower 680w
2 Gigs of Kinston HyperX PC3200


Do I need that NTLM_AUTH??

---

### Post by mmillman on 2008-04-15
Bumping

---

### Post by LIEFofEeofol on 2008-04-16
u could always run steam in a Virtual Machine,
i do that,
there are several free ones on Linux.
and u don't even need a valid windoze license
u get 30 days free,
and maybe if u used snapshots u could just keep it free forever.


iv integrated (seemless) mine into the desktop,
[IMG]http://file045b.bebo.com/10/original/2008/04/15/23/2494245066a7460758668o.jpg[/IMG]

---

