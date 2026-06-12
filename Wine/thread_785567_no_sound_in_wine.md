---
title: "no sound in wine"
date: 2008-05-07
forum: Wine
---

### Post by hatchet_lips on 2008-05-07
1.  im completely new to linux/ubuntu
2.  ive searched for an answer and cant find one thats up to date.
3.  when i watch flash based media in ubuntu it its all chopped up, real bad framerate.  to fix this i thought i would run firefox in wine.  it looks a lot better but it has no sound.

when i test sound in wine configuration i get an audio test failed error.  i only have ALSA checked.  hardware accel is full, bit rate if 44100, bits per sample is 16, driver emulation is unchecked.

im using wine 0.9.59 with ubuntu 8.04, loading up firefox 2 in wine.

i would post the massive mess that my terminal vomits (of which i can understand nothing) but i keep getting errors about having too many images when i try to post it.  i dont know why im even getting that error since i can find no BB or HTML code in the stuff im trying to post from terminal.

im pretty stuck at this point, any help would be greatly appreciated!!

---

### Post by Mushed on 2008-05-07
Have you checked this out? [http://ubuntuforums.org/showthread.php?t=785567](http://ubuntuforums.org/showthread.php?t=785567) 

But running Firfox in Wine isn't really a good idea. It would be much better just to figure out what the problem is in linux, instead of trying to figure out what is wrong with wine. There are a million bugs in wine.

---

### Post by cogadh on 2008-05-07
> **hatchet_lips said:**
> 1.  im completely new to linux/ubuntu
2.  ive searched for an answer and cant find one thats up to date.
3.  when i watch flash based media in ubuntu it its all chopped up, real bad framerate.  to fix this i thought i would run firefox in wine.  it looks a lot better but it has no sound.

when i test sound in wine configuration i get an audio test failed error.  i only have ALSA checked.  hardware accel is full, bit rate if 44100, bits per sample is 16, driver emulation is unchecked.

im using wine 0.9.59 with ubuntu 8.04, loading up firefox 2 in wine.

i would post the massive mess that my terminal vomits (of which i can understand nothing) but i keep getting errors about having too many images when i try to post it.  i dont know why im even getting that error since i can find no BB or HTML code in the stuff im trying to post from terminal.

im pretty stuck at this point, any help would be greatly appreciated!!

You are getting the "too many images" error because the forum is automatically converting some of the text from the error messages into smilies. You can get around that problem by using the "[CODE]" tags around the error message or by checking the "Disable smilies in text" box before submitting your post. 

As for your problem, it is probably due to a missing PulseAudio compatibility package, either pulseaudio-esound-compat or libasound2-plugins. The error message info would help confirm that.

> **Mushed said:**
> Have you checked this out? [http://ubuntuforums.org/showthread.php?t=785567](http://ubuntuforums.org/showthread.php?t=785567)
You do realize that you linked right back to this thread, don't you?

---

### Post by Mushed on 2008-05-07
lol fail. [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by hatchet_lips on 2008-05-07
> **Mushed said:**
> lol fail. [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

ive read this, and its how im currently set up.  i have another thread asking about getting flash to run pretty in ubuntu itself, but its not garnered much attention.  having my media run in linux would be ideal of course, but its not, and i dont know how to fix it.


also, cogadh, thanks for the help with posting.  im not in linux atm, so i may try posting the spew that wine gives me later.  i have both pulseaudio-esound-compat and libasound2-plugins installed, though i cant tell if they are having problems.  thanks for the help thus far!

---

### Post by hatchet_lips on 2008-05-08
sorry for the double post, but this is going to be long.

i used wine to load up firefox, tried playing a clip from hulu.com, and then closed firefox.  heres everything that terminal had to say about it:



bp@bp-desktop:~$ wine "C:\Program Files\Mozilla Firefox\firefox.exe"
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:iphlpapi:NotifyAddrChange (Handle 0x7dce8a08, overlapped 0x7dce89ec): stub
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0xb463dc)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:system:SetProcessDPIAware stub!
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:imm:ImmReleaseContext (0x10058, 0x7f028800): stub
err:ole:CoGetClassObject class {591209c7-767b-42b2-9fba-44ee4615f2c7} not registered
err:ole:CoGetClassObject class {591209c7-767b-42b2-9fba-44ee4615f2c7} not registered
err:ole:CoGetClassObject no class object {591209c7-767b-42b2-9fba-44ee4615f2c7} could be created for context 0x3
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:secur32:schan_FreeCredentialsHandle (0x7adfbbd0): stub
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:secur32:schan_FreeCredentialsHandle (0x7b65c298): stub
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:secur32:schan_FreeCredentialsHandle (0x7fcae370): stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:imm:ImmGetOpenStatus (0x7f028800): semi-stub
fixme:win:EnumDisplayDevicesW ((null),0,0x7f22ea14,0x00000000), stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x302a6480
fixme:ddraw:IDirectDrawImpl_GetScanLine (0x789a91b8)->(0x7f22ee14): Semi-Stub
fixme:d3d_surface:IWineD3DBaseSurfaceImpl_Blt Can't handle WINEDDBLT_ASYNC flag right now.
fixme:d3d:IWineD3DClipperImpl_SetClipList (0x7fca3888,(nil),0),stub!
err:clipboard:CLIPBOARD_CloseClipboard Failed to set clipboard.
bp@bp-desktop:~$ 


any help is really appreciated!!!  after several tweaks with linux by itself ive given up on getting flash media to play in an acceptable manner, so id really like to get sound working in wine as the video looks a lot better.

---

### Post by cogadh on 2008-05-08
First things first, lets get rid of those preloader error messages:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

I don't think it will fix the sound issue, but it may clear up some of that mess and make the whole troubleshooting process a little more manageable.

Also, those ntlm_auth errors should go away if you install the winbind package:
```
sudo apt-get install winbind
```

On a side note, this is at least the third or fourth time I've heard of someone having Flash performance problems in Ubuntu since the release of 8.04. I've always felt that Flash performance is perfectly fine in 7.10 (at least equal to the performance I get out of Windows). I may be jumping to conclusions here, but this could indicate a larger issue with 8.04 itself. I used 8.04 for about 24 hours before I decided it was not up to the standards I've come to expect from Ubuntu and went back to 7.10, this could be something to add to my list of reasons to stay with 7.10.

---

### Post by hatchet_lips on 2008-05-08
thanks for the quick reply cogadh, i really appreciate it.  in my searches to fix my problems i too have seen several people having issues with flash.  sadly, flash media makes up the largest part of my viewing entertainment, so its a real drawback for me as far as using 8.04.  ill try these things out, thanks again!




i followed your advice on the 2 things above and it fixed my sound!!  thanks a ton!  i still have errors though regarding ALSA, though im unable to make out what the problem is really.  maybe i dont have good drivers for my sound card?  im not sure.  heres what i get:



bp@bp-desktop:~$ wine "C:\Program Files\Mozilla Firefox\firefox.exe"
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:iphlpapi:NotifyAddrChange (Handle 0x7dcfea08, overlapped 0x7dcfe9ec): stub
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0xb463dc)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:system:SetProcessDPIAware stub!
err:ole:CoGetClassObject class {591209c7-767b-42b2-9fba-44ee4615f2c7} not registered
err:ole:CoGetClassObject class {591209c7-767b-42b2-9fba-44ee4615f2c7} not registered
err:ole:CoGetClassObject no class object {591209c7-767b-42b2-9fba-44ee4615f2c7} could be created for context 0x3
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:imm:ImmReleaseContext (0x1005a, 0x13b200): stub
fixme:secur32:schan_FreeCredentialsHandle (0x26691b0): stub
fixme:system:SystemParametersInfoW Unknown action: 108
fixme:secur32:schan_FreeCredentialsHandle (0x1f148a8): stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:imm:ImmGetOpenStatus (0x13b200): semi-stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33ea14,0x00000000), stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x302a6480
fixme:ddraw:IDirectDrawImpl_GetScanLine (0x1646900)->(0x33ee14): Semi-Stub
fixme:d3d_surface:IWineD3DBaseSurfaceImpl_Blt Can't handle WINEDDBLT_ASYNC flag right now.
fixme:d3d:IWineD3DClipperImpl_SetClipList (0x2207af0,(nil),0),stub!
fixme:imm:ImmGetDefaultIMEWnd (0xd0038 - (nil) 0x13b200 ): semi-stub
err:clipboard:CLIPBOARD_CloseClipboard Failed to set clipboard.




my sound problem is fixed as far as i can tell, so i dont care about all this as long as it works.  thanks again!

---

### Post by cogadh on 2008-05-08
Just an FYI, those "fixme" ALSA messages you are getting just indicate that you have a soundcard that is not capable of hardware sound mixing. Its not a big deal, as sound still works. I get stuff like that all the time with my Audigy LS sound card and I've just learned to ignore them.

One minor thing you might want to try doing differently that may eliminate a few more of those error messages is cd to the Firefox install directory and then run it with Wine:
```
cd ~/.wine/drive_c/Program\ Files/Mozilla\ Firefox/
wine firefox.exe
```
Most Windows applications like to be run from within the directory where they are installed, they're kind of picky that way.

---

### Post by ubuntu-freak on 2008-05-08
The libflashsupport package should fix the choppy, stuttery playback of Flash. Make sure you don't have other Flash packages installed and give Epiphany browser a try also. Bit extreme to run Firefox in Wine, especially as Wine doesn't support PulseAudio. Saying that, install pulseaudio-utils and see if that helps. Also, you can revert to ALSA by navigating to System > Preferences > Sound and selecting ALSA instead of Auto Detect. You will have to tell some apps in their preferences that you're now using ALSA. Reboot as well.
 
Nathan

---

### Post by cogadh on 2008-05-08
Is that a Hardy only package? On my Gutsy machine, that package name does not exist. There are several "libflash" packages (libflash-mozplugin, libflash-dev, etc.) but no "libflashsupport".

BTW - Wine doesn't need to support PulseAudio, since PulseAudio is ALSA compatible.

---

### Post by ubuntu-freak on 2008-05-08
> **cogadh said:**
> Is that a Hardy only package? On my Gutsy machine, that package name does not exist. There are several "libflash" packages (libflash-mozplugin, libflash-dev, etc.) but no "libflashsupport".

BTW - Wine doesn't need to support PulseAudio, since PulseAudio is ALSA compatible.

 
Yeah, it's a Hardy only package which adds PulseAudio support to the Adobe Flash plugin. Without it you experience jittery and poor playback, crashes etc.
 
Wine is currently unable to use the PulseAudio ALSA plugin, as far as I know.
 
Nathan

---

### Post by cogadh on 2008-05-08
As long as the PulseAudio ALSA compatibility package is installed and Wine is set to use ALSA, sound in Wine will work fine. At least thats the way it was in Gutsy, Hardy may be different now.

---

### Post by ubuntu-freak on 2008-05-08
> **cogadh said:**
> As long as the PulseAudio ALSA compatibility package is installed and Wine is set to use ALSA, sound in Wine will work fine. At least thats the way it was in Gutsy, Hardy may be different now.

 
Gutsy used the ALSA sound server, Hardy uses the PulseAudio sound server. Wine doesn't like the PulseAudio ALSA plugin.
 
Nathan

---

### Post by cogadh on 2008-05-08
Gutsy had PulseAudio available in the repositories. I installed it, removed ALSA, Wine still worked fine. It took quite  bit of work to make it happen (Pulse needed some very specific configuring), but it definitely worked. I've since moved over to Kubuntu and that still uses ALSA, so no worries about future PulseAudio problems.

EDIT - You know what? Now that I think about it, I may have actually resorted to using the OSS setting for sound in Wine when I was using PulseAudio. To be honest, I did my little Pulse experiment so long ago and tried so many things to get it working right with all my apps, I could be remembering what finally worked incorrectly.

---

### Post by ubuntu-freak on 2008-05-08
> **cogadh said:**
> Gutsy had PulseAudio available in the repositories. I installed it, removed ALSA, Wine still worked fine. It took quite  bit of work to make it happen (Pulse needed some very specific configuring), but it definitely worked. I've since moved over to Kubuntu and that still uses ALSA, so no worries about future PulseAudio problems.

EDIT - You know what? Now that I think about it, I may have actually resorted to using the OSS setting for sound in Wine when I was using PulseAudio. To be honest, I did my little Pulse experiment so long ago and tried so many things to get it working right with all my apps, I could be remembering what finally worked incorrectly.


I'm certain it doesn't like the ALSA plugin and doesn't have a native PulseAudio driver, the Wine devs aren't too interested in making one just yet either.
 
Do a Google search, but with the word "hardy" included, so you don't end up with old search results.
 
Nathan

---

### Post by hatchet_lips on 2008-05-09
i have libflashsupport installed.  i follwed your startup guide to the letter nathan and everything worked great (many thanks!!).  ive read and reread the troubleshooting section attached to your guide as well and nothing has helped.

i installed epiphany but flash plays back just as choppy in it as it does firefox.  i was playing around with it yesterday and i turned off all my desktop effects and i got a much better flash playback.  though even then it wasnt comparable to windows playback by a long shot.

i have a 512md ATI card.  if i can handle team fortress 2 at close to 150 fps surely i can have desktop effects and decent flash playback at the same time.  i thought maybe it was my video card drivers, but i checked them and they are the only ATI drivers i could find and they appear to be working properly.  id love to watch flash in a native environment, but using wine is the only way i get quality close to what i have in windows.

---

### Post by ubuntu-freak on 2008-05-09
> **hatchet_lips said:**
> i have libflashsupport installed.  i follwed your startup guide to the letter nathan and everything worked great (many thanks!!).  ive read and reread the troubleshooting section attached to your guide as well and nothing has helped.

i installed epiphany but flash plays back just as choppy in it as it does firefox.  i was playing around with it yesterday and i turned off all my desktop effects and i got a much better flash playback.  though even then it wasnt comparable to windows playback by a long shot.

i have a 512md ATI card.  if i can handle team fortress 2 at close to 150 fps surely i can have desktop effects and decent flash playback at the same time.  i thought maybe it was my video card drivers, but i checked them and they are the only ATI drivers i could find and they appear to be working properly.  id love to watch flash in a native environment, but using wine is the only way i get quality close to what i have in windows.

 
Flash playback in Linux isn't accelerated. I'm surprised you had to disable effects merely to improve Flash playback though, but ATI chipsets are giving some users headaches at the mo. How did you install your ATI driver? The Hardware Drivers manager or Envy?
 
Nathan

---

### Post by hatchet_lips on 2008-05-09
i used the hardware drivers manager.  when i first installed ubuntu thats what popped up and so thats what i installed.  ive seen envy mentioned in my search to improve flash playback.  is it worth looking into?  if so, do you know where i might be able to find a guide as to how to uninstall my current ATI drivers and reinstall them with envy?  it doesnt seem like something thats so common there would be several commands lying around for me to copy and paste into terminal like your media guide had.

---

### Post by go_beep_yourself on 2008-05-09
I think Pulseaudio and proprietary applications don't play nicely together. I can't have sound from two or more apps when one of them is closed source such as amarok and flash or skype and urban terror. I first have to close out of firefox (has the flash running) and then restart amarok for it to play a song in Ubuntu 8.04 with Pulseaudio.

---

### Post by ubuntu-freak on 2008-05-09
> **hatchet_lips said:**
> i used the hardware drivers manager.  when i first installed ubuntu thats what popped up and so thats what i installed.  ive seen envy mentioned in my search to improve flash playback.  is it worth looking into?  if so, do you know where i might be able to find a guide as to how to uninstall my current ATI drivers and reinstall them with envy?  it doesnt seem like something thats so common there would be several commands lying around for me to copy and paste into terminal like your media guide had.

 
Disable the driver in System > Administration > Hardware Drivers and reboot. There is a sticky thread in the Multimedia & Video forum which mentions Envy. Here is a link to the site though: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html).
 
Nathan

---

### Post by hatchet_lips on 2008-05-09
i did this and i let envy auto detect my hardware and install ATI drivers.  now when i boot into linux everything appears to be working normally as i log in.  once i get to my desktop though, i cant see anything.  i see my top and bottom panels, and i can see my transparent cube, but i see no meus or icons, but they are there.  i can click in their general area and i see menu bars drop down, but there are no words or anything.  its like im getting just half of my display or something.

needless to say ubuntu is unusable in this state, is there a way to revert the change i made?  or is there something else i should be trying at this point?

---

### Post by cogadh on 2008-05-09
EDIT - nvm, brain fart

---

### Post by ubuntu-freak on 2008-05-09
> **hatchet_lips said:**
> i did this and i let envy auto detect my hardware and install ATI drivers.  now when i boot into linux everything appears to be working normally as i log in.  once i get to my desktop though, i cant see anything.  i see my top and bottom panels, and i can see my transparent cube, but i see no meus or icons, but they are there.  i can click in their general area and i see menu bars drop down, but there are no words or anything.  its like im getting just half of my display or something.

needless to say ubuntu is unusable in this state, is there a way to revert the change i made?  or is there something else i should be trying at this point?

 
This is madness. Have you rebooted again? Can you see applications if you open them? Try and open the Terminal and type:
 
**metacity --replace** 
 
I think that should work.
 
Nathan
 
P.S. Use Alt F2 and type the command there if you have to. May be worth keeping effects off, until the next driver update.

---

### Post by hatchet_lips on 2008-05-09
> **reassuringlyoffensive said:**
> This is madness. Have you rebooted again? Can you see applications if you open them? Try and open the Terminal and type:
 
**metacity --replace** 
 
I think that should work.
 
Nathan

i rebooted several times hoping that it would work itself out but it didnt.

ive already removed envyng through recovery mode as detailed on the envy site.  do you think i should go back and try envy again and then use this metacity --replace command if i encounter the same problem?  i didnt try opening the terminal when my desktop lacked a face, so i dont even know if it works or not.


ExpertAnalysis, i have considered completely removing ubuntu and trying a fresh install.  this was my first install of linux ever and i intended it to be for learning purposes only.  id like to keep that as a last resort though, because ive made relatively no changes or tweaks to it and i dont feel that a fresh install would fix the problems.  though maybe thats just the pessimist in me.

---

### Post by ubuntu-freak on 2008-05-09
> **hatchet_lips said:**
> i rebooted several times hoping that it would work itself out but it didnt.

ive already removed envyng through recovery mode as detailed on the envy site.  do you think i should go back and try envy again and then use this metacity --replace command if i encounter the same problem?  i didnt try opening the terminal when my desktop lacked a face, so i dont even know if it works or not.


ExpertAnalysis, i have considered completely removing ubuntu and trying a fresh install.  this was my first install of linux ever and i intended it to be for learning purposes only.  id like to keep that as a last resort though, because ive made relatively no changes or tweaks to it and i dont feel that a fresh install would fix the problems.  though maybe thats just the pessimist in me.

 
Did you upgrade from Gutsy or just install Hardy fresh? You only had text and icons missing cos you have effects enabled. Disable them in System> Preferences > Appearance > Effects. Shame you uninstalled Envy so quick.
 
Nathan

---

### Post by hatchet_lips on 2008-05-09
this is a new hardy install.  ive never worked with ubuntu or linux before this.


i reinstalled envy and had it setup my ATI drivers again.  before rebooting i made sure effects were turned off completely.  when i booted i had the same trouble as before.  i used alt+F2 to input metacity --replace though i could see nothing that i was typing.  that worked, and it brought everyting back into view.  i check my hardware drivers manager and it shows my ATI driver as not being in use.  which is fine i thought, i assumed envy is running it or something.

but my video problems are worse now.  everything moves extrememly slow and choppy.  it acts like there are no video card drivers installed.  when i scroll through windows or move the windows themselves everything happens in big choppy chunks.

---

### Post by ubuntu-freak on 2008-05-09
> **hatchet_lips said:**
> this is a new hardy install.  ive never worked with ubuntu or linux before this.


i reinstalled envy and had it setup my ATI drivers again.  before rebooting i made sure effects were turned off completely.  when i booted i had the same trouble as before.  i used alt+F2 to input metacity --replace though i could see nothing that i was typing.  that worked, and it brought everyting back into view.  i check my hardware drivers manager and it shows my ATI driver as not being in use.  which is fine i thought, i assumed envy is running it or something.

but my video problems are worse now.  everything moves extrememly slow and choppy.  it acts like there are no video card drivers installed.  when i scroll through windows or move the windows themselves everything happens in big choppy chunks.

 
Forget Envy then, seems to be more trouble than it's worth, with your chipset at least. I don't understand why Flash was so bad for you anyway, it's not accelerated for anyone in Linux, but performs okay for the most part. Make absolutely certain that you have libflashsupport installed. Do you have any sound issues at all? In general I mean. Did standard video streams play okay previously?
 
Nathan

---

### Post by hatchet_lips on 2008-05-10
ive double check libflashsupport several times, and reinstalled it all at least twice.  the only sound issue ive had was in wine and that got sorted.  when i first installed ubuntu i installed whatever flash player stuff ubuntu suggested.  it was the plugin that gave me silver play buttons on all media.  i believe flash had issues then because i went back through and located your guide and followed it.  it made general surfing of the web smoother and more enjoyable, but flash was no better.  any video ive ever streamed from the net from any site has had the same choppiness.  ive not tried playing anything from the computer itself though.  i dont watch movies on my computer so that was never a concern for me.  as far as i can remember ive had issues with flash since i installed ubuntu.

---

### Post by ubuntu-freak on 2008-05-10
> **hatchet_lips said:**
> ive double check libflashsupport several times, and reinstalled it all at least twice.  the only sound issue ive had was in wine and that got sorted.  when i first installed ubuntu i installed whatever flash player stuff ubuntu suggested.  it was the plugin that gave me silver play buttons on all media.  i believe flash had issues then because i went back through and located your guide and followed it.  it made general surfing of the web smoother and more enjoyable, but flash was no better.  any video ive ever streamed from the net from any site has had the same choppiness.  ive not tried playing anything from the computer itself though.  i dont watch movies on my computer so that was never a concern for me.  as far as i can remember ive had issues with flash since i installed ubuntu.

 
Check if swfdec-mozilla, or any Gnash package are installed. Someone else I helped said Synaptic still showed swfdec as installed, despite executing my purge command. Purging flashplugin-nonfree and installing it manually may help also. That's all you can do now, unless you can find an older version of Flash somewhere. 
 
Nathan

---

