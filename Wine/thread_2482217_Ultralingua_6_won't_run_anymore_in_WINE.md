---
title: "Ultralingua 6 won't run anymore in WINE"
date: 2022-12-24
forum: Wine
---

### Post by Tom_ZeCat on 2022-12-24
Ultralingua 6 is a language dictionary that I use with dictionaries like English/German and English/French. I've always been able to get it to run perfectly under WINE. It was one of the few Windows apps, in fact, that I could run without a hitch via WINE.

That is, until I updated to Kubuntu 22.04. Now suddenly, try as I might, I can't see to get it to win. Previously, I had WINE 6.0 and Q4WINE installed. I uninstalled both of those and installed the Flatpak package of WINE. It still won't run.  I'm thinking maybe I have to revert to WINE 5.0? Or is there something I need to add which will make WINE run 32-bit apps? I had some old code for installing 32-bit capability to WINE, but it comes up as redacted.

I checked on WINEhq, and there's no info at all about Ultralingua 6, which in itself is strange.  When I first got Ultralingua 6 to work years ago, I posted a bunch of info about it at winehq.  

I THINK I might need to revert to WINE 5.0. Does anyone know? For now, I have it installed under VirtualBox with Windows 2000, which fortunately is light on resources.  But this is a major setback if I can't run Ultralingua 6 natively in Linux via WINE anymore. If anyone knows what I should do to get it running, please let me know. I would greatly appreciate any insight.  

In my notes, I have some command line code that's supposed to make sure WINE can run 32-bit programs.  It's as follows: 

```
1. sudo dpkg --add-architecture i386
2. sudo add-apt-repository ppa:wine/wine-builds
3. sudo apt-get update
4. sudo apt-get install --install-recommends winehq-devel

```

However, it would appear that code has been obsoleted.  I get an error that says it's depreciated.  

Some other WINE install code I have doesn't work.  It's as follows: 

```
wget https://dl.winehq.org/wine-builds/Release.key 
sudo apt-key add Release.key 
sudo apt-add-repository 'https://dl.winehq.org/wine-builds/ubuntu/'
```

With that, I get the following error: 

```
tom@tom-Inspiron-3650:~$ sudo apt-key add Release.key 
Warning: apt-key is deprecated. Manage keyring files in trusted.gpg.d instead (see apt-key(8)). 
OK
```

Another thing:
I do not have Ultralingua's setup program. I bought this thing years ago, we're talking maybe about 1995. All I have left is the install that was once on my Windows machine. I've still been able to manually install that under WINE in all previous versions of Kubuntu going back to 13.04.&#8203;  

I'm stuck, and would appreciate any suggestions on getting Ultralingua 6 to run in WINE.  Up till now, this application not only ran in WINE; it ran perfectly.  Before the update to 22.04, it ran as well in WINE as it runs in Windows.

---

### Post by Paddy Landau on 2022-12-25
On my system, I have no problem running a 32-bit Windows app. It was a fresh Ubuntu 22.04 installation, and all that I did extra was to install both winetricks and playonlinux from the standard repositories. Because I need stability, I didn't add any PPAs to pull these in; I just used the defaults. These two apps probably pulled in extra dependencies that made it work. Try that to see if it makes a difference.

Otherwise, you might be stuck with your VM, given that Ultralingua is no longer compatible. If you use a shared folder, it should be all right to use.

That's the problem with using apps that aren't designed for Linux. I wonder if one of the [Linux alternatives]("https://alternativeto.net/software/ultralingua/") would help?

---

### Post by Tom_ZeCat on 2022-12-25
> **Paddy Landau said:**
> On my system, I have no problem running a 32-bit Windows app. It was a fresh Ubuntu 22.04 installation, and all that I did extra was to install both winetricks and playonlinux from the standard repositories. Because I need stability, I didn't add any PPAs to pull these in; I just used the defaults. These two apps probably pulled in extra dependencies that made it work. Try that to see if it makes a difference.

Otherwise, you might be stuck with your VM, given that Ultralingua is no longer compatible. If you use a shared folder, it should be all right to use.

That's the problem with using apps that aren't designed for Linux. I wonder if one of the [Linux alternatives]("https://alternativeto.net/software/ultralingua/") would help?

I also use GoldenDict with several BGL dictionaries.  It works pretty well, but Ultralingua does a better job telling me the gender of French and German nouns.  

I'll try what you suggest.

---

### Post by Paddy Landau on 2022-12-26
> **Tom_ZeCat said:**
> … Ultralingua does a better job telling me the gender of French and German nouns.
Have you tried [Google Translate]("https://translate.google.com/")? That tells you the genders.
> **Tom_ZeCat said:**
> I'll try what you suggest.
Let us know what happens.

---

