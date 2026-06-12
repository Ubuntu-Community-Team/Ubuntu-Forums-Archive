---
title: "Dynamic lighting in Wine"
date: 2012-04-08
forum: Wine
---

### Post by Drowz0r on 2012-04-08
Hello all

I'm using PlayOnLinux and Wine to play some steam games. So far everything has been working fine, with a bit of tweaking here and there.

Currently I am playing a Half Life mod called Cry of Fear and it uses dynamic lighting and something to do with the OpenGL.dll registery file.

Without this working, things like the flashlight in game don't work because they use dynamic lighting and this DLL file is for dynamic linking... or something
[I]
Essentially this is what I've tried without success:

Reinstalling
Running in WinXP mode
Running in Win7 mode
Replacing the DLL file
Running in game terminal commands to confirm it's enabled
Play in D3D mode
Play in OpenGL mode[/I]

I've noticed a section called "Install Packages" in the PlayOnLinux; Wine configuration bit.

Is there a certain package I need to install in order to make certain things work? I noticed there are many different files called d3dx10, d3dx11 etc...

Should I install all of these or will one over-write the other?

Additionally, some games like star trek online will install and launch fine but their initial launcher is partly web-based and will not allow me to click certain things. I think this is due to the lack of working flash in PoL but when I click to install packages such as: Flashplayer_ActiveX or Flashplayer it just crashes or gives an "access denied" error.

Can anyone help here?

I'm on Wine 1.3.37

Does it need an update? Software/update centre says it's fine.

---

### Post by nothingspecial on 2012-04-10
*Thread moved to **Wine**.*

---

### Post by Drowz0r on 2012-04-10
> **nothingspecial said:**
> *Thread moved to **Wine**.*

(Thanks)

---

I don't suppose anyone here can help? I can provide more information if required. Just let me know what you need.

Could it be that even though I'm telling the game to render in OpenGL mode, that wine is forcing it to render in D3D? Is there a way to check how wine renders?

---

### Post by dino99 on 2012-04-11
better to install a fresh clean 1.5.1 .wine , then read the game doc to know what it need.

---

### Post by Drowz0r on 2012-04-11
> **dino99 said:**
> better to install a fresh clean 1.5.1 .wine , then read the game doc to know what it need.

Hello.

Thanks for your info.

The thing is, when I install Steam through PlayOnLinux it automatically downloads this specific version of wine and when I install other things, it downloads a specific version for them too!

When looking in the Ubuntu software centre there are only versions 1.2 and 1.3?

The latest stable release according to the website is 1.4 while development (I assume unstable) release is 1.5.

Admittedly I'm still sorta new to Ubuntu. WineHQ doesn't seem to have a simple "download" area and software centre doesn't have it... so what should I do from here?

I tried following the instructions here: [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

And added the source "*ppa:ubuntu-wine/ppa*" but when I click to update my software I get this error (attached).

Any ideas? :c

---

### Post by Drowz0r on 2012-04-11
Ok I ignored the GUI way of doing things and simply did it through the terminal.

I've installed wine 1.4 and 1.5 versions but can only select the two I already had installed  which are 1.3.37 and 1.2.3.

Selectable here (attached).

---

### Post by Drowz0r on 2012-04-11
Ok so I was able to add 1.5.1 to PlayOnLinux through "tools -> Manage Wine Versions"

When I run it in 1.5.1 mode nothing changes though :c

Strangely I was then able to download the updates from the update manager too, but no change.

---

### Post by Drowz0r on 2012-04-11
Just tried installing CrossOver but there is some kind of bug with it at the moment after checking the forums. I installed it but it doesn't show in Dash Home or the Software centre or anywhere else... but it is showing as installed when I run the installer again.

Frustrated, I figured I'd stick with wine and uninstall CrossOver BUT I can't seem to get it off my machine.

It's worse than AOL!

---

### Post by Drowz0r on 2012-04-12
Got CrossOver working after the 3rd reinstall.

It constantly crashes though, a lot more than regular wine or PlayOnLinux with wine.

Seeing as it runs off wine in some way, I've made sure all my wine settings are for a 1024 desktop res but the windows only appear in a 640 (default game settings) resolution. I'm unable to change the res in game as it believes that is the limit of the desktop space. CrossOver itself doesn't seem to have any option of you changing it - the options are very limited.

---

### Post by Drowz0r on 2012-04-12
> **Drowz0r said:**
> Got CrossOver working after the 3rd reinstall.

It constantly crashes though, a lot more than regular wine or PlayOnLinux with wine.

Seeing as it runs off wine in some way, I've made sure all my wine settings are for a 1024 desktop res but the windows only appear in a 640 (default game settings) resolution. I'm unable to change the res in game as it believes that is the limit of the desktop space. CrossOver itself doesn't seem to have any option of you changing it - the options are very limited.

Well ok so I found another way to edit wine settings within CrossOver which are different to the "normal" wine settings.

Though I managed to get an emulated desktop at the correct resolution, the game still jumps back to 640.

---

### Post by Drowz0r on 2012-04-12
I only seem to be able to run the games correctly if I run them windowed, in a Windows emulated desktop mode... which creates a humongous amount of lag.

PlayOnLinux with Wine seems to perform a lot better than this. Is that normal? Considering CrossOver is pay to use.

---

### Post by Drowz0r on 2012-04-12
I think I'll quit on this and start  fresh thread a little later. I've uninstalled cross-over and installed some other things on my original PlayOnLinux/Wine thing.

Thanks for the help anyway all^

---

### Post by Drowz0r on 2012-04-21
Went back to POL and eventually got everything working through there instead, CrossOver didn't seem to work.

Dynamic lighting still an issue though.

---

