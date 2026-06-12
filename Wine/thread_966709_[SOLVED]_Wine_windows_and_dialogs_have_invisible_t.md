---
title: "[SOLVED] Wine windows and dialogs have invisible text"
date: 2008-11-01
forum: Wine
---

### Post by DJ_Peng on 2008-11-01
I upgraded to Intrepid a week or so ago and I grabbed a copy of CrossOver Pro thanks to the Lame Duck Challenge but in the last couple of days I'm unable to see any text in any Wine-based windows. You can see what I mean in the attached screenshot of winecfg.

I've been searching for hours all over the tubes trying to find a solution. I did complete uninstalls, and blew away any folder I could find, and I even moved the fonts I'm using on my desktop into the /windows/fonts folder. After blowing away the .wine folder yet again I launched winecfg from the Terminal and this is what I got
> peng:~$ winecfg
wine: created the configuration directory '/home/peng/.wine'
fixme:system:SetProcessDPIAware stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d6299f8, overlapped 0x7d6299dc): stub
fixme:shell:DllCanUnloadNow stub
wine: configuration in '/home/peng/.wine' has been updated.
peng:~$ I'm also attaching a screenie of my GNOME font settings. This is the current settings as reported by themeinfo:
> peng:~$ themeinfo

Ubuntu 8.10

  Emerald:               Mac4Lin Emerald Beta based on imetal
  GTK:                   Unity
  Font (Apps):           AquaBase 8.599609375
  Font (Terminal):       Monospace 12
  Icons:                 Mac4Lin_Icons_v1.0_RC
  Wall:                  ICHC-kitten-is-spooning-correctly.jpg

 Saturday 01 November 2008Anyone have any ideas what I'm missing?

---

### Post by DJ_Peng on 2008-11-02
Forgive me for posting again so soon after I started the thread but I wanted to add an additional screenie of the [Gentibus CD]("http://http://www.gentibus.com/index.html") window running under CrossOver Linux Pro.

I had hoped today's new version of human-theme with a fix for [bug #288851]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-artwork/+bug/288851") would have fixed it, but the screenie of Gentibus was shot after today's updates and a reboot for the new kernel updates.

---

### Post by Trap3d on 2008-11-02
what wine are you using? 1.1.7? if so downgrade to 1.0.1 if anything else i cant help yaz...

---

### Post by DJ_Peng on 2008-11-03
Sorry about that. I'm recently upgraded to 1.1.8pre+debug-1~ppa1, but I had already rolled back to 1.0.1-0ubuntu2 (intrepid) and still had the issue. I performed another roll back and the issue persists even with the default Intrepid human-theme (0.28.5). Still no help, although I do want to do a reboot to see if that changes anything.

I was thinking late yesterday (when I was afk for the night) that I had added some additional themes so later today I did a roll back to bare minimum themes installed and see if that helps after a reboot.

*ETA: Nope. No good. Not even with getting Compiz working again thanks to the nvidia-96 Alberto Milone submitted to intrepid-proposed.* :(

---

### Post by Trap3d on 2008-11-03
try googling googles ur best friend, and did you remove every single thing associated to wine in software sources? i had the thing with sound did a downgrade but it didnt work cuz i didnt delete wine stuff in software sources....

---

### Post by DJ_Peng on 2008-11-03
Yeah, I did that first off. I think it's an [Nvidia regression]("http://www.nvnews.net/vbulletin/showthread.php?t=122350") based on what I'm seeing. I may have to disable my Nvidia drivers and switch to the open source nv drivers to do some work in WINE until the bug gets squashed in the driver. But that may have to be a trial for another day since I'm on cooking duty today.

---

### Post by Trap3d on 2008-11-03
well im out of ideas good luck

---

### Post by DJ_Peng on 2008-11-03
Thanks for trying.

---

### Post by DJ_Peng on 2008-11-06
Thanks to a [comment on the bug]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107/comments/144") by Peter Remmers I saw an [entry on the WINE FAQ]("http://wiki.winehq.org/FAQ#head-dec980f6deabdb11b789c981bf49e10e70929eaf") that I missed somehow. I followed the instructions and I'm now 100% able to run WINE apps again.

For those who need a little more explicit instructions I edited my [blog post]("http://nancib.wordpress.com/2008/11/02/does-anyone-know-what-borked-wine-this-week/") to show how I resolved it.

Thanks to everyone who helped diagnose and resolve the issue.

---

### Post by aherbert01 on 2008-12-19
This fix worked partially for me.  It seems to have fixed my wine font issues, yet I am still experiencing the same problem with Picasa 3.  Anyone else having this problem?

I've attached a SS of the busted Picasa window alongside a normal winecfg.

Edit:  Apparently picasa has its own user.reg that needs the same line appended.  Oops.

---

### Post by DJ_Peng on 2008-12-20
Is there a reason you're running Picasa under WINE? There is a native Linux version available in their [Google Linux repos]("http://www.google.com/linuxrepositories/") so you can even install it with apt/synaptic.

---

### Post by ErikZane on 2009-03-05
> **DJ_Peng said:**
> Is there a reason you're running Picasa under WINE? There is a native Linux version available in their [Google Linux repos]("http://www.google.com/linuxrepositories/") so you can even install it with apt/synaptic.

For the record, I'm not entirely sure that Picasa is Linux native.  I installed Picasa using apt and I had the same problem.  Regardless, it does use a wrapper function to execute regedit to implement the same basic fix as is shown [here]("http://groups.google.com/group/Google-Labs-Picasa-for-Linux/tree/browse_frm/month/2008-11/30493efd84329635?rnum=101&_done=%2Fgroup%2FGoogle-Labs-Picasa-for-Linux%2Fbrowse_frm%2Fmonth%2F2008-11%3F") in entries 4 & 5.

---

### Post by DJ_Peng on 2009-03-06
After more investigation it looks like Picasa for Linux was in fact a modified Picasa for Windows with a WINE wrapper, same as with Google Earth. It actually makes me want to use it less as I find the label of being a Linux app somewhat misleading. Making it worse is that it seems to use it's own WINE installation rather than using any WINE install that a user already has, making it a real pain to tweak and maintain. If not for the less than wonderful alternatives for sharing images (Flickr is not an option IMO due to my kicking Y! to the curb last year) I'd forget even using Picasa. But that's just me. YMMV

---

