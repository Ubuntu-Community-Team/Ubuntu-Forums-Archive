---
title: "Distro Differences?"
date: 2008-09-01
forum: Wine
---

### Post by fepple on 2008-09-01
Hello,

Several of us have been using Wine to play Warhammer Online. Until recently it worked fine with 1.1.2 on Ubuntu (Hardy). Then the games patcher was updated and it no longer runs instead it hangs without returning when first run. This problem seems specific to Ubuntu as it still works for others.

I've tried this on two separate machines and had the same problem after the patcher updated, another Ubuntu user has had the same problem.

I've tried Wine 1.1.2, 1.1.3 and various installs from GIT but all have the same problem.

I've then tried the same install of the game under Gentoo and it works (using 1.1.3 or 1.1.0).

Is there something specific to the Distro like default wine config or dependencies that could be causing this problem?

Thanks,
Matt


(this is a pea roast of [this thread]("http://forum.winehq.org/viewtopic.php?t=2166") that so far has gone unanswered)

---

### Post by jacksaff on 2008-09-01
Try launching it from the terminal and have a look at the errors that wine spits out.

---

### Post by fepple on 2008-09-01
The problem is it seems to be looping or deadlocked.  All I get is

> $ wine warpatch.exe 
fixme:shdocvw:PersistStorage_InitNew (0x136188)->(0x7c0da0)


Then the patcher never appears.  Its showing activity in top but i've left it all night and it never appears

---

### Post by aoanla on 2008-09-01
Does Gentoo use PulseAudio, or is it still using ALSA?

It might be worth trying other distros, to see if you can narrow the issue down.

---

### Post by Drk Guy on 2008-09-01
I think you've never heard of Gentoo before, because of Gentoo's about choices, you can choose to run either ALSA or PulseAudio, so it's much of a user decision.

I've used Gentoo for some days, made custom install from stage3, but it was very un-pleasant to compile everything off, so i got back to ubuntu.

---

### Post by fepple on 2008-09-01
I had both setup to use ALSA, but this is just getting the patcher to work which doesn't require sound.  In Gentoo the patcher would work even when I didn't have ALSA setup up

---

### Post by aoanla on 2008-09-01
> **Drk Guy said:**
> I think you've never heard of Gentoo before, because of Gentoo's about choices, you can choose to run either ALSA or PulseAudio, so it's much of a user decision.

In fact, I've installed Gentoo before, and I don't recall ever setting up PulseAudio with it. Of course, yes, Gentoo is all about choices (and spending ages compiling everything), but that doesn't mean that PulseAudio is assumed to be the default sound solution. Since Wine has had problems with PulseAudio before, it seemed logical that people using ALSA in Gentoo would be a possible cause of the difference in effectiveness.
In addition, I'm not sure if your reply was deliberately phrased in a slightly condescending manner, but it was. You might want to watch that.

Are people installing Wine in Gentoo building from source, or are you pulling in prebuilt versions?

---

### Post by Ferrat on 2008-09-01
> **aoanla said:**
> In fact, I've installed Gentoo before, and I don't recall ever setting up PulseAudio with it. Of course, yes, Gentoo is all about choices (and spending ages compiling everything), but that doesn't mean that PulseAudio is assumed to be the default sound solution. Since Wine has had problems with PulseAudio before, it seemed logical that people using ALSA in Gentoo would be a possible cause of the difference in effectiveness.
In addition, I'm not sure if your reply was deliberately phrased in a slightly condescending manner, but it was. You might want to watch that.

Are people installing Wine in Gentoo building from source, or are you pulling in prebuilt versions?

Don't know about Warhammer Online but WINE still has a few issues with pulseaudio.

---

### Post by aoanla on 2008-09-01
Indeed so. Although, wine 1.1.3 claims to include some fixes for PulseAudio support, so...

---

### Post by FrozenFOXX on 2008-09-17
I'm having this same issue myself.  I don't have PulseAudio installed, just running Kubuntu 8.04 64-bit.  Even followed up on the Wine appdb page and got it to get past the persiststorage error (used wineprefix to point to WAR's directory) but unfortunately it then starts throwing ELF and similar errors.  Will be able to post more when I'm home, but apparently this is a wider issue that affects Ubuntu.

---

### Post by oedipuss on 2008-09-19
How did you get past that???
I tried starting the patcher with wineprefix pointing to where it is, but it's just the same behaviour...

---

