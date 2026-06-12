---
title: "Feedback on the repo priority feature?"
date: 2008-06-21
forum: openSUSE and SUSE Linux Enterprise
---

### Post by 67GTA on 2008-06-21
I had loads of trouble with 10.3 with the opensuse and packman repos conflicting. For example, I installed all of the gstreamer packages from opensuse and could not get MP3 support. I realized that I needed packman's version of gstreamer for that. After adding the packman repo, and trying to install gstreamer, there were numerous conflicts where I had to choose to keep or get rid of conflicting packages. Does the new repo priority feature help with this aspect? If I were to set packman at 0(highest) and opensuse at 99(lowest), would it just install the highest version and not ask me 10 million questions?

---

### Post by some-guy on 2008-06-21
> **67GTA said:**
> I had loads of trouble with 10.3 with the opensuse and packman repos conflicting. For example, I installed all of the gstreamer packages from opensuse and could not get MP3 support. I realized that I needed packman's version of gstreamer for that. After adding the packman repo, and trying to install gstreamer, there were numerous conflicts where I had to choose to keep or get rid of conflicting packages. Does the new repo priority feature help with this aspect? If I were to set packman at 0(highest) and opensuse at 99(lowest), would it just install the highest version and not ask me 10 million questions?
that should be right

---

### Post by lxuser2008-X on 2008-06-27
> **67GTA said:**
> I had loads of trouble with 10.3 with the opensuse and packman repos conflicting. For example, [COLOR="Red"]I installed all of the gstreamer packages from opensuse and could not get MP3 support.[/COLOR] **I realized that I needed packman's version of gstreamer for that.**

No need to install any other repos outside the oss and non-oss (the official ones supported by the distro developers) to get MP3 playback in 10.3 -->. All you need to do is to install the **gst-fluendo-mp3** plugin found in the non-oss repo (on DVD or Online) and Amarok will play your mp3s.

Cheers

---

### Post by some-guy on 2008-06-27
These are the essential ones:
OSS
Non-OSS
Packman
and driver ones that might be needed

;)

---

### Post by 67GTA on 2008-06-27
I actually asked this before I got my opensuse DVD. I've got it installed with KDE 3.5.9, and the package management is awesome now compared to 10.3. I've found I don't need to mess with the priority feature. It seems like it automatically uses the highest version. It also resolves conflicts in the background unless it is an important one. Even then, the options are much easier to under stand than the clumsy conflict resolution dialogs in 10.3. I am very impressed.

---

### Post by some-guy on 2008-06-27
I set Packman to the highest, so that libxine1 always overrides xine-lib, as well as packman's gstreamer

---

