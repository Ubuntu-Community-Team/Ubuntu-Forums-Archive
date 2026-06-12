---
title: "World of Warcraft"
date: 2012-09-27
forum: Wine
---

### Post by LinXNut on 2012-09-27
Hey guys just a couple questions. I like World of Warcraft and I know that wine would be able to run it perfectly fine. However, I am using Windows 7 now, and my laptop can only easily handle "Fair" graphics in game. If I were to switch to Ubuntu, would the FPS be lower than it is in windows? Also, is there a way I can run it in Ubuntu to just try it without installing Ubuntu onto my laptop? 

Thanks,
LinXNut

---

### Post by sir.sargento on 2012-09-28
> **LinXNut said:**
> Hey guys just a couple questions. I like World of Warcraft and I know that wine would be able to run it perfectly fine. However, I am using Windows 7 now, and my laptop can only easily handle "Fair" graphics in game. If I were to switch to Ubuntu, would the FPS be lower than it is in windows? Also, is there a way I can run it in Ubuntu to just try it without installing Ubuntu onto my laptop? 

Thanks,
LinXNut

Hello,

I am not sure if you would be able to install wine and wow while using a Live version of Ubuntu... So I cannot help you there. But I can tell you that WoW runs as good on linux via wine as it did when I ran it on windows. For some people it require some tweaking and for others it works instantly with wine. I have had to use a few tricks from the ubuntu wiki myself to get WoW working pretty much flawlessly at times. The only time I ever have problems is when they release a big patch. Here is the wiki I was referring to. Hope it helps.

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Tony

---

### Post by yinkoo on 2012-09-29
i had the same issue trying wow to run properly on ubuntu. wine solution didn't work for me. now i gotta need to try some oracle vm, and get windows. 
but ..let me try some on wine .. hope your link would help.  ;)

---

### Post by cwwilson721 on 2012-09-29
Odds are, if your laptop uses Intel graphics at all, it would either run horribly slow, or not at all. There are SOME workarounds that SOMETIMES work, but... (Search this forum for "Intel+WoW" )

As for using a VM to run Windows then running WoW in it...

It might work.

But the framerates would be terrible. Using a VM is running another computer inside your computer, using up RAM, CPU, etc. Imagine running a Dodge Viper SRT-10 inside a Ford Escort. Yes, you would be able to sit in the seats, but...

---

### Post by yinkoo on 2012-09-30
i tried installation with wine and setup wow.  then i did some configuration. 
> $ gedit ~/.wine/drive_c/Program Files/World of Warcraft/wtf/Config.wtfbut config.wtf file shows some error in editing its file/ adding lines.  
> SET gxApi "opengl" my config file has nth inside. 

things done:  
winecfg   <ok>
extra dll <ok>
directx <ok>

wow is running. but don't see anything at all except hearing the sound. mine is ATI- VESA M92 graphics.

:(

---

### Post by cwwilson721 on 2012-09-30
Do you have the ATi Proprietary drivers installed?

---

### Post by yinkoo on 2012-09-30
yes. it's installed. any idea..

---

### Post by rdenton on 2012-10-05
I was having trouble getting WoW running properly since the Mists of Pandaria expansion.

I followed a guide a friend gave me and used the OpenGL api and it's working flawlessly!

[http://geebzor.com/tech/linux/wow-mists-pandaria-ubuntu-12/](http://geebzor.com/tech/linux/wow-mists-pandaria-ubuntu-12/)

---

### Post by holastickboy on 2012-10-06
I recommend installing the latest 1.5 series of WINE (with 64 bit support if you can).  From there, the easiest way is to copy the installation from a Windows drive, and it should work straight away (assuming that video drivers have been installed correctly).

I am using an AMD Phenom II quad core running at 3.4ghz, and an AMD Radeon 6850 OC'd to 1ghz, and find that there is a performance loss with WINE, but it's perfectly playable currently.  In fact, I have started recording my experience with it, as I am leveling a monk while on Linux 100% of the time (want to prove that you can play wow from beginning to end with Linux).  Just make sure to enable opengl rendering if you are an AMD video card user first!

---

### Post by yinkoo on 2012-10-06
guys .. it works perfectly now.  so cool playing on linux. 
i  re-installed eth on windows, copied the folder to linux, configured  > SET gxAPI “OpenGL”. wine works too . perfect !  you guys  are awesome :guitar:

---

### Post by cwwilson721 on 2012-10-06
> **holastickboy said:**
> I recommend installing the latest 1.5 series of WINE (with 64 bit support if you can).  From there, the easiest way is to copy the installation from a Windows drive, and it should work straight away (assuming that video drivers have been installed correctly).

I am using an AMD Phenom II quad core running at 3.4ghz, and an AMD Radeon 6850 OC'd to 1ghz, and find that there is a performance loss with WINE, but it's perfectly playable currently.  In fact, I have started recording my experience with it, as I am leveling a monk while on Linux 100% of the time[COLOR="Red"]*** (want to prove that you can play wow from beginning to end with Linux)***[/COLOR].  Just make sure to enable opengl rendering if you are an AMD video card user first!
I've bben playing on WoW/wine since the beginning ("Vanilla"). 

Most of the time, WoW/wine runs faster in OpenGL than Windows/D3D (at least, on my hardware).

But I've NEVER run it on ATi/AMD. I've always had a Nvidia card. Their Linux drivers are just plain better/faster/easier to use and install.

---

### Post by yinkoo on 2012-10-06
> **cwwilson721 said:**
> I've bben playing on WoW/wine since the beginning ("Vanilla"). 

Most of the time, WoW/wine runs faster in OpenGL than Windows/D3D (at least, on my hardware).

But I've NEVER run it on ATi/AMD. I've always had a Nvidia card. Their Linux drivers are just plain better/faster/easier to use and install.

yeh.. linux is faster. and ur link helps too.  ;)

---

