---
title: "Picasa installed itself and used a part of WINE"
date: 2013-08-28
forum: Wine
---

### Post by Mark_in_Hollywood on 2013-08-28
Although deprecated for Linux, the Google product, Picasa, runs just fine on this computer. It does use some parts of Wine, obviously. I had not installed Wine prior to installing Picasa. I found a .deb that "just works". 

After 7 years, my public library, which uses OverDrive Media Console now has a way to install it's "Read" e-reader in Wine. I have borrowed a book on Apache-servers and want to have a look.

My question is: If I install Wine will it break the Picasa installation I have now? Is there actually a way to know this without a team of software/hardware engineer peering over my shoulder? As much as I would like a fully functional Wine, I would be crazy to break Picasa, which I use in a commercial context.

---

### Post by oldfred on 2013-08-28
I have not tried installing wine after the old Linux Picasa.

But I install wine and then download the newest Windows version of Picasa and install that.

This is how I install Picasa.

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install wine winetricks

Configure Wine to set up directory,  Applications, Wine, Configure

Then download picasa for windows
 ([http://dl.google.com/picasa/picasa39-setup.exe](http://dl.google.com/picasa/picasa39-setup.exe))
cd && wget [http://dl.google.com/picasa/picasa39-setup.exe](http://dl.google.com/picasa/picasa39-setup.exe)
Move it into .wine/drive_c/Program Files
wine picasa39-setup.exe

All photos are on another hard drive and a new install finds them but takes time.
I had to teach my wife to always export edited files to make sure we do not lose any edits as those are internal to Picasa and I have not copied it from one install to another.

---

### Post by Mark_in_Hollywood on 2013-08-28
Odd. When I did: sudo apt-get install wine winetricks, the apt-get reported them as both installed and newest versions. At the time I installed Picasa, about 2 months ago (re-install), as the terminal lines flew by, I saw no mention of Wine or Winetricks. Thanks, oldfred.

---

### Post by bayvista on 2013-11-27
Can you sign on to Google from Picasa? (Top  right hand corner)

---

### Post by oldfred on 2013-11-27
I just tried and whatever google app it is just opens a blank screen. But we do not have a Google account.

But we do not use that so never tried it before. And one processor goes to max and does not stop even after closing the sign on window. I have to close Picasa to get processor to get back to normal.

---

