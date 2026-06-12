---
title: "Looking for WMV codecs"
date: 2006-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by tomdkat on 2006-09-11
Ok, I've got VLC, Mplayer, Xine, and Totem installed for movie playback.  I've got some video clips in WMV format that none can play, with Xine and VLC coming the closest since they at least display a useful message.

Both players report not having codecs to decode the WMV 9 (WMV3) format.  Anyone know where I can get codecs?

Yes, these are adult oriented video clips.  :)

Thanks!

Peace...

---

### Post by Eggbanjo on 2006-09-11
i having the same type of difficulty with WMV, only VLC seems to play some of the clips and others just the sounds.

---

### Post by tomdkat on 2006-09-11
> **Eggbanjo said:**
> i having the same type of difficulty with WMV, only VLC seems to play some of the clips and others just the sounds.I feel your pain.  :)  Some of the WMVs I have work just fine in MPlayer or VLC but others just won't play.

The strange thing is before I installed Ubuntu on my new machine, I got Xine, built from source, to play the clips that I can't play now on my old Slackware-based 32-bit machine.  The problem there was the machine was so slow the playback was choppy but the video appeared.

Peace...

---

### Post by jamesford on 2006-09-11
the only way i know of is to install 32 bit mplayer and 32 bit w32codecs to go with it. theres a howto [here]("http://www.ubuntuforums.org/showthread.php?t=188974")

---

### Post by jeanbshp on 2006-09-11
Do you mean the w32codecs?  win32 binary codecs can be installed
thru the Synaptic Package Manager.  Just make sure that you've checked
all the repositories. Click on search and type in w32codecs.

---

### Post by Eggbanjo on 2006-09-11
installing totem (xine) cleared them all up for me ;)

---

### Post by Kilz on 2006-09-11
> **jeanbshp said:**
> Do you mean the w32codecs?  win32 binary codecs can be installed
thru the Synaptic Package Manager.  Just make sure that you've checked
all the repositories. Click on search and type in w32codecs.

They may be instalable with the 32bit Ubuntu version that way. But not the 64bit version.

---

### Post by tomdkat on 2006-09-11
> **Eggbanjo said:**
> installing totem (xine) cleared them all up for me ;)Ok, I'll give that a try.  :)  I thought I had installed the Xine engine for Totem but I might be mistaken.  I have YET to play a video clip with Totem.  We'll see if this will be my saving grace.  :)

Peace...

---

### Post by tomdkat on 2006-09-11
> **Kilz said:**
> They may be instalable with the 32bit Ubuntu version that way. But not the 64bit version.Ok, is there a solution for 64-bit versions, if the Totem/Xine install doesn't work?  Or am I stuck (at least for now)?

Peace...

---

### Post by kuja on 2006-09-11
You can fetch the 32-bit codecs package  manually, or grab from the mplayer website. The thing is, it won't work with a 64-bit player. You have to be using a 32-bit player to use the win32 codecs. I recommend following the link that Jamesford gave you.

---

### Post by jimmygoon on 2006-09-11
> **tomdkat said:**
> Ok, I've got VLC, Mplayer, Xine, and Totem installed for movie playback.  I've got some video clips in WMV format that none can play, with Xine and VLC coming the closest since they at least display a useful message.

Both players report not having codecs to decode the WMV 9 (WMV3) format.  Anyone know where I can get codecs?

_*** Yes, these are adult oriented video clips.  :)***_

Thanks!

Peace...

I think that Ubuntu:CE can help you with solving that little program of yours :roll: tsk tsk tsk [/sarcasm]

I'm kidding you know... Do you have 64bit? if so, I'm to the point where I just recommend install ubuntu-32 anyways... (edit: I just saw this was in the 64 bitsection ... I'm leaving it because I thought the U:CE bit was funny)

---

### Post by tomdkat on 2006-09-11
> **Eggbanjo said:**
> installing totem (xine) cleared them all up for me ;)
I just installed Totem-xine and I got the same WMV 9 message I got when running Xine directly.  :(

Oh well.  :)

Peace...

---

### Post by tomdkat on 2006-09-11
> **jimmygoon said:**
> I think that Ubuntu:CE can help you with solving that little program of yours :roll: tsk tsk tsk [/sarcasm]Well, I was hoping this forum would have helped with that problem of mine too.... the problem of NOT being able to watch my clips!  :D  

It's all good... ;)

Peace...

---

### Post by Kilz on 2006-09-12
> **jimmygoon said:**
> I think that Ubuntu:CE can help you with solving that little program of yours :roll: tsk tsk tsk [/sarcasm]

I'm kidding you know... Do you have 64bit? if so, I'm to the point where I just recommend install ubuntu-32 anyways... (edit: I just saw this was in the 64 bitsection ... I'm leaving it because I thought the U:CE bit was funny)

We are using Linux, some WMV 9 or Windows Media Video files will not play regardless of what version of Ubuntu you run. They have drm in them. The best player is the [32bit mplayer though]("http://www.ubuntuforums.org/showthread.php?t=188974") it will install to 64bit with this howto. It will show more wmv files that others. After installing it, click on a wmv file, chose open with other application, click at bottom "use a custom command" type in mplayer32.

---

### Post by tomdkat on 2006-09-12
> **Kilz said:**
> The best player is the [32bit mplayer though]("http://www.ubuntuforums.org/showthread.php?t=188974") it will install to 64bit with this howto.Thanks for the link!

Peace...

---

### Post by floydwaferfield on 2006-09-15
tomdkat, if your biggest problem is that you can't watch midget scat porn, or whatever fetish you're into, then maybe you need to take a deep breath and re-examine your life.

---

### Post by tomdkat on 2006-09-19
> **floydwaferfield said:**
> tomdkat, if your biggest problem is that you can't watch midget scat porn, or whatever fetish you're into, then maybe you need to take a deep breath and re-examine your life.Do you mean my biggest problem with Ubuntu or my biggest problem, in general?

If referring to my Ubuntu issues, it's not the biggest problem I've faced but one that's definitely on the list.

As for re-examining my life, I've taken your advice and taken the deep breath and determined midget scat porn is probably something I really wouldn't be in to.  Thanks for the help!  ;)

Peace...

---

### Post by fabertawe on 2006-09-20
Odd thing here... I have Mplayer, VLC and Xine (no Totem) installed. I can only play WMVs in Mplayer and it took ages to load until I installed 'xine-ui' (Xine Movie Player) which I installed when DVD playback stopped. I can play encrypted DVDs again but only in Xine and since installing that Mplayer loads instantly again!

Paul

---

