---
title: "Wanted: 64bit Multimedia Solution"
date: 2006-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Circleback on 2006-06-01
I am looking for a way to install all the codecs and what not for 64 bit Kubuntu. Is there any little script like bumps or automatrix out there that can help me? Ill probably be using Kaffiene and Kmplayer but need the correct xine and win32codec packages. Thanks.

---

### Post by Jason_25 on 2006-06-01
I normally install libxine-extracodecs on kubuntu and go from there.

---

### Post by davmor2 on 2006-06-01
just install all the gstreamer0.10 codecs and most media will just play.

---

### Post by kuja on 2006-06-01
I really doubt you're going to have much luck getting the win32 codecs working in 64bit - To Play things that require win32 codecs you're likely going to need a 32-bit player.

---

### Post by RAOF on 2006-06-01
[QUOTE=kuja]I really doubt you're going to have much luck getting the win32 codecs working in 64bit - To Play things that require win32 codecs you're likely going to need a 32-bit player.[/QUOTE]
Yes.  However, pretty much the only thing that you **need** the win32codecs for is WMV3/Windows Video 9/VC-1 (they're all the same thing, just different names).

**Everything** else has native, 64bit support.  Either in GStreamer (install gstreamer0.10-plugins-*, where * is: base, good, ugly, ugly-multiverse, bad, bad-multiverse), or Xine, with libxine-extracodecs.

---

### Post by Circleback on 2006-06-02
Great ill try that then. How about the libdvdcss package? Any sources for that?

---

### Post by Arathorn on 2006-06-02
Could you tell me where I can find libxine-extracodecs? I have multiverse enabled but it doesn't show up in Adept.

---

### Post by Terracotta on 2006-06-02
[QUOTE=Arathorn]Could you tell me where I can find libxine-extracodecs? I have multiverse enabled but it doesn't show up in Adept.[/QUOTE]
 libxine-extracodecs should be there, did you update after enabling multiverse?

For libdvdcss type:
sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
(chances are this last thing doesn't work on 64bit)
(googling after "libdvdcss2 deb" might help a bit further)

For more information on win32 and dvd:
[http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Arathorn on 2006-06-02
Yes I updated multiple times.
Could you take a look at this screenshot and tell me what's missing?
[http://img.photobucket.com/albums/v334/mfmeulenbelt/schermafdruk1.png](http://img.photobucket.com/albums/v334/mfmeulenbelt/schermafdruk1.png)

EDIT: Alright I'm a retard, linked to the wrong file.

---

### Post by RAOF on 2006-06-02
Might I recommend my humble AMD64 repository?  It's got the latest libdvdcss, built for AMD64 :)

[raof.dyndns.org/falcon](raof.dyndns.org/falcon), and the more available mirror, [http://ubuntu.moshen.de/](http://ubuntu.moshen.de/)

---

### Post by Chareos on 2006-06-02
Hi RAOF, I've installed your libdvdcss2_1.2.9-0.0ubuntu0_amd64.deb

Still I can't watch a dvd from Kaffeine (xne)
Am I missing something ?
(kubuntu breezy 64 bit here)


Thank you a lot for any help.

---

### Post by Terracotta on 2006-06-02
In your sources.list there's only the backports multiverse enabled

Put at the end of the third enabled repository multiverse like this:
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper universe MULTIVERSE

The backports are just repositories for programs that are/will be in Edgy Eft, so that you can enjoy newer version of programs without having the need to brake your system too hard, but I'd recommend to disable the backports repositories, chances are it still might brake the system (a bit).

Ps, if it still doesn't work you can send me a pm, I'm from Belgium so dutch is allowed :)

---

### Post by JoWilly on 2006-06-02
[QUOTE=RAOF]Might I recommend my humble AMD64 repository?  It's got the latest libdvdcss, built for AMD64 :)

[raof.dyndns.org/falcon](raof.dyndns.org/falcon), and the more available mirror, [http://ubuntu.moshen.de/](http://ubuntu.moshen.de/)[/QUOTE]

Yes !

/me taking the oportunity to thank you for this nice repo I have been using for some time now :)

---

### Post by Arathorn on 2006-06-15
I'm sorry for digging this thread up again, but I've been away from my computer since my last post and I still haven't got restricted formats working. RAOF, I have added your repository but libxine-extracodecs just doesn't show up, although I should have two repositories with that package now. Why doesn't it show up?

EDIT: Got it working now.

---

