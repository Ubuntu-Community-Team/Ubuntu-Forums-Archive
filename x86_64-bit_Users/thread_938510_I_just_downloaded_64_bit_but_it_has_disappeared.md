---
title: "I just downloaded 64 bit but it has disappeared"
date: 2008-10-05
forum: x86 64-bit Users
---

### Post by kellyanne on 2008-10-05
Hi, I'm brand new to ubuntu and very new to Linux, have suse 10.3 now.

I downloaded the 64 bit ubuntu and its not on my system. I went to downloads in firefox and clicked open and its just doing nothing, I searched with beagle and it only has read me files. So right now am downloading the 32 bit from a different mirror and have fingers are crossed that it works 

But could anyone tell me how to get the file I already have downloaded?

Thank you

---

### Post by Eto_Demerzel on 2008-10-05
When you say you downloaded the 64 bit Ubuntu, do you mean you downloaded an .iso file?

Secondly, do you know to which folder you are saving downloaded files in Firefox? You can see it in the 'Main' tab in Edit->Preferences in Firefox. Could you go to that folder and check to see what you've downloaded?

---

### Post by kellyanne on 2008-10-05
Hi I downloaded the ISO from this site. I usually download to desktop but it asked me if wanted to download to nero so thinking it knew better than me....I did that.

It is not in nero on desktop in system anywhere, just read me documents it looks like from my beagle search.

---

### Post by kellyanne on 2008-10-05
Oh, and I'm using konquerer this time so maybe it will go through?

---

### Post by kellyanne on 2008-10-05
One other question...

When I do finally get this thing loaded up will I be asked to choose between KDE and Gnome? Would you recommend one over the other for a newbie? Gnome is what I have with suse, but don't know that I like it very much, but have never used Kde soo.....

---

### Post by Eto_Demerzel on 2008-10-05
> I usually download to desktop but it asked me if wanted to download to nero so thinking it knew better than me....I did that.

I'm not sure what you mean when you say that you downloaded to nero. I've not used it. 

Programs like nero would keep a tab on all the .iso files in your system. Perhaps it knows where the downloaded .iso file is. So try this: Open the nero program. Go to burn image (or a similar option) in Nero. It will ask you for the path to the .iso file to burn. The default path (in the dialog box that pops up) might have your .iso.

And about desktop environments:
When you finally install Ubuntu you get gnome as default. If you want KDE, you have to install Kubuntu. Of course, once you install either, you could install the other desktop environment and run that.

---

### Post by aoanla on 2008-10-05
> **Eto_Demerzel said:**
> I'm not sure what you mean when you say that you downloaded to nero. I've not used it. 

Almost certainly, they mean that there was an "open with Nero" option, which would presumably launch Nero to burn the ISO to suitable media on completion of the download?

In which case, I guess it's in /tmp somewhere.

---

### Post by Eto_Demerzel on 2008-10-05
Well, the simple solution would be to do this in command line

```
locate *.iso
```

If this doesn't turn up something, then its not on your system.

Also try something like

```
locate -i *.iso*
```

cause it could be named something like something.iso.PART etc. if the download is not complete.

---

### Post by howefield on 2008-10-05
> **kellyanne said:**
> One other question...

When I do finally get this thing loaded up will I be asked to choose between KDE and Gnome? Would you recommend one over the other for a newbie? Gnome is what I have with suse, but don't know that I like it very much, but have never used Kde soo.....
If you are downloading Ubuntu, then it will have the gnome desktop. Kubuntu has KDE. Although which ever CD you download and install, you will be able  to install other desktop environments via the package manager.

---

### Post by Yellow Pasque on 2008-10-06
If you've used GNOME and dislike it, try KDE/Kubuntu. The desktop environment is usually a matter of personal preference, not technical knowledge. GNOME and KDE satisfy most people, but other desktop environments exist for other niches.

---

