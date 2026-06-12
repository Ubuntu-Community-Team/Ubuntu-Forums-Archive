---
title: "Does AptOnCD work?  Can't find a solution"
date: 2009-08-08
forum: x86 64-bit Users
---

### Post by Jazmac on 2009-08-08
Maybe I'm not understanding what APTonCD is supposed to do.  I had to reinstall Ubuntu and found APTonCD.  Sounds like it will back up all my settings and installed packages and burn them to CD.  Then all I need to do is after I reinstall Ubuntu, I run the restore from APTonCD, mark all updates from the the package manager and I'm back to where I was before my reinstall.

That isn't the case.

What is APTonCD is supposed to do?  I'm still noobish and this is probably a tool more experienced Ubuntu users have long since abandoned.

How does it work?

-JazMac

---

### Post by Yellow Pasque on 2009-08-08
IIRC, APTonCD creates a software repository on a CD from the .deb packages you have installed.

I don't think it restores all of your custom settings and configuration though, especially per-user settings. I don't think it backs up your desktop wallpaper, Firefox bookmarks, Pidgin buddies, or anything like that.

---

### Post by theozzlives on 2009-08-08
It's to use when installing Ubuntu without an internet connection.

---

### Post by Jazmac on 2009-08-09
> **Temüjin said:**
> IIRC, APTonCD creates a software repository on a CD from the .deb packages you have installed.

I don't think it restores all of your custom settings and configuration though, especially per-user settings. I don't think it backs up your desktop wallpaper, Firefox bookmarks, Pidgin buddies, or anything like that.

Oh ok.  I got the impression it would back up my settings and installed packages.  I read this really wrong.  Hmmm. ok.  

I'll just rebuild manually.  More practice for me.

Thanks

-JazMac

---

### Post by Cavsfan on 2009-10-25
> **Jazmac said:**
> Oh ok.  I got the impression it would back up my settings and installed packages.  I read this really wrong.  Hmmm. ok.  

I'll just rebuild manually.  More practice for me.

Thanks

-JazMac

I believe it does backup your installed packages, just not settings.
I used it a couple of times when I was more noobish than I am now (however I am still a noob, just a little less :|) and it worked great!

Now I have another issue with AptOnCD. I was wanting to "start over" with it.
I reformatted the DVD that it had used and uninstalled it. but when I try to re-install it
with Synaptic, it wants me to put in the DVD that I had created with it before. ](*,)

I tried using a copy command 
sudo cp /var/cache/apt/archives ~/Desktop/bacup
That I found on this thread [http://ubuntuforums.org/showthread.php?t=1300029&highlight=aptoncd](http://ubuntuforums.org/showthread.php?t=1300029&highlight=aptoncd) , but kept getting this error 
cp: omitting directory `/var/cache/apt/archives'
While trying everything I could think of.

Also, with AptOnCD supposedly uninstalled, when I click on Places and then Home Folder, it still shows AptOnCd listed in the left pane under my drives and above Trash.

Anyone have a clue as to what I need to do to either get AptOnCD back to it's starting point (like I just installed it) or get this copy command working?
Thanks in advance!

---

