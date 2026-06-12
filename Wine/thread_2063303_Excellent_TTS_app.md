---
title: "Excellent TTS app"
date: 2012-09-26
forum: Wine
---

### Post by smakarl on 2012-09-26
Textaloud 3 TTS from nextup.com . It is excellent. 
Written for Windows. I have asked them for a direct Deb app.

1. Install the new WINE from the Ubuntu Software Center..

2. Configure WINE via the graphical WINE Configuration interface. You may need to adjust the Windows API version or the audio interface.
I had no need. And all Windows APIs seemed to work.

3. Install the SAPI5 interface. SAPI5 interface is required for NeoSpeech premium voices to be used and for TextAloud on Linux. SAPI5 download is free and is available at
  
[http://www.webaloud.com/files/Microsoft](http://www.webaloud.com/files/Microsoft) ... TTS-51.msi     

* Without this Textaloud does not find the voice data.

4. Install TextAloud using the WINE application installer. I needed no special selections during the install process.

5. Install the voices you want with the WINE app. installer .

* The Mozilla plug-in select read , & the copy auto-read from other apps only work from apps installed under WINE . With those not under WINE you must manually copy & paste to Textaloud in the WINE environment .

* enjoy, Karl Schueler

---

### Post by smakarl on 2012-09-27
Typo correction in the links ... the full line below is the link but did not ´ take ´.

[http://www.webaloud.com/files/Microsoft](http://www.webaloud.com/files/Microsoft) ... TTS-51.msi 

[http://www.nextup.com/phpBB2/viewtopic.php?t=3349](http://www.nextup.com/phpBB2/viewtopic.php?t=3349)      souce page

---

### Post by smakarl on 2012-10-11
Textaloud (Nextup.com) : NEWEST COMPREHENSIVE GUIDE 11 Oct. 2012

1. Install WINE. WINE provides a microsoft-free Windows API needed to run TextAloud on Linux. If WINE is not installed yet on your system, you will have to download and install appropriate package (download is free) from 
[http://www.WINEhq.com/site/download](http://www.WINEhq.com/site/download) 

See WINE User Guide for detailed instructions: 
[http://www.winehq.org/site/docs/wineusr-guide/index](http://www.winehq.org/site/docs/wineusr-guide/index) 

2. Configure WINE. Newest builds have graphic interface and are easy to configure. Just run 'winecfg' command to invoke the configuration applet. Some Windows versions are toucher than others.

Make sure WINE is set to use appropriate sound drivers. Older Linux distributions (kernel 2.4) typically used OSS drivers, while 2.6 kernels have switched to ALSA. Also set Acceleration to &#8216;Standard&#8217; and uncheck &#8216;Driver Emulation&#8217; box under audio settings tab. 

3.  Install the SAPI5 interface. SAPI5 interface is required for NeoSpeech premium voices to be used in TextAloud on Linux. SAPI5 download is free and is available at 

[http://www.webaloud.com/files/Microsoft](http://www.webaloud.com/files/Microsoft) ... TTS-51.msi   or
[http://www.webaloud.com/files/Microsoft-English-TTS-51.msi](http://www.webaloud.com/files/Microsoft-English-TTS-51.msi))

Also,  the Microsoft Sapi5 versions of Mary and Mike voices are available at ([http://www.nextup.com/files/MarMike5.msi](http://www.nextup.com/files/MarMike5.msi)) 

Note that these voices do not work with Windows Vista and later, so you probably should set your Windows emulation to XP before installing these.

4. Install TextAloud. 

5.  Launch TextAloud to verify it works ok with free Microsoft voices bundled with SAPI5 package and then exit. If you see the splash screen but TextAloud freezes at the initialization stage, you should try to change audio settings in WINE. The problem is that TextAloud just can&#8217;t find appropriate audio driver. So try switching to a different audio driver in WINE. 

6. Sttill problems? The sapi.dll sometimes fails to install. The sapi.dll should be here 

.wine/drive_c/´Program Files´/´Common Files´/´Microsoft Shared´/Speech

If sapi.dll is there, you can try registering the dll manually, using regsvr32. Run regsvr32 in the terminal window, like this:

$ regsvr32 sapi.dll
* I had the sapi.dll fine on 1 system others no (or I just did not find it (installed to wrong folder?). I emailed the sapi.dll to myself and put it in the correct folder. 
Then I ran  egsvr32 sapi.dll   .  ALL systems are running WINE (XP) Textaloud fine .

The sapi setup installs several dll's, and writes lots of registry entries. The sapi.dll file seems to be the only install faulure.

Other potential souces: Starting with Windows XP, Sapi 5 is built into the Windows operating system.  On actual XP system, you can do a low level reinstall of sapi5 using setup files in the folder c:\windows\inf (with a Windows XP install cd).  I don't see these setup files in windows\inf on Ubuntu. 
Make sure you're using XP emulation.  The dll is an XP dll, and the dll location is for XP only.  
The dll version and location is different in Vista / Win 7.

Contact Nextup.com tech support & ask them to email the sapi.dll you need to you so that you can patch it in.

7. Install the voices that you want NeoSpeech , Microsoft , AT&T, etc.

8. Launch TextAloud and enjoy using premium voices with this great text-to-speech application on Linux. 

* Note: Under WINE The full Textaloud features of click-to-speak in Firefox & auto speak from copy only function under WINE. If you wish to send text to Textaloud from locations outside of WINE you must manually copy & paste. Hopefully a Textaloud DEB package will be developed.

---

### Post by chis@ on 2012-11-29
[COLOR="Magenta"]For Linux, you can only install Cepstral voices, last time I checked on their web site.

If they want $$ from me, they better come up with a Linux install package, fully compatible.

Meanwhile, I stick with free Chromium iSpeech extension[/COLOR] O:)

---

